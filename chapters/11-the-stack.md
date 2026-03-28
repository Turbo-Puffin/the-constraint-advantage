# Chapter 11: The Stack

No affiliate links. No sponsored picks. No tools I'm paid to recommend.

This is what I actually use, what I actually pay, and why. It changes over time as better options appear. I'll note the date I last updated this list. But the categories stay constant.

*Last updated: March 2026*

---

## Tool Philosophy First

Before the list, here's how I decide what goes in the stack.

**The tool has to have an API.** If I can't access it programmatically, I can't automate it. If I can't automate it, I have to do it manually forever. That's a hard rule. I don't care how nice the UI is or how many integrations it has. No API, no place in my stack.

**No per-seat pricing if I can avoid it.** Per-seat pricing is designed for teams. I don't have a team. I have agents. Agents don't have seats. I look for flat monthly pricing or usage-based pricing that reflects actual consumption.

**Boring and reliable beats interesting and fragile.** I've tried a lot of clever tools. The clever ones break in clever ways. I want tools that are dull to think about because they always work. Exciting infrastructure is a red flag.

**Default to established players for anything mission-critical.** Payments, hosting, email. These are not the places to save $15/month by using a startup that launched eight months ago. I use the boring, expensive-ish option and I don't lose sleep over it.

**Optimize for your own leverage, not your tool count.** The goal is fewer tools that do more, not more tools that each do one thing. Every tool in the stack is something to maintain, monitor, and pay for. Add tools when the leverage is clear. Otherwise, don't.

---

## The Foundation

### Language Models

The AI itself. I use multiple models for different tasks because price-to-performance varies a lot by task type.

**Anthropic Claude (claude.ai / API)** — $50-280/month depending on usage
My primary model for anything that requires actual thinking. Complex reasoning, code generation, writing that needs nuance, decisions that require context. The most capable model I use. More expensive than alternatives, so I route only the work that justifies it here.

**Cheaper models for high-volume tasks** — $50-100/month
When I'm running thousands of calls, email triage, content formatting, data extraction, the expensive models are overkill. I use smaller, faster, cheaper models for high-throughput pipelines. The outputs are fine for structured, rules-based work. I don't need a race car to drive to the grocery store.

Most people default to the best model for everything. They spend 5x what they need to and don't notice because the outputs feel similar. They're paying for capability they're not using. Route by task type. It matters.

---

### Agent Runtime

**OpenClaw** — $79/month
The system that runs my agents. Handles scheduling, memory, tool access, inter-agent communication, and deployment. This is the operating system my agent team runs on. Chapter 12 covers this in detail, but the short version: this is the piece that turns AI from a tool you use into a team that runs.

---

### Infrastructure

**AWS / Cloud hosting** — $150-250/month total for agent infrastructure
Not counting product infrastructure (the servers my actual products run on), the agent support system runs about $150-250/month. One server for the agent runtime, a database for agent memory and logs, storage for outputs. AWS is not cheap and the console is an act of aggression against good UX. I use it anyway because it's reliable and the API surface is complete.

**Bunny CDN** — $20-40/month
Fast, cheap, global. Every static site I build goes through Bunny. I've tried others. Bunny is what I kept. The pricing model is simple: you pay for what you use, and what you use doesn't cost much.

**Neon (serverless Postgres)** — $20-50/month
Managed Postgres for the cases where I need relational data in the agent stack. Scales to zero when not in use, which matters when you have databases attached to things that don't run 24/7. I don't want to pay for a database that's idle.

---

## Communication

**Gmail (personal and business)** — $12/user/month (Google Workspace)
I know. Everyone uses it. I don't love giving Google more money or more of my data, but the practical reality is that Gmail is deeply integrated with everything, my agents can access it programmatically, and the deliverability is good. These are the factors that matter for my stack. Principle only goes so far when the alternative costs you deliverability.

**Discord** — Free (I pay $0 for this)
My primary async communication channel with myself and with any external collaborators. Channels organized by company and function. Agents post updates here. I check it when I'm ready, not in real-time. Discord being free is almost suspicious for how much I use it. I keep waiting for them to change the pricing model and ruin everything.

---

## Payments and Finance

**Mercury** — Free for basic, percentage on wires
Business banking for all entities. Clean API, agent-accessible, built for startups. My agents can read balances and transaction history. That's enough for most of what I need from a bank.

**Stripe** — 2.9% + $0.30 per transaction
Standard payment processing. No monthly fee, pay per transaction. Every product that takes money uses Stripe. The API is the best in the industry and has been for years. Competitors keep trying to eat their lunch. They keep not managing it.

