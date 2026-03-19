# Chapter 11: The Stack

No affiliate links. No sponsored picks. No tools I'm paid to recommend.

This is what I actually use, what I actually pay, and why. It changes over time as better options appear — I'll note the date I last updated this list — but the categories stay constant.

*Last updated: March 2026*

---

## The Foundation

### Language Models

The AI itself. I use multiple models for different tasks because price-to-performance varies significantly by task type.

**Anthropic Claude (claude.ai / API)** — $50-280/month depending on usage
My primary model for complex reasoning, code generation, and writing tasks that require nuance. The most capable model I use. More expensive than alternatives, so I route only the tasks that justify it.

**Cheaper models for high-volume tasks** — $50-100/month
For tasks where I'm running thousands of calls (email triage, content formatting, data extraction), the expensive models are overkill. I use smaller, faster, cheaper models for high-throughput pipelines.

Rule of thumb: use the smartest model for creative and reasoning tasks, the cheapest capable model for repetitive tasks with clear rules. Most people default to the best model for everything and spend 5x what they need to.

---

### Agent Runtime

**OpenClaw** — $79/month
The system that runs my agents. Handles scheduling, memory, tool access, inter-agent communication, and deployment. This is the operating system my agent team runs on. Chapter 12 covers this in detail.

---

### Infrastructure

**AWS / Cloud hosting** — $150-250/month total for agent infrastructure
Not counting product infrastructure (the servers my actual products run on), the agent support system costs roughly $150-250/month. One server for the agent runtime, a database for agent memory and logs, storage for outputs.

**Bunny CDN** — $20-40/month
For static sites and content delivery. Fast, cheap, global. Every static site I build goes through Bunny.

**Neon (serverless Postgres)** — $20-50/month
Managed Postgres for the few cases where I need relational data in my agent stack. Scales to zero when not in use.

---

## Communication

**Gmail (personal and business)** — $12/user/month (Google Workspace)
I know. Everyone uses it. The advantage is that it's deeply integrated with everything and my agents can access it programmatically.

**Discord** — Free (I pay $0 for this)
My primary async communication channel with myself and with any external collaborators. Channels organized by company and function. Agents post updates here. I check it when I'm ready, not in real-time.

---

## Payments and Finance

**Mercury** — Free for basic, percentage on wires
Business banking for all entities. Clean API, agent-accessible, solid for startup-stage companies.

**Stripe** — 2.9% + $0.30 per transaction
Standard payment processing. No monthly fee, pay per transaction. Every product that takes money uses Stripe.

**Lemon Squeezy** — Similar percentage to Stripe
For digital products where I want built-in tax handling and simpler global distribution. Less setup than Stripe for simple products.

---

## Code and Deployment

**GitHub** — $4/month (Pro)
All code, all companies. Private repos, GitHub Actions for CI/CD.

**GitHub Actions** — Included in GitHub
Every deploy is automated through Actions. No manual deploys. Ever. The agent pushes code, Actions runs tests, Actions deploys to production.

This is a hard rule: if I can't automate the deploy, I haven't finished building the deploy system.

---

## Domains and DNS

**Porkbun** — $9-15/year per domain
Cheap, simple, good UI. I buy all domains here.

**Bunny DNS** — Free
All DNS management through Bunny since it integrates with the CDN. Fast propagation, simple API.

---

## Analytics

**Measure.events** — Built it, use it free
Privacy-friendly analytics I built myself. Simple pageview and event tracking without cookies or consent banners. This isn't an option for most people reading this — see below.

**Plausible** — $9-19/month
If I hadn't built Measure, I'd use Plausible. Same privacy-first approach, simple setup, fast. Not Google Analytics.

I don't use Google Analytics on any property I care about. The privacy overhead and complexity isn't worth it for the data I actually look at, which is: are people coming, are they staying, what are they doing.

---

## Content and Distribution

**Postpone** — Varies
Social media scheduling. Connects to Twitter/X, Instagram, LinkedIn, TikTok. My content agent generates posts, Postpone publishes them.

**Beehiiv** — $39-99/month
Newsletter platform for the properties that have email lists. Clean, simple, good deliverability.

---

## Project Management

**Linear** — $8/user/month
For tracking work that's in progress across companies. My agents can create issues, update status, and close tickets. I review the board once a day.

I don't use Jira. I've never used Jira and I never will.

---

## The Full Monthly Breakdown

| Category | Tool | Monthly Cost |
|---|---|---|
| AI models | Anthropic + secondary | $280-380 |
| Agent runtime | OpenClaw | $79 |
| Cloud infra | AWS | $180 |
| CDN | Bunny | $30 |
| Database | Neon | $25 |
| Banking | Mercury | $0 |
| Email | Google Workspace | $12 |
| Code/deploy | GitHub | $4 |
| Analytics | Measure.events | $0 |
| Social scheduling | Postpone | $30 |
| Email marketing | Beehiiv | $49 |
| Project mgmt | Linear | $8 |
| Misc SaaS | Various | $50 |
| **Total** | | **~$747/month** |

That's my full operating stack across four companies, less than $750/month.

Not counting the cost to run the products themselves (servers, databases for the actual products, third-party APIs the products use) — just the agent and operator infrastructure.

---

## What I'd Cut If Budget Were Tighter

If I was just starting and needed to run lean:

- OpenClaw: could use cheaper or open-source alternative early on, add it when the leverage is obvious
- Beehiiv: skip until you have a real email list
- Postpone: post manually until you're producing enough content to justify automation
- Linear: use GitHub Issues or a Notion table until you have enough work to need real tracking

Getting the core working — language models, some hosting, GitHub — you can start for under $200/month.

---

## What I'd Never Cut

- Good language model access. This is your leverage multiplier. Don't cheap out.
- GitHub + automated deploys. Manual deploys are how mistakes happen at 11 PM.
- Reliable hosting. Not the cheapest hosting — reliable hosting. Downtime costs more than the savings.

The rest is optimization. Get the core right, then optimize.
