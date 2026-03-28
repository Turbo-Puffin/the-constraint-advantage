# Chapter 3: Big Teams Are a Bug

There's a famous equation in project management that nobody wants to talk about.

The number of communication channels in a team is **n(n-1)/2**, where n is the number of people.

- 2 people: 1 channel
- 5 people: 10 channels
- 10 people: 45 channels
- 20 people: 190 channels
- 50 people: 1,225 channels

Fair warning: this formula describes potential channels, not active friction. A tight team of ten can manage 45 relationships just fine if trust is high and roles are clear. The formula doesn't prove that big teams always fail. It proves that big teams always carry overhead. And overhead compounds.

Every person you add creates new pathways that need maintenance. Every pathway is a place where context gets lost, decisions get delayed, and misunderstandings breed. A well-run team manages this. Most teams are not well-run.

A 10-person startup has 45 relationship channels. Not Slack channels. Not group chats. Pairs of people who need to stay aligned on priorities, context, and what the word "done" means this week.

You know what has zero communication channels? One person with AI agents.

Zero.

---

I've worked on teams of every size. Agency teams. Government teams. Startup teams.

The pattern is always the same.

**Phase 1 (2-3 people):** Everything is fast. Decisions happen in minutes. Everyone knows everything. Shipping is effortless. You wonder why anyone would ever make this harder.

**Phase 2 (5-8 people):** Meetings start appearing. Someone creates a "communication protocol." There's a weekly sync that nobody thinks is necessary but everyone attends. Shipping slows down, but you blame it on growing complexity. You are wrong. The complexity grew because you grew.

**Phase 3 (10-15 people):** You now have managers. The people who used to do the work now manage the people doing the work. You have a project manager whose entire job is to coordinate between teams that didn't exist six months ago. Shipping requires approval from three people, one of whom is always on vacation.

**Phase 4 (20+ people):** You have meetings about meetings. Someone's title is "Director of Engineering" and they haven't written code in a year. There's an alignment session every quarter that costs $50,000 in combined salary-hours and produces a document nobody reads. You've hired a recruiter to help you hire more people to do the work that three people used to do.

Each phase feels necessary from the inside. "We need more people because we're growing." But the growth is causing the need for more people. It's circular.

You're not scaling. You're inflating.

---

Fred Brooks wrote about this in 1975. *The Mythical Man-Month.* His core insight: adding people to a late project makes it later. The communication overhead of each new person outweighs their productive contribution.

That was fifty years ago. The book is still relevant because the problem hasn't changed. Human communication is expensive. Coordination is expensive. Alignment is expensive.

What has changed is that we have an alternative now.

AI agents don't coordinate through meetings. They share state through databases and files. They don't need to align on priorities because they have one priority: whatever you told them. They don't have opinions about the roadmap. They don't politic for resources. They don't form factions.

When I need to build a feature, I don't schedule a kickoff meeting, then a sprint planning session, then assign it to an engineer who needs two days of context before starting, then review it when they're done, then hand it off to QA, then get deployment approval.

I describe the feature. The agent builds it. I review it. It ships.

Start to finish: hours, not weeks.

---

I worked on this firsthand at the City of Boston.

Municipal government is not supposed to be fast. The constraints are real: union rules, budget cycles, approval chains, the pace of public accountability. Every decision lives in public. Every dollar is someone's tax money.

But inside those constraints, the team we built moved. We made decisions in hours, not weeks. We shipped boston.gov and took it open source in October 2016. Other cities forked it. It became a national model.

We didn't do that by hiring more people. We did it by being ruthlessly clear about what mattered.

"Developing with people, not for people" was the philosophy. It sounds simple. It's not. It means every feature decision starts with: does this solve a real problem for a real person who needs to use this? Not a use case document. Not a stakeholder assumption. A real person.

When you have structural constraints, you can't afford to build things nobody needs. You have to prioritize. Prioritizing forces clarity. Clarity is fast.

That small, constrained, over-accountable team built something that held up. Something other cities wanted. Not despite the constraints. Because of them.

---

The org-chart problem shows up everywhere I've worked since Boston.

I see it most clearly in public sector digital transformation, where Rudder works now. Government agencies are often large by design. Dozens of departments. Hundreds of stakeholders. Everyone has an opinion about the website because everyone uses it.

We worked with a state early childhood agency that needed their public-facing site rebuilt. The existing site was organized around the agency's org chart. Not around what families actually needed to do.

