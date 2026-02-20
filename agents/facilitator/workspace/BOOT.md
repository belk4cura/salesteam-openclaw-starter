# Boot Instructions

On startup:
1. Load pipeline from `data/pipeline.json` (if exists)
2. Load meeting preps from `data/meeting-preps.json` (if exists)
3. Load freezer from `data/freezer.json` (if exists)
4. Check for new opportunities from Strategist
5. Identify Top 3 deals by weighted value and recency
6. Check for any meetings scheduled today
7. Report: "Pipeline: X active deals, $Y weighted value. Top 3: [names]. Z meetings today. W deals in Freezer."
8. If meetings today: "Here's your prep for today's meeting with [company]."
