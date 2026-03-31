# Alarm & Snooze — Issues Analysis + Fix Plan
## ChronaCare / Remedi
## Analysis by Max — March 18, 2026

---

## What's Broken and Why

### The Core Problem: This Is a Web App
The current alarm system uses `setInterval` inside a browser tab. This means:

| Scenario | Alarms Work? |
|----------|-------------|
| Browser tab open, screen on, user interacted | ✅ Yes |
| Browser tab open but phone screen off | ❌ No |
| Browser tab in background (other app open) | ❌ Unreliable |
| Browser tab closed | ❌ No |
| Phone locked | ❌ No |

**For a pill reminder app, most of the critical use cases involve the app NOT being open.** This is the fundamental problem.

### Issue 1 — Web Audio API Blocked on Mobile
`soundService.ts` creates an `AudioContext` at module load time. On iOS Safari and most mobile browsers, AudioContext requires a user gesture (tap) to start. Creating it on load means it starts in "suspended" state. Even though the code calls `audioContext.resume()`, on iOS this often silently fails without a direct user interaction in the same call stack.

**Result:** No sound plays on iPhone/Safari even when the tab is open.

### Issue 2 — No Browser Notification
The app plays a sound but never shows a system notification pop-up. Even in a web context, the Browser Notification API (`Notification.requestPermission()`) would show a visible alert. Without it, if the user's volume is low or they're not looking at the screen, they miss the reminder entirely.

### Issue 3 — Reminder Refire Bug
The reminder check fires once per minute at the exact minute boundary. If a user marks a dose as "taken" and then un-marks it (toggles back), the interval won't re-fire for that minute — it already passed. The reminder only fires again the next day at the same time.

### Issue 4 — Snooze After Reminder Fires
When a snooze expires (30-second check), the `snoozedUntil` is cleared. But the reminder checker already passed that minute — so the alarm won't re-sound until the NEXT scheduled time (next day). The snooze "unsnooze" is silent, which defeats the purpose.

---

## The Real Fix: Capacitor + Local Notifications

The only way to make pill reminders actually work on mobile is to use **native local notifications** — the same system iOS/Android apps use. These:
- Work when the app is completely closed
- Work when the phone screen is off
- Show up in the notification center
- Make the phone vibrate and sound
- Don't depend on the browser tab being open

**The plugin:** `@capacitor/local-notifications`

With Capacitor, we schedule a local notification for each reminder. iOS/Android handles delivery — even if Remedi is not running.

```
User sets reminder: "Metformin at 8:00 AM, every day"
  → Capacitor schedules recurring local notification
  → iOS/Android delivers it at 8:00 AM regardless of app state
  → User taps notification → opens app → marks as taken
```

---

## Interim Fixes for Web Version (While Capacitor Is Being Set Up)

These don't solve the fundamental limitation but improve the experience for users who keep the tab open:

### Fix 1 — Add Browser Notification API
Request notification permission on first login. Show a system notification when a reminder fires (in addition to sound). At least catches users who aren't looking at the screen.

### Fix 2 — Fix AudioContext on Mobile
Move AudioContext creation to inside the `playSound()` function, triggered only by user interaction (or use a lazy singleton). Resume it properly with user gesture detection.

### Fix 3 — Fix Snooze Re-fire
After snooze expires, immediately re-trigger the alarm (sound + notification), not just clear the flag.

### Fix 4 — Add Clear Warning to Users
Add a visible banner: "For reliable reminders, keep this tab open. Download the app for full notification support." Honest is better than broken.

---

## Capacitor Migration Plan

### What Capacitor Does
Capacitor wraps the existing React web app in a native iOS/Android shell. The web code stays the same — Capacitor adds a bridge to native device features.

### Steps
1. **Install Capacitor** into the ChronaCare repo
2. **Add iOS + Android projects** (`npx cap add ios`, `npx cap add android`)
3. **Install plugins:**
   - `@capacitor/local-notifications` — replaces the Web Audio alarm system
   - `@capacitor/haptics` — vibration on reminder
   - `@capacitor/app` — handle app state (background/foreground)
4. **Replace `soundService.ts`** with Capacitor local notification scheduling
5. **Schedule notifications** when reminders are saved/edited, cancel when deleted
6. **Test on device** (requires Mac + Xcode for iOS)
7. **Build for App Store**

### What Stays the Same
- All React components
- All Supabase integration
- All UI/UX
- All AI features

### What Changes
- Alarm delivery method (local notifications instead of Web Audio)
- Need Xcode on a Mac to build iOS binary (or use a cloud build service like Expo EAS or Bitrise)

### No Mac Solution
Since James doesn't have a Mac, iOS builds can be done via:
- **Ionic Appflow** — cloud CI/CD for Capacitor (free tier available)
- **Bitrise** — cloud build for iOS/Android
- **GitHub Actions + Fastlane** — free with Apple Developer account

### Build Order
1. Interim web fixes (3-4 hours) — add Browser Notifications, fix AudioContext
2. Capacitor setup + Android build (2-3 days) — Android doesn't need a Mac
3. Cloud iOS build setup (1-2 days)
4. App Store submission prep

---

## Summary

| Problem | Root Cause | Fix |
|---------|-----------|-----|
| Alarms don't work on mobile | Web app can't run background tasks | Capacitor local notifications |
| No sound on iOS | AudioContext blocked without user gesture | Fix lazy init + add Browser Notification API |
| Snooze doesn't re-alarm | Interval already passed | Re-trigger alarm on snooze expiry |
| App needs to stay open | Fundamental web limitation | Capacitor wraps app natively |

**Bottom line: The alarm system needs Capacitor to actually work for a real pill reminder app. This is the same conclusion we reached for App Store submission — Capacitor solves both problems at once.**

---
*Analysis by Max — March 18, 2026*
