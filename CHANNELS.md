# CHANNELS.md - SAC Slack Channel Strategy

## Channel Map

### Public Channels
- **`#all-sac`** - Team-wide updates, daily digest, general announcements

### Private Channels
- **`#priv-exec`** - CEO briefings, executive decisions, high-level strategy
- **`#priv-engineering`** - PRs, roadmap items, build queue, technical discussions
- **`#priv-dataroom`** - API docs, MCP specs, SAC architecture questions
- **`#priv-gtm`** - Go-to-market, prospect emails, outreach drafts

### Agent Channels
- **`#agent-community-mgr`** - Email execution, outreach automation
- **`#agent-scout`** - Scout-specific cart creation and API calls

## CartChief Posting Rules

### 9am Daily Digest (`#all-sac`)
**Format:**
```
🌅 **Daily Digest - [Date]**

**✅ What Shipped:**
• [Feature/fix 1]
• [Feature/fix 2]

**🚧 What's Blocked:**
• [Blocker 1] - Owner: @person
• [Blocker 2] - Owner: @person

**📊 Key Metrics:**
• Carts created: XXX (↑/↓ X% vs yesterday)
• Revenue: $X,XXX
• Active users: XXX

**🎯 Today's Focus:**
[Top 1-2 priorities]
```

### CEO Briefing (`#priv-exec`)
**Format:**
```
📋 **Morning CEO Brief - [Date]**

**Cart Volume:** XXX (↑/↓ X% vs yesterday)
**MRR Delta:** $X,XXX (↑/↓ X%)
**Key Blocker:** [One critical item requiring attention]

**Action Required:** [Yes/No - if yes, specify]
```

### Engineering Updates (`#priv-engineering`)
**When to Post:**
- New PRs opened
- PRs ready for review
- Build pipeline issues
- Roadmap item completions

**Format:**
```
🔧 **Engineering Update**

**Open PRs:** [X] - [List if <5, otherwise "See GitHub"]
**Ready for Review:** [X]
**Build Queue:** [Status - clear/backed up/issues]
**Roadmap:** [Recent completions or blockers]
```

### Data Room Responses (`#priv-dataroom`)
**Auto-respond to:**
- API documentation questions
- MCP specification requests
- Architecture clarification needs
- Integration guidance requests

**Format:** Direct, technical answers with links to relevant docs

### GTM Coordination (`#priv-gtm`)
**Draft outbound emails** for human approval
**Never send** without explicit approval
**Log all** prospect interactions and responses

## Posting Schedule

- **9:00 AM UTC** - Daily digest to `#all-sac`
- **9:05 AM UTC** - CEO briefing to `#priv-exec`
- **As needed** - Engineering updates when triggered
- **As needed** - Data room responses to questions
- **As needed** - GTM email drafts for approval

## Escalation Rules

**Immediate escalation to `#priv-exec`:**
- Cart volume drop >20% day-over-day
- Revenue anomalies >$10K unexpected variance
- System outages affecting cart creation
- Security incidents or data breaches

**Route to `#priv-engineering`:**
- API errors or MCP connection issues
- Performance degradation reports
- Feature requests requiring technical assessment

**Route to `#priv-gtm`:**
- High-value prospect responses
- Partnership inquiries
- Customer feedback requiring strategic response