# Chapter 6: What AI Agents Actually Are

The word "agent" has been stretched so far it's nearly meaningless.

Your bank's chatbot that says "I'm sorry, I didn't understand that. Did you mean: check balance?" — not an agent. The auto-responder on a support ticket that says "We've received your message and will respond in 24 hours" — not an agent. The autocomplete that finishes your sentences in Gmail — definitely not an agent.

But marketing teams love the word. Every product with a language model bolted on is suddenly an "AI agent" and every company is breathlessly explaining their "agentic AI strategy." The result is that when you actually want to describe what a real AI agent does, you have to spend five minutes clearing out the noise first.

So here's the clear version.

---

An AI agent is a system that takes **goal-directed autonomous action** using real tools in the real world.

Not "answers questions." Takes action.

Not "generates text." Does things.

When my agent monitors my servers and a problem appears, it's not composing a summary of what's wrong. It's SSHing into the server, reading the logs, running diagnostics, writing a patch, testing it, deploying it, and verifying the fix. Then it sends me a summary.

The difference between a chatbot and an agent is the same as the difference between a consultant and an employee. The consultant gives advice. The employee does the thing. Most "AI agents" on the market today are consultants. Mine are employees.

---

Let me break down what an actual agent needs to function:

**A model.** The language model that understands the goal, reasons about how to achieve it, and decides what to do next. This is the brain. Different models have different capabilities and costs — I'll cover the specific stack in Chapter 11.

**Memory.** The agent needs to know things: the current state of the task, facts about the environment, what it's already tried. This can be a file it can read and write, a database, or conversation history. Without memory, every agent call starts from zero. With memory, it learns the landscape over time.

**Tools.** The ability to take action. Read a file. Write a file. Run a command. Call an API. Send an email. Make a payment. Query a database. The more tools an agent has, the more it can do. Tools are the agent's hands.

**A runtime.** The loop that runs the agent: give it the goal, let it think, watch it take action, evaluate the result, let it think again, take another action. The runtime is what makes it *autonomous* rather than a one-shot query.

**Guardrails.** What it's not allowed to do. This is the one most people forget to design carefully, and it's the one that matters most. A powerful agent without good guardrails is a liability. A powerful agent with thoughtful guardrails is a force multiplier.

---

The question I get most often: "How do you trust it?"

The honest answer: carefully, incrementally, with verification.

I didn't wake up one morning and hand an AI agent the keys to my production databases, my email accounts, and my Stripe account. I built trust the same way you'd build trust with a new employee — gradually, with oversight, starting with low-stakes tasks.

The first agent I ran had one job: read my emails and summarize the important ones. No sending, no deleting, no replying. Just read and report. I could verify every output. I could catch every error. Over weeks, I built confidence in how it handled different types of content.

Then I added a tool: draft a reply. Still no sending. I'd read the draft, fix anything wrong, and send it myself. The agent learned my style through corrections. I learned its failure modes through observation.

Then I let it send routine replies autonomously, with a rule: flag anything that involves money, commitments, or anything I haven't explicitly pre-approved.

That progression — observe, assist, automate — is how you build a trustworthy agent stack. Not by giving it everything at once and hoping for the best.

---

There are three patterns I use for most of my agents:

**The Monitor.** Watches something continuously and alerts or acts when a condition is met. My server monitoring agent is a monitor. My email triage agent is a monitor. The trigger is an external event; the agent decides what that event means and what to do about it.

**The Worker.** Given a goal, works until it's done. My coding agent is a worker. I describe a feature; it builds the feature. It might take 20 tool calls to get there — reading files, writing code, running tests, fixing failures — but it runs autonomously until the job is complete.

**The Scheduler.** Runs on a clock. My content generation agent is a scheduler. Every morning at 7 AM, it checks what needs to be posted today, generates the content, and queues it. No trigger from me. No initiation required.

Most real-world use cases are combinations of these patterns. A monitor that detects a condition, triggers a worker to handle it, and then the worker reports back on a schedule. You build these like Lego.

---

The thing that surprises people most when they see this in action isn't the sophistication. It's the mundanity.

AI agents doing real business work mostly look boring. Log in, read the data, write the report, send the message. It's not dramatic. There's no moment where the AI reveals some insight that changes everything. It's just... the work, getting done, while you're somewhere else.

That mundanity is the point. The 70% of business operations that are routine, repetitive, and rule-following — that's what agents are for. Not the inspiring 30% that requires real judgment. The boring 70% that eats your calendar, drains your energy, and keeps you from doing the work that actually matters.

Free up the 70%, and the 30% becomes your whole job. That's what I've been building toward for seven years. Not AI that's smarter than me. AI that handles the parts I shouldn't be spending my time on anyway.
