# Chapter 3: Big Teams Are a Bug

There's a famous equation in project management that nobody wants to talk about.

The number of communication channels in a team is **n(n-1)/2**, where n is the number of people.

- 2 people: 1 channel
- 5 people: 10 channels
- 10 people: 45 channels
- 20 people: 190 channels
- 50 people: 1,225 channels

This isn't theory. This is physics. Every person you add to a team creates new communication pathways that must be maintained, synchronized, and managed. Every pathway is a potential source of misunderstanding, delay, and conflict.

A 10-person startup has 45 communication channels. Not Slack channels — *relationship channels.* Forty-five pairs of people who need to stay aligned on priorities, context, and decisions.

You know what has zero communication channels? One person with AI agents.

Zero.

---

I've worked on teams of every size. Government teams. Startup teams. Agency teams. Enterprise teams.

The pattern is always the same:

**Phase 1 (2-3 people):** Everything is fast. Decisions happen in minutes. Everyone knows everything. Shipping is effortless.

**Phase 2 (5-8 people):** Meetings start appearing. Someone creates a "communication protocol." There's a weekly sync that nobody thinks is necessary but everyone attends. Shipping slows down, but you blame it on "growing complexity."

**Phase 3 (10-15 people):** You now have managers. The people who were doing the work are now managing the people who are doing the work. You have a project manager whose job is to coordinate between teams that didn't exist six months ago. Shipping requires approval from three people, one of whom is on vacation.

**Phase 4 (20+ people):** You have meetings about meetings. Someone's job title is "Director of Engineering" and they haven't written code in a year. There's an "alignment session" every quarter that costs $50,000 in combined salary-hours and produces a document nobody reads. You've hired a recruiter to help you hire more people to do the work that three people used to do.

Each phase feels necessary from the inside. "We need more people because we're growing." But the growth itself is causing the need for more people. It's circular.

You're not scaling. You're inflating.

---

Fred Brooks wrote about this in 1975. *The Mythical Man-Month.* His core insight: adding people to a late project makes it later. The communication overhead of each new person outweighs their productive contribution.

That was fifty years ago. The book is still relevant because the fundamental problem hasn't changed. Human communication is expensive. Coordination is expensive. Alignment is expensive.

What *has* changed is that we now have an alternative.

AI agents don't need to communicate with each other through meetings. They share state through databases and files. They don't need to "align on priorities" because they have one priority: whatever you told them to do. They don't have opinions about the roadmap. They don't politic for resources. They don't form factions.

When I need to build a feature, I don't schedule a meeting to discuss the feature, then a sprint planning session to size the feature, then assign the feature to an engineer who needs two days of context before starting, then a code review meeting when they're done, then a QA cycle, then a deployment approval.

I describe the feature. The agent builds it. I review it. It ships.

Start to finish: hours, not weeks.

---

"But what about complex problems that need multiple perspectives?"

Good question. And it reveals a real advantage of human teams — diverse viewpoints catch blind spots.

But I'd argue that most of the "multiple perspectives" in team settings are *redundant* perspectives. Eight engineers in a room debating whether to use PostgreSQL or MongoDB aren't bringing eight unique worldviews. They're having the same argument that's been had ten thousand times, and the decision will be made based on whoever is most stubborn or most senior, not on the merits.

The actually valuable perspectives — "this approach has a security flaw," "this won't scale past 10K users," "the customer doesn't actually want this" — don't require eight people. They require *one* person who's thought carefully about it.

I get my "multiple perspectives" from AI. I ask it to argue against my approach. I ask it to find flaws. I ask it to consider edge cases I'm missing. I get 90% of the value of a team brainstorm in 5% of the time, with 0% of the politics.

---

Here's the math that made me a believer.

In 2023, Basecamp — the company that literally wrote the book on small teams — had about 75 employees running a business with millions of users.

In 2024, WhatsApp was acquired for $19 billion with 55 engineers.

Instagram had 13 employees when Facebook bought it for $1 billion.

These are extreme examples, but they prove the point: headcount and output are not correlated the way people assume.

The companies that change industries are almost always small teams that stayed small longer than anyone thought possible. They achieved this by being disciplined about what work actually needs to happen versus what work feels productive.

Most work in most companies is coordination work. It's work about work. Meetings about what to build, documents about what was decided, updates about what's in progress, reviews of what was done.

Take all that away and what's left? The actual building.

That's what a solo operator with AI agents has. Just the building. No overhead. No drag. No organizational theater.

---

I'm not naive about this. There are companies that genuinely need large teams. If you're building a physical product, you need manufacturing. If you're in healthcare, you need licensed professionals. If you're SpaceX, you need rocket engineers and you can't automate the welding (yet).

But for software companies? Digital products? Content businesses? Professional services?

The number of people you actually *need* is almost certainly smaller than the number of people you *have.* And for a surprising number of these businesses, the right number might be one.

One person who's clear about what they're building and why.

One person with the right tools.

One person who treats headcount as a last resort, not a first instinct.

Big teams aren't a feature. They're a bug. A bug we've been shipping for decades because we didn't have a better option.

Now we do.
