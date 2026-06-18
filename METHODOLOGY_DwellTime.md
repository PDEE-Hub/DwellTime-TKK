# Methodology: Dwell Time Analysis — ทกท. (v2)

อ้างอิงกฎจาก `SKILL_DwellTime_TKK.md` (ผู้ใช้เขียน) — เอกสารนี้อธิบาย **วิธีคิด/วิธีคำนวณ** ที่ใช้จริงใน `Dwell_Time_Dashboard_2567-2569.html` และข้อมูลที่ส่งต่อให้ pipeline การเงิน (pat-data-analyst → pat-narrative-writer → Fintrix / Monthly Report)

โครงสร้างเอกสารแยกเป็น 2 ส่วนตามจุดประสงค์การใช้งาน — **Part A ใช้งานจริงตอนนี้** (สนับสนุนการเงิน) **Part B เก็บไว้สำหรับอนาคต** (ด้าน operation) ตามที่ตกลงกันไว้

---

## Part A — ใช้สนับสนุน Financial Dashboard / Monthly Report (ใช้งานจริงตอนนี้)

### A.1 แหล่งข้อมูล

ไฟล์ดิบ 7 ไฟล์ ครอบคลุม ก.ค.2565 – เม.ย.2569 (~2.79 ล้าน record):

| ไฟล์ | ช่วง |
|---|---|
| `DwellTimeJul2022-Feb2024_Import.xlsx` / `_Export.xlsx` | ก.ค.2565 – ก.พ.2567 |
| `DwellImportMarch2024_September2025.xlsx` / `DwellExportMarch2024_September2025.xlsx` | มี.ค.2567 – ก.ย.2568 |
| `DwellImport_Export_Octorber2025_April2026.xlsx` | ต.ค.2568 – เม.ย.2569 |
| `สรุป Dwell.xlsx` | ภาพรวมรายเดือนย้อนถึงปี 2560 (ใช้เป็น baseline ระยะยาวเสริม) |

คอลัมน์หลักที่ใช้: `dwell` (จำนวนวัน, คำนวณมาแล้วในระบบ TOS), `time_out` (ใช้ตรวจ batch artifact), `category` (IMPRT/EXPRT)

### A.2 Segmentation 3 ชั้น (กฎหลัก — ต้องทำก่อนคำนวณ KPI ใดๆ)

```
Express  = dwell ≤ 1 วัน         → แยกดูเป็น best-practice signal เท่านั้น ไม่รวมใน KPI หลัก
Normal   = dwell 2-30 วัน        → ✅ ใช้เป็นฐานคำนวณ mean/median/p90 ของ KPI หลักเสมอ
Anomaly  = dwell > 30 วัน        → แยกวิเคราะห์ ไม่รวมใน mean/median ของ KPI หลัก
```

**เหตุผล:** ถ้าเอา record ทั้งหมดมาเฉลี่ยตรงๆ ค่าเฉลี่ยจะถูกบิดเบือนทั้งสองด้าน — Express (เยอะและเร็ว) ดึงค่าเฉลี่ยลง ส่วน Anomaly (น้อยแต่ยาวมาก เช่น ตู้ค้าง 1,000+ วัน) ดึงค่าเฉลี่ยขึ้น สูตรเดิม (v1) ที่ใช้ "ตัด record >90 วันออกแบบเดียว" ยังปนทั้ง Express และบาง Anomaly (31-90 วัน) เข้าไปในค่าเฉลี่ย ทำให้ตัวเลขคลาดเคลื่อนจาก skill baseline ที่มีอยู่แล้ว (FY69: Import 5.17 / Export 6.57 วัน)

### A.3 Batch-timestamp detection (กรอง artifact ออกจาก Anomaly)

```python
suspicious = big.groupby('time_out').size().reset_index(name='count')
suspicious = suspicious[suspicious['count'] > 5]
```

ถ้าตู้หลายใบ (ในที่นี้ใช้ threshold >5 ใบ) มี `time_out` ตรงกันเป๊ะถึงระดับวินาที → เป็น system close-out / batch event ไม่ใช่ dwell จริงของตู้นั้น ต้องแยกออกจากการตีความ "Anomaly" ก่อนสรุปว่าผิดปกติจริง

**ผลตรวจรอบนี้ (v2):** เจอ cluster ใหญ่กว่าที่ skill เดิมระบุไว้ (2 จุด, 77 ตู้) เช่น 2026-01-31 08:05 (438 ตู้), 2023-09-30 16:10 (371 ตู้) — **ยังไม่สรุปว่าทั้งหมดเป็น artifact จริง** เพราะบางจุดอาจเป็นตู้ลงเรือพร้อมกันจริง (ระบบ gate scan ครั้งเดียวทั้งล็อต) ต้องให้ทีม yard operation ยืนยันเพิ่ม — **ไม่กระทบ KPI หลัก** เพราะ batch ที่เจอทั้งหมดอยู่ใน Anomaly tier (>30 วัน) ซึ่งไม่ถูกใช้คำนวณ mean/median ของ Normal segment อยู่แล้ว

### A.4 นิยามช่วงเวลา Baseline vs Recent

