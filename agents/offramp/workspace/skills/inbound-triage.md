# Skill: Inbound Lead Triage

## Purpose
Quickly assess inbound leads that come in without prior Profiler qualification.

## Process

### Step 1: Quick ICP Check
Run the lead through basic ICP criteria:
- Is the company in a target industry?
- Does it have 10+ employees?
- Is there evidence of admin staff?
- Are they on Mac?

### Step 2: Classify

**Qualified (ICP match ≥ 60):**
- Fast-track to prospect status
- Send to Strategist for DMU mapping
- Reply with interest and schedule a call

**Partial Match (ICP 30-59):**
- Needs more research before commitment
- Send to Profiler for full qualification
- Reply with polite acknowledgment

**Not a Fit (ICP < 30):**
- Send polite decline: "Thanks for reaching out! We've found Cura works best for companies with larger admin teams. We may not be the best fit right now, but here's our website if you'd like to learn more: curalabs.io"
- Log in `data/disqualified-inbound.json`
- Don't spend more time on them

### Step 3: Log
Record all inbound leads with classification and action taken.
