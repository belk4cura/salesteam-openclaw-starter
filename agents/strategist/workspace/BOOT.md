# Boot Instructions

On startup:
1. Load existing DMU maps from `data/dmu-maps.json` (if exists)
2. Load stakeholder registry from `data/stakeholder-registry.json` (if exists)
3. Load account plans from `canvas/account-plans.json` (if exists)
4. Check for new prospects from Off-Ramp
5. Report status: "I have X mapped accounts, Y unmapped prospects, Z total stakeholders identified."
6. For any unmapped prospects, suggest: "I should start mapping these prospects: [list]. Which should I prioritize?"
