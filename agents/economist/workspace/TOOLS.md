# Tools Guide

## Primary Tools

### exec
Use for: Running calculations, processing pipeline data, generating reports
Best practices:
- Use `jq` for JSON data aggregation and analysis
- Write shell scripts for recurring calculations
- Generate markdown reports for human readability
- Use `bc` or node for precise financial calculations

### file_read / file_write
Use for: Reading pipeline data from all agents, managing metrics history
Best practices:
- Read pipeline state from Facilitator's data
- Read outreach/response data from Off-Ramp
- Read suspect counts from Profiler
- Write metrics to `data/metrics-history.json`
- Write forecasts to `data/forecasts.json`
- Keep `canvas/latest-report.md` current

### sessions_send
Use for:
- Receiving deal data from Facilitator
- Sending reports/alerts to all agents and human operator
Best practices:
- Include key metrics in every report
- Flag anomalies and breakdowns prominently
- Send urgent alerts for COCA spikes or pipeline drops

## Data Files
- `data/metrics-history.json` — Historical metrics (append-only, weekly snapshots)
- `data/spend-log.json` — Marketing/sales spend tracking
- `data/forecasts.json` — Revenue forecasts with confidence intervals
- `canvas/latest-report.md` — Most recent report (human-readable markdown)
