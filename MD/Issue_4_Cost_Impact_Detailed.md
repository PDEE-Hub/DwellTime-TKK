# 🎯 ISSUE 4: COST IMPACT (ผลกระทบด้านค่าใช้จ่าย)

## **Question:** 
> "โอเค ได้รายได้เพิ่มจากตู้ค้างนาน แต่ต้นทุนเพิ่มไปกี่บาท?"

---

## 📊 FRAMEWORK: Operating Cost Correlation with Dwell Time

### **HYPOTHESIS (สิ่งที่เราคิดว่าเป็นจริง):**

```
Longer Dwell Time
     ↓
Containers age in yard longer
     ↓
├─ More wear & tear (paint, seals, hinges)
├─ More rust/corrosion (especially metal containers)
├─ More internal damage (flooring, ventilation)
├─ More pest infestation risk
     ↓
Higher Repair/Maintenance Costs
     ↓
If repair cost increase > revenue uplift
  → Net negative impact ❌

If repair cost increase < revenue uplift
  → Net positive, but need assessment ✅
```

---

## 🔍 DETAILED COST DRIVER ANALYSIS (FY68 vs FY69 Separated)

### **COST DRIVER #1: Repair & Maintenance (ค่าซ่อมบำรุง)**

**Status:** ⚠️ Data available in Finance Dashboard (unclear link to dwell)

```
Fiscal Year         Avg Monthly     Ytd/Period      Annual*         Change vs Base   Likely Cause
────────────────────────────────────────────────────────────────────────────────────────────────
FY65-67 (Base)      [฿ X ม.]        [฿ Y ล้าน]      [฿ Z ล้าน]      —                —

FY68                [฿ A ม.]        [฿ B ล้าน]      [฿ C ล้าน]      [+% vs base]     ⚠️ Likely: longer dwell
                                                                                      = older containers
                                                                                      = more repairs

FY69 (7m to Apr)    [฿ D ม.]        [฿ E ล้าน]      [฿ F ล้าน] est  [+% vs base]     ⚠️ Same hypothesis
```

**Complication (from v5 dashboard):**
- Month 7 FY2569 shows "-39.5 ล้าน repair Accrual Reversal"
- This is an **accrual reversal** (not a cost increase, just accounting adjustment)
- **Does NOT tell us if repair activity actually increased**

