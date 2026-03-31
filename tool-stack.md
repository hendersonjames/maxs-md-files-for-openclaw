# LeadHub + Workspace Tool Stack
## Complete Tool Inventory
### Compiled by Max — March 13, 2026

---

## 🏗️ BUILD STACK (What the apps run on)

| Tool | Purpose | Status | Cost |
|------|---------|--------|------|
| **Google Antigravity** | Primary dev environment | ✅ Active | Free |
| **GitHub** (hendersonjames) | Version control, code storage | ✅ Active | Free |
| **Vercel** | App hosting + deployment | ✅ Active (LeadHub live) | Free tier |
| **Supabase** (LEADHUB project) | Database + auth | ✅ Active | Free tier |
| **React / TypeScript / Vite** | Frontend framework | ✅ Active | Open source |

---

## 🤖 AI & SEARCH APIS

| Tool | Purpose | Status | Cost |
|------|---------|--------|------|
| **Google Gemini API** | Core AI — lead analysis, qualification, chat | ✅ Active (key stored) | Pay-per-use |
| **Gemini grounding (Google Search)** | Real-time web search for lead signals | ✅ Active | Included w/ Gemini |
| **Gemini Thinking Mode** | Complex strategy + business planning | ✅ Active | Pay-per-use |

### Google Tools to Add

| Tool | Purpose | Priority | Notes |
|------|---------|----------|-------|
| **Google Maps / Places API** | Find properties, validate addresses, map leads | 🔴 High | Needed for contractor landing pages + lead mapping |
| **Google My Business API** | Pull contractor profiles, reviews, gaps | 🟡 Medium | Key for admin panel — find contractors to sell to |
| **Gmail API** | Read/send email from workspace (Max's email access) | 🟡 Medium | Read-only first; pairs with Himalaya |
| **Google Calendar API** | Schedule follow-ups, job appointments | 🟡 Medium | Phase 4 feature |
| **Google Sheets API** | Export leads to spreadsheet for contractors | 🟢 Low | Nice-to-have |
| **Google Analytics** | Track LeadHub app usage | 🟢 Low | Add after launch |

---

## 📧 EMAIL (Himalaya)

| Tool | Purpose | Status | Notes |
|------|---------|--------|-------|
| **Himalaya CLI v1.2.0** | Terminal email client — Max reads/sends email | ✅ Installed at `/tmp/himalaya` | Needs Gmail config |
| **Gmail IMAP/SMTP** | Backend for Himalaya | ⏳ Needs James to set up App Password | james76036@gmail.com |
| **SendGrid** (future) | Transactional email — notify contractors of new leads | 🔲 Not started | $0 for 100 emails/day |

**To activate email access — James needs to do 2 steps:**
1. Go to myaccount.google.com → Security → 2-Step Verification → App Passwords
2. Create an App Password for "Mail" on "Other device" — name it "Max"
3. Share the 16-character password with me → I'll configure Himalaya and can start monitoring email

*Note: James must explicitly approve this before any email access is granted.*

---

## 💬 OUTREACH & NOTIFICATIONS (Planned)

| Tool | Purpose | Priority | Cost |
|------|---------|----------|------|
| **Twilio** | SMS/text contractors when a new lead arrives | 🔴 High (Phase 4) | ~$0.01/SMS |
| **SendGrid** | Email notifications to contractors | 🔴 High (Phase 4) | Free up to 100/day |
| **Telegram Bot** (existing) | James's command channel to Max | ✅ Active | Free |

---

## 🕵️ LEAD SOURCING TOOLS (For Facebook/Community Scraping)

| Tool | Purpose | Status | Notes |
|------|---------|--------|-------|
| **Gemini + Google Search** | Scrapes public web incl. Facebook public groups | ✅ Active | Works now, limited depth |
| **Facebook Graph API** | Access public page posts, groups (limited) | 🔲 Not started | Requires FB app approval |
| **Apify** | Professional web scraping (Facebook, Nextdoor, Craigslist) | 🔲 Evaluate | $49/month for basic |
| **SerpAPI / Serper.dev** | Google search results API (homeowner queries) | 🔲 Evaluate | $50/month or free tier |
| **Craigslist scraper** | "Services needed" posts in local areas | 🔲 Evaluate | Free, no official API |

**Recommended first:** Use Gemini Search grounding (already active) to scan Facebook public groups + community pages. Add Apify only if we need deeper access.

---

## 💰 PAYMENTS (When we monetize)

| Tool | Purpose | Priority | Cost |
|------|---------|----------|------|
| **Stripe** | Contractor subscriptions, one-time payments | 🔴 High (Phase 5) | 2.9% + $0.30/transaction |
| **Stripe Billing** | Recurring monthly subscriptions | 🔴 High (Phase 5) | Included with Stripe |

---

## 📋 BUSINESS / OPERATIONS

| Tool | Purpose | Status | Cost |
|------|---------|--------|-------|
| **Obsidian** | James's personal knowledge base | ✅ Active | Free |
| **NotebookLM** | Deep research + document analysis | ✅ Active | Free |
| **GitHub Projects** | Task tracking for app dev | 🔲 Not set up | Free |
| **Notion** | Strategy docs, PRDs, roadmap | 🔲 Not set up | Free |
| **Bitwarden** | Password manager | 🔲 Pending | Free |

---

## 🚀 FREELANCE INCOME (Upwork + Fiverr)

| Tool | Purpose | Status |
|------|---------|--------|
| **Upwork** | Primary freelance platform | 🔲 Profiles drafted, not posted |
| **Fiverr** | Secondary freelance platform | 🔲 Profiles drafted, not posted |
| **LeadHub (live app)** | Portfolio piece to show clients | ✅ Live at ai-lead-gen-one.vercel.app |

---

## 📱 FUTURE: MOBILE (ChronaCare + LeadHub Mobile)

| Tool | Purpose | Priority |
|------|---------|----------|
| **Expo / React Native** | Cross-platform mobile app | 🔴 High for ChronaCare |
| **Apple Developer Program** | App Store submission | ~$124/year |
| **Supabase Push Notifications** | Pill reminders on mobile | ChronaCare Phase 2 |

---

## 🗺️ PRIORITY ORDER FOR NEXT INTEGRATIONS

1. **Himalaya email** — install skill, connect james76036@gmail.com (Max can then monitor email)
2. **Google Maps/Places API** — needed for landing pages + property search
3. **Twilio SMS** — contractor lead notifications (high retention value)
4. **SendGrid** — transactional email (lead alerts, welcome emails)
5. **Facebook Graph API or Apify** — community lead scraping at scale
6. **Stripe** — when first contractor is ready to pay
7. **Google Calendar** — schedule follow-ups from pipeline

---

## 🔐 CREDENTIALS (All stored securely)

| Service | Location |
|---------|---------|
| Supabase LeadHub | `/root/.openclaw/credentials/supabase-leadhub.env` |
| GitHub PAT | `/root/.openclaw/credentials/github.env` ⚠️ needs rotation |
| Gemini API Key | `/root/.openclaw/credentials/supabase-leadhub.env` |
| Telegram Bot Token | OpenClaw config |

---

*Compiled by Max — March 13, 2026*
*Ready for James's review*
