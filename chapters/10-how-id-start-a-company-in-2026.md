# Chapter 10: How I'd Start a Company in 2026

If I were starting from scratch today, I'd do almost nothing the same as I would have in 2019.

Not because the fundamentals changed. They didn't. You still need a problem worth solving, a customer willing to pay, and a way to reach them. That's it. That's the whole thing.

Everything around those fundamentals has changed. The tools. The cost structure. The speed at which you can test. The realistic scope of what one person can actually operate. All of it is different. The 2019 playbook leaves a lot of leverage on the table in 2026.

Here's what I'd do.

---

## Month 0: Define the Constraint First

Before writing a line of code or talking to a customer, I'd write down my operating constraints.

Not my goals. My constraints.

- Maximum monthly burn (what can I run this for indefinitely?)
- Maximum team size (mine is zero, yours might be one or two)
- Maximum time I'm willing to commit before deciding whether to continue
- Categories of work I'm not willing to do myself

The constraints come first because they define the architecture. A company designed to run on $2,000/month looks completely different from one designed to run on $50,000/month. Both can be profitable. But you can't reverse-engineer constraints from the company. You build the company from the constraints.

A company built for $2,000/month uses different tools, serves a different customer segment, prices differently, and requires different operational decisions than one built for $50,000/month. Those aren't just cost differences. They're design differences. Getting the constraints right at the start means every decision after it has a clear filter.

Here's how I frame the burn question: what monthly cost would let me run this indefinitely without financial pressure? Not "how much can I afford for six months" but "what could I sustain for three years if it took that long to work." That number sets the ceiling for everything else.

The team size constraint matters more than people realize. If your constraint is zero employees, you make different product choices. You avoid things that require human support at scale. You build things that run without intervention. You choose tools that have APIs. These constraints shape the product before the product exists.

This step takes one hour. Most people skip it entirely. Then they build something that requires a team to run, wonder why it feels like a second job, and blame the business when they should blame the design.

Write the constraints down. Put them somewhere you'll see them. Every decision you make from here gets measured against them.

---

## Month 0-1: Validate Without Building

The biggest mistake first-time founders make is building before confirming someone will pay.

In 2026, validation costs almost nothing.

**1. Write the sales page first.** Describe the product as if it exists. Force yourself to articulate the specific value for a specific person. If you can't write a compelling page, the product isn't clear yet. Not because it isn't built. Because you don't understand it.

This step is uncomfortable the first time. You want to say the product does everything for everyone. The exercise forces you to pick. One specific person. One specific problem. One specific outcome they get. If you can't say it in two sentences, you don't have a product yet. You have an idea.

**2. Run $100 in paid traffic to it.** Not to a waitlist. To a buy button. A "pay now, get access in 30 days" page. Find out if anyone clicks.

A waitlist tells you people are curious. A buy button tells you people have a problem painful enough to pay to solve. These are different things. Curiosity doesn't pay the bills. Only run to a waitlist if you have a reason to believe the audience genuinely can't buy yet. Otherwise, run to a real offer.

**3. Have 10 conversations.** Not surveys. Conversations. Find the specific type of person you're building for and ask them to describe their current solution and its frustrations. Don't pitch. Listen.

The conversations are not for validation in the strict sense. They're for understanding. What do these people call the problem? How do they describe the pain? What have they already tried? What did they give up on and why? This language is your marketing copy. You can't write it without them.

If you can't get strangers to click a buy button and can't find ten people with the problem you're solving, change the idea before any code gets written.

AI helps with almost all of this. It drafts the sales page in twenty minutes. It researches who has this problem and where they gather. It generates interview question frameworks. It synthesizes the notes from your ten conversations. An AI can't have the conversations for you. But it can prepare you for them and make sense of what you hear.

The validation phase used to take months and cost real money. Now it takes two weeks and costs $100 plus your time. There's no excuse to skip it.

---

## Month 1-3: Build the Smallest Possible Version

Once you have signal, people who clicked or people who said "I would pay for that" with enough conviction that you believe them, build.

Build the smallest thing that delivers the core value. Not the full vision. Not the thing you'd be proud to show your former colleagues. The thing that solves the specific problem for the specific person who told you they'd pay.

The temptation here is to add. One more feature because it'll only take a day. One more integration because customers will definitely ask for it. One more screen because the flow feels incomplete without it. Resist all of it. Every feature you add before you have paying customers is a bet on your assumptions. Most assumptions are wrong.

In 2026, a solo founder with a good AI coding agent can build a SaaS product in two to four weeks that would have taken three engineers three months in 2020. Not because AI replaced engineering judgment. It hasn't. AI eliminated the mechanical parts of implementation.

The mechanical parts used to eat 60% of engineering time. CRUD endpoints, authentication, payment integration, deployment configuration, testing boilerplate, database migrations. An AI agent handles all of this. You focus on the 40% that requires genuine design decisions.

What are genuine design decisions? The data model. The user flow. The pricing structure. What's in the free tier versus the paid tier. Where the system can fail gracefully and where it cannot. These decisions require your judgment. An AI will implement your judgment very fast. But it can't replace the judgment itself.

Ship in weeks, not quarters.

---

## Month 2-4: Sell Before You Optimize

The instinct after shipping is to improve the product. Add features, polish the UI, fix the annoyances.

The correct move is to sell.

Sales solves every other problem. When you're selling, you learn what's actually wrong with the product from real customers who paid money. When you're selling, you have revenue to invest in improvements. When you're selling, you have proof the thing works.

When you optimize before you sell, you optimize for your assumptions about what customers want. Sometimes you're right. Often you're not.

In 2026, sales without a sales team looks like:

