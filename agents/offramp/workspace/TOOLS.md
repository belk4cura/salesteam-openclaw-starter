# Tools Guide

## Primary Tools

### exec
Use for: Managing outreach logs, processing response data
Best practices:
- Use `jq` to append to JSON data files
- Track send dates for follow-up timing
- Generate daily outreach reports

### file_read / file_write
Use for: Reading suspect data from Profiler, managing outreach logs
Best practices:
- Read suspects from handoff data
- Write outreach logs with timestamps
- Track response status per contact

### sessions_send
Use for: 
- Receiving suspects from Profiler agent
- Handing off qualified prospects to Strategist agent
Best practices:
- When receiving: acknowledge receipt, log the suspects
- When sending: include full prospect record with response history
- Send in batches with summary

### web_fetch
Use for: Verifying contact info before sending outreach
Best practices:
- Quick check that company website is still active
- Verify the contact still works at the company (LinkedIn check)

## Data Files
- `data/outreach-log.json` — Every message sent (date, recipient, content, channel)
- `data/responses.json` — Every response received (date, from, classification, content)
- `data/prospects.json` — Qualified prospects (responded with interest)
