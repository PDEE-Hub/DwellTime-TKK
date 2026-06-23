# 📝 INFOGRAPHIC IMPROVEMENTS — DETAILED SPECIFICATION
## Version: DRAFT (รูป r่างตัวอย่าง — ยังไม่ใช่ final design)

---

## 🎯 REQUIREMENT 1: DWELL TIME — Add FY68

### **Current State:**
```
Side-by-side comparison:
┌─────────────┬──────────────┐
│ ปีฐาน       │ ตอนนี้       │
│ FY65-67     │ FY69         │
└─────────────┴──────────────┘
```

### **Requested State:**
```
3-way comparison:
┌─────────────┬──────────────┬──────────────┐
│ ปีฐาน       │ ปีที่แล้ว    │ ตอนนี้       │
│ FY65-67     │ FY68         │ FY69         │
├─────────────┼──────────────┼──────────────┤
│ Import:     │ Import:      │ Import:      │
│ 5.18 วัน    │ 5.70 วัน     │ 5.72 วัน     │
│             │ +0.52d       │ +0.54d       │
│             │ (+10.0%)     │ (+10.4%)     │
│             │              │              │
│ Export:     │ Export:      │ Export:      │
│ 5.37 วัน    │ 6.28 วัน     │ 5.92 วัน     │
│             │ +0.91d       │ +0.55d       │
│             │ (+16.9%)     │ (+10.2%)     │
└─────────────┴──────────────┴──────────────┘
```

### **Visual Approach:**
- Option A: 3 side-by-side boxes (color gradient: gray → yellow → red)
- Option B: 3 line charts (one for Import, one for Export) showing progression
- **Recommended:** Option A (easier to scan)

### **Data Points Needed:**
```
FY65-67 (Base):  Import 5.18d, Export 5.37d ✅
FY68:            Import 5.70d, Export 6.28d ✅
FY69:            Import 5.72d, Export 5.92d ✅
```

### **Narrative Message:**
```
"ตู้ค้างเฉลี่ยเพิ่มขึ้นทีละนิดตั้งแต่ FY68
ปี 68 พุ่งขึ้นชัด (Export เพิ่มถึง +16.9%)
ปี 69 ค่อนข้างคงตัว (แต่ยังสูงกว่าปีฐาน)"
```

---

## 🎯 REQUIREMENT 2: DISTRIBUTION SHIFT — Add FY68

### **Current State:**
```
Stacked bar: FY65-67 baseline vs FY69 current (2 bars)
```

### **Requested State:**
```
Stacked bars: FY65-67 baseline | FY68 | FY69 (3 bars, progression)

FY65-67  ███████████ [Green ≤7d: 45%] ██ [Yellow 8-14d: 30%] █ [Red 15-30d: 15%] [Dark Red >30d: 10%]

FY68     ██████████ [Green: 42%] ███ [Yellow: 32%] ██ [Red: 18%] █ [Dark Red: 8%] ← Starting to shift

FY69     ██████████ [Green: 40%] ██ [Yellow: 28%] ██ [Red: 17%] ██ [Dark Red: 15%] ← 4.2× growth
                                                                          ↑
                                                                    THIS GREW
```

### **Visual Approach:**
- Vertical stacked bars (FY65-67 | FY68 | FY69)
- Clear color legend: Green/Yellow/Orange/Red = severity
- Callout box showing >30d growth: "10% → 8% → 15%" = "4.2× increase"

### **Data Points Needed:**
```
Dwell brackets (% distribution) for both Import & Export:
  FY65-67: [%], [%], [%], [%], [%], [%], [%] ✅ (from v5 file)
  FY68:    [%], [%], [%], [%], [%], [%], [%] ⚠️ NEED TO EXTRACT
  FY69:    [%], [%], [%], [%], [%], [%], [%] ✅ (from v5 file)
```

### **Narrative Message:**
```
"ตู้ค้างปกติ (≤7 วัน) ลดลงเรื่อย ๆ
ตู้ที่ติดปัญหา (>30 วัน) เพิ่มขึ้นมาก
FY68 ยังไม่รุนแรง แต่ FY69 มีสัญญาณเตือนชัด"
```

---

## 🎯 REQUIREMENT 3: REVENUE IMPACT — Show Formula + 3-Year Comparison

### **Current State:**
```
Large KPI card: ~115 ล้านบาท (FY69 7m)
```

### **Requested State:**