- **Content** that attracts the right people. Blog posts, videos, social threads on topics your customers search for.
- **Community** where your customers already gather. Forums, Slack groups, subreddits, Discord servers.
- **Direct outreach** to specific people who fit your ideal customer profile.
- **Partnerships** with adjacent tools or communities where your customers already are.

Of these, content is the highest-leverage long-term play and the lowest-leverage short-term play. A post you write today might bring customers six months from now. Probably not this week. Direct outreach is the opposite. Slow to scale, immediate feedback. You reach out, they respond or they don't, you learn something either way.

Start with direct outreach while you're building the content engine. Do both. Neither alone is enough.

AI can assist with all of it. Content generation, research, outreach drafting, follow-up sequences. But the judgment, what to say, to whom, when, is still yours. That part doesn't get automated.

One more thing: talk to your first customers like they're doing you a favor. They are. They took a chance on an unproven product. They get white-glove service, fast responses, and a founder who answers the phone. That level of service doesn't scale. Good. You're not trying to scale it. You're trying to understand what they bought and why, so you can build more of that and sell it to more people.

---

## Month 3-6: Build the Agent Stack

Once you have paying customers and a validated product, build the operational layer that lets you scale without hiring.

Not before. Before you know what you're operating, you don't know what to automate. Automating a process you're about to change wastes effort. Automating a stable, proven process is pure leverage.

The agent stack I'd build, in order:

**1. Customer support automation.** This is the highest leverage starting point. Every ticket you handle manually is a template for an agent to handle next time.

**2. Monitoring and alerting.** Stop being the only thing standing between problems and impact.

**3. Content and distribution.** Regular publishing on a regular schedule, handled by an agent that knows your brand and your calendar.

**4. Financial tracking.** Invoices, payment follow-up, reconciliation. Not complex. Time-consuming and important.

**5. Growth and outreach.** Prospecting, follow-up sequences, partnership outreach.

Build them in sequence. Not all at once.

Why this order? Each one builds on the last. Customer support automation gives you the most immediate feedback loop. You know within days whether the agent is handling things correctly because unhappy customers tell you. Monitoring is similar: either the alert fired accurately or it didn't. The feedback is fast and unambiguous.

Content and financial tracking have slower feedback. A content agent running for a week tells you almost nothing. The same agent running for three months tells you a lot. So you start the feedback-fast agents first, get them tuned and trusted, then layer in the slower ones.

Growth and outreach agents come last because they interact with the outside world at scale. Getting those wrong has real consequences. By the time you build them, you've spent several months calibrating your judgment about what the agents do and don't handle well. You're not flying blind.

Here's what building the first agent actually feels like: it's slower than you expect. You set it up, it runs, and the first three outputs are wrong in ways you didn't predict. Not catastrophically wrong. Just subtly off in ways that make you realize you didn't write the instructions clearly enough.

So you rewrite the instructions. It runs again. Better, but still missing something. You add more context. You tweak the prompt. You define what "good" looks like with actual examples.

This takes longer than "a few hours." Budget a week for each agent, including the tuning time.

The first sign it's working is when you stop thinking about it. You set it up, it runs, you glance at the output, and it looks right. Then it looks right again. Then again. At some point you realize you haven't manually done that task in two weeks. That's the moment. That's when you understand what leverage actually feels like.

The second sign is when it catches something you would have missed. A customer ticket that came in at 2 AM, handled before you woke up. A monitoring alert that flagged a spike before it became an outage. A follow-up email sent to a lead you'd forgotten about. The agent isn't just doing your work. It's doing work you wouldn't have gotten to.

Give each agent two to four weeks to prove itself before adding the next. If it's not saving you meaningful time by week four, the problem is in how you defined it. Go back and rewrite the context.

---

## What's Different in 2026 vs 2020

**Speed.** A solo founder can ship in weeks what used to take quarters. The compression is real and still accelerating.

**Cost.** The infrastructure to run a software business got dramatically cheaper. SaaS products that cost $20K/year to build and operate in 2020 cost $3-5K today.

**Scope.** One person can realistically operate more product surface area than ever before. I run four companies. That was not possible six years ago.

**Moat.** The traditional technical moat, "we have engineers and you don't," is weaker than it's ever been. The new moat is distribution, brand, and relationships. These are still human things. AI doesn't replicate them.

**Competition.** Because it's easier to build, more things get built. Standing out requires better judgment about what's worth building, not just better execution of building it.

The unfair advantage available to solo operators today isn't that AI does everything. It's that AI removes the operational floor that used to require a team. You can compete with companies ten times your size because your cost structure is one-tenth of theirs, and the leverage per person is ten times what it was.

I think about this every time someone asks why I don't hire. The honest answer is that adding a person adds coordination overhead that erases a chunk of their output. An agent adds capability without adding coordination. That math changes at some scale. But for where I operate, the math is clear.

That gap won't stay this wide forever. But right now, it's there.

---

## The Biggest Mistake People Make

People read a chapter like this and immediately start automating everything.

Don't.

The mistake is automating before you know what you're automating. You set up agents for tasks you haven't done manually long enough to understand. The agents run. The outputs look plausible. You stop checking. Then three weeks later you realize the agent has been doing the task wrong in a consistent, hard-to-detect way because your instructions were based on assumptions rather than experience.

Automation compounds. Good processes get better. Bad processes get consistently bad at scale.

The rule is simple: don't automate anything you haven't done manually at least twenty times. By the twentieth time, you know the edge cases. You know what "wrong" looks like. You know what the output should feel like when it's right.

Before that, you're just guessing. And an automated guess runs twenty times a day without you watching.

Do the work first. Build the pattern. Then hand the pattern to an agent.

Use it before everyone else figures out how.
