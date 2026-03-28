# Chapter 9b: The Day It Broke

I should tell you about October.

The previous chapter makes autonomous incident response sound clean. Forty-three incidents handled while I slept. Four-minute reviews over coffee. A tidy document of wins. That's all true.

October was not in that document.

---

It was a Tuesday. I was at my desk, not asleep, not traveling. Working. Which is why it took me three hours to notice.

The support agent had been running for about four months at that point. Its job: read incoming support tickets, draft responses, send them when the confidence threshold was met. I'd tuned the threshold carefully over those four months. Routine questions, it answered and sent. Anything ambiguous, it drafted and queued for my review. Or so I thought.

At 11:47 AM, I got a reply from a customer. The tone was confused, then upset. She was asking why we had quoted her a different price than what she'd been told in a previous conversation.

I didn't understand the question at first. I pulled up her ticket history.

The agent had sent her a pricing breakdown. A detailed one. Specific numbers, specific tiers. The problem: it had pulled those numbers from the wrong context. It cross-referenced a pricing template meant for a different product line, one we hadn't publicly launched yet, with rates twenty percent lower than what she was actually on.

She had forwarded that email to her CFO.

---

I sat with that for a moment.

Then I went looking.

It had been sending since 9:08 AM. Forty-one tickets in that window, seventeen of which touched pricing in any way. Of those seventeen, eleven got responses with numbers. Three of those eleven had incorrect numbers, drawn from the wrong template.

Three customers. Two had already replied. One had forwarded to someone internally. The other was asking to be moved to the "new pricing" immediately.

The third hadn't responded yet. I caught her before she saw it.

The fix was straightforward enough: take down the wrong template, update the context the agent was drawing from, audit and correct the seventeen tickets manually. That took about ninety minutes.

Explaining it to the two customers who had already received wrong information took longer. One was understanding. One was not. The one who was not had just signed a renewal two weeks prior and felt, reasonably, like the timing was suspicious. It took two calls and a discount to close that out.

Total cost, counting my time and the discount: somewhere around $600 and half a day I hadn't planned to spend.

Not catastrophic. But real.

---

Here's what went wrong.

The pricing templates lived in a shared context store. When I'd added the new product line templates, I'd labeled them clearly, but I hadn't added exclusion logic to the support agent's context-loading rules. The agent was supposed to draw from "active product pricing." Instead, it drew from "all pricing templates," which now included the draft ones.

My fault. I changed the context store without updating the agent's configuration. I'd done it quickly, told myself I'd clean it up later, and forgot.

The confidence threshold I'd tuned so carefully? It evaluated answer quality based on coherence and completeness. A coherent, complete response with wrong numbers from the wrong template passed the threshold fine. The agent had no way to know the numbers were wrong. It just knew they were formatted correctly.

I'd optimized for "does the response look right" when I should have also been checking "is the data source correct."

---

After I fixed it, I sat down and mapped out what I would have needed to catch this before it happened.

The gap wasn't in the agent. The gap was in how I managed changes to the system around the agent.

When I updated the context store, I had no checklist. No process. No test run. I just made the change and moved on. With a regular piece of software, a change like that might cause an obvious error. A crash, a failed build, something visible. This change was invisible. The agent kept running fine. It just ran on wrong data.

I added three things after October:

**1. A context change log.** Any time I update what an agent can draw from, I log it, what changed and which agents are affected. Takes thirty seconds. Has saved me from myself twice since then.

**2. Staging runs on sensitive agents.** The support agent now runs new configuration against a sample of real past tickets before going live. I review the outputs before flipping the switch. Not forever, just for a week after any config change.

**3. A data source audit in the agent's prompt.** When the support agent drafts a response that includes pricing, it now names the specific template it drew from. That name shows up in the queued draft. I can see at a glance if it's pulling from the right place. This added two lines to the prompt and costs me nothing.

None of these are complicated. All of them would have caught October before it became October.

---

I still use the support agent. It still sends responses autonomously. The confidence threshold is still there. I didn't roll back anything meaningful.

What I did was add friction to the parts of the system I manage, not the parts the agent manages. The agent was doing its job. I was the one making unreviewed changes to its environment and expecting nothing to break.

The agents work. My process for updating the agents needed to be better.

---

I don't tell this story to balance out the chapter before it. The forty-three handled incidents are still real. The 3 AM deploy still happens the way I described it.

I tell it because October is where I learned something I couldn't have learned from the wins. The wins teach you that the system works. The failures teach you where the system ends and you begin.

The handoff point between the agent's responsibility and mine wasn't where I thought it was. I'd been drawing the line at "what the agent decides to do." The real line is broader. It includes "what environment I give the agent to work in" and "what I do when I change that environment."

That's on me. Not the agent.

I own the system. The system includes the agent. When the system produces a bad output, the question isn't just "what did the agent do wrong." It's "what did I set up, or fail to set up, that made this possible."

October gave me that question. It's a better question than the one I had before.
