# Skill: Buying Signal Detection

## Purpose
Analyze prospect communications (emails, meeting notes, chat messages) to identify buying signals and Slow No risks.

## Buying Signals (Score: +1 to +3 per signal)

### Strong Buying Signals (+3)
- Asks about pricing, seat counts, or licensing
- Asks about implementation timeline or onboarding process
- Introduces you to additional stakeholders unprompted
- Shares internal budget cycle information
- Requests a pilot or trial
- Asks about contract terms or SLA
- Mentions a specific start date or deadline

### Moderate Buying Signals (+2)
- Asks detailed technical questions (integration, security, data handling)
- Shares specific pain points with examples
- Compares you to competitors (means they're evaluating seriously)
- Asks about customer references or case studies
- Forwards your materials to colleagues internally
- Attends meetings with prepared questions

### Weak Buying Signals (+1)
- Responds promptly to emails
- Agrees to next meeting
- Asks general questions about the product
- Visits the website (if tracking is in place)

## Slow No / Risk Signals (Score: -1 to -3 per signal)

### Strong Risk Signals (-3)
- "Management is reviewing" (with no timeline)
- Cancels or reschedules 2+ times
- Goes silent for 14+ days after engagement
- "We've decided to handle this internally"
- Budget was cut or frozen
- Key champion leaves the company

### Moderate Risk Signals (-2)
- "Send me more info" (without committing to next step)
- "We're evaluating several options" (non-specific)
- "Let me think about it" (no specific follow-up date)
- Only communicates via email (avoids calls)
- Meeting attendance drops (fewer people each time)

### Weak Risk Signals (-1)
- Slow email responses (3+ days)
- Asks same questions repeatedly (not progressing)
- Vague about timeline
- Defers to unnamed others ("I need to check with my team")

## Scoring
Sum all signal scores. Interpret:
- **Score 7+:** HOT — prioritize this deal, push for close
- **Score 4-6:** WARM — keep momentum, address any risk signals
- **Score 1-3:** LUKEWARM — needs action to re-engage
- **Score 0 or below:** COLD — consider Freezer

## Output
```json
{
  "deal_id": "deal-xxx",
  "signal_score": 8,
  "classification": "HOT",
  "buying_signals": ["Asked about pricing (+3)", "Introduced VP of IT (+3)", "Asked about Q2 start (+2)"],
  "risk_signals": ["Slow email response (-1)"],
  "recommended_action": "Push for proposal. They're ready.",
  "urgency": "high"
}
```
