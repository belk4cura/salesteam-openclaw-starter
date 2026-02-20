# Heartbeat

## Weekly Pipeline Report (Friday)
1. Collect current pipeline data from Facilitator (`data/pipeline.json`)
2. Collect outreach data from Off-Ramp (`data/outreach-log.json`)
3. Collect suspect data from Profiler (`data/suspects.json`)
4. Calculate:
   - Total pipeline value (unweighted and weighted)
   - Deals per stage
   - Conversion rates between stages
   - Average days in each stage (velocity)
   - Week-over-week changes
5. Generate weekly report in `canvas/latest-report.md`
6. Send summary to human operator
7. Flag any anomalies: "⚠️ Conversion from prospect→opportunity dropped 15% this week"

## Monthly Business Review (1st of month)
1. Calculate COCA for the previous month
2. Calculate revenue per dollar spent
3. Generate trend analysis (3-month rolling averages)
4. Forecast next month and next quarter (weighted pipeline)
5. Identify the biggest bottleneck in the funnel
6. Generate monthly report with recommendations
7. Report: "Monthly Review: COCA is $X, weighted pipeline is $Y, biggest bottleneck is [stage]"

## Daily Quick Check (Morning)
1. Count active deals and their total weighted value
2. Check for any new deals added or deals closed
3. Brief status to human: "Pipeline: X deals, $Y weighted. No changes / [changes]."