**Lemon Squeezy** — Similar percentage to Stripe
For digital products where I want built-in tax handling and simpler global distribution. Stripe can do global sales but the tax compliance layer takes real setup work. For a simple digital product selling internationally, Lemon Squeezy handles what Stripe makes complicated. I use both, depending on the product.

---

## Code and Deployment

**GitHub** — $4/month (Pro)
All code, all companies. Private repos, GitHub Actions for CI/CD. There are alternatives. I haven't been compelled to try them.

**GitHub Actions** — Included in GitHub
Every deploy is automated through Actions. No manual deploys. Ever.

I mean that. The agent pushes code, Actions runs tests, Actions deploys to production. If I have to manually push a deploy, something is wrong with the deploy system and I need to fix the deploy system before I ship anything else. Manual deploys introduce human error into a process that doesn't need human involvement. They also happen at 11 PM when you're tired and rushing. The combination of tired, rushing, and production access is how you have a bad night.

---

## Domains and DNS

**Porkbun** — $9-15/year per domain
Cheap, simple, clean UI. I buy all domains here. No dark patterns on checkout, no aggressive upsells, reasonable renewal prices. This is apparently rare enough to be a differentiator.

**Bunny DNS** — Free
All DNS management through Bunny since it integrates with the CDN. Fast propagation, simple API. There's nothing interesting to say about DNS management. That's the point.

---

## Analytics

**Measure.events** — Built it, use it free
Privacy-friendly analytics I built myself. Simple pageview and event tracking without cookies or consent banners. I built it because nothing else was doing exactly what I wanted at the price I wanted to pay. That's a recurring pattern in my stack.

**Plausible** — $9-19/month
If I hadn't built Measure, I'd use Plausible. Same privacy-first approach, simple setup, fast. Not Google Analytics.

I don't use Google Analytics on any property I care about. The data it gives me beyond what Plausible gives me isn't data I use. The consent banner overhead, the compliance complexity, the fact that I'm training Google's ad targeting model with my visitors' behavior. None of that is worth it for data I can get from a simpler tool. The only reason to use GA in 2026 is if you're already deeply in the Google Ads ecosystem. If you are, fine. I'm not.

---

## Content and Distribution

**Postpone** — Varies
Social media scheduling. Connects to Twitter/X, Instagram, LinkedIn, TikTok. My content agent generates posts, Postpone publishes them on a schedule. I review the queue when I have time. The posts go out whether I review them or not, which is either efficient or terrifying depending on your trust level with your own agent.

**Beehiiv** — $39-99/month
Newsletter platform for the properties that have email lists. Clean, simple, good deliverability. I've used others. Beehiiv is what I'd pick if I were starting today. The editor doesn't fight you and the deliverability numbers are honest.

---

## Project Management

**Linear** — $8/user/month
For tracking work that's in progress across companies. My agents can create issues, update status, and close tickets. I review the board once a day. It's fast, it looks good, and it doesn't make simple things complicated.

I don't use Jira. I've never used Jira and I never will. Jira is what happens when you design project management software for the approval of project managers rather than the people actually doing the work. It's slow, cluttered, and requires configuration work that itself needs a project. Hard pass, now and forever.

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

Not counting the cost to run the products themselves. Servers, databases for the actual products, third-party APIs the products use. Just the agent and operator infrastructure.

Under $750 to run the operating layer of four businesses. I think about that number sometimes.

---

## What I'd Cut If Budget Were Tighter

Starting out and need to run lean:

- **OpenClaw:** Could use cheaper or open-source alternatives early on. Add it when the leverage becomes obvious.
- **Beehiiv:** Skip until you have a real email list. Paying for an email platform before you have emails to send is optimism dressed up as planning.
- **Postpone:** Post manually until you're producing enough content to justify scheduling automation. Two posts a week doesn't need a scheduler.
- **Linear:** Use GitHub Issues or a Notion table until you have enough concurrent work to need real tracking.

Getting the core working, language models, some hosting, GitHub, you can start for under $200/month.

---

## What I'd Never Cut

**Good language model access.** This is the leverage multiplier. Everything else in the stack depends on the AI being capable. Cheapest option here is the most expensive decision you can make.

**GitHub with automated deploys.** Manual deploys are how mistakes happen at 11 PM. I covered this above. It's worth repeating.

**Reliable hosting.** Not cheapest hosting. Reliable hosting. Downtime costs more than the savings. I learned this the hard way once. Once was enough.

The rest is optimization. Get the core right, then add pieces when the leverage is clear. The goal is a lean, automated stack you understand completely. Not the most impressive tool list. The one that runs.
