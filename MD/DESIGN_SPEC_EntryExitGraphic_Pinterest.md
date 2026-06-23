# 🎨 VISUAL DESIGN SPEC
## Entry-Exit Pattern: Container Behavior Change (Pinterest Aesthetic)

---

## 📌 DESIGN CONCEPT

**Goal:** Show behavioral change visually
- **Before:** Typical entry-exit pattern (Tue in → Fri out)
- **After:** Current pattern (Thu in → Mon afternoon out)
- **Insight:** Entry day changes → triggers different dwell behavior

**Aesthetic:** Modern, minimal, Pinterest-style
- Clean typography (Google Fonts: Inter, Poppins)
- Color-coded severity (Green/Amber/Red)
- Generous whitespace
- 2-column layout (Before | After)
- Smooth animations (if interactive)

---

## 🎯 LAYOUT STRUCTURE

```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│  🕐 Container Entry & Exit Behavior                         │
│     How port customers' pickup patterns changed              │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  BEFORE (FY 2566-2567)      │      AFTER (FY 2569)         │
│  ──────────────────────     │     ──────────────────       │
│                             │                              │
│  [Timeline 1]               │      [Timeline 2]            │
│  Mon Tue Wed Thu Fri        │      Mon Tue Wed Thu Fri     │
│  [visual timeline]          │      [visual timeline]       │
│                             │                              │
│  Entry: Tue (typical)       │      Entry: Thu (earlier)    │
│  Dwell: 3 days             │      Dwell: 4-5 days         │
│  Exit: Fri (on time)        │      Exit: Mon (delayed)     │
│                             │                              │
│  ✅ Normal flow             │      ⚠️ Pattern shift        │
│                             │                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Key Insight Box                                            │
│  "Entry day shifted earlier, but exit delayed by 3 days"   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎨 COLOR PALETTE

| Element | Color | Usage |
|---------|-------|-------|
| Monday-Friday (weekday) | `#3B82F6` (Blue) | Normal business day |
| Saturday-Sunday (weekend) | `#F59E0B` (Amber) | Weekend (no activity) |
| Entry day (normal) | `#10B981` (Green) | Expected entry |
| Entry day (changed) | `#D84040` (Red) | Early entry (unexpected) |
| Dwell zone (safe) | `#10B981` (Green) | ≤7 days |
| Dwell zone (warning) | `#F59E0B` (Amber) | 8-14 days |
| Dwell zone (problem) | `#D84040` (Red) | 15+ days |
| Background | `#FAFAFA` (Off-white) | Clean canvas |
| Text primary | `#1F2937` (Dark gray) | Main text |
| Text secondary | `#6B7280` (Light gray) | Supporting text |

---

## 📐 TYPOGRAPHY

```
Font Family: Inter (Google Fonts)
            + Poppins (headings)

Hierarchy:
  Title:        Poppins 28px, Bold, Dark gray
  Subtitle:     Inter 16px, Regular, Light gray
  Timeline Day: Inter 14px, Medium, Blue (Mon-Fri) / Amber (Sat-Sun)
  Label:        Inter 13px, Regular, Dark gray
  Annotation:   Inter 12px, Regular, Light gray
  
Spacing:
  Title → Subtitle:     12px
  Subtitle → Content:   24px
  Before | After gap:   32px
  Item spacing:         16px
```

---

## 🕐 TIMELINE VISUALIZATION (Two versions)

### **VERSION A: Linear Timeline Bar** (Simple, Clean)

```
BEFORE PATTERN:

Mon         Tue         Wed         Thu         Fri         Sat         Sun
[   ]       [ENTRY]     [DWELL]     [DWELL]     [EXIT]      [   ]       [   ]
            ✅ Entry    2 days      waiting     ✅ Exit
            (morning)               (normal)    (Friday)
                        └─── ~3 days total ───┘

Timeline bar: 
  - Each day = equal width rectangle
  - Mon: light gray (empty)
  - Tue: GREEN (entry point, indicator ▼)
  - Wed-Thu: BLUE (dwell period, slightly darker)
  - Fri: GREEN (exit point, indicator ▲)
  - Sat-Sun: AMBER (weekend, hatched pattern)


AFTER PATTERN:

Mon         Tue         Wed         Thu         Fri         Sat         Sun
[   ]       [   ]       [   ]       [ENTRY]     [DWELL]     [DWELL]     [DWELL]
                                    ⚠️ Early    1 day       weekend     waiting
                                    entry       wait        (stuck)     →
                                                                        next Mon?
            └──────────────── 4-5+ days ────────────────────→

Timeline bar:
  - Mon-Wed: light gray
  - Thu: AMBER/RED (early entry, unexpected)
  - Fri: BLUE (dwell starts)
  - Sat-Sun: AMBER (weekend, hatched)
  - continues → Monday (delayed exit)
  
Annotation: "3 days longer, crosses weekend"
```

### **VERSION B: Compact Calendar Heatmap** (More visual)

