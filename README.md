# CuraLabs OpenClaw Sales Agent Configuration

A 5-agent B2B sales pipeline built on [OpenClaw](https://github.com/open-claw/openclaw), implementing Kent Summers' "Facilitator" methodology. Clone this repo as your `~/.openclaw` directory and follow the setup steps below.

---

## Agent Team

| Agent | ID | Emoji | Role | Skills |
|-------|-----|-------|------|--------|
| **Scout** | `profiler` | 🔍 | Market Research, ICP Qualification, **Dispatcher** | icp-matching, buyer-identification, contact-retrieval |
| **Gatekeeper** | `offramp` | 🚪 | 2-Sentence Outreach, Fast-No Disqualification | two-sentence-outreach, early-offramp, inbound-triage |
| **Mapper** | `strategist` | 🗺️ | DMU Mapping, Stakeholder Widening | dmu-mapping, widening-scripts, reciprocity-planning |
| **Closer** | `facilitator` | ⚡ | Give/Get Meeting Prep, Pipeline Velocity | meeting-prep, buying-signal-detection, freezer-management |
| **Ledger** | `economist` | 📊 | COCA, Weighted Pipeline, Conversion Tracking | coca-calculation, weighted-pipeline, conversion-tracking |

### Pipeline Flow

```
You → Scout (dispatcher) → routes to appropriate agent
                    ↓
Research → Scout handles directly
Outreach → Gatekeeper
Strategy → Mapper
Deals    → Closer
Metrics  → Ledger
```

Scout is the default agent and dispatcher. When you send a message, Scout determines which agent should handle it and routes accordingly. Each agent can delegate to specific peers (see `subagents.allowAgents` in `openclaw.json`).

---

## Setup Instructions

> **These instructions are written so that a human OR a coding agent can follow them step by step.**

### Prerequisites

You need the following installed on your machine:

| Tool | Version | Install Command |
|------|---------|-----------------|
| Node.js | ≥ 22.12 | `brew install node` or [nodejs.org](https://nodejs.org) |
| OpenClaw CLI | latest | `npm install -g openclaw` |
| LiteLLM | latest | `pip3 install 'litellm[proxy]' google-cloud-aiplatform` |
| Google Cloud CLI | latest | `brew install google-cloud-sdk` or [cloud.google.com/sdk](https://cloud.google.com/sdk/docs/install) |

### Step 1: Clone this repo as your OpenClaw config directory

```bash
git clone <YOUR_REPO_URL> ~/.openclaw
```

> **Important:** The directory MUST be `~/.openclaw`. OpenClaw looks for its configuration there by default.

If you already have a `~/.openclaw` directory, back it up first:
```bash
mv ~/.openclaw ~/.openclaw.backup
git clone <YOUR_REPO_URL> ~/.openclaw
```

### Step 2: Install OpenClaw and LiteLLM

```bash
# Install OpenClaw CLI globally
npm install -g openclaw

# Install LiteLLM with Vertex AI support
pip3 install 'litellm[proxy]' google-cloud-aiplatform
```

### Step 3: Configure Google Cloud for Vertex AI

The agents use Claude Opus 4.6 via Google Vertex AI. You need a Google Cloud project with Vertex AI enabled.

```bash
# Log in to Google Cloud
gcloud auth login

# Set your Google Cloud account
gcloud config set account YOUR_EMAIL@YOUR_DOMAIN.com

# Set your Google Cloud project (must have Vertex AI API enabled)
gcloud config set project YOUR_GCP_PROJECT_ID

# Set application default credentials (required by LiteLLM)
gcloud auth application-default login --project YOUR_GCP_PROJECT_ID
```

**To enable Vertex AI on your project** (if not already enabled):
```bash
gcloud services enable aiplatform.googleapis.com --project YOUR_GCP_PROJECT_ID
```

### Step 4: Fill in your credentials in `openclaw.json`

Open `~/.openclaw/openclaw.json` and replace these placeholder values:

| Placeholder | What to put there | How to get it |
|-------------|-------------------|---------------|
| `YOUR_TELEGRAM_BOT_TOKEN` | Your Telegram bot token | Message [@BotFather](https://t.me/BotFather) on Telegram → `/newbot` → follow prompts → copy the token |
| `YOUR_GATEWAY_AUTH_TOKEN` | A random 48-character hex string | Run: `openssl rand -hex 24` |

**Example replacements:**
```json
"botToken": "1234567890:ABCdefGHIjklMNOpqrSTUvwxYZ"
```
```json
"token": "a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6"
```

> **If you don't want Telegram:** Set `"enabled": false` in the `channels.telegram` section and skip the bot token.

> **If you don't want iMessage:** Set `"enabled": false` in the `channels.imessage` section.

### Step 5: Start the LiteLLM proxy (Terminal 1)

This proxy translates OpenAI-format API calls into Vertex AI calls for Claude:

```bash
VERTEXAI_PROJECT=YOUR_GCP_PROJECT_ID \
VERTEXAI_LOCATION=us-east5 \
litellm --model vertex_ai/claude-opus-4-6 --port 18321 --drop_params
```

> **Note:** Change `us-east5` to your preferred Vertex AI region. The model must be available in that region.

Leave this terminal running.

### Step 6: Start the OpenClaw gateway (Terminal 2)

```bash
openclaw gateway
```

On first run, OpenClaw will:
- Auto-generate device identity files (`identity/device.json`, `identity/device-auth.json`)
- Auto-pair the CLI as an operator device (`devices/paired.json`)

Leave this terminal running.

### Step 7: Connect Telegram (optional)

If you configured a Telegram bot token:

1. Find your bot on Telegram and send it any message (e.g., "hello")
2. The bot will reply with a pairing code
3. In a new terminal, approve the pairing:
   ```bash
   openclaw pairing approve telegram <PAIRING_CODE>
   ```
4. Your Telegram user ID will be added to `credentials/telegram-allowFrom.json` automatically

### Step 8: Verify everything works

```bash
# Chat with the Scout agent (default dispatcher)
openclaw chat profiler

# Try asking it about the ICP
# Type: "What is our ideal customer profile?"

# Or send a message directly
openclaw agent --agent profiler --message "What industries are we targeting?" --local
```

You should get a response from Scout using the ICP data in `shared-canvas/icp-config.json`.

---

## Configuration Reference

### Model

- **Model:** Claude Opus 4.6 via Google Vertex AI
- **Proxy:** LiteLLM on `localhost:18321` translates OpenAI API → Vertex AI
- **Cost:** $15/M input tokens, $75/M output tokens

### Channels

| Channel | Default State | Notes |
|---------|--------------|-------|
| Telegram | Enabled | Requires bot token from @BotFather |
| iMessage | Enabled | Requires macOS with `imsg` CLI tool |
| CLI | Always available | `openclaw chat <agent_id>` |

### Agent Settings

- **Max Concurrent Agents:** 8
- **Max Concurrent Subagents:** 12
- **Heartbeat:** Every 30 minutes
- **Compaction Mode:** Safeguard

---

## ICP (Ideal Customer Profile)

The sales team targets businesses with **10-500 employees** and **5+ admin staff** across these industries:

1. **Professional Services** — Consulting, Accounting (CPA), Law, Architecture/Engineering
2. **Financial Advisory & Wealth Management** — RIAs, Independent advisors, Insurance agencies
3. **Healthcare & Medical Groups** — Multi-physician practices, Dental groups, PT chains
4. **Software & Technology** — SaaS companies (50-500 employees), Dev agencies, IT services
5. **Real Estate & Property Management** — Brokerages, Property management, Commercial RE
6. **Marketing & Creative Agencies** — Digital marketing, PR firms, Design studios

Full ICP criteria are in `shared-canvas/icp-config.json`.

---

## File Structure

```
~/.openclaw/
├── openclaw.json                          # Main config — agents, model, channels, gateway
├── README.md                              # This file
├── shared-canvas/
│   └── icp-config.json                    # ICP criteria used by sales agents
├── credentials/
│   ├── telegram-allowFrom.json            # Telegram user IDs allowed to message the bot
│   └── telegram-pairing.json              # Pending Telegram pairing requests
├── identity/
│   ├── device.json                        # Auto-generated device keypair
│   └── device-auth.json                   # Auto-generated auth tokens
├── devices/
│   ├── paired.json                        # Paired devices (CLI, web UI, etc.)
│   └── pending.json                       # Pending device pairing requests
├── agents/
│   ├── profiler/workspace/                # Scout — market research & dispatcher
│   │   ├── SOUL.md, IDENTITY.md, etc.
│   │   └── skills/
│   │       ├── icp-matching.md
│   │       ├── buyer-identification.md
│   │       └── contact-retrieval.md
│   ├── offramp/workspace/                 # Gatekeeper — outreach & disqualification
│   │   ├── SOUL.md, IDENTITY.md, etc.
│   │   └── skills/
│   │       ├── two-sentence-outreach.md
│   │       ├── early-offramp.md
│   │       └── inbound-triage.md
│   ├── strategist/workspace/              # Mapper — DMU mapping & widening
│   │   ├── SOUL.md, IDENTITY.md, etc.
│   │   └── skills/
│   │       ├── dmu-mapping.md
│   │       ├── widening-scripts.md
│   │       └── reciprocity-planning.md
│   ├── facilitator/workspace/             # Closer — deal management
│   │   ├── SOUL.md, IDENTITY.md, etc.
│   │   └── skills/
│   │       ├── meeting-prep.md
│   │       ├── buying-signal-detection.md
│   │       └── freezer-management.md
│   └── economist/workspace/               # Ledger — pipeline metrics
│       ├── SOUL.md, IDENTITY.md, etc.
│       └── skills/
│           ├── coca-calculation.md
│           ├── weighted-pipeline.md
│           └── conversion-tracking.md
├── cron/
│   └── jobs.json                          # Scheduled jobs (empty by default)
├── canvas/
│   └── index.html                         # Web UI canvas
├── completions/                           # Shell completions (auto-generated)
└── telegram/
    └── update-offset-default.json         # Telegram polling offset
```

---

## Customization

### Change the AI model

Edit the `models.providers` section in `openclaw.json`. The agents reference the model as `vertex-claude/vertex_ai/claude-opus-4-6`. To use a different model:

1. Update the model entry in `models.providers.vertex-claude.models`
2. Update `agents.defaults.model.primary` and each agent's `model` field
3. Restart the LiteLLM proxy with the new model name

### Disable a channel

Set `"enabled": false` in the relevant `channels` section:
```json
"channels": {
  "telegram": { "enabled": false, ... },
  "imessage": { "enabled": false, ... }
}
```

### Modify the ICP

Edit `shared-canvas/icp-config.json` to change target industries, company size, disqualifiers, buying triggers, etc.

### Add more agents

Add new entries to the `agents.list` array in `openclaw.json` and create corresponding `agents/<id>/workspace/` directories with SOUL.md and skill files.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `Connection refused on port 18321` | LiteLLM proxy isn't running. Start it (Step 5). |
| `Connection refused on port 18789` | OpenClaw gateway isn't running. Start it (Step 6). |
| `Vertex AI permission denied` | Run `gcloud auth application-default login` again. Check that Vertex AI API is enabled on your project. |
| `Telegram bot not responding` | Check bot token is correct. Run `openclaw pairing approve telegram <CODE>` to pair. |
| `Agent not found` | Make sure the agent's directory exists under `agents/` and its entry is in `openclaw.json`. |
| Identity files are empty | Normal on first clone. Run `openclaw gateway` — it auto-generates them. |
