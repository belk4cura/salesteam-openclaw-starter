# Tools Guide

## Primary Tools

### exec
Use for: Processing pipeline data, generating meeting prep sheets, calculating deal metrics
Best practices:
- Use `jq` for JSON data manipulation
- Generate markdown meeting prep documents
- Calculate days-in-stage for velocity tracking
- Automate Freezer threshold checks

### file_read / file_write
Use for: Managing pipeline, meeting preps, freezer lists
Best practices:
- Read deal data from `data/pipeline.json`
- Write meeting prep sheets to `data/meeting-preps.json`
- Manage the Freezer in `data/freezer.json`
- Keep `canvas/active-deals.json` current with Top 3

### sessions_send
Use for:
- Receiving mapped opportunities from Strategist
- Sending deal data to Economist for analytics
- Alerting the human about buying signals or Slow No risks
Best practices:
- Include full deal record with every handoff
- Send urgency flags for time-sensitive signals
- Include recommended actions

### sessions_spawn
Use for: Spawning sub-tasks for complex deal analysis
Best practices:
- Spawn analysis of email threads for signal detection
- Spawn meeting prep generation for multiple deals simultaneously

## Data Files
- `data/pipeline.json` — Full pipeline state (all active deals)
- `data/meeting-preps.json` — Generated meeting preparation sheets
- `data/freezer.json` — Frozen/stalled deals
- `canvas/active-deals.json` — Top 3 active deals (current focus)
