# Credit Management Plan
## Why You Ran Out + How to Fix It

---

## What's Eating Credits

### 1. Daily Cron Briefings (Biggest drain)
Two cron jobs fire every day as **isolated AI sessions**:
- **Morning briefing** (10 AM MT) — generates a full AI analysis, AI news, priorities
- **Evening wrap-up** (9:30 PM MT) — generates a full end-of-day debrief

Each one runs for ~200 seconds = a full AI session. That's **2 heavy AI sessions per day**, every day, whether or not you're actively using the app. On a 5,000 credit/month plan, these alone could consume a large chunk.

### 2. Our Active Conversations
Each message exchange uses credits. Long, complex responses (like code generation, research) cost more than short ones.

### 3. OpenClaw vs Gemini API (separate buckets)
- **OpenClaw credits** = what powers our conversations and briefings
- **Gemini API** = what powers the LeadHub app features (charged to James's Google account separately)
These are independent — running out of one doesn't affect the other.

---

## Recommendations (pick what works for you)

### Option A — Pause the daily briefings (saves most)
Disable the two cron jobs. I'll brief you when you ask, or when I notice something genuinely important and reach out proactively. Since we've been actively chatting, the scheduled briefings are mostly duplicating what we already discuss.

**Savings estimate:** ~60% credit reduction

### Option B — Simplify the briefings (save some, keep routine)
Keep the crons but change them to fire short, light messages (5 bullet points max, no AI news research unless you ask). Reduces tokens dramatically while keeping the daily rhythm.

**Savings estimate:** ~40% credit reduction

### Option C — Move briefings to heartbeat (smarter)
Use the heartbeat system (checks every 30 min) instead of isolated cron sessions. Only triggers a real AI response when something needs attention. Silent otherwise.

**Savings estimate:** ~50% credit reduction + smarter

---

## Other Credit-Saving Habits

**For our conversations:**
- Shorter questions = shorter answers = fewer tokens
- "Yes/no" acknowledgments don't burn much — 👍 reactions are even better
- Ask for summaries instead of deep analysis unless you need it

**For the apps:**
- LeadHub currently uses `gemini-2.5-flash` for Lead Finder and `gemini-2.5-pro` for Qualifier
- Switching Qualifier to `gemini-2.5-flash` would cut Gemini API costs ~80% with minimal quality loss
- These come from James's Google AI Studio credit pool, not OpenClaw

---

## My Recommendation

**Do Option A (pause briefings) for now.** We're actively working together every day — the automated briefings are redundant and expensive. When we're in a slower phase (app is deployed, not actively building), turn them back on.

**Say the word and I'll disable both cron jobs immediately.**

---
*Analysis by Max — March 13, 2026*
