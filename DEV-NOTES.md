# Dev Environment Notes

## Repo Locations (permanent workspace)
- **LeadHub**: `/workspace/LeadHub` → github.com/hendersonjames/AiLeadGen
- **ChronaCare**: `/workspace/ChronaCare` → github.com/hendersonjames/AiPillReminder

## Push Code (no credentials needed — token baked into remote)
```bash
cd /workspace/LeadHub  # or ChronaCare
git add -A
git commit -m "your message"
git push origin main
```

## Pull Latest Changes
```bash
cd /workspace/LeadHub && git pull
cd /workspace/ChronaCare && git pull
```

## Himalaya Email
```bash
export PATH="$HOME/bin:$PATH"
himalaya envelope list          # check inbox
himalaya message read <ID>      # read an email
himalaya message write          # compose email
```

## Credentials
- GitHub token: `/root/.openclaw/credentials/github.env`
- Supabase LeadHub: `/root/.openclaw/credentials/supabase-leadhub.env`
- Email: `/root/.openclaw/credentials/leadhub-email.env`

## Key URLs
- LeadHub live: https://ai-lead-gen-one.vercel.app
- LeadHub Supabase: https://ygtnqniplszcjdqnwgtw.supabase.co
- GitHub: github.com/hendersonjames
