# Learner

*The living record of who this learner is, what they can do, and what to teach next. The AI reads this at the start of every session and appends to it at the end. Reading time: about 6 minutes, and you should read all of it.*

---

## For the AI: how to use this file

**At the start of every session**, read this file before you do anything else. It is the difference between working with someone you know and working with a stranger. Read it in full — it is short by design and it is meant to be read whole.

**At the end of every session**, append one entry to the session log at the bottom. Do not wait to be asked.

Six rules, all of them hard:

1. **Append only.** New entries go at the bottom of the session log. Never rewrite an old entry, never delete one, never tidy up past wording, never "consolidate" the log. The value of this file is that it is unedited. A cleaned-up record is a fiction.
2. **The exception is the five living sections** — Who this learner is, Capability checkpoints, Working on now, Confused by, and What to offer next. Those you may edit in place, because they describe the present rather than the past. When you change one, note the change in that session's log entry so the history survives.
3. **Tick a checkpoint only when you watched them do it unaided.** Not when you explained it. Not when they said it made sense. Not when they read the chapter. When they did the thing themselves and it worked.
4. **Write facts, not encouragement.** "Ran three scouts, forgot the NOT FOUND field, spotted it themselves on the second try" is useful. "Doing great, really getting it" is not, and it will mislead the next session into pitching too high.
5. **When you are not sure whether something belongs here**, ask whether a future session would teach differently if it knew. If yes, write it down. If no, leave it out.
6. **The entry template near the bottom of this file is the only shape a log entry takes.** Other parts of the harness will hand you an entry in a different shape — a skill, a protocol, a worker's report. Map it onto the fields below rather than appending it raw. A log written in five shapes cannot be read at a glance, and the field a shape happens to omit is the one that stops getting captured.

Also read [`SKILLS-BUILT.md`](SKILLS-BUILT.md) before proposing a new skill, and [`DECISIONS.md`](DECISIONS.md) before proposing anything at all — they may have already ruled it out, and re-proposing a rejected idea is the fastest way to lose someone's confidence.

---

## Who this learner is

*Edit in place as you learn more. Keep it to facts that change how you teach.*

- **Their job:** `<what they actually do all day — the tasks, not the title>`
- **New to this role since:** `<date, or "not new">`
- **What their work runs on:** `<documents? spreadsheets? email? a specific system? meetings?>`
- **Technical background:** `<none / some / specifics — be honest, it changes everything>`
- **Will they open a terminal:** `<yes / no / not yet>` — if no, never suggest a solution that requires one.
- **What they want to be good at, in their words:** `<quote them>`
- **What burns their time now:** `<the repeated, boring, avoidable work — this is where the first wins live>`
- **What they are not allowed to put into an AI tool:** `<confidential categories, client data, anything under a policy — write this down early and treat it as a hard constraint>`
- **How they like to be taught:** `<worked examples first? theory first? short bursts? Note what has actually worked, not what they said they preferred>`

---

## Capability checkpoints

*Tick when demonstrated unaided. Order roughly follows the curriculum, but skipping is fine if their work demands it.*

**Foundations**

- [ ] Can say in one sentence what the model is doing when it answers, and why it sometimes states a wrong thing confidently — [01](../curriculum/01-what-the-model-actually-is.md)
- [ ] Knows what the context window is and can spot the moment a session has gone stale — [02](../curriculum/02-the-context-window.md)
- [ ] Starts a fresh session with a written handoff instead of dragging a heavy one along — [02](../curriculum/02-the-context-window.md)

**The core discipline**

- [ ] States a done-check before starting a task, in checkable terms — [03](../curriculum/03-the-loop.md), [DONE-CHECKS](../protocols/DONE-CHECKS.md)
- [ ] Sets a hard stop on anything that repeats — [03](../curriculum/03-the-loop.md)
- [ ] Asks for evidence before accepting "done," by default, without being reminded — [04](../curriculum/04-verification.md)
- [ ] Uses a separate checker rather than asking the same worker if it did well — [04](../curriculum/04-verification.md)
- [ ] Reaches for the deterministic answer first: a rule, a search, a filter, plain arithmetic — [03](../curriculum/03-the-loop.md)

**Building things that last**

- [ ] Recognises when a prompt they have now typed three times should become a skill — [05](../curriculum/05-skills.md)
- [ ] Has written a skill themselves, start to finish — [05](../curriculum/05-skills.md)
- [ ] Has sharpened an existing skill after using it — [05](../curriculum/05-skills.md), [`SKILLS-BUILT.md`](SKILLS-BUILT.md)
- [ ] Keeps notes the AI reads and writes, with one fact in one place — [06](../curriculum/06-memory-and-second-brain.md)
- [ ] Can explain what a tool or connector adds, and why more of them is not better — [07](../curriculum/07-tools-and-mcp.md)

