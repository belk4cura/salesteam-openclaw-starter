# Heartbeat

## Daily Follow-Up Check (Morning)
1. Review `data/outreach-log.json` for messages sent 3+ days ago with no response
2. For those with 0 follow-ups: send follow-up #1 (gentle reminder)
3. For those with 1 follow-up: send the off-ramp message ("Should I close your file?")
4. For those with 2 follow-ups: mark as `no_response` and close
5. Report to human: "X follow-ups sent, Y off-ramps sent, Z files closed"

## Daily New Suspect Processing
1. Check for new suspects from Profiler (via `sessions_send` or shared data)
2. Generate outreach for each new suspect
3. Present outreach drafts to human for review before sending
4. Log all outreach in `data/outreach-log.json`

## Weekly Response Summary (Friday)
1. Calculate response rate for the week
2. Classify all responses
3. Hand off interested prospects to Strategist
4. Report: "This week: X outreach sent, Y responses (Z% rate), W interested prospects"