Families who landed on the site needed to find child care, understand their options, apply for benefits. That's it. Three jobs. Clear and human.

The old site made them navigate by department. You had to know which program you were looking for before you could find it. That's the org chart solving its own problem. It tells the agency's story. It doesn't help the family.

We rebuilt the site around those three jobs. WCAG-compliant. Responsive. Built to work on whatever device someone had in their hand when they needed it.

The site got better because we stripped out what the org chart was demanding and kept only what families needed. The constraint wasn't the budget or the timeline. The constraint was: we only build what serves the user.

That's a choice. And it's a hard one in an environment where every department head wants a presence on the homepage.

But the outcome speaks. A site built around user need is one people can actually use.

---

"But what about complex problems that need multiple perspectives?"

Good question. It reveals a real advantage of human teams. Diverse viewpoints catch blind spots. That's real.

But most "multiple perspectives" in team settings are redundant perspectives. Eight engineers in a room debating PostgreSQL vs. MongoDB aren't bringing eight unique worldviews. They're having the same argument that's happened ten thousand times before. The decision will go to whoever is most stubborn or most senior. Not to the best answer.

The valuable perspectives — "this approach has a security flaw," "this won't scale past 10K users," "the customer doesn't actually want this" — don't require eight people. They require one person who's thought carefully about it.

I get my multiple perspectives from AI. I ask it to argue against my approach. I ask it to find the flaws. I ask it to consider edge cases I'm missing. I get 90% of the value of a team brainstorm in 5% of the time. With 0% of the politics.

---

Here's the evidence that broke my assumptions.

Basecamp has roughly 75 employees running a multi-product business with millions of paying users. They've had that headcount for years by design, not by accident. They wrote the book on it. Literally. DHH and Jason Fried have spent decades arguing that headcount is a trap. Their business keeps proving them right.

Linear built a project management tool that went after Jira and Asana directly. Two products that had hundreds of engineers behind them. Linear shipped with a team small enough to fit in a single room. The product was faster, cleaner, and more opinionated. Users noticed. Linear grew fast because the team stayed small enough to move fast. The small team wasn't a handicap. It was the competitive edge.

Notion built a product used by tens of millions of people. Their engineering team stayed lean for years after they hit scale. When you look at the output per engineer, the numbers don't make sense if you believe the conventional wisdom that more product requires more people.

Vercel built and ran the infrastructure platform that deploys millions of sites globally. For years, their team size would have embarrassed a company with a tenth of their traffic. They scaled infrastructure faster than headcount because they had to. That pressure made them better.

These aren't edge cases. These are the companies people actually want to work at and build like.

The pattern is clear: the teams that move fastest are the teams that stayed disciplined about who they added and why. They treated headcount as a liability, not an asset. Because it is.

---

Most work in most companies is coordination work. Work about work. Meetings about what to build. Documents about what was decided. Updates about what's in progress. Reviews of what's already done.

Strip all of that away and what's left? The actual building.

That's what a solo operator with AI agents has. Just the building. No overhead. No drag. No organizational theater.

I ran a team at an agency. Every hire felt like progress. Every new person on the org chart felt like leverage. Then I watched the meetings multiply. The Slack channels multiply. The "who owns this" conversations multiply. The output per person dropped every quarter even as total headcount climbed.

I ran my next work alone, with tools. No org chart. No coordination layer. No overhead. Output per week went up. I moved faster at month six than I had at month one because I wasn't managing a team. I was just building.

That's not a story about AI. That's a story about what happens when you remove the drag.

AI just makes it permanent. Scalable. Repeatable.

---

I'm not naive about this. Some businesses genuinely need large teams. If you're building physical products, you need manufacturing. Healthcare requires licensed professionals. If you're SpaceX, you need rocket engineers and nobody's automating the welding yet.

But software? Digital products? Content businesses? Professional services?

The number of people you actually need is almost certainly smaller than the number you have. And for a surprising number of these businesses, the right number might be one.

One person who's clear about what they're building and why.

One person with the right tools.

One person who treats headcount as a last resort, not a first instinct.

The formula at the top of this chapter doesn't lie. More people means more channels. More channels means more overhead. More overhead means slower decisions, slower shipping, and more meetings about why things are slow.

Big teams aren't a feature. They're a bug. A bug we've been shipping for decades because we didn't have a better option.

Now we do.
