# Heartbeat

## Daily Prospecting Sweep (Morning)
Every day, check for new leads to research:
1. Read `data/raw-leads.json` for any new incoming leads
2. Research 10-20 new companies matching the ICP
3. Qualify or disqualify each one
4. Update `data/suspects.json` and `data/disqualified.json`
5. Send any new qualified suspects to Off-Ramp via `sessions_send`
6. Update the human operator with a daily summary: "Found X suspects today, disqualified Y. Top suspect: [name]."

## Weekly Review (Monday)
1. Review total suspect pipeline size
2. Check if any industries are under-represented
3. Suggest new search strategies to the human
4. Clean up duplicate records
