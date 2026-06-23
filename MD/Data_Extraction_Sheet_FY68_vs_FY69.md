# 📊 DATA EXTRACTION SHEET
## Dwell Time Brackets & Cost Impact Analysis
### Separated: FY68 vs FY69 (By Year, Not Combined)

---

## 🎯 SECTION A: DWELL TIME BRACKETS — % of Containers

### **A1: IMPORT (ตู้นำเข้า)**

```
Dwell Range          FY65-67(Base)    FY68            FY69           Change(FY68-69)
─────────────────────────────────────────────────────────────────────────────────
≤ 3 days (Free)      [%]              [%]             [%]            [±%]
4-5 days (Fast)      [%]              [%]             [%]            [±%]
6-7 days (Normal)    [%]              [%]             [%]            [±%]  ← Peak
8-10 days (Delay)    [%]              [%]             [%]            [±%]
11-15 days (Problem) [%]              [%]             [%]            [±%]
16-30 days (Stuck)   [%]              [%]             [%]            [±%]
> 30 days (Critical) [%]              [%]             [%]            [±%]
─────────────────────────────────────────────────────────────────────────────────
TOTAL               100%              100%            100%             —
```

**Key Insight (from dashboard):**
- Peak (highest %) in FY65-67: 6-7 days
- Peak in FY68: Stays 6-7 days BUT distribution widens
- Peak in FY69: Still 6-7 days BUT tail grows into 8-10, 16-30, >30d ranges

---

### **A2: EXPORT (ตู้ส่งออก)**

```
Dwell Range          FY65-67(Base)    FY68            FY69           Change(FY68-69)
─────────────────────────────────────────────────────────────────────────────────
≤ 3 days (Free)      [%]              [%]             [%]            [±%]
4-5 days (Fast)      [%]              [%]             [%]            [±%]  ← Peak (Base)
6-7 days (Normal)    [%]              [%]             [%]            [±%]
8-10 days (Delay)    [%]              [%]             [%]            [±%]  🔴 JUMPED in FY68
11-15 days (Problem) [%]              [%]             [%]            [±%]
16-30 days (Stuck)   [%]              [%]             [%]            [±%]  🔴 GROWING
> 30 days (Critical) [%]              [%]             [%]            [±%]  🚨 4.2× GROWTH
─────────────────────────────────────────────────────────────────────────────────
TOTAL               100%              100%            100%             —
```

**Key Insight (from dashboard):**
- FY65-67: Peak at 4-5 days, tail minimal
- FY68: 8-10 days jumped from 9.8% → 18.5% (ALERT)
- FY69: >30 days grew 4.2× (biggest problem)

---

## 🎯 SECTION B: COST IMPACT ANALYSIS

### **B1: Operating Cost Drivers (with FY68 & FY69 separated)**

```
Cost Category           FY65-67(Base)    FY68            FY69           Change      Dwell-Related?
───────────────────────────────────────────────────────────────────────────────────────────────
REPAIR/MAINTENANCE      [฿/mo]          [฿/mo]          [฿/mo]         [+%]        ✅ YES
  └─ Hypothesis:        aging containers, damage from longer storage, wear & tear
                        Longer dwell = older container age = higher repair risk

CLEANING/PREP           [฿/mo]          [฿/mo]          [฿/mo]         [+%]        ⚠️ MAYBE
  └─ Hypothesis:        More container throughput (to absorb longer dwell?)
                        = more prep/cleaning cycles = cost up

YARD LABOR              [฿/mo]          [฿/mo]          [฿/mo]         [+%]        ⚠️ MAYBE
  └─ Hypothesis:        Longer dwell = more relocations needed (make space for new)
                        = more manual labor, forklift hrs = cost up

FUEL/ENERGY             [฿/mo]          [฿/mo]          [฿/mo]         [+%]        ⚠️ MAYBE
  └─ Hypothesis:        More equipment movement to manage congestion
                        = more fuel burn for equipment = cost up

INSURANCE               [฿/mo]          [฿/mo]          [฿/mo]         [+%]        ❌ WEAK
  └─ Hypothesis:        Storage itself doesn't drive insurance premiums
                        (not inventory holder = ทกท. doesn't insure containers)
```

---

### **B2: Net Cost-Benefit Analysis (Revenue vs Cost)**