#### **3A: Formula Explanation (Small box above KPI)**
```
┌─────────────────────────────────────────────┐
│ 🧮 วิธีคำนวณ:                               │
│                                             │
│ เก็บค่าฝากเพิ่ม = Σ(Dwell day increase   │
│                    × Container size       │
│                    × Storage fee rate)     │
│                                             │
│ เช่น: ตู้ 40 ฟุต ค้างเพิ่ม 0.5 วัน         │
│      × อัตรา 100 บาท/วัน/40ft             │
│      = 50 บาท/ตู้                         │
│      × 10,000 ตู้ต่อเดือน                 │
│      = 500,000 บาท/เดือน                  │
│      = 6 ล้านบาท/ปี                      │
│                                             │
│ (รวม Import + Export ≈ 115 ล้าน/7m FY69) │
└─────────────────────────────────────────────┘
```

#### **3B: 3-Year Comparison (Main KPI area)**

```
┌─────────────────────────────────────────────┐
│ เก็บค่าฝากได้เพิ่ม — เปรียบเทียบ 3 ปี    │
├─────────────────────────────────────────────┤
│                                             │
│  ปีฐาน (FY65-67)    ปี 68           ปี 69  │
│  ค่าฝาก ปกติ   ┐   ค่าฝาก เพิ่ม  ┐  ค่าฝาก │
│                │   ขึ้นแล้ว      │  เพิ่มมาก│
│  Baseline  →   →   +? ล้าน    →   +115 ล้าน│
│                │   (7-12m)       │  (7m)   │
│             ┘                    ┘         │
│                                             │
│              💰 ANNUAL ESTIMATE:             │
│              ~197 ล้านบาท/ปี                │
│                                             │
│  ┌────────────────┬────────────────┐       │
│  │ Import: X ล้าน │ Export: Y ล้าน │       │
│  └────────────────┴────────────────┘       │
│                                             │
│  * อัตราค่าภาระ: หนังสือ ค.ศ.2543         │
│  * FY69 data = 7 เดือนเท่านั้น (ต.ค.-เม.ย) │
│                                             │
└─────────────────────────────────────────────┘
```

### **Visual Approach:**
- Small formula box (collapsible or always shown)
- 3 columns comparing baseline | FY68 | FY69
- Show progression of revenue lift
- Import/Export split below

### **Data Points Needed:**
```
FY65-67: Baseline storage fee revenue ✅
FY68:    Revenue uplift (7-12m estimate) ⚠️ NEED TO CALCULATE
FY69:    Revenue uplift ~115 ล้าน (7m) ✅
```

### **Narrative Message:**
```
"รายได้จากค่าฝากเพิ่มขึ้นคง ๆ
FY68: เริ่มเห็นการเพิ่มขึ้น
FY69: พุ่งถึง 115 ล้านบาท (7 เดือนแรก)
ถ้าเต็มปี คาดว่าจะได้ประมาณ 197 ล้านบาท"
```

---

## 🎯 REQUIREMENT 4: COST IMPACT — Link to Financial Data + Explanation

### **Current State:**
```
2-panel: Revenue ✅ | Cost ❓ (marked as TBD)
```

### **Requested State:**

#### **4A: Left Panel — Revenue (unchanged)**
```
✅ Storage Fee Revenue Increase
  ~115 ล้านบาท (7m FY2569)
```

#### **4B: Right Panel — Cost (NEW: fetch from GL + explanation)**

```
┌──────────────────────────────────────────────┐
│ ⚠️ ค่าใช้จ่ายที่เพิ่มขึ้น                     │
├──────────────────────────────────────────────┤
│                                              │
│ ค่าซ่อมบำรุง:                                │
│  FY65-67: X ล้านบาท/ปี                      │
│  FY68:    Y ล้านบาท/ปี (+Z%)               │
│  FY69:    W ล้านบาท/ปี (+Q%)               │
│                                              │
│ ค่าแรงงาน/เชื้อเพลิง:                        │
│  [Estimated increase if dwell↑]             │
│                                              │
│  Hypothesis:                                 │
│  • ตู้ค้างนาน → เก่า → ซ่อมเพิ่ม           │
│  • Yard บีบแน่น → ทำงาน + ตัดสินใจยาก    │
│  → ค่าแรงเพิ่ม                              │
│                                              │
│ 📊 ที่มา: จากงบการเงิน (GL)                 │
│                                              │
│ ⚠️ ยังไม่ชัดเจนถึงที่: ต้องตรวจสอบ          │
│ correlation กับ dwell time นาน              │
│                                              │
│ Next: ติดต่อ Maintenance team               │
│       ขอข้อมูล repair ticket log            │
│       (dwell day vs repair count)            │
│                                              │
└──────────────────────────────────────────────┘
```