```
BEFORE:                          AFTER:

Week Grid:                       Week Grid:

Mon Tue Wed Thu Fri Sat Sun      Mon Tue Wed Thu Fri Sat Sun
 ☐   🟢  🔵  🔵  🟢  ☐   ☐       ☐   ☐   ☐  🟠  🔵  🟠  🟠
                                              ↓ entry early
Entry:  Tue morning                         ↓ stuck over weekend
Exit:   Fri afternoon                       → Exit Mon (delayed)

Legend:
  ☐ = No activity
  🟢 = Entry/Exit (Green)
  🔵 = Dwell (Blue)
  🟠 = Weekend or Delay (Amber/Red)
```

---

## 🎯 COMPARISON BOX (Below Timeline)

```
┌────────────────────────────────────────────────────────────┐
│                                                              │
│  BEFORE               │            AFTER                    │
│  ────────────────────│────────────────────                 │
│                      │                                      │
│  Entry Day: Tuesday  │  Entry Day: Thursday ⚠️             │
│  (typical time)      │  (earlier than expected)            │
│                      │                                      │
│  Dwell: 3 days       │  Dwell: 4-5+ days ⚠️               │
│  (normal range)      │  (longer, crosses weekend)         │
│                      │                                      │
│  Exit: Friday        │  Exit: Monday Afternoon 🔴          │
│  (on schedule)       │  (delayed after weekend)           │
│                      │                                      │
│  ✅ Pattern:         │  🔴 Pattern:                        │
│  Predictable         │  Unpredictable (weekend effect)    │
│                      │                                      │
└────────────────────────────────────────────────────────────┘
```

---

## 💡 KEY INSIGHT BOX (Bottom)

```
┌────────────────────────────────────────────────────────────┐
│                                                              │
│  🔍 What Changed?                                           │
│                                                              │
│  1. Importers entering containers earlier (Thu vs Tue)    │
│     → Might indicate rush cargo or new business pattern   │
│                                                              │
│  2. Weekend trap: Fri/Sat entry → no exit activity       │
│     → Sunday closed → exit delayed to Monday              │
│                                                              │
│  3. Delayed exit: Monday afternoon vs Friday              │
│     → 3 extra days average                                │
│     → Potential: Customs delay, doc processing, importer │
│                                                              │
│  Next: Investigate which importers have this pattern      │
│                                                              │
└────────────────────────────────────────────────────────────┘
```

---

## 📱 RESPONSIVE BEHAVIOR

```
Desktop (1200px+):
  - 2-column layout (Before | After) side by side
  - Full timeline bars visible
  - All labels readable

Tablet (768px-1199px):
  - Stack to 1 column if needed
  - Scale timeline proportionally
  - Adjust spacing

Mobile (< 768px):
  - Single column
  - Smaller timeline
  - Stacked comparison boxes
  - Readable font size (≥12px)
```

---

## ✨ ANIMATION / INTERACTIVITY (Optional)

```
Hover state (desktop):
  - Timeline bar highlights on hover
  - Tooltip shows: "Entry: Thu 08:00 AM"
  - Dwell period color intensifies
  - Exit indicator emphasizes

Tap state (mobile):
  - Click timeline → shows detail popup
  - Swipe to compare Before/After
  
Loading:
  - Smooth fade-in for timeline
  - Staggered animation: Entry → Dwell → Exit
  - Duration: 0.8-1.2 seconds
```

---

## 🎯 EXECUTION OPTIONS

### **Option 1: Figma Design** (Most beautiful)
- Designer creates vector mockup
- Export as PNG/SVG for presentation
- Reusable for reports
- Takes: 2-4 hours

### **Option 2: HTML/CSS Interactive** (Functional + Pretty)
- Responsive, works on all devices
- Can be embedded in dashboard
- Interactive hover/tap states
- Takes: 1-2 hours

### **Option 3: Canva Template** (Quickest)
- Use Pinterest-inspired template
- Drag-and-drop customization
- Ready to present in 30 min
- Export as PNG/PDF

---

## 📊 SAMPLE DATA TO VISUALIZE

```
BEFORE Pattern (FY2566-2567 Baseline):
├─ 35% of containers: Mon entry → Thu exit (3 days) ✅ Optimal
├─ 40% of containers: Tue entry → Fri exit (3 days) ✅ Optimal
├─ 20% of containers: Wed entry → Mon next (5 days) ⚠️ Weekend trap
└─ 5% of containers: Any day → 10+ days 🔴 Stuck

AFTER Pattern (FY2569 Current):
├─ 25% of containers: Mon entry → Thu exit (3 days) ✅ Still fast
├─ 30% of containers: Tue entry → Fri exit (3 days) ✅ Still fast
├─ 30% of containers: Wed entry → Mon next (5-6 days) ⚠️ Growing
└─ 15% of containers: Thu/Fri entry → Mon next (5-8 days) 🔴 Growing stuck
```

**Key observation:** Weekend entry/exit behavior has become dominant (30%→45%)

---

## 🎨 DESIGN INSPIRATION SOURCES

- Pinterest: "data visualization timeline"
- Modern infographic style: Clean, minimal, high contrast
- Color psychology: Green (good) → Amber (caution) → Red (problem)
- Example layouts:
  - Canva's timeline templates
  - Behance data visualization projects
  - Dribbble "timeline infographic" designs

---

**Design Status:** 📝 SPECIFICATION READY  
**Next Step:** Choose execution option (Figma / HTML / Canva)  
**Estimated Time:** 30 min (Canva) → 4 hours (Figma)
