# CartChief

CartChief is a digital Chief of Staff agent built on [OpenClaw](https://openclaw.ai) for the Share-a-Cart team. Its mandate: streamline team operations, coordinate development workflows, and support strategic initiatives.

CartChief handles PM work, internal communications, team coordination, and helps create agent automations and workflows for the SAC team's $2-5M annual revenue business.

## What CartChief Does

### Cart Operations
- Create carts from natural language requests
- Retrieve carts by ID and merge multiple carts
- Monitor cart activity across 200+ supported retailers
- Delete carts and manage cart lifecycle

### Org Intelligence (Slack)
- Post 9am daily digest to `#all-sac` (what shipped, what's blocked, key metrics)
- Post morning CEO briefing to `#priv-exec` (cart vol, MRR delta, one blocker)
- Surface open PRs, roadmap items, and build queue in `#priv-engineering`
- Answer questions about API docs, MCP specs, and SAC architecture in `#priv-dataroom`

### Customer Outreach
- Draft outbound prospect emails in `#priv-gtm` for human approval before send
- Execute approved sends via `#agent-community-mgr`
- Log replies and surface warm leads back to the GTM channel
- Suggest follow-up responses based on reply content

### Analytics
- Pull and summarize Google Analytics — traffic, conversions, top referrers
- Pull and summarize Shopify analytics — orders, revenue, top products
- Monitor cart creation and share activity across the 200+ supported retailers
- Flag anomalies (drops in cart vol, traffic spikes, approval backlogs)

### Subscription & Billing
- Check subscription offer eligibility by store, plan tier, and cart value
- Surface upgrade prompts for Pro-eligible users

### Admin / Org Management
- List and filter org users by role
- Submit carts for approval and route to the right approver
- Approve or reject carts with notes
- Pull org-level cart analytics by date range, requester, or vendor

CartChief is triggered via:

- **Slack DM or channel mention** — Direct team communication and support
- **Heartbeat checks** — Proactive monitoring and updates
- **Cross-session coordination** — Orchestrate multiple agent workflows

This agent was originally deployed as follows:

- **OpenClaw Instance** — Running on team infrastructure
- **Slack** — Connected via Socket Mode for team communication  
- **Model** — Powered by Anthropic Claude Sonnet for strategic thinking
- **Mandate** — Configured as Chief of Staff with team context and permissions

To replicate this setup, follow the steps below.

## Deployment

### Option 1: XO (Recommended)

Go to [beta.xo.builders](https://beta.xo.builders) and create a new agent instance. Name it `cartchief-agent` or similar.

### Option 2: Self-Host

Install OpenClaw locally:

```bash
npm install -g openclaw
openclaw gateway
```

Clone this repo into your OpenClaw workspace:

```bash
git clone https://github.com/MateoDev/cartchief-agent ~/.openclaw/workspace
```

Or copy the files manually into your agent's workspace directory.

## Slack Setup

Follow the official guide to create your Slack app and get your tokens:
👉 [Connect Slack to OpenClaw](https://docs.xo.builders/agents/openclaw/channels/connect-slack#create-the-slack-app)

Steps:

1. Go to [api.slack.com/apps](https://api.slack.com/apps) → Create New App → From a manifest
2. Paste the manifest from the guide (enables Socket Mode + all required bot scopes)
3. Install to Workspace → copy Bot Token (`xoxb-...`)
4. Basic Information → App-Level Tokens → generate with `connections:write` → copy App Token (`xapp-...`)

## Model Configuration

CartChief works with any LLM provider supported by OpenClaw. Anthropic Claude is recommended for strategic thinking and complex coordination tasks.

| Provider | Models | Get API Key |
|----------|--------|-------------|
| Anthropic ⭐ Recommended | claude-sonnet-4-5, claude-haiku-3-5 | [console.anthropic.com](https://console.anthropic.com) |
| OpenAI | gpt-4o, gpt-4o-mini | [platform.openai.com](https://platform.openai.com) |
| Google | gemini-1.5-pro, gemini-1.5-flash | [aistudio.google.com](https://aistudio.google.com) |

Create `~/.openclaw/openclaw.json` — never commit this file, it contains your credentials:

```json
{
  "env": {
    "ANTHROPIC_API_KEY": "your-anthropic-key-here"
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "anthropic/claude-sonnet-4-20250514"
      }
    }
  },
  "channels": {
    "slack": {
      "enabled": true,
      "mode": "socket",
      "botToken": "xoxb-your-bot-token",
      "appToken": "xapp-your-app-token",
      "dmPolicy": "open",
      "groupPolicy": "open",
      "allowFrom": ["*"],
      "ackReaction": "zap"
    }
  },
  "plugins": {
    "entries": {
      "anthropic": { "enabled": true },
      "slack": { "enabled": true, "config": {} }
    }
  }
}
```

## Knowledge Base Setup

CartChief's effectiveness comes from having access to your company's context and documentation. Here's how to set up the knowledge base without exposing sensitive data:

### 🔒 Private Document Management

**What CartChief Needs Access To:**
- Company policies and procedures
- Product documentation and roadmaps
- Team processes and workflows
- Strategic documents and OKRs
- Historical decisions and context

**✅ Secure Setup Options:**

#### Option 1: XO RAG/VectorDB (Recommended)
- Upload documents directly to your XO instance dashboard
- Documents stay private to your agent instance
- Automatic embedding and retrieval
- No code repository involved

#### Option 2: Local Knowledge Base
- Store documents in `knowledge/` directory (add to `.gitignore`)
- Use OpenClaw's memory system for context
- Keep sensitive files local only

#### Option 3: Private Document References
- Create `KNOWLEDGE_INDEX.md` with document titles/topics
- Store actual documents in private Google Drive/Notion
- Agent can ask you to retrieve specific documents when needed

### 📝 Document Categories for CartChief

Create this structure in your private knowledge base:

```
knowledge/
├── company/
│   ├── mission-vision-values.md
│   ├── organizational-chart.md
│   └── company-policies.md
├── products/
│   ├── share-a-cart-overview.md
│   ├── technical-architecture.md
│   └── roadmap-2024.md
├── processes/
│   ├── development-workflow.md
│   ├── release-process.md
│   └── meeting-cadence.md
├── partnerships/
│   ├── affiliate-programs.md
│   └── vendor-relationships.md
└── metrics/
    ├── kpi-definitions.md
    ├── reporting-schedule.md
    └── dashboard-links.md
```

### 🚨 Security Guidelines

**Never commit to public repos:**
- Customer data or PII
- Financial information
- API keys or credentials
- Internal strategy documents
- Legal agreements or contracts

**Safe to include in repos:**
- Process templates (without specific data)
- Configuration examples
- Public-facing documentation
- General workflow descriptions

## Agent Initialization

On first run, DM CartChief in Slack from your admin account and tell it:

```
"You are CartChief — your job is to serve as digital Chief of Staff for the Share-a-Cart team. Read SOUL.md, USER.md, and AGENTS.md to understand your role and responsibilities."
```

This initializes CartChief's context. Team members can then interact with it for project coordination, strategic support, and workflow automation.

## File Structure

| File | Purpose |
|------|---------|
| `SOUL.md` | CartChief's core personality and operating principles |
| `AGENTS.md` | Session startup rules, memory structure, team interaction patterns |
| `USER.md` | Team context, member info, confidentiality rules |
| `IDENTITY.md` | Agent name, role, emoji branding |
| `HEARTBEAT.md` | Proactive monitoring and background task config |
| `TOOLS.md` | SAC-specific endpoints, credentials, and configuration |
| `CARTCHIEF_PERSISTENT.md` | MCP connection rules, tool usage, and output formats |
| `CHANNELS.md` | Slack channel strategy, posting rules, and escalation |
| `OUTREACH.md` | Email workflows, approval process, and lead management |
| `ANALYTICS.md` | Analytics integration, monitoring, and anomaly detection |
| `knowledge/metrics/` | KPI definitions, reporting schedules, and dashboard links |
| `memory/` | Daily logs and persistent memory files |

## Team Automation Capabilities

CartChief can help the SAC team create and deploy various automations:

### Development Workflows
- **Code review coordination** — Automated PR notifications and review assignments
- **Release management** — Deploy coordination and stakeholder updates
- **Issue triage** — Automated labeling and assignment based on team capacity

### Business Operations
- **Revenue monitoring** — Automated reports on affiliate performance
- **Partner communications** — EVM Capital updates and milestone tracking  
- **Team metrics** — Productivity dashboards and goal tracking

### Strategic Initiatives
- **90-day execution support** — EVM Capital partnership milestone management
- **Growth experiment coordination** — A/B test planning and results analysis
- **Risk diversification** — Platform dependency monitoring and mitigation planning

## Example Interactions

### Project Coordination
```
@CartChief Can you create a timeline for the Q2 revenue diversification initiative? Include EVM milestones and team capacity constraints.
```

### Automation Requests
```
@CartChief Set up a workflow that notifies the team when affiliate revenue drops 10% day-over-day and suggests immediate actions.
```

### Strategic Support
```
@CartChief Prepare a weekly summary for Ed covering team progress, blockers, and EVM partnership status. Keep it confidential.
```

## Links

- [OpenClaw](https://openclaw.ai) — AI agent platform
- [XO](https://xo.builders) — Agent hosting  
- [Share-a-Cart](https://share-a-cart.com) — The business CartChief supports
- [EVM Capital](https://evm.capital) — Strategic partner