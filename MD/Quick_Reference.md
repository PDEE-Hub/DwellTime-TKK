# 🚀 QUICK REFERENCE — Dwell Time × Revenue Infographic for VS Code

## **TL;DR: งานนี้คืออะไร?**

📊 **สร้าง 1 ไฟล์ HTML Infographic ที่อธิบาย:**
- ทำไมรายได้ ทกท. เพิ่มขึ้น? → **ตู้ค้างนาน (Dwell Time)**
- เพิ่มขึ้นกี่บาท? → **~115 ล้านบาท (7 months FY2569)**
- แต่มีต้นทุนสูงไหม? → **ยังไม่ชัด (need deeper analysis)**

---

## **5 ISSUES (แยกชัดเจน ไม่ปนกัน)**

### 1️⃣ **DWELL TIME WENT UP** ✅ Confirmed
| Period | Import | Export | Change |
|--------|--------|--------|--------|
| FY65-67 (Base) | 5.18d | 5.37d | — |
| FY69 (Current) | 5.72d | 5.92d | +0.54d / +0.55d |

**Visual:** Side-by-side boxes (ง่ายที่สุด) หรือ dual line chart

---

### 2️⃣ **DISTRIBUTION SHIFTED** 🚨 Export Alert
**Key finding:** Export >30d containers = **4.2× more** (ปีก่อน vs ตอนนี้)

**Visual:** Stacked horizontal bar (5 colors = 5 dwell ranges)
- Green (≤7d) | Amber (8-14d) | Orange (15-30d) | Red (>30d) | Dark Red (>30d Export)

---

### 3️⃣ **REVENUE IMPACT** 💰 The Gain
**Number:** **~115 ล้านบาท** (เก็บค่าฝากได้เพิ่ม)
- 7 months FY2569 data
- Extrapolated: ≈197 ล้านบาท/year

**Visual:** Large KPI card + monthly bar chart breakdown

---

### 4️⃣ **COST IMPACT** 🤷 Unknown (Hypothesis)
**Status:** Needs deeper analysis
- Repair costs fluctuate month-to-month
- Hypothesis: Longer dwell → more damage → higher repair
- **Action:** Correlate with dwell time

**Visual:** 2-panel (Revenue ✅ | Cost ❓) — Cost side marked as "TBD"

---

### 5️⃣ **OPERATIONAL PATTERN** 📅 When/How
**What:** When do containers arrive? When do they exit? How long do they stay?

**Visual:** Timeline / Gantt + Waterfall (shows dwell distribution flow)

---

## **FILES CREATED (ใช้ใน VS Code)**

```
/home/claude/
├── Infographic_DwellTime_Revenue_FRAMEWORK.md
│   └─ ยาว, detail, สำหรับ architecture
│
├── Issue_Decomposition_Dwell_Revenue.md
│   └─ ยาว, ชัดเจนทีละ issue, สำหรับ Claude Code execution
│
└── Quick_Reference.md
    └─ ไฟล์นี้ — อ่านเร็วก่อน
```

---

## **DATA AVAILABLE vs MISSING**

| Issue | Data Status | Source |
|-------|------|--------|
| 1️⃣ Dwell Time | ✅ **READY** | Dwell_Time_Dashboard_2567-2569.html |
| 2️⃣ Dwell Brackets (%) | ⚠️ **Need extract** | Same HTML file (in chart) |
| 3️⃣ Revenue Impact | ✅ **115 ล้าน READY** | v5 file states it |
| 4️⃣ Repair/Op Costs | ❓ **Need search** | Finance Dashboard (not uploaded) |
| 5️⃣ Entry/Exit Patterns | ⚠️ **Need extract** | Raw data or existing dashboard |

---

## **NEXT STEP: PROMPT FOR CLAUDE CODE**

```
Build infographic HTML for: "Dwell Time × Revenue Linkage — ทกท."

Input Framework: Issue_Decomposition_Dwell_Revenue.md

Data extracted from: Dwell_Time_Dashboard_2567-2569.html

Key Numbers (CONFIRMED):
  • FY65-67 baseline: Import 5.18d, Export 5.37d
  • FY69 current: Import 5.72d, Export 5.92d
  • Change: +~0.5d on both (+10%)
  • Revenue uplift: ~115 ล้าน (7m) / ~197 ล้าน (annual estimate)
  • Export >30d containers: 4.2× increase

Layout (5 sections):
  1. Dwell Time Comparison (side-by-side boxes)
  2. Dwell Distribution Shift (stacked bar, 5 colors)
  3. Revenue Gain (large KPI + monthly breakdown)
  4. Cost Impact (2-panel, Cost side marked TBD)
  5. Entry/Exit Pattern (timeline or waterfall)

Colors:
  - Baseline: #666
  - Current: #14b8a6 (teal)
  - Alert: #f59e0b (amber)
  - Problem: #d84040 (red)
  - Safe: #10b981 (green)

Tone: Business storytelling, NOT academic
Audience: Management + ops team (non-technical)
Output: Single HTML file (standalone, no external data)
```

---

## **VISUAL DESIGN QUICK TIPS**

✅ **DO:**
- Simplicity first (average dwell, not mean/median debate)
- Color coding severity (green/amber/red)
- Large KPI cards for numbers
- Callout boxes for insights
- Mobile responsive

