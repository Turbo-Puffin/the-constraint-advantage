# Chapter 9b: The Day It Broke

The previous chapter makes autonomous incident response sound clean.

Wake up to summaries. Four-minute reviews. Handled incidents while you slept. A system that runs while you're somewhere else.

That's all true. And I'd be doing you a disservice if I stopped there.

---

At some point, every system has a day where something breaks in a way the system wasn't designed for. Not a production incident. Not a server going down. Something quieter. A wrong output that kept running without anyone noticing, because the output looked right and the system had no way to know it wasn't.

[STORY NEEDED: Hondo, describe a real incident where an agent produced wrong output that ran unchecked for a period of time — maybe a content agent, support agent, or code agent that did the task correctly but based on wrong inputs or stale context. The specific details here need to come from you. The lesson below is the real lesson, and it's yours.]

---

What I can tell you is the shape of the problem, because I've seen it happen more than once across different systems.

The failure mode is almost never dramatic. It's not a server crash or a payment error or a data loss event. Those are loud. They announce themselves.

The quiet failure is when the agent does exactly what it was told to do, on the wrong data, or with the wrong context, or according to instructions that were accurate when you wrote them but drifted from reality without you noticing.

The system ran. The output looked correct. The volume kept going. And somewhere along the way, "correct-looking" and "actually correct" diverged.

---

When this kind of failure happens, the instinct is to question the agent. What did it do wrong?

The more useful question is: what did I set up that made this possible?

The agent doesn't know the difference between current data and stale data. It doesn't know that the process you documented in January no longer matches the process you're running in June. It doesn't know that the context store you updated last Tuesday now includes a template it shouldn't be drawing from for this use case.

The agent knows what it knows. It executes what it was designed to execute. The inputs come from the environment you built around it.

When the output is wrong, the environment is usually where the fault lives.

---

This is the hardest mental model shift in building agent systems.

With human employees, the responsibility model is blurry. When someone makes a mistake, there's a negotiation about whose fault it was, whether they had enough context, whether the process was clear, whether the expectations were reasonable. There's judgment on both sides.

With agents, the responsibility model is clean. The agent executes your design. If the execution is wrong, the design is wrong. If the context was stale, the context management is your responsibility. If the guardrails didn't catch the case, you didn't design wide enough guardrails.

That's not a criticism. It's a feature. Clean accountability is faster than negotiated accountability. When the system produces a bad output, you know where to look. You don't have to figure out who to have the conversation with.

You just go fix the system.

---

The lesson I've internalized from every bad day with agents:

**Changes to the system's environment are changes to the system.** Treat them that way.

Most operational errors in agent systems happen not because the agent logic broke. They happen because someone, usually me, changed something in the environment the agent depends on — a data source, a template, a process — without thinking through how the agent would interpret that change.

The agent keeps running. It picks up the change. It does its job. The job is now wrong.

The fix is process, not technology. Before updating anything the agents depend on, ask: which agents use this? What would they do differently with the updated version? Is that what I want?

Thirty seconds of that question has saved me from finding out the hard way a few times.

The first few times you build agents, you're focused on the agent logic. Does the agent reason correctly? Does it take the right actions? You tune that carefully.

The thing you tune less carefully in the beginning is the maintenance process for the environment around the agent. That's where the gaps live. Not in the logic. In what happens when the world changes and the agent doesn't know it changed.

---

I still use agents for everything I described in the previous chapter. I have not rolled back the autonomy because something broke. I've added better safeguards around what I do when I change the inputs those agents depend on.

The agents work. My process for updating their environment needed to be better.

That's not a failure of the approach. That's how systems mature. You find the edges. You close them. You run more reliably next quarter than you did last quarter.

The day something breaks is not the reason to abandon the system. It's the day the system earns a new rule.

Build that rule. Move forward.