**Questions to answer:**
1. Did actual repair count (# of repairs) increase in FY68 vs FY69?
2. Did repair cost per container increase (due to older containers requiring more work)?
3. Or was accrual timing the only thing that changed?

**How to verify:**
```
Data source: Maintenance Logs (not in Dwell dashboard)
  → Count repairs per month: FY65-67 vs FY68 vs FY69
  → Filter by container type (20ft vs 40ft)
  → Correlate with dwell time brackets (>30d containers more repairs?)
```

---

### **COST DRIVER #2: Cleaning & Preparation (ค่าทำความสะอาดเตรียมตู้)**

**Status:** ❌ No direct data (inferred from operations)

```
Fiscal Year         Activity        Assumption                   Change vs Base   Dwell-Linked?
──────────────────────────────────────────────────────────────────────────────────────────
FY65-67 (Base)      [units/mo]       1 clean per container,       —                —
                                      at departure or arrival

FY68                [units/mo]       If longer dwell + more      [+% IF TRUE]      ⚠️ MAYBE
                                      inventory → more prep?
                                      e.g., containers sit
                                      longer before next use

FY69                [units/mo]       Same logic as FY68          [+% IF TRUE]      ⚠️ MAYBE
```

**Uncertainty:**
- ทกท. might clean on **entry** (not per dwell length)
- OR clean on **exit** (cleaning frequency doesn't change with dwell)
- **Without ops data = cannot confirm link**

**How to verify:**
```
Data source: Yard Operations Logs
  → Count cleaning events per month
  → Distinguish: entry clean vs exit clean
  → Trend over FY65-67 vs FY68 vs FY69
```

---

### **COST DRIVER #3: Yard Labor (ค่าแรงงานลาน)**

**Status:** ❌ No direct data (inferred from operations)

```
Fiscal Year         Labor Hours      Hypothesis                  Change vs Base   Dwell-Linked?
──────────────────────────────────────────────────────────────────────────────────────────
FY65-67 (Base)      [hrs/mo]         Baseline labor to move      —                —
                                      containers in/out

FY68                [hrs/mo]         Longer dwell → containers   [+ hrs IF TRUE]  ⚠️ MAYBE
                                      stack deeper (less space)
                                      → more relocations to find
                                      & retrieve stored units
                                      → more labor hours

FY69                [hrs/mo]         Same crowding issue        [+ hrs IF TRUE]  ⚠️ MAYBE
```

**Logic chain (IF true):**
```
Longer avg dwell (5.18d → 5.72d)
     ↓
More containers in yard at same time
     ↓
Yard utilization % increases
     ↓
Stacking deeper, harder to retrieve
     ↓
Forklift operators take longer to find containers
     ↓
Yard labor hours ↑
```

**But this is SPECULATIVE without actual labor data**

**How to verify:**
```
Data source: Yard Operations + Forklift Logs
  → Track container retrievals per day
  → Measure retrieval time by storage depth
  → Compare FY65-67 vs FY68 vs FY69
  → Cross-tabulate with dwell brackets
```

---

### **COST DRIVER #4: Fuel & Equipment (ค่าน้ำมัน/พลังงาน)**

**Status:** ❌ No direct data (inferred from labor increase)

```
Fiscal Year         Equipment Use   Assumption                  Change vs Base   Dwell-Linked?
────────────────────────────────────────────────────────────────────────────────────────────
FY65-67 (Base)      [fuel/mo]        Forklift, RTG, fuel        —                —

FY68                [fuel/mo]        If yard labor ↑ (from       [+ fuel IF TRUE] ⚠️ MAYBE
                                      Cost Driver #3)
                                      → equipment run time ↑
                                      → fuel consumption ↑

FY69                [fuel/mo]        Same as FY68               [+ fuel IF TRUE] ⚠️ MAYBE
```

**Correlation chain (IF true):**
```
More labor hours (see Cost Driver #3)
     ↓
Equipment runs longer per day
     ↓
Fuel consumption per month ↑
```

**Again, SPECULATIVE without actual fuel data**

---

### **COST DRIVER #5: Insurance (ประกันภัย)**

**Status:** ❌ Weak link (unlikely to be dwell-driven)

```
Reasoning:
──────────────────────────────────────────────────────
ทกท. does NOT own the containers → ทกท. is storage provider
Insurance is held by: Shipping lines, importers, exporters
(NOT by ทกท.)

Therefore: Dwell time does NOT affect ทกท.'s insurance costs
(ทกท. doesn't insure containers)

Conclusion: ❌ SKIP this cost driver
```

---

## 📊 COST IMPACT SUMMARY TABLE (Template for Fill-in)

```
╔═══════════════════════╦════════════════╦════════════════╦════════════════╦═════════════════╗
║ Cost Category         ║ FY65-67        ║ FY68           ║ FY69           ║ Dwell-Linked?   ║
║                       ║ (Baseline)     ║ vs Base        ║ vs Base        ║                 ║
╠═══════════════════════╬════════════════╬════════════════╬════════════════╬═════════════════╣
║ Repair/Maintenance    ║ X ล้าน/ปี      ║ Y ล้าน (+Z%)   ║ W ล้าน (+Q%)   ║ ✅ YES (likely) ║
║   (Actual repairs)    ║                ║                ║                ║                 ║
║   └─ Data Status: ⚠️  ║ [Need verif]   ║ [Need verif]   ║ [Need verif]   ║                 ║
╠═══════════════════════╬════════════════╬════════════════╬════════════════╬═════════════════╣
║ Cleaning/Prep         ║ A ล้าน/ปี      ║ B ล้าน (+C%)   ║ D ล้าน (+E%)   ║ ⚠️ MAYBE        ║
║                       ║                ║                ║                ║                 ║
║   └─ Data Status: ❌  ║ [Unknown]      ║ [Unknown]      ║ [Unknown]      ║                 ║
╠═══════════════════════╬════════════════╬════════════════╬════════════════╬═════════════════╣
║ Yard Labor            ║ F ล้าน/ปี      ║ G ล้าน (+H%)   ║ I ล้าน (+J%)   ║ ⚠️ MAYBE        ║
║   (Forklift hours)    ║                ║                ║                ║                 ║
║   └─ Data Status: ❌  ║ [Unknown]      ║ [Unknown]      ║ [Unknown]      ║                 ║
╠═══════════════════════╬════════════════╬════════════════╬════════════════╬═════════════════╣
║ Fuel/Energy           ║ K ล้าน/ปี      ║ L ล้าน (+M%)   ║ N ล้าน (+O%)   ║ ⚠️ MAYBE        ║
║   (Equipment fuel)    ║                ║                ║                ║                 ║
║   └─ Data Status: ❌  ║ [Unknown]      ║ [Unknown]      ║ [Unknown]      ║                 ║
╠═══════════════════════╬════════════════╬════════════════╬════════════════╬═════════════════╣
║ Insurance             ║ P ล้าน/ปี      ║ — (not linked) ║ — (not linked) ║ ❌ NO           ║
║                       ║                ║                ║                ║                 ║
║   └─ Data Status: —   ║ (N/A)          ║ (N/A)          ║ (N/A)          ║                 ║
╚═══════════════════════╩════════════════╩════════════════╩════════════════╩═════════════════╝

TOTAL OPERATING COST    [X+A+F+K ล้าน]  [Y+B+G+L ล้าน]  [W+D+I+N ล้าน]  [Total change]
                        /ปี             /ปี (est.)       /ปี (est.)
```

---

## 🎯 NET COST-BENEFIT ANALYSIS (FY68 vs FY69)

```
FY68 Analysis:
──────────────
Revenue Uplift        : ? ล้านบาท
Operating Cost Increase: ? ล้านบาท
─────────────────────────────────
NET IMPACT           : ? ล้านบาท

Status: ❌ CANNOT CALCULATE (data incomplete)


FY69 Analysis (7m to Apr 2569):
──────────────────────────────
Revenue Uplift        : ~115 ล้านบาท (confirmed)
Operating Cost Increase: ??? ล้านบาท (unknown)
                        
Annual Projection     : ~197 ล้านบาท revenue
                        ??? ล้านบาท cost
─────────────────────────────────
NET IMPACT           : ??? ล้านบาท

IF cost = 50 ล้าน:   NET = +147 ล้าน ✅ (Strong positive)
IF cost = 115 ล้าน:  NET = +82 ล้าน ✅ (Still positive)
IF cost = 197 ล้าน:  NET = 0 ล้าน 🤷 (Break-even)
IF cost > 197 ล้าน:  NET = negative ❌ (Loss)
```

---

## 💡 WHAT TO SAY IN INFOGRAPHIC (Issue 4)

### **Honest Approach (Recommended):**

```
┌──────────────────────────────────────────────────┐
│ Revenue Gain: ✅ CLEAR (~115 ล้าน for 7m)       │
│                                                  │
│ Cost Impact: 🤷 UNCLEAR (need maintenance data)  │
│                                                  │
│ Hypothesis: Longer dwell likely increases      │
│ repair costs (aged containers → more damage)    │
│                                                  │
│ Next Step: Correlate repair logs with dwell    │
│ time data to quantify actual cost impact        │
└──────────────────────────────────────────────────┘
```

### **Alternative Approaches:**

#### **Option A: Optimistic (with caveats)**
```
"If repair costs are <50% of revenue gain,
 net impact is still strongly positive."
```

#### **Option B: Conservative (worst-case)**
```
"In worst case (repair = 100% of revenue gain),
 we break even on the strategy."
```

#### **Option C: Data-driven (recommended)**
```
"We cannot fully assess cost impact yet.
 Here's what we need to know:
 • FY68 vs FY69 repair activity trends
 • Link between dwell bracket and repair frequency
 • Yard labor utilization data
 
 Once we have this, we can give a definitive answer."
```

**→ Go with Option C in infographic** (honest, professional, actionable)

---

## 📋 DATA COLLECTION CHECKLIST

### **HIGH PRIORITY (Do immediately):**
- [ ] Extract monthly repair cost from Finance GL: FY65-67 vs FY68 vs FY69
- [ ] Count repair jobs/tickets: FY65-67 vs FY68 vs FY69 (by month)
- [ ] Ask Maintenance team: Any observed increase in damage patterns?

### **MEDIUM PRIORITY (Do soon):**
- [ ] Yard operations: Labor hours breakdown (entry/retrieval/stacking)
- [ ] Container cleaning: Event count and timing (entry vs exit)
- [ ] Equipment fuel logs: Monthly fuel consumption trend

### **LOW PRIORITY (Future):**
- [ ] Yard utilization %: Peak stacking depth over time
- [ ] Forklift GPS data: Retrieval time per container by location depth
- [ ] Forecasting model: Cost projection if dwell continues to grow

---

## 📞 WHO TO CONTACT FOR DATA

| Data Type | Owner/Department | Contact | Status |
|-----------|------------------|---------|--------|
| Repair costs & tickets | Maintenance/Engineering | [Manager name] | ⚠️ NEED |
| Labor hours (yard ops) | Yard Operations | [Manager name] | ⚠️ NEED |
| Equipment fuel logs | Fleet/Equipment team | [Manager name] | ⚠️ NEED |
| Container cleaning log | Yard Operations | [Manager name] | ⚠️ NEED |
| GL cost data | Finance/Accounting | [Manager name] | ✅ HAVE |

---

**Status:** 🟡 **TEMPLATE READY — Awaiting cost data verification**  
**Next Step:** Reach out to Maintenance team for repair correlation analysis  
**Owner:** Palabordee (Port Authority)  
**Date:** June 2026
