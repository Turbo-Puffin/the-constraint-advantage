# Chapter 6: What AI Agents Actually Are

The word "agent" has been stretched so far it's nearly meaningless.

Your bank's chatbot that says "I'm sorry, I didn't understand that. Did you mean: check balance?" Not an agent. The auto-responder on a support ticket that says "We've received your message and will respond in 24 hours." Not an agent. The autocomplete that finishes your sentences in Gmail. Definitely not an agent.

But marketing teams love the word. Every product with a language model bolted on is suddenly an "AI agent" and every company is breathlessly explaining their "agentic AI strategy." The result is that when you actually want to describe what a real AI agent does, you spend five minutes clearing out the noise first.

So here's the clear version.

---

An AI agent is a system that takes **goal-directed autonomous action** using real tools in the real world.

Not "answers questions." Takes action.

Not "generates text." Does things.

When my agent monitors my servers and a problem appears, it's not composing a summary of what's wrong. It's SSHing into the server, reading the logs, running diagnostics, writing a patch, testing it, deploying it, and verifying the fix. Then it sends me a summary.

The difference between a chatbot and an agent is the same as the difference between a consultant and an employee. The consultant gives advice. The employee does the thing. Most "AI agents" on the market today are consultants. Mine are employees.

---

Let me break down what an actual agent needs to function.

**A model.** The language model that understands the goal, reasons about how to achieve it, and decides what to do next. This is the brain. Different models have different capabilities and costs. I'll cover the specific stack in Chapter 11.

**Memory.** The agent needs to know things: the current state of the task, facts about the environment, what it's already tried. This can be a file it can read and write, a database, or conversation history. Without memory, every agent call starts from zero. With memory, it learns the landscape over time.

**Tools.** The ability to take action. Read a file. Write a file. Run a command. Call an API. Send an email. Make a payment. Query a database. The more tools an agent has, the more it can do. Tools are the agent's hands.

**A runtime.** The loop that runs the agent: give it the goal, let it think, watch it take action, evaluate the result, let it think again, take another action. The runtime is what makes it *autonomous* rather than a one-shot query.

**Guardrails.** What it's not allowed to do. This is the one most people forget to design carefully, and it's the one that matters most. A powerful agent without good guardrails is a liability. A powerful agent with thoughtful guardrails is a force multiplier.

Guardrails deserve more than a bullet point. Most people think about them as restrictions. Don't do X. Don't touch Y. That's part of it. But well-designed guardrails also include escalation paths. When the agent encounters something outside its boundaries, where does it go? Most of my agents have three modes: act, flag, and stop. Act on things within defined parameters. Flag things that are edge cases I haven't handled. Stop entirely and wait for me if something doesn't fit either category.

The instinct is to make guardrails as permissive as possible so the agent can do more. That instinct is backwards. Tighter guardrails make the agent more trustworthy faster. A narrow, well-behaved agent that handles 60% of the work autonomously is more valuable than a broad agent that handles 90% of the work but requires constant supervision because it occasionally does something wrong.

Start narrow. Expand deliberately.

---

The question I get most often: "How do you trust it?"

The honest answer: carefully, incrementally, with verification.

I didn't wake up one morning and hand an AI agent the keys to my production databases, my email accounts, and my Stripe account. I built trust the same way you'd build trust with a new employee. Gradually. With oversight. Starting with low-stakes tasks.

The analogy to a new employee is worth taking seriously. When you hire someone, you don't give them production access on day one. You give them read-only dashboards and have them shadow existing processes. Then you give them small tasks with low blast radius. Then you let them operate more independently as they demonstrate good judgment. You're calibrating autonomy to demonstrated competence.

The mistake people make with AI agents is skipping the calibration entirely. They set up the agent, give it full access, and then wonder why something eventually goes wrong. The something-going-wrong is not a failure of AI. It's a failure of process. You wouldn't onboard a human that way.