### **Visual Approach:**
- Left: Revenue (clear green ✅)
- Right: Cost (yellow ⚠️ — data from GL + hypothesis)
- Small boxes showing: FY65-67 → FY68 → FY69 (cost trend)
- Callout: "Longer dwell → older containers → repairs ↑"
- Action item: "Need correlation analysis"

### **Data Points Needed:**
```
From Finance Dashboard / GL:
  Repair/Maintenance cost FY65-67: [฿] ✅ (need query)
  Repair/Maintenance cost FY68: [฿] ✅ (need query)
  Repair/Maintenance cost FY69: [฿] ✅ (need query)
  
+ Other operating costs if available:
  Cleaning, Yard labor, Fuel, etc.
```

### **Narrative Message:**
```
"รายได้เพิ่ม ✅ แต่ต้นทุนหลายอย่างก็เพิ่มตามไป ⚠️
ค่าซ่อม: เห็นแนวโน้มเพิ่มขึ้นจากงบการเงิน
ค่าแรงงาน/เชื้อเพลิง: ยังไม่มีข้อมูลตรง

หากต้นทุนเพิ่ม < รายได้เพิ่ม → net positive ✅
หากต้นทุนเพิ่ม > รายได้เพิ่ม → need strategy review ⚠️"
```

---

## 🎯 REQUIREMENT 5: OPERATIONAL PATTERN — Entry vs Exit Behavior

### **Current State:**
```
Timeline bar showing 3-7d | 8-14d | 15-30d | >30d zones
+ Waterfall showing % exits per bracket
```

### **Requested State:**

#### **5A: Pattern Visualization (Main)**

```
Day of Week Pattern:

ENTRY DAY (When containers arrive):
┌──────┬──────┬──────┬──────┬──────┬──────┬──────┐
│ Mon  │ Tue  │ Wed  │ Thu  │ Fri  │ Sat  │ Sun  │
├──────┼──────┼──────┼──────┼──────┼──────┼──────┤
│ 18%  │ 22%  │ 20%  │ 15%  │ 12%  │ 8%   │ 5%   │ ← Import pattern
│      │      │      │      │      │      │      │
│ 15%  │ 18%  │ 17%  │ 20%  │ 16%  │ 10%  │ 4%   │ ← Export pattern
└──────┴──────┴──────┴──────┴──────┴──────┴──────┘

EXIT DAY (When containers leave):
┌──────┬──────┬──────┬──────┬──────┬──────┬──────┐
│ Mon  │ Tue  │ Wed  │ Thu  │ Fri  │ Sat  │ Sun  │
├──────┼──────┼──────┼──────┼──────┼──────┼──────┤
│ 22%  │ 20%  │ 18%  │ 18%  │ 15%  │ 5%   │ 2%   │ ← Import pattern
│      │      │      │      │      │      │      │
│ 18%  │ 18%  │ 20%  │ 20%  │ 14%  │ 8%   │ 2%   │ ← Export pattern
└──────┴──────┴──────┴──────┴──────┴──────┴──────┘

DWELL PATTERN by Entry-Exit Combination:

Entry Friday + Exit Mon-Tue:
  Dwell = 2-3 days (normal, fast) ✅
  % of total: X%

Entry Friday + Exit following Mon-Wed:
  Dwell = 2-3 days BUT weekend delay
  (Fri entry, Sat-Sun nothing happens, exit Mon)
  = apparent long dwell, but actually fast
  % of total: Y%

Entry Fri-Sat + Exit following Wed-Fri:
  Dwell = 3-5 days (normal to slightly long)
  BUT crosses weekend → delays look longer
  % of total: Z%

Entry Mon-Wed + Exit Fri or Later:
  Dwell = 3-5 days (normal) ✅

Entry Any Day + NO EXIT until next week:
  Dwell = 8-30 days (stuck) 🔴
  Could be: Customs hold, paperwork delay,
            importer not ready, documentation issues
  % of total: P% ← THIS GREW 4.2×
```

#### **5B: Behavior Observation Box**

