# 🎯 INFOGRAPHIC DASHBOARD FRAMEWORK
## "Dwell Time × Revenue Linkage" — ทกท. Revenue Growth Story

**Status:** Ready for Claude Code (PDEE-AI) execution in VS Code  
**Output Target:** Interactive HTML Infographic + Dashboard (standalone.html)  
**Audience:** ทกท. Management & Operational Teams (non-technical)  
**Design Tone:** Data storytelling + visual impact (NOT academic analysis)

---

## 📌 CORE NARRATIVE

> **ทกท. รายได้เพิ่มขึ้น — ไม่ใช่เพราะตู้เพิ่มขึ้น แต่เพราะตู้ค้างนาน**  
> เมื่อตู้ค้างเฉลี่ยเพิ่มขึ้นไปเกือบครึ่งวันต่อตู้ ลดรายได้ที่กำหนดมาหรือสนับสนุนกำไรฝ่ายอื่น ← **ต้องพูดทั้งสองฝั่ง**

---

## 🔍 ANALYTICAL FRAMEWORK — Separate Issues Clearly

### **ISSUE 1: DWELL TIME SHIFT (ข้อมูลพื้นฐาน)**
*"ตู้ค้างนานขึ้นจริงหรือเปล่า?"*

#### Data Points Required:
| Metric | FY65-67 (Baseline) | FY68 | FY69 (7m to Apr69) | Change |
|--------|-------------------|------|-------------------|---------|
| **Import Dwell (Mean)** | 5.18d | 5.70d | 5.72d | +0.54d (+10.4%) |
| **Export Dwell (Mean)** | 5.37d | 6.28d | 5.92d | +0.55d (+10.2%) |
| **Import Dwell (Median)** | [EXTRACT] | [EXTRACT] | [EXTRACT] | [CALCULATE] |
| **Export Dwell (Median)** | [EXTRACT] | [EXTRACT] | [EXTRACT] | [CALCULATE] |

**Visual Approach for Non-Technical Audience:**
- ❌ DO NOT show Mean/Median side-by-side (confuses people)
- ✅ DO use **single line chart: baseline (gray) vs current (color)** — very simple
- ✅ Annotation: "ปีฐาน: X วัน | ตอนนี้: Y วัน | ต่างกัน: +Z วัน (ประมาณเพิ่ม ~3 ชั่วโมง)"
- Add callout: **Why Mean not Median?** → "ตู้ส่วนน้อยค้างนานกว่า" (tail in distribution)

---

### **ISSUE 2: DISTRIBUTION SHIFT (ตู้ค้างเกินกี่วัน)**
*"ตู้ส่วนใหญ่ค้างกี่วัน? มีตู้ค้างนานมากขึ้นไปหรือเปล่า?"*

#### Data Points Required:
**Dwell Time Brackets — % of containers:**

```
Dwell Range     FY65-67    FY68       FY69       Change (pp)    Category
≤ 3d (Free)     [%]        [%]        [%]        [±pp]          ✅ Healthy
4-7d (Normal)   [%]        [%]        [%]        [±pp]          Good
8-14d (Delay)   [%]        [%]        [%]        [±pp]          ⚠️ Watch
15-30d (Stuck)  [%]        [%]        [%]        [±pp]          🔴 Problem
>30d (Chronic)  [%]        [%]        [%]        [±pp] × 4.2x   🚨 Crisis (Export only)
```

**Key Insight from v5 file:** "ฝั่ง Export มีสัดส่วนตู้ค้างเกิน 30 วัน **สูงขึ้น 4.2 เท่า**" ← **ประเด็นสำคัญที่สุด**

**Visual Approach:**
- 🎨 **Stacked Bar Chart** (horizontal, simple):
  - X-axis: [FY65-67 | FY68 | FY69]
  - Y-axis: 100% stacked
  - Color coding: Green (≤7d) | Yellow (8-14d) | Red (15-30d) | Dark Red (>30d)
  - Key annotation box: "Export >30d: 4.2× increase" with emphasis
- ❌ NO density plots, NO histograms (too complex)

---

### **ISSUE 3: REVENUE IMPACT (เรื่องที่คน CEO ต้องรู้)**
*"ตู้ค้างนาน = เก็บค่าฝากได้เพิ่มขึ้นกี่บาท?"*

#### Data Points Required:
**Incremental Storage Fee Revenue** (at current dwell vs baseline):

```
                    FY68                    FY69 (7m)           FY69 Annualized*
Impact Type         Amount (ลบ.)            Amount (ลบ.)        Estimate (ลบ.)
─────────────────────────────────────────────────────────────────────────
Import Revenue Lift   ~[X1]                  ~[X2]               ~[X2×12/7]
Export Revenue Lift   ~[X3]                  ~[X4]               ~[X4×12/7]
COMBINED             ~[X1+X3]                ~[X2+X4]            ~[(X2+X4)×12/7]
```

