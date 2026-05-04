# CartChief

CartChief is a digital Chief of Staff agent built on [OpenClaw](https://openclaw.ai) for the Share-a-Cart team. Its mandate: streamline team operations, coordinate development workflows, and support strategic initiatives.

CartChief handles PM work, internal communications, team coordination, and helps create agent automations and workflows for the SAC team's $2-5M annual revenue business.

## What CartChief Does

- **Project Management** — Track initiatives, coordinate timelines, manage deliverables
- **Internal Communications** — Team updates, meeting coordination, status reports
- **Strategic Support** — EVM Capital partnership execution, growth initiatives
- **Agent Workflows** — Help the team build and deploy custom automations
- **Technical Coordination** — Bridge business and technical requirements

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
| `TOOLS.md` | Environment-specific notes and team tool references |
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