```
┌──────────────────────────────────────────────┐
│ 👁️ พฤติกรรมการฝากตู้                        │
├──────────────────────────────────────────────┤
│                                              │
│ ตู้ปกติ (3-7d):                             │
│  • เข้า Mon-Wed → ออก ในสัปดาห์เดียวกัน    │
│  • เข้า Fri → ติดวันหยุด → ออก Mon-Tue    │
│  • Importer ตั้งใจ → ออกไปได้เร็ว          │
│                                              │
│ ตู้ค้างนาน (8-30d):                        │
│  • เข้า Fri → ไม่มี event ถึง Wed/Thu      │
│  • เข้า Mon → ไม่มี event ถึง Fri/Mon     │
│  • Pattern: เข้าแล้วนิ่ง (no pickup)       │
│                                              │
│ 🚨 ตู้ติด (>30d):                          │
│  • Entry day ≠ typical exit day             │
│  • Customs hold / doc delay / storage fee   │
│  • สายเรือ / บริษัท specific               │
│    (ไหนที่มีตู้ติดเยอะ)                    │
│                                              │
│ 🔍 FUTURE ANALYSIS:                         │
│  ► Which shipping lines have stuck containers?│
│  ► Which importers delay pickup?            │
│  ► Pattern repeat weekly?                   │
│  ► Can we predict problem containers early? │
│                                              │
└──────────────────────────────────────────────┘
```

### **Visual Approach:**
- Heatmap: Entry day × Exit day × % containers (color intensity)
- OR bar chart: % that exit within 7d vs 8-14d vs >30d
- Color-code by day: weekday (blue) vs weekend (yellow)
- Annotation: "Friday entries often tick over into next Monday = appears long but not"

### **Data Points Needed:**
```
Distribution of (Entry Day, Exit Day, Dwell Bracket) combinations:
  For Import: [data matrix] ⚠️ NEED TO EXTRACT from raw
  For Export: [data matrix] ⚠️ NEED TO EXTRACT from raw
  
By shipping line/company (future):
  Container arrival patterns ⚠️ FUTURE ANALYSIS
  Stuck container tracking ⚠️ FUTURE ANALYSIS
```

### **Narrative Message:**
```
"ตู้ปกติ: เข้าเก่าพอเร็ว (ส่วนใหญ่ Mon-Wed → exit ในสัปดาห์)
ตู้ค้างนาน: เข้าแล้วนิ่ง ไม่เคลื่อนไหว (likely customs or doc delay)

ข้อสังเกต:
• Fri entries มักติดวันหยุด → จึงดูเหมือนค้างนาน
• >30d containers มี pattern: entry + long gap + no activity
• สาเหตุ: ไม่ชาติอรรถไทย (คุกจี) อย่างให้รู้แน่นอน
  Likely: customs, documentation, importer readiness

อนาคต:
• ติดตาม: ไหนสายเรือ / บริษัท ที่มีตู้ติดเยอะ?
• ตรวจสอบ: เหตุผลของการหน่วงโดยเฉพาะ
• ลดความเสี่ยง: ระบุ stuck containers ก่อนหน่วง 5-7 วัน"
```

---

## 🎯 REQUIREMENT 6: Status of This Document

### **⚠️ THIS IS A DRAFT (ร่างตัวอย่าง) — NOT FINAL DESIGN**

```
What this HTML template is:
✅ Visual mockup / wireframe
✅ Placeholder structure
✅ Demonstration of 5 sections
✅ Reference for Claude Code to build upon

What this is NOT:
❌ Final polished design
❌ Production-ready
❌ With real data (mostly sample data)
❌ Optimized for printing
❌ Mobile-tested thoroughly
```

### **Next Steps:**
1. Use as reference → Feed requirements to Claude Code
2. Claude Code builds improved version with:
   - FY68 included (all sections)
   - Formula explanation
   - Cost data linked
   - Entry-exit pattern visualization
   - Better interactivity
3. Test with colleague → get feedback
4. Polish design → finalize
5. Deploy to hub

---

## 📋 SUMMARY OF CHANGES NEEDED

| Section | Change | Impact | Priority |
|---------|--------|--------|----------|
| 1. Dwell Time | Add FY68 column | Show progression | 🔴 HIGH |
| 2. Distribution | Add FY68 stacked bar | Show shift start | 🔴 HIGH |
| 3. Revenue | Add formula + 3-year | Explain calculation | 🔴 HIGH |
| 4. Cost | Link GL data + hypothesis | Show trade-off | 🔴 HIGH |
| 5. Pattern | Add entry/exit heatmap | Identify bottleneck | 🟡 MEDIUM |
| 6. Status | Mark as DRAFT | Set expectation | 🟡 MEDIUM |

---

**Document Status:** 📝 SPECIFICATION READY  
**For:** Claude Code (to build improved HTML template)  
**Owner:** Palabordee (Port Authority)  
**Date:** June 2026
