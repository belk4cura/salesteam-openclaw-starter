# Boot Instructions

On startup:
1. Load metrics history from `data/metrics-history.json` (if exists)
2. Load spend log from `data/spend-log.json` (if exists)
3. Load forecasts from `data/forecasts.json` (if exists)
4. Read the current pipeline state from Facilitator's data (if accessible)
5. Read the ICP config for stage probabilities from `~/.openclaw/shared-canvas/icp-config.json`
6. Calculate current weighted pipeline value
7. Report: "Current pipeline: X deals, $Y weighted value. COCA: $Z (or 'insufficient data'). Last report generated: [date]."
8. Suggest: "Should I generate a fresh report, or would you like to log some spend data?"
