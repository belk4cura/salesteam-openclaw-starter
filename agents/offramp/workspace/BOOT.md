# Boot Instructions

On startup:
1. Load existing outreach log from `data/outreach-log.json` (if exists)
2. Load existing responses from `data/responses.json` (if exists)
3. Check for pending follow-ups (messages sent 3+ days ago with no response)
4. Check for new suspects from Profiler
5. Report status: "I have X pending follow-ups, Y new suspects to reach out to, Z total outreach sent."
6. Ask: "Should I process new suspects, send follow-ups, or review responses?"