The three stages are: Observe, Assist, Automate. You do not skip ahead.

**Stage One: Observe.**

The first agent I ran had one job. Read my emails and summarize the important ones. No sending, no deleting, no replying. Just read and report.

This stage looks almost pointless. The agent isn't saving you time. It's saving you from surprises later. You're watching how it categorizes things. Watching what it considers "important." Catching the times it misreads tone, or flags a routine vendor email as urgent, or buries a message that needed your attention today.

Every error at this stage is free. No damage done. You read the summary, you see the miss, you correct the classification logic or update the prompt. Repeat. Over a few weeks, the error rate drops. Your confidence goes up. Not because you decided to trust it. Because it earned the trust by showing you how it behaves.

This stage usually takes two to four weeks, depending on the volume of whatever the agent is watching. Don't rush it. The instinct is to move faster because you're impatient and the agent seems to be working fine. The instinct is wrong. Fine-seeming is different from understood.

What you're building in Stage One is a mental model of how the agent reasons. You want to understand its tendencies before you give it any ability to act. Does it skew conservative or aggressive? Does it handle ambiguous inputs well or does it guess badly when context is thin? Does it have blind spots in specific categories? These are things you can only learn by watching it work through a real, representative volume of inputs. Not five test cases you made up. Real inputs. Real conditions.

**Stage Two: Assist.**

Once you understand how the agent behaves on read-only tasks, you add write access. Draft, don't send. Suggest, don't execute.

With the email agent: it starts drafting replies. I read every draft. I fix what's wrong. I send it myself. The agent sees my corrections through the updated instructions I give it when I notice patterns in my fixes. It learns my voice. My preferences. My habit of replying to vendor emails with two sentences instead of six.

The verification at this stage looks different than Stage One. In Stage One you're checking for classification errors. In Stage Two you're checking for tone, judgment, and appropriateness. You're looking for the drafts that would have embarrassed you if they'd gone out unsupervised. There will be some. That's fine. They're caught before any damage.

This stage can run for a month or more for high-stakes domains. Emails involving clients, money, or commitments get the longest observation period. Low-stakes domains move faster. An agent that drafts social posts for review is a lower bar than one drafting client proposals.

The measure that tells you you're ready to move on: you've reviewed a hundred drafts and made only small edits on the last twenty. The agent's output and your output look basically the same.

**Stage Three: Automate.**

The agent now acts autonomously, within explicit rules you've defined.

With the email agent: it handles routine replies on its own. Vendor check-ins. Acknowledgment emails. Standard support questions that have a known answer. But the rules are written carefully. Anything involving money: flag me. Anything involving a commitment I haven't pre-approved: flag me. Anything with ambiguous tone or a thread I haven't seen before: flag me.

The flags are the ongoing verification mechanism. You're no longer reviewing every action. But you're reviewing every edge case, because the edge cases are what the system routes to you. Over time, you handle a flagged edge case, decide how it should go, and encode that decision as a new rule. The automation coverage expands. The flags decrease.

This is also the stage where you start to see real time savings. The first two stages cost you time. You're reviewing outputs carefully. You're correcting things. You're updating instructions. It feels slower than just doing the work yourself. It is slower. That's normal. You're training the system.

By Stage Three, the math flips. The agent is handling volume you couldn't handle yourself. It's handling it at 11 PM on a Tuesday when you're not working. It's handling it on the same day you decide to take a Friday off. You stop being the bottleneck for routine work.

---

There are three patterns I use for most of my agents.

**The Monitor.** Watches something continuously and alerts or acts when a condition is met. My server monitoring agent is a monitor. My email triage agent is a monitor. The trigger is an external event. The agent decides what that event means and what to do about it.

Monitors run cheap when nothing is happening. They only burn real resources when they detect a condition worth handling. For most operational monitoring tasks, this is the right pattern. You want constant vigilance at low cost, with bursts of action when needed.

