# Doctor Report Feature — Product Spec
## Remedi / ChronaCare — Phase 2 Feature
## Spec by Max — March 18, 2026

---

## Overview

A shareable medication adherence report that users can bring to a doctor's appointment or share via email. Shows what medications are being taken, how consistently, and any patterns worth discussing.

**Value:** Doctors ask "are you taking your medications?" — this gives a real, data-backed answer. MyTherapy offers this and it's one of their most-loved features.

**Legal framing:** "Your personal medication log" — not "medical records." Always include disclaimer: generated from self-reported data, for personal reference only.

---

## What the Report Shows

### Section 1 — Medication Summary
- Medication name + dosage
- Scheduled frequency (e.g., "Daily at 8:00 AM, 9:00 PM")
- Report period (last 30 days / last 90 days — user selects)

### Section 2 — Adherence Rate (Per Medication)
- % of scheduled doses taken on time
- Visual indicator (e.g., green/yellow/red)
- Example: "Metformin 500mg — 87% adherence (last 30 days)"

### Section 3 — Calendar View
- Monthly grid showing each day
- Color-coded: green = all doses taken, yellow = partial, red = missed, gray = not scheduled
- At a glance: "I was good most of the month except that week of the 14th"

### Section 4 — Detailed History Log
- Chronological list of every dose event
- Taken / Snoozed / Missed
- Date + time

### Footer — Disclaimer
"This report was generated from self-reported data entered by the user in the Remedi app. It is intended for personal reference only and is not a substitute for professional medical advice, diagnosis, or treatment. Data accuracy depends on consistent app usage."

---

## Technical Requirements

### Data We Already Have ✅
- Pill name, dosage
- Reminder times + days of week (to calculate scheduled doses)
- History log (taken / snoozed events with timestamps)

### Data Gap ⚠️ — Need to Build
**Missed dose tracking is not currently implemented.**

Right now we only log when a user marks a dose as taken or snoozed. We do NOT log when a dose was scheduled but the user did nothing. To calculate true adherence rate we need to track missed doses.

**Fix:** Add a daily midnight check that compares scheduled doses against the history log and records any unactioned reminders as "missed." This runs client-side when the app is opened.

### Adherence Calculation
```
Scheduled doses in period = 
  (# of days in period where daysOfWeek matched) × (# of reminders per pill)

Taken doses = count of history entries with action='taken' in period

Adherence % = (Taken / Scheduled) × 100
```

### Export Options
- **Print/PDF:** `window.print()` with print-optimized CSS — works on all devices, no extra libraries
- **Share (Phase 2):** Generate a unique shareable link (stored in Supabase) that expires after 7 days

---

## UI/UX

- Accessible from main screen via "Report" button in header or settings menu
- User selects: time period (30 days / 90 days / custom)
- User selects: which medications to include (default all)
- Clean, professional layout — designed to be legible on paper if printed
- Print button + Share button

---

## Build Estimate
- Missed dose tracking logic: 1 day
- Report component (UI): 2 days
- Print/PDF CSS: 0.5 day
- Shareable link system: 2 days (optional Phase 2)

**Total MVP (print only, no shareable link): ~3.5 days**

---

## Monetization Angle
This is a natural **premium feature**:
- Free: reminders + basic history
- Premium ($2.99/mo or $19.99/yr): Doctor reports + family sharing + export
- Positions the app as genuinely useful, not just a timer

---
*Spec by Max — March 18, 2026*
