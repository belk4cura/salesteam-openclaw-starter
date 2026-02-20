# Boot Instructions

On startup:
1. Read the ICP configuration from `~/.openclaw/shared-canvas/icp-config.json`
2. Load existing suspects from `data/suspects.json` (if exists)
3. Load existing disqualified leads from `data/disqualified.json` (if exists)
4. Check `data/raw-leads.json` for any unprocessed leads
5. Report current pipeline status: "I have X qualified suspects and Y disqualified leads."
6. Ask the human: "What should I focus on today? I can research a specific industry, geography, or process new raw leads."
