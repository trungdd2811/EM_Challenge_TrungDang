## Part C: Two Situations

### C1: Saturday 01:40, balances higher than expected, numbers still moving

**First message: S., not the CEO.**

> *"S., urgent: region 2 balances still increasing. Need you online now, call in 5."*

CEO simultaneously: *"Investigating now. I'll confirm money impact and have first assessment in 15 minutes."* I don't say "we're losing money" or "it's fine": I don't know yet, but I acknowledge the specific question.

**First question to S. is not "why" but "can we stop it."** Something is crediting. Can we pause scheduled jobs in region 2 right now, without knowing root cause? That is the only goal of the first 20 minutes.

On the call I don't debug: I ask scoping questions: *What jobs are scheduled in region 2? Are the increases uniform (suggests a job) or random (suggests logic bug)? All members or a subset?* S. narrows scope in 10–15 minutes without me needing to understand the code.

If we identify a job: pause it. Don't rollback, don't delete: preserve evidence.

**~02:30 CEO update:**

> *"Identified and paused the likely process. Balances stopped increasing. Scope: [X] members region 2, exact amount being calculated. Recovery plan within the hour."*

Format stays fixed every update: what we know / what we don't / what we're doing / next update time.

**Through the night:** S. queries total incorrect credits. I build the impact assessment: member count, amount, start timestamp (critical for clawback and regulatory), whether it hit external systems. I don't wake T.: unrelated to wallet balances.

**Morning:** Full brief to CEO with real numbers. Support team gets a script. Clawback goes to CEO + legal/compliance: regulatory implications, not my call alone. Post-mortem Monday, mandatory, written output.

No fix committed at 3am without review. No number to CEO until verified.

---
### C2: L. publicly challenges the 90-day plan in sprint planning

**In the room: immediately:**

> *"That matters. L., which specific step do you think will slow us down most?"*

"Process theater" is a general claim. A specific question shifts the room from "opposing" to "improving": and signals I'm not afraid of being challenged. I don't say "let's take this offline": that dismisses L. publicly, and L. is who the org respects most.

After L. responds:

> *"Let's have the full conversation right after this: not now, sprint to plan. Checklist applies this sprint. If a step blocks your work, flag it to me this week. It's not sacred."*

Meeting stays on track. L. isn't shut down. Team sees it's improvable: just not by vote in sprint planning.

**After the meeting: 1:1:**

> *"You said what others might be thinking. What specifically is the problem?"*

**If L. has a valid point:** I adjust and tell the team L.'s feedback improved it. Shows I don't protect my own plans.

**If L. lacks context:** *"Here's why now, not after launch: incidents #1, #4, and PR #482 on day 9. If you still think it's wrong, keep talking. But don't encourage the team to skip it until we agree on something better."*

**If mixed (L. is right on some items, wrong on others):** I separate them: *"You're right about [specific step]: let's adjust that. But [other steps] are non-negotiable because [incident pattern]. Help me get the balance right."*

L. is an asset. Goal is alignment, not winning.