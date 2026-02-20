# Skill: Freezer Management

## Purpose
Manage stalled deals by moving them out of active pipeline focus and into a long-term nurture sequence. The Freezer prevents wasted time and emotional attachment to dead deals.

## Kent Summers' Rule
**"Treat expensive opportunities like perishable food."**
Deals that sit on the counter too long go bad. Put them in the Freezer before they spoil — and before you waste precious time on them that should go to live opportunities.

## Freezer Thresholds

### Warning (14 days no activity)
- Flag the deal in daily review
- Alert the human: "[Company] hasn't had activity in 14 days. Should we take action or freeze?"
- Suggest a specific re-engagement action (send a piece of candy, ask a direct question)

### Freeze (30 days no activity)
- Move the deal to `data/freezer.json`
- Remove from Top 3 and active pipeline focus
- Set a revisit date (90 days from freeze)
- Send Off-Ramp a notification to send the prospect a polite check-in later
- Alert the human: "[Company] moved to Freezer. Revisit date: [date]."

### Permanent Close (180 days in Freezer with no response to revisit)
- Move to `closed_lost` status
- Archive the deal record
- Log the reason: "Frozen for 180 days, no response to revisit attempts"

## Revisit Process
When a frozen deal hits its revisit date:
1. Check if the company still matches ICP (they might have changed)
2. Check if the champion is still at the company (LinkedIn)
3. If still relevant: send a brief, no-pressure check-in via Off-Ramp
4. If company changed or champion left: close permanently

## Freezer Reporting
Track:
- Number of deals in Freezer
- Total value of frozen deals
- Average time in Freezer before revisit
- Revisit success rate (how many come back to active)
- Most common freeze reason

## Rules
- NEVER keep more than 3-5 deals in active focus. Everything else should be in Freezer or not yet in pipeline.
- Frozen deals get ZERO active attention. Only revisit on schedule.
- Don't let the human "check in" on frozen deals. Redirect them to active deals.