❌ **DON'T:**
- Show density plots, histograms (too complex)
- Mix Mean/Median in visible area
- Small font, cramped layout
- Technical jargon
- Too many decimals (round to .5d or whole day)

---

## **KNOWN CAVEATS (ต้องเขียนไว้ที่ footer)**

1. ✏️ **Revenue uplift** = ค่าประมาณจาก หนังสือค่าภาระ ค.ศ.2543 (อัตราเดิม)
   - ยังไม่ได้ปรับอัตราใหม่
   - ยังไม่ใช่รายได้จริงในบัญชี

2. ✏️ **Repair cost correlation** = Hypothesis only
   - Need 24+ months trend data
   - Need to correlate with dwell by container type

3. ✏️ **Entry/Exit pattern** = If available in dashboard
   - If not available, can note "To be added in next version"

4. ✏️ **FY2569 data** = 7 months only (Oct 2568 - Apr 2569)
   - Not full year, extrapolation is estimate

---

## **VS CODE / CLAUDE CODE WORKFLOW**

### Step 1: Prepare Prompt
```
File: /home/claude/Issue_Decomposition_Dwell_Revenue.md
+ This Quick Reference
+ Uploaded HTML: /mnt/user-data/uploads/Dwell_Time_Dashboard_2567-2569.html

→ Copy-paste both framework files + reference into Claude Code
```

### Step 2: Run Claude Code
```bash
# In VS Code terminal:
cd /home/claude

# PDEE-AI will build:
# → /home/claude/infographic_dwell_revenue.html
```

### Step 3: Review Output
```
Expected output:
  ✅ 1 standalone HTML file
  ✅ 5 sections (dwell → distribution → revenue → cost → pattern)
  ✅ Responsive (mobile ≥ 360px)
  ✅ Color-coded severity
  ✅ No external data files needed
```

### Step 4: Test
- [ ] Open in browser (Chrome/Safari)
- [ ] Check mobile view (iPhone 12 size)
- [ ] Verify all numbers match source
- [ ] Share with 1 non-technical colleague → "What did you understand?" (should take ~2-3 min to grasp)

---

## **CUSTOMIZATION OPTIONS (If needed)**

**Language:**
- Thai (default for internal) ✅
- Can add English labels if international share

**Interactivity:**
- Tab switch: Baseline ↔ Current ✅
- Hover tooltips (optional)
- Export as PNG (optional)

**Data Update:**
- Hard-coded in HTML (current)
- OR connect to JSON (future)

---

## **SUCCESS CRITERIA**

✅ **This infographic is successful if:**

1. Non-technical person (colleague) reads it in <3 minutes and understands:
   - "Dwell time went up from ~5 to ~6 days"
   - "We collected ~115 ล้าน extra storage fees"
   - "But we don't know full cost impact yet"
   - "Export >30d is a problem (4.2× worse)"

2. Design is clean (not cluttered)

3. Numbers are verifiable (can trace back to source)

4. Tone is professional (not sensational)

---

## **FILE REFERENCES**

| File | Size | Purpose | Status |
|------|------|---------|--------|
| Dwell_Time_Dashboard_2567-2569.html | 84K | Source data + v5 summary | ✅ Uploaded |
| Infographic_DwellTime_Revenue_FRAMEWORK.md | — | Architecture + layout specs | ✅ Created |
| Issue_Decomposition_Dwell_Revenue.md | — | Detailed issue breakdown | ✅ Created |
| Quick_Reference.md | — | This file | ✅ Current |

---

## **OWNER & TIMELINE**

- **Owner:** Palabordee (Port Authority Evaluation Division)
- **Target Output:** infographic_dwell_revenue.html (standalone HTML)
- **Timeline:** 1-2 hours in Claude Code (est.)
- **Review:** Non-technical colleague feedback (30 min)
- **Final:** Ready to share with management by end of day

---

**Last Updated:** June 2026  
**Status:** 🟢 Ready for VS Code execution  
**Next Action:** Copy framework + Quick Reference → Claude Code prompt

---

## **QUICK COPY-PASTE PROMPT FOR CLAUDE CODE**

```
Prompt Title: Build Dwell Time × Revenue Infographic

I want to create an interactive infographic that explains why Bangkok Port 
(ทกท.) revenue increased from FY2566-2569. It's NOT because container volume 
increased, but because containers are staying in the yard LONGER.

Data Summary:
- Dwell time increased: Import +0.54d (5.18→5.72d), Export +0.55d (5.37→5.92d)
- Distribution shift: Export >30d containers = 4.2× more
- Revenue impact: ~115 ล้าน additional storage fee (7m FY2569)
- Cost impact: Unknown (hypothesis: longer dwell → more repairs needed)
- Pattern: Unclear entry/exit patterns (need to check if data available)

Use framework: Issue_Decomposition_Dwell_Revenue.md (in same directory)

Create: infographic_dwell_revenue.html
  • 5 sections (dwell comparison → distribution → revenue → cost → pattern)
  • Responsive mobile (≥360px)
  • Color-coded severity (Green/Amber/Orange/Red)
  • Tone: Business storytelling, not academic
  • Audience: ทกท. management + ops (non-technical)

Design style: Use existing hub theme colors if possible
  Colors: Baseline #666 | Current #14b8a6 | Alert #f59e0b | Problem #d84040
  Font: Use standard web fonts (no custom required)

Include: Data sources, last updated, caveats at footer
```

---

**Ready? → Paste this into Claude Code in VS Code and execute.**