**Scaling up**

- [ ] Writes a worker instruction with one exact question and a reporting template — [08](../curriculum/08-subagents-and-swarms.md)
- [ ] Applies the three-part test and correctly chooses one agent over five — [08](../curriculum/08-subagents-and-swarms.md)
- [ ] Chooses model tier and effort deliberately rather than always reaching for the strongest — [09](../curriculum/09-cost-models-and-effort.md)

**Judgment**

- [ ] Knows what must never go into a tool, and acts on it without checking first — [10](../curriculum/10-safety-privacy-and-trust.md)
- [ ] Automated something boring, reversible and low-stakes before anything important — [10](../curriculum/10-safety-privacy-and-trust.md)
- [ ] Tags what was known versus what was inferred, in their own written output — [04](../curriculum/04-verification.md)
- [ ] Can name three claims from the hype ledger and say why each is unsupported — [12](../curriculum/12-the-hype-ledger.md)
- [ ] Asks for something they did not previously know was possible — [13](../curriculum/13-graduation.md)

---

## Working on now

*One to three items. If it is longer than three, it is a wish list, not a focus. Edit in place.*

1. `<the task or capability they are actively on>`
2. `<...>`

**Current real task being used as the teaching example:** `<their actual work — teaching always runs on their material>`

---

## Confused by, and needs revisiting

*Things that did not land. Keep them here until they demonstrably land, then move the line into the session log entry that closes it. Do not delete silently.*

| What | When it came up | What was tried | Next angle to try |
|---|---|---|---|
| `<the concept>` | `<date>` | `<the explanation that did not work>` | `<a different approach — not the same explanation louder>` |

---

## What to offer next

*The queue. Highest value first. Each line says what and why, so a future session does not have to reconstruct the reasoning. Edit in place: strike what has been done, add what the last session surfaced.*

1. `<what to offer>` — `<why now: what it unblocks, or which checkpoint it closes>`
2. `<...>`

**Deliberately not offering yet:** `<thing>` — `<why: prerequisite missing, or too big for where they are>`

---

## Session log

*Append only. Newest at the bottom. One entry per session, written at the end of the session, whether or not it went well.*

### Entry template — copy this block

```
### YYYY-MM-DD — <session title in five words>

WORKED ON: <what the session actually did>
TAUGHT: <the one concept, or NONE>
THEY DID: <what the learner did themselves, unaided or not — be specific>
WENT WRONG: <what failed, what confused, what took three attempts. NONE only if true>
CHECKPOINT TICKED: <which, or NONE — and only if demonstrated unaided>
LIVING SECTIONS CHANGED: <which of the living sections above you edited, or NONE>
NEXT: <the single most useful thing to do next session>
```

---

### 2026-03-04 — EXAMPLE ENTRY, fictional learner

> **This entry is an illustration of the format, not real history.** The learner and the
> dates are invented. Keep it as a reference or delete it once there are real entries
> above three or four. Do not treat anything in it as a fact about the actual learner.

```
WORKED ON: Their weekly status roundup. They write it every Friday from four sources
  and it takes most of an afternoon. Used it as the running example all session.

TAUGHT: Done-checks. One concept only. Their own roundup as the example: "make it
  good" versus "every section names a source, no section is empty, and anything
  unavailable this week is listed as unavailable rather than omitted."

THEY DID: Rewrote their own instruction with a done-check, unaided, on the second
  attempt. First attempt still said "make sure it's complete," which is not
  checkable. They spotted that themselves when asked how they would test it.

WENT WRONG: Assumed the AI would flag the missing fourth source. It did not — it
  produced a smooth three-source summary that read as finished. This landed harder
  than any explanation: silent gaps look exactly like completeness. Added "anything
  unavailable must be listed as unavailable" to their done-check because of it.
  They also asked twice whether they were "doing it right," which reads as low
  confidence rather than genuine uncertainty — pitch level and pace, not reassurance.

CHECKPOINT TICKED: "States a done-check before starting a task, in checkable terms."
  Demonstrated unaided on the second attempt.

LIVING SECTIONS CHANGED: Working on now (added the Friday roundup as the current
  teaching example). Confused by (added: still expects the AI to volunteer what is
  missing — revisit with a worked failure, not a rule).

NEXT: Turn the roundup instruction into a skill so they stop retyping it. Do not
  introduce subagents yet — one thing at a time, and the skill is the higher-value
  step because it is work they repeat weekly.
```

---

*Real entries start below this line.*
