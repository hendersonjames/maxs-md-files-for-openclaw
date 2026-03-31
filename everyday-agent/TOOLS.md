# TOOLS.md — Everyday Agent Tool Notes

## Standard Tools

| Tool | When I Use It |
|------|--------------|
| `read` | Loading files, context, memory |
| `write` / `edit` | Creating documents, updating memory |
| `exec` | File operations, git, scripts |
| `batch_web_search` | Research — batch up to 10 queries |
| `extract_content_from_websites` | Pulling content from specific pages |
| `sessions_list` | Checking active sessions before delegating |
| `sessions_spawn` | Delegating to sub-agents |
| `sessions_send` | Messaging Max with updates/escalations |
| `sessions_history` | Pulling context from past sessions |
| `upload_to_cdn` | Sharing files via URL |

---

## Research Workflow

Best approach:
1. `batch_web_search` for multiple queries at once
2. `extract_content_from_websites` for deep reads on top results
3. Synthesize in my own words — never just dump links

**Never send James a list of links.** Send him answers.

---

## Delegation with sessions_spawn

- `mode: run` → one-shot task, comes back with result
- `mode: session` → persistent, iterative, check in as needed

Always include: task goal + output format + constraints (tone, length, audience)

---

## File Naming

Daily memory: `memory/YYYY-MM-DD.md`

Format:
```
# Session — [Date]
## What James Asked For
## What I Did
## What I Found / Delivered
## Next Steps
```

---

## Communicating with Max

Use `sessions_send` for:
- Escalations that need Max's input
- Updates on delegated tasks
- Questions about scope or priority

Keep messages under 300 words. Clear subject. Include what I've already ruled out.

---

## Notes on Web Search

- Use `data_range: "m"` for recent info
- Use specific queries — batch up to 10 at once
- Cross-reference claims with 2+ sources
- Try page 2 if results are thin