The key design decision for a monitor is: what counts as a condition worth acting on? This matters more than the action itself. A monitor that fires on everything is just noise. A monitor that's too conservative misses things that needed attention. You calibrate this threshold in Stage One, when you're watching the outputs carefully.

**The Worker.** Given a goal, works until it's done. My coding agent is a worker. I describe a feature. It builds the feature. It might take 20 tool calls to get there: reading files, writing code, running tests, fixing failures. It runs autonomously until the job is complete.

Workers are where you feel the leverage most acutely. The mental shift is real. You describe a job. You walk away. You come back and the job is done. Or mostly done, with a summary of what it couldn't resolve and what it needs from you.

The calibration for workers is scope. A worker given a vague goal will make vague progress. "Improve the onboarding flow" is not a worker goal. "Rewrite the onboarding copy on screens 3 and 4 to reduce reading level and match the voice of the homepage" is a worker goal. Specificity is leverage. The more clearly you define the job, the better the output.

**The Scheduler.** Runs on a clock. My content generation agent is a scheduler. Every morning at 7 AM, it checks what needs to be posted today, generates the content, and queues it. No trigger from me. No initiation required.

Schedulers are the closest thing to a true employee who just shows up and does the work. They're also the most important ones to design carefully, because they act without being asked. A misconfigured scheduler can generate wrong outputs or take wrong actions at volume before you notice. Build schedulers last, after you've validated the underlying logic in interactive modes first.

Most real-world use cases are combinations of these patterns. A monitor detects a condition. It triggers a worker to handle it. The worker reports back on a schedule. You build these like Lego.

One combination I use regularly: a monitor watches my analytics dashboard for anomalies. A traffic spike, a conversion drop, a payment failure rate above a threshold. When the monitor fires, it triggers a worker. The worker pulls the relevant data, runs a diagnostic, and writes a summary of what it found and what it recommends. That summary lands in my inbox by the time I wake up. The whole thing costs me about $4 in API calls per month.

That same pipeline, staffed with a human analyst on-call, would cost at minimum $60K a year for someone junior. A senior analyst would run $120K or more. And the human wouldn't be watching at 2 AM when the anomaly hit. They'd see it in the morning and start the investigation then. By which point I've already read the summary and made a decision.

I'm not describing this to brag. I'm describing it to be precise about what's actually different now. These are not science fiction workflows. They're boring operational plumbing that happens to run automatically and cost almost nothing.

---

The thing that surprises people most when they see this in action isn't the sophistication. It's the mundanity.

AI agents doing real business work mostly look boring. Log in, read the data, write the report, send the message. It's not dramatic. There's no moment where the AI reveals some insight that changes everything. It's just the work, getting done, while you're somewhere else.

That mundanity is the point. The 70% of business operations that are routine, repetitive, and rule-following: that's what agents are for. Not the inspiring 30% that requires real judgment. The boring 70% that eats your calendar, drains your energy, and keeps you from doing the work that actually matters.

Free up the 70%, and the 30% becomes your whole job. That's what I've been building toward for seven years. Not AI that's smarter than me. AI that handles the parts I shouldn't be spending my time on anyway.

The goal was never a robot that thinks better than I do. The goal was a system that handles the work I was never supposed to be doing in the first place.

The hype around AI tends to focus on the impressive end of the spectrum. Models that write poetry. Systems that beat humans at complex reasoning benchmarks. The demos always feature something dramatic.

But the business value is almost entirely in the undramatic. Writing the weekly status report that nobody enjoys writing. Monitoring the dashboard that needs to be watched but doesn't need judgment most of the time. Handling the support email that has a known answer. Categorizing the expense that follows a predictable pattern.

None of that is impressive. All of it is time-consuming. When you add it up across a week, it's often fifteen or twenty hours of work that required a human's time but not a human's intelligence.

That's the actual opportunity. Not artificial general intelligence. Artificial routine.

Build for that. You'll get more done than most teams twice your size.