```
METRIC                          FY68 Impact         FY69 Impact (7m)    FY69 Annual (Est.)
─────────────────────────────────────────────────────────────────────────────────────
Revenue Uplift (Storage Fee)    +[฿]                +115 ล้านบาท         ~197 ล้านบาท
  ├─ Import contribution        +[฿]                +[X ล้านบาท]        +[X×12/7]
  └─ Export contribution        +[฿]                +[Y ล้านบาท]        +[Y×12/7]

Cost Increase (Operating)       ??? ล้านบาท         ??? ล้านบาท         ??? ล้านบาท
  ├─ Repair/Maintenance         +[฿]                +[A ล้านบาท]        +[A×12/7]
  ├─ Cleaning/Prep              +[฿]                +[B ล้านบาท]        +[B×12/7]
  ├─ Yard Labor                 +[฿]                +[C ล้านบาท]        +[C×12/7]
  └─ Fuel/Energy                +[฿]                +[D ล้านบาท]        +[D×12/7]
                                ─────               ─────────────        ──────────
NET IMPACT (Revenue - Cost)     ??? ล้านบาท         ??? ล้านบาท         ??? ล้านบาท

💡 IF (A+B+C+D) < 115:
   → Revenue growth is NET POSITIVE ✅
   
💡 IF (A+B+C+D) > 115:
   → Revenue growth is offset by costs ⚠️
   
💡 IF (A+B+C+D) ≈ 115:
   → Break-even (no real profit improvement) 🤷
```

---

## 🔴 CRITICAL GAPS (Data Still Missing)

| Gap | Impact | Status | Next Step |
|-----|--------|--------|-----------|
| **Actual repair cost FY68 vs FY69** | Cannot quantify cost correlation | ❌ MISSING | Query Finance Dashboard / Maintenance logs |
| **Container count by dwell bracket FY68 vs FY69** | Cannot calculate weighted revenue impact | ⚠️ PARTIAL | Extract from raw data if available |
| **Customs hold vs importer delay breakdown** | Cannot identify bottleneck root cause | ❌ MISSING | Survey Export ops team (Export >30d reason) |
| **Container size mix (20ft/40ft/45ft) by dwell** | Cannot assess if larger containers have longer dwell | ⚠️ MAYBE | Check raw data by nominal_length |
| **Yard utilization % by dwell bracket** | Cannot assess if crowding is driving longer dwell | ❌ MISSING | Need yard mapping data (not in this dashboard) |

---

## 📋 DATA EXTRACTION PRIORITY

### **Priority 1 (Critical for narrative):**
```
✅ DONE:  Dwell time mean/median (FY68 vs FY69)
✅ DONE:  Distribution shift visualization (>30d = 4.2×)
✅ DONE:  Revenue uplift estimation (~115 ล้าน)
❌ TODO:  Repair cost correlation (FY68 vs FY69 comparison)
```

### **Priority 2 (Nice to have):**
```
⚠️ PARTIAL: Entry/exit pattern by day-of-week (if in raw data)
⚠️ PARTIAL: Container size impact on dwell (20ft vs 40ft)
❌ TODO:    Customs hold identification (requires ops insight)
```

### **Priority 3 (Future versions):**
```
❌ TODO:    Yard utilization heatmap (requires spatial data)
❌ TODO:    Forecasting: what if dwell continues to grow? (modeling)
```

---

## 🎯 RECOMMENDED INFOGRAPHIC STRUCTURE

Based on available data:

```
┌─────────────────────────────────────────────────────────────┐
│ ISSUE 1: Dwell Time UP (5.18d → 5.72d)                    │
│  → Visualization: Side-by-side comparison                   │
│  → Data: ✅ READY                                           │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ ISSUE 2: Distribution Shift (>30d = 4.2× increase)         │
│  → Visualization: Stacked bar (FY68 vs FY69)               │
│  → Data: ✅ READY (show FY68 & FY69 separate bars)         │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ ISSUE 3: Revenue Impact (~115 ล้าน)                       │
│  → Visualization: Large KPI + monthly breakdown             │
│  → Data: ✅ READY (FY69 = 7m data, annual estimate)       │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ ISSUE 4: Cost Impact (UNKNOWN — honest assessment)         │
│  → Visualization: 2-panel (Revenue ✅ | Cost ❓)           │
│  → Data: ❌ NOT READY (mark as TBD / hypothesis)           │
│  → Action: "Need maintenance data to correlate"             │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ ISSUE 5: Operational Pattern (When/How long)               │
│  → Visualization: Timeline + distribution waterfall          │
│  → Data: ⚠️ PARTIAL (from dashboard v5)                    │
└─────────────────────────────────────────────────────────────┘
```

---

## 💾 HOW TO USE THIS SHEET

1. **Fill in the [%] and [฿] values** from:
   - Dashboard matrix tables (for dwell brackets)
   - Finance Dashboard or GL exports (for cost data)

2. **Once filled, use to:**
   - Calculate weighted revenue impact by dwell segment
   - Compare FY68 vs FY69 cost trends
   - Identify which cost driver is most affected by dwell

3. **Then reference in infographic:**
   - Use filled data in Issue 2 (distribution) visualization
   - Use cost comparison in Issue 4 (cost impact) panel
   - Call out 4.2× >30d growth as key finding

---

**Status:** 🟡 **TEMPLATE READY — Awaiting data fill-in**  
**Next Step:** Extract bracket % from dashboard matrix + cost data from Finance  
**Owner:** Palabordee (Port Authority)
