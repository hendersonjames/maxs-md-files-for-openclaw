# ChronaCare Launch Checklist
## Step-by-step to get the pill reminder app live

---

## ✅ ALREADY DONE (code is ready in GitHub)
- [x] Core app built (pills, reminders, snooze, AI chat, history)
- [x] Supabase auth added (email + Google OAuth)
- [x] Cloud sync added (pills save to Supabase, debounced, with status indicator)
- [x] Auth screen styled and ready
- [x] `supabase-schema.sql` written and ready to run
- [x] Code pushed to github.com/hendersonjames/AiPillReminder

---

## 🔲 STEP 1 — Create a New Supabase Project (5 min)
**James does this:**
1. Go to supabase.com → New Project
2. Name it: **CHRONACARE** (separate from LeadHub)
3. Set a strong password (save in Bitwarden when set up)
4. Region: US East
5. Once created, go to **Project Settings → API** and copy:
   - **Project URL** (`https://xxxxx.supabase.co`)
   - **anon/public key** (starts with `eyJ...` or `sb_publishable_...`)
6. Send both to Max

## 🔲 STEP 2 — Run the Database Schema (3 min)
**James does this:**
1. In Supabase → SQL Editor → New Query
2. Open github.com/hendersonjames/AiPillReminder → `supabase-schema.sql`
3. Copy all content → paste into SQL Editor → Run
4. Should see: `pills` table created with RLS policies
5. Confirm in Table Editor → pills table visible

## 🔲 STEP 3 — Deploy to Vercel (5 min)
**James does this:**
1. Go to vercel.com → New Project
2. Import repo: `hendersonjames/AiPillReminder`
3. Before clicking Deploy, add environment variables:
   - `VITE_SUPABASE_URL` = (URL from Step 1)
   - `VITE_SUPABASE_PUBLISHABLE_KEY` = (anon key from Step 1)
   - `GEMINI_API_KEY` = `AIzaSyDsDkTCiEPIpaqx5QXSeKe_Jk4a_m5KTyM`
4. Click Deploy
5. Send Max the Vercel URL

## 🔲 STEP 4 — Fix Supabase Auth Settings (2 min)
**James does this (same fix as LeadHub):**
1. Supabase → Authentication → URL Configuration
2. Set Site URL to the Vercel URL from Step 3
3. Add Vercel URL + `/**` to Redirect URLs
4. Authentication → Email Auth → turn OFF email confirmation
5. Save

## 🔲 STEP 5 — Test the App (5 min)
**James + Max together:**
1. Open the Vercel URL
2. Sign up with email + password
3. Add a pill (should see real-time AI suggestions as you type)
4. Set a reminder time
5. Check Supabase Table Editor → pills table → should see the entry
6. Sign out → sign in again → pills should still be there (cloud sync working)

---

## OPTIONAL NEXT STEPS (Phase 2)
- [ ] **App name decision** — pick final name before App Store submission
- [ ] **Apple Developer Program** — $99/year, needed for App Store submission
- [ ] **Convert to React Native/Expo** — needed for true mobile push notifications
- [ ] **Push notifications** — most valuable feature for a reminder app
- [ ] **Google OAuth** — needs Google Cloud project (James setting up)
- [ ] **Family sharing** — let caregivers track medications for loved ones
- [ ] **Refill reminders** — alert when supply is running low
- [ ] **Doctor export** — PDF of medication history to share with doctor

---

## App Name Ideas (current: ChronaCare)

**Existing names already taken:**
- MediSafe, DoseCast, EveryDose, MyTherapy, CareZone, Pillo, CareClinic, MyDoses

**New name candidates (likely available):**
| Name | Vibe | Notes |
|------|------|-------|
| **Remedi** | Smart, friendly | "Remedy" + "Reminder" blended — clever, easy to say |
| **PillSage** | Intelligent, calm | Sage = wisdom + AI, clear what it does |
| **MedGenie** | Friendly, AI-forward | Genie suggests instant smart help |
| **DoseWise** | Trustworthy | Wisdom + dosing, sounds reliable |
| **Vitapill** | Positive, health-forward | Vita = life, feels uplifting |
| **PillPal** | Casual, friendly | Very approachable — probably needs availability check |
| **RxBuddy** | Friendly | Rx = medical, Buddy = companion |
| **MedMate** | Simple, clear | Medication + mate (companion) |

**Max's top pick: Remedi** — it's a real word (remedy) that implies the app fixes the forgetting problem, AND it contains "reminder" phonetically. Memorable, searchable, and unique.

---
*Checklist created by Max — March 13, 2026*
*Ready to execute when James creates the Supabase project*