```
Baseline = ก.ค.2565 – ธ.ค.2567   (ก่อนที่ Fintrix สังเกตเห็น margin/ค่าซ่อมเปลี่ยน)
Recent   = ม.ค.2568 – เม.ย.2569  (ช่วงที่การเงินเริ่มเห็น pattern)
```
ตัดเดือน **ก.พ.2567 ออกจากทั้งสองช่วง** เพราะข้อมูลไม่ครบเดือน (มีแค่ 1-2 วันแรก)

### A.5 ผลลัพธ์ปัจจุบัน (Normal segment, ตัด batch/partial แล้ว)

| | Baseline | Recent | เปลี่ยนแปลง |
|---|---|---|---|
| Import mean | 5.16 วัน | 5.71 วัน | +10.7% |
| Import median | 4 วัน | 4 วัน | 0% |
| Export mean | 5.33 วัน | 5.90 วัน | +10.7% |
| Export median | 5 วัน | 5 วัน | 0% |

**สิ่งที่เปลี่ยนจาก v1:** ตัวเลข % เปลี่ยนแปลงลดลงจาก v1 (Import +12.0%/+33.3% median) เป็น v1 ใช้ filter หยาบที่ทำให้ median ขยับเกินจริง — ตัวเลข v2 นี้น่าเชื่อถือกว่าเพราะใช้ segmentation ที่ตรงกับนิยามของ skill ที่ผ่านการตรวจสอบมาก่อนแล้ว **ทิศทางเดียวกัน (dwell สูงขึ้นจริงทั้งคู่) แต่ขนาดน้อยกว่าที่ v1 รายงานไว้**

### A.6 Threshold สีสำหรับ Score Strip (ใช้ตามที่ skill กำหนด)

```
Import:  ≤5.5d 🟢 ปลอดภัย | 5.5-6.5d 🟡 พึงระวัง | >6.5d 🔴 อันตราย
Export:  ≤7.0d 🟢 ปลอดภัย | 7.0-8.0d 🟡 พึงระวัง | >8.0d 🔴 อันตราย
Warehouse Intensity (>7d%): <15% 🟢 | 15-20% 🟡 | 20-25% 🟠 | >25% 🔴
```

### A.7 ข้อจำกัดที่ต้องระบุไว้ทุกครั้งที่ใช้ตัวเลขชุดนี้

- ตัวเลข trend ยาว (2565-2569) เป็นการรวมข้อมูลจาก **คนละไฟล์ต้นทาง 3 ชุด** — แม้ schema ตรงกันแต่ระบบ source อาจมีคุณภาพต่างกันเล็กน้อยในแต่ละช่วง (ดู A.1 และ data quality notes ใน dashboard)
- เป็น **trend ระดับเดือน** เหมาะกับการอธิบาย narrative การเงินรายเดือน/รายปีงบ ไม่เหมาะกับการใช้ฟันธงเหตุการณ์ระดับวัน/สัปดาห์ (ต้องใช้ Part B สำหรับนั้น)

---

## Part B — เก็บไว้สำหรับงานด้าน Operation ในอนาคต (ยังไม่ทำตอนนี้)

ส่วนนี้คือสิ่งที่มีอยู่แล้วใน `SKILL_DwellTime_TKK.md` และ `DwellTime_TKK_Dashboard_1.html` ที่ผู้ใช้ทำไว้ก่อนหน้า — **ไม่ได้ลบหรือแก้ไข** เก็บไว้เป็น reference เผื่อแยกทำเป็น initiative ด้าน operation ในอนาคต:

- **Time-of-day analysis** — "Seam Effect" ที่ 08:00 (ช่วงเปลี่ยนกะ dwell สูงผิดปกติ 7.49 วัน)
- **Day-of-week analysis** — "Weekend Penalty" hypothesis (ตู้เข้าพฤหัส-ศุกร์มีโอกาส "นอน" ผ่านเสาร์-อาทิตย์)
- **Operator/shipping-line prefix ranking** — เทียบ performance ระหว่าง TSSU/WHSU/...TRHU/TWCU
- **Slot utilization & throughput efficiency** — สมมติฐาน capacity ลาน 20,000 TEU
- **Revenue opportunity narrative** — escalating fee structure, "คลังสินค้ากลางกรุงเทพ", rehandling cost ที่ซ่อนอยู่
- **Research agenda ที่ skill ระบุไว้** — ต้องการ customs clearance timestamp, container status history, vessel schedule, consignee data เพื่อตอบคำถามเชิงลึกกว่านี้

**เมื่อจะแยกทำ Part B ในอนาคต:** ใช้ raw data ชุดเดียวกันได้เลย (ไม่ต้องดึงใหม่) แต่ต้องตัดสินใจก่อนว่ากลุ่มผู้ใช้ปลายทางคือใคร (ทีม yard operation หรือผู้บริหารท่า) เพราะ output ที่เหมาะกับแต่ละกลุ่มต่างกัน (dashboard เชิงปฏิบัติการ vs slide เชิงนโยบาย)

---

*Version 2.0 — มิถุนายน 2569 · อ้างอิง SKILL_DwellTime_TKK.md เป็นแหล่งกฎหลัก*
