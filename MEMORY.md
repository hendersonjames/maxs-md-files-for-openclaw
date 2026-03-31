# MEMORY.md — Max's Long-Term Memory

## Who I Am
- **Name:** Max
- **Role:** Chief of Staff & Business Partner
- **Reports to:** James Henderson
- **Platform:** OpenClaw (MiniMax/orbit model)
- **Channel:** Telegram (James's primary contact method)

---

## Who James Is
- **Name:** James Henderson
- **Location:** Orem, Utah, USA
- **Timezone:** MDT (UTC-6) — confirmed March 19, 2026 (Thursday his time; server shows March 20 Friday)
- **Communication style:** Direct, prefers honest pushback. Uses 👍 to acknowledge — don't over-respond.
- **Goal:** Build AI-powered products and services. Wants a genuine business partner, not a task runner.
- **Constraint:** Minimal budget right now. Free tools where possible.
- **Approval rule:** Nothing gets actioned externally without James's explicit approval.
- **Devices:** iPhone + Chromebook (no Mac)

---

## Projects

### Dev Environment
- **LeadHub repo (local):** `/workspace/LeadHub` — git push works directly (token in remote URL)
- **ChronaCare repo (local):** `/workspace/ChronaCare` — git push works directly
- **Dev notes:** `/workspace/DEV-NOTES.md`
- **Himalaya binary:** `~/bin/himalaya` (add `$HOME/bin` to PATH)
- **Himalaya config:** broken — getleadhub@gmail.com account blocked by Google; new email needed

---

### 1. LeadHub — AI Lead Gen + CRM for Contractors
- **Live URL:** https://ai-lead-gen-one.vercel.app ✅
- **GitHub:** github.com/hendersonjames/AiLeadGen
- **Phase 1 ✅** Auth + Supabase + Pipeline CRM
- **Phase 2 ✅** Save-to-pipeline from Lead Finder + Qualifier
- **Phase 3 ✅** Lead detail view (click card → full panel, stage movement, notes, AI report)
- **Phase 4 🔧** Vapi AI phone receptionist — AI answers calls ✅, webhook returning 500 (call data not saving to Supabase) — debugging tomorrow
- **Lead Finder:** Finds homeowner signals (storm damage, aging homes, permits, community posts)
- **Supabase:** ygtnqniplszcjdqnwgtw (LEADHUB project)
- **Next:** Fix Vapi webhook 500 error → then Admin panel

---

### 2. ChronaCare — AI Pill Reminder
- **Live URL:** https://ai-pill-reminder.vercel.app ✅
- **GitHub:** github.com/hendersonjames/AiPillReminder
- **Status:** LIVE — auth + cloud sync working ✅
- **Supabase:** qtnyrywhtashompuqqlf (CHRONACARE project)
- **Supabase URL:** https://qtnyrywhtashompuqqlf.supabase.co
- **Credentials:** /root/.openclaw/credentials/supabase-chronacare.env
- **Key differentiator:** Real-time AI medication suggestions as you type — no competitor does this
- **App name:** TBD — finalists: **Remedi** (top pick) and **RxBuddy** (James's picks)
- **Name change timing:** When custom domain is set up — do branding all at once
- **Next:** App Store prep (Privacy Policy, ToS, Capacitor wrapper, icons)

---

### 3. Freelance — Upwork + Fiverr + Freelancer.com
- **Status:** Gig profiles written, NOT posted — pending James review
- **File:** /workspace/memory/freelance-gigs-v2.md
- **Notion:** Notes → "Freelance Gigs — 3 Gigs × 3 Platforms"
- **3 Gigs:**
  1. AI-Powered Website for Small Business ($299/$597/$997)
  2. AI Phone Receptionist ($197/$397/$697)
  3. Business Automation with AI ($197/$447/$797)
- **Platforms:** Fiverr + Upwork + Freelancer.com (all three)
- **Audience:** Any small business — NOT limited to contractors
- **Strategy:** Website/phone/automation gig = front door → monthly retainer ($149-299/mo) = the business
- **Upwork hourly rate:** $65-85/hr
- **NOT posted yet** — James must approve before anything goes live

---

### 4. PA Platform — AI Staff Member for SMBs (Concept Stage)
- **Concept:** Vertical-specific AI "staff member" — not a tool, an AI employee
- **Core hook:** "Never miss a call. Never lose a lead." — AI phone answering 24/7
- **Pricing model:** $149-299/month subscription
- **Tech stack:** Vapi + Twilio + Gemini + Supabase + LeadHub
- **Prove with:** LeadHub contractors first, then expand to auto repair, real estate, insurance
- **Status:** Concept approved, LeadHub Phase 4 is the first implementation

---

## Infrastructure

### Hosting
- **Current:** MiniMax hosted OpenClaw
- **Plan:** Move to VPS end of March (finishing out the month on MiniMax)
- **VPS candidates:** Hetzner (better value) vs Hostinger (friendlier UI) — James comparing
- **Why moving:** More control, cost efficiency, flexibility for PA platform client deployments

### Cron Jobs
- Both daily briefings **DISABLED** (March 13) — were burning credits unnecessarily
  - Morning briefing ID: 5f1f710f-5455-41e0-a90d-38df8e4ec916 (disabled)
  - Evening wrap-up ID: 676c6ad3-aef6-4855-9b2f-480e81d3a67f (disabled)
- Re-enable when we're in a slower phase

### Email
- **qualityaisystems@gmail.com** — ✅ WORKING (set up March 19 James time / March 20 server)
- **Himalaya binary:** `/workspace/bin/himalaya` (v1.2.0)
- **Himalaya config:** `/workspace/himalaya-config.toml`
- **Credentials:** `/root/.openclaw/credentials/leadhub-email.env`
- **Usage:** `/workspace/bin/himalaya -c /workspace/himalaya-config.toml envelope list`

### Notion
- **Connected:** Max integration token saved at ~/.config/notion/api_key ✅
- **Workspace:** James Henderson's Workspace
- **Structure built:**
  - ⚡ Max HQ
    - 🏠 LeadHub → Vapi Setup Guide
    - 💊 ChronaCare → Launch Checklist (all done ✅, App Store prep ⬜)
    - 📋 Docs & Compliance → Setup Guides (Supabase, Vercel, GitHub)
    - 📝 Notes → Freelance Profiles (old + new v2)
    - 🔬 Research → Tool Stack inventory

---

## Tech Stack
- **Dev:** Google Antigravity (primary), GitHub (hendersonjames)
- **Hosting:** Vercel (free tier)
- **Database/Auth:** Supabase (free tier)
- **AI:** Google Gemini API (key: stored in credentials)
- **Phone AI:** Vapi ✅ account set up, assistant created, free number provisioned
- **Note-taking:** Obsidian + NotebookLM
- **Docs/Wiki:** Notion (connected ✅)
- **Password manager:** Bitwarden ✅ set up

---

## Credentials & Access
- **Supabase LeadHub:** /root/.openclaw/credentials/supabase-leadhub.env
- **Supabase ChronaCare:** /root/.openclaw/credentials/supabase-chronacare.env
- **GitHub token:** /root/.openclaw/credentials/github.env ⚠️ NEEDS ROTATION
- **Notion API key:** ~/.config/notion/api_key ✅
- **Gemini API key:** AIzaSyDsDkTCiEPIpaqx5QXSeKe_Jk4a_m5KTyM (in supabase-leadhub.env)

---

## Key Decisions Made
- **Coding autonomy (March 2026):** Max executes planned coding work without asking. Flag if scope goes significantly outside plan.
- **Sub-agent crew:** Dev Agent → self-tests → Test Agent (independent QA) → Max → James. See GUARDRAILS-PREP.md.
- **Emails & financials:** Always James's approval — no change.
- **James approves everything** — no autonomous external actions (except planned coding)
- **B2B only for LeadHub** — contractor is the customer, not the homeowner
- **Free stack first** — ship on free tiers, upgrade when revenue justifies
- **Freelance to fund** — Upwork + Fiverr + Freelancer.com as income bridge
- **3 gigs strategy** — website / phone / automation; any small business, not just contractors
- **Monthly recurring is the real business** — gigs are acquisition, retainer is revenue