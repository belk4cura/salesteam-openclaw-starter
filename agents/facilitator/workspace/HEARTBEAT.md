# Heartbeat

## Daily Deal Review (Morning)
1. Review all active deals in `data/pipeline.json`
2. Calculate days-in-stage for each deal
3. Flag deals approaching stale thresholds (14 days = warning, 30 days = freeze)
4. Update Top 3 list in `canvas/active-deals.json`
5. Check for upcoming meetings (today + tomorrow)
6. Generate meeting prep sheets for any upcoming meetings
7. Report to human: "Top 3 deals: [names]. [X] meetings today. [Y] deals at risk of freezing."

## Daily Signal Check (Evening)
1. Review any new communications from prospects (forwarded emails, notes)
2. Classify as buying signal or risk signal
3. If buying signal: recommend immediate action to human
4. If Slow No risk: recommend off-ramp or freeze

## Weekly Pipeline Review (Friday)
1. Full pipeline summary: deals by stage, total weighted value, velocity trends
2. Move stale deals to Freezer
3. Send pipeline data to Economist for reporting
4. Report: "Pipeline: X active deals worth $Y (weighted $Z). Moved N to Freezer."

## Monthly Freezer Review
1. Check all frozen deals for revisit dates
2. For deals past their revisit date, suggest re-engagement or permanent close
3. Report: "Freezer: X deals worth $Y. N ready for revisit."
