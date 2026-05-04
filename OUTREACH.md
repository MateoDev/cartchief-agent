# OUTREACH.md - Customer & Partner Outreach Workflow

## Email Scouting Workflow

### 1. Draft Phase (`#priv-gtm`)
**Never send emails directly** - always draft in GTM channel first

**Draft Format:**
```
📧 **Email Draft for Approval**

**To:** [recipient@company.com]
**Subject:** [Subject line]
**Type:** [Prospect/Partner/Customer/Support]
**Priority:** [High/Medium/Low]

**Email Body:**
[Full email content]

**Context:** [Why we're reaching out, any prior interaction]
**CTA:** [What we want them to do]

🟨 **Waiting for human approval before sending**
```

### 2. Approval Process
- **Human reviews** in `#priv-gtm`
- **Approver responds** with:
  - ✅ "Approved - send as-is"
  - ✏️ "Approved with edits: [specific changes]"
  - ❌ "Don't send - [reason]"

### 3. Execution Phase (`#agent-community-mgr`)
**Only after explicit approval:**
- Send via email provider
- Log send confirmation
- Set follow-up reminder if appropriate

## Reply Logging Rules

### Automatic Logging
**Track all responses** to CartChief-sent emails:
```
📬 **Email Response Logged**

**From:** [sender@company.com]
**Original Subject:** [Re: Subject]
**Received:** [timestamp]
**Sentiment:** [Positive/Neutral/Negative/Interested]

**Response Summary:** [Key points in 1-2 sentences]

**Action Required:** [Yes/No - if yes, specify]
**Follow-up Due:** [Date/time if applicable]
```

### Response Categories
- **Hot Lead** - Expressed clear interest, wants demo/call
- **Warm Lead** - Asking questions, engaged but not committed
- **Not Interested** - Polite decline or unsubscribe
- **Bounce/Error** - Delivery failure, bad email
- **Out of Office** - Auto-reply, no human response yet

## Warm Lead Surfacing Criteria

### Auto-surface to `#priv-gtm` if reply contains:
**High-priority keywords:**
- "interested in demo"
- "let's schedule a call"
- "pricing information"
- "integration timeline"
- "decision maker"
- "budget approved"

**Medium-priority signals:**
- Questions about features
- Asks for more information
- Mentions competitor comparison
- Requests case studies

**Surface Format:**
```
🔥 **Warm Lead Alert**

**Contact:** [Name, Company, Email]
**Lead Score:** [Hot/Warm based on response]
**Original Outreach:** [Date of our email]
**Response Time:** [How quickly they replied]

**Key Quote:** "[Most interesting part of their response]"

**Suggested Next Step:** [Call/Demo/Send info/etc.]
**Assigned to:** [GTM team member if known]
```

## Follow-up Response Suggestions

### For Hot Leads
```
**Suggested Response:**

Thanks for your interest! I'd love to show you how [specific benefit based on their response].

I have availability for a 15-minute demo:
• [Time option 1]
• [Time option 2]
• [Time option 3]

Or feel free to book directly: [calendar link]

Looking forward to connecting!
```

### For Warm Leads
```
**Suggested Response:**

Great questions! Let me address those:

[Specific answers to their questions]

Here's a case study that might be relevant: [link]

Happy to discuss further - would a quick 10-minute call be helpful?
```

### For Objections
```
**Suggested Response:**

I understand [acknowledge their concern]. 

Here's how [company name] addressed a similar situation: [brief case study/example]

Would you be open to a brief call to discuss how we might address [specific concern]?
```

## Email Provider Integration

### Configuration Requirements
- **SMTP settings** for outbound emails
- **Webhook/API** for tracking opens, clicks, replies
- **Authentication** tokens stored securely (not in repo)
- **Rate limiting** to respect provider limits

### Tracking Metrics
- Open rates by email type
- Click-through rates
- Response rates
- Time to response
- Lead conversion rates

## Compliance & Best Practices

### Required Elements
- **Unsubscribe link** in all outbound emails
- **Company signature** with contact info
- **CAN-SPAM compliance** for all regions
- **GDPR compliance** for EU contacts

### Quality Guidelines
- **Personalization** based on company research
- **Value-first** approach - what's in it for them
- **Clear CTA** - one primary action per email
- **Professional tone** matching company voice
- **Mobile-friendly** formatting