**From v5 file:** "ราว ~115 ล้านบาท (ข้อมูล 7 เดือนแรกของปี 2569)"

**Calculation Method (show user:**
```
For each container tier (20ft, 40ft, 45ft):
  - Current avg dwell → lookup storage fee bracket per day
  - Baseline avg dwell → lookup storage fee bracket per day
  - Difference = (Current bracket rate - Baseline bracket rate) × (Current dwell - Baseline dwell)
  - × Container count in period
  = Incremental revenue
```

**Visual Approach:**
- 🎨 **Large Impact Card** (like KPI card):
  - "Revenue Uplift from Longer Dwell" 
  - Large number: **~115 ล้าน บาท** (7 months data 2569)
  - Sub: "Extrapolated to 12 months: ~197 ล้าน บาท"
  - Small callout: *"ที่มา: Container × Dwell day × Storage fee bracket (หนังสือค่าภาระ ค.ศ.2543)"*

---

### **ISSUE 4: COST IMPACT (ฝ่ายอื่นจะเสีย)**
*"โอเค ได้รายได้เพิ่ม แต่ค่าใช้จ่ายเพิ่มไปกี่บาท?"*

#### Data Points Required:
**Operating Cost Increase (linked to longer dwell):**

```
Cost Driver             FY65-67    FY68/69     Change     Likely Cause (longer dwell?)
─────────────────────────────────────────────────────────────────────────────
Repair/Maintenance      [₿/mo]     [₿/mo]      [+%]       YES — aged containers, damage
Cleaning/Prep           [₿/mo]     [₿/mo]      [+%]       MAYBE — more throughput = more prep
Yard Labor              [₿/mo]     [₿/mo]      [+%]       MAYBE — more relocations, stacking
Fuel/Energy             [₿/mo]     [₿/mo]      [+%]       MAYBE — more equipment movement
Insurance               [₿/mo]     [₿/mo]      [+%]       WEAK — storage doesn't drive insurance
```

**From v5 file inference:** 
- "ค่าซ่อม (Repair Accrual) ผันผวน" → FY2569 month 7 had "-39.5 ลบ. repair Accrual Reversal"
- This is a reversal, not a new cost increase, so **unclear causal link yet**

**Visual Approach:**
- 🎨 **2-panel comparison:**
  - LEFT: "Revenue Gain from ↑ Dwell"  → **+115 ล้าน (7m 2569)**
  - RIGHT: "Operating Cost Increase?" → [UNKNOWN] "🤷 Repair costs fluctuate month-to-month; need deeper analysis"
  - Callout: **"⚠️ First hypothesis: Longer dwell = more damage risk → higher repair. Verify with Maintenance team."**

---

### **ISSUE 5: OPERATIONAL PATTERNS (เรื่องการออกเดินทาง)**
*"ตู้ส่วนใหญ่เข้ามาแล้วค้างกี่วัน? รูปแบบการเข้าเป็นยังไง?"*

#### Data Points Required:
**Dwell Profile by Day-of-Arrival & Day-of-Departure:**

```
Arrival Pattern (Day of Week)   % of Import   % of Export    Avg Dwell (days)
Mon-Wed                         [%]           [%]            [d]
Thu-Sat                         [%]           [%]            [d]
Sun (Holiday effect)            [%]           [%]            [d]

Departure Pattern (Grouped)     % completed   Avg dwell in group
Depart 3-5d (Fast)              [%]           [d]
Depart 6-10d (Normal)           [%]           [d]
Depart 11-20d (Delayed)         [%]           [d]
Depart >20d (Problem)           [%]           [d]
```

**Visual Approach:**
- 🎨 **Timeline view (like Gantt but simpler):**
  - Horizontal bars showing typical entry→exit dwell patterns
  - Mark free period (3d), normal zone (4-7d), warning zone (8-14d)
  - Annotation: "Most containers (X%) enter on weekday, exit by day 7. Y% stuck >30d (mostly Export)."

---

## 🎨 VISUAL DESIGN STRUCTURE (Infographic layout)

### **Layout Zones (Top to Bottom):**

```
┌─────────────────────────────────────────────────────┐
│ HEADER: "ทำไมรายได้ ทกท. เพิ่มขึ้น?"                  │
│ Subtitle: "และมันมีต้นทุนสูงแค่ไหน"                   │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ SECTION 1: "ตู้ค้างนาน | The Core Fact"           │
│ ┌──────────────────────────────────────────────────┐ │
│ │ Side-by-side comparison boxes:                   │ │
│ │ [FY65-67 BASELINE]     [FY69 CURRENT]            │ │
│ │ Import:  5.18d    →    5.72d  [+0.54d]          │ │
│ │ Export:  5.37d    →    5.92d  [+0.55d]          │ │
│ │                                                   │ │
│ │ 📈 Line chart below (very simple)                │ │
│ └──────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ SECTION 2: "ตู้ที่ค้างเกินกำหนด | Distribution"   │
│ ┌──────────────────────────────────────────────────┐ │
│ │ Stacked Bar Chart (3 bars = 3 periods):         │ │
│ │ [██ Green ██ Yellow ██ Red ██ Dark Red]          │ │
│ │                                                   │ │
│ │ Key callout box:                                 │ │
│ │ 🚨 "Export >30 days: 4.2× more containers"       │ │
│ └──────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ SECTION 3: "ผลต่อรายได้ | The Gain"               │
│ ┌──────────────────────────────────────────────────┐ │
│ │  [LARGE KPI CARD]                                │ │
│ │   ~115 ล้านบาท                                    │ │
│ │   Additional storage fee revenue (7 months 2569) │ │
│ │   ≈ 197 ล้านบาท / ปี (estimate)                 │ │
│ │                                                   │ │
│ │  Breakdown bar:                                  │ │
│ │  [Import: X ลบ.] [Export: Y ลบ.]                │ │
│ └──────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ SECTION 4: "ต้นทุน: ค่าซ่อม & การบำรุง | The Cost" │
│ ┌──────────────────────────────────────────────────┐ │
│ │ 2-column layout:                                 │ │
│ │ [Repair Cost]          [Question Mark]           │ │
│ │ FY65-67: X ลบ./mo     "Need Maintenance data"   │ │
│ │ FY69:    Y ลบ./mo     ⚠️ Hypothesis:             │ │
│ │ Δ: +Z%                Longer dwell → More        │ │
│ │                       damage → Higher repair     │ │
│ └──────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ SECTION 5: "รูปแบบการเข้าออก | The Pattern"       │
│ ┌──────────────────────────────────────────────────┐ │
│ │ Mini Gantt / Timeline visualization:            │ │
│ │ [Free 3d] [Normal 4-7d] [Delay] [Stuck >20d]   │ │
│ │                                                   │ │
│ │ Facts:                                           │ │
│ │ • Most arrive Mon-Wed                            │ │
│ │ • X% exit by day 7 (normal)                      │ │
│ │ • Y% stuck >30d (mostly Export)                  │ │
│ └──────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ FOOTER: Data sources, caveats, last updated date    │
└─────────────────────────────────────────────────────┘
```

---

## 🛠️ DATA EXTRACTION CHECKLIST

**From Uploaded Dashboard (Dwell_Time_Dashboard_2567-2569.html):**

- [x] Mean dwell per period (Import/Export, by FY)
- [ ] **EXTRACT:** Median dwell per period (if in chart object)
- [x] Revenue impact estimate (~115 ล้าน for 7m 2569)
- [ ] **EXTRACT:** Container count by dwell bracket (% in each range)
- [ ] **EXTRACT:** Repair/Maintenance cost trend (if available in dashboard)
- [ ] **EXTRACT:** Arrival/Departure day patterns (if chart exists)
- [ ] **EXTRACT:** Baseline period container volume (to calculate per-container impact)

---

## 💻 CLAUDE CODE PROMPT TEMPLATE

**For PDEE-AI (VS Code) execution:**

```
Task: Build Infographic Dashboard for "Dwell Time × Revenue Linkage"

Input:
- Framework file: This markdown
- Data source: Extracted from Dwell_Time_Dashboard_2567-2569.html
- Baseline period: FY2566-2567
- Comparison period: FY2568 & FY2569 (7m)

Output:
- File: infographic_dwell_revenue.html
- Format: Self-contained standalone (no external data files)
- Styling: glassmorphism + animated (use existing hub CSS variables)
- Interactivity: Hover tooltips, tab switches (Baseline ↔ Current)
- Responsive: Mobile-friendly (min 360px)

Design Philosophy:
✅ Simplicity first (no Mean/Median debate visible to user)
✅ Color-coded severity (Green/Yellow/Red/Dark Red)
✅ Large KPI cards for key numbers
✅ Minimal text, maximum visuals
✅ Tone: "This is interesting for business. Look."

Colors:
- Baseline/Historical: Gray (#888)
- Current/Positive Impact: Teal (#14b8a6)
- Warning/Caution: Amber (#f59e0b)
- Problem/Negative: Red (#ef4444)
- Distribution good (≤7d): Green (#10b981)
```

---

## 📋 NEXT STEPS

1. **Extract missing data points** from `Dwell_Time_Dashboard_2567-2569.html`
   - Dwell bracket distribution (%)
   - Repair cost comparison (if available)
   - Arrival/departure patterns

2. **Run Claude Code in VS Code** with this framework + extracted data

3. **Build `infographic_dwell_revenue.html`** following the layout above

4. **Test with non-technical audience** (quick 5-min feedback)

5. **Iterate:** Simplify further if any section confuses

---

**Created:** June 2026  
**Status:** Ready for VS Code + Claude Code execution  
**Framework Owner:** Palabordee (Port Authority Evaluation Division)
