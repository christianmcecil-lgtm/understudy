# Mastery

*The tracked curriculum: twenty-two topics, what counts as knowing each one, and the evidence that it was actually known. The AI reads this at the start of every teaching session — and before any quiz, coaching intervention, or practice review — and writes to it whenever a rung moves or a topic is recalled. Reading time: about 8 minutes, and you should read all of it before teaching anything.*

---

## For the AI: how to read and update this file

This file is two things at once. For the learner it is a report card. For you it is the map — it tells you where they are, what to teach next, and what to quiz on. It is the file that stops teaching from drifting into a pleasant conversation with nothing behind it.

**Read it whole at the start of every teaching session, and before any quiz, coaching intervention, or practice review.** It is long-ish but it is the cheapest orientation available: one read tells you what they know, what they half-know, and what they have never seen. An ordinary working session does not open it — the START phase of [`protocols/SESSION-PROTOCOL.md`](../protocols/SESSION-PROTOCOL.md) loads two files and this is not one of them.

**Write to it at the end of every session in which a rung moved or a topic was recalled**, and at the moment a rung is earned, not later from memory.

The shape of a teaching session — what to do with this map once you have read it — is in [`protocols/TEACHING-PROTOCOL.md`](../protocols/TEACHING-PROTOCOL.md). This file is the state; that file is the method.

There is deliberately **no summary table** at the top of this file. One fact in one place: the status of a topic lives in its own heading and nowhere else. A summary table would be a second copy of the same fact, and second copies drift.

### The four-rung ladder

Every topic sits on one of four rungs. The box in the topic heading is the rung.

| Rung | Means | What earns it |
|---|---|---|
| `[ ]` | Untouched | Nothing yet. They may have heard the word. That is not a rung. |
| `[~]` | Explained to them | You taught it. They followed along and did not object. This rung is worth almost nothing on its own and you should treat it that way. |
| `[>]` | Explained back by them | They said it back in their own words, using an example from their own work, without the chapter in front of them. |
| `[x]` | Demonstrated on their own real work | They used it, unaided, on something that actually mattered to them, and it worked. |

**Only `[x]` counts as known.** Everything else is progress, not knowledge.

The tell that separates `[~]` from `[>]`: a real explain-back uses **their** examples — their Friday report, their client, their inbox. A fuzzy one reuses the harness's words and the harness's examples. If you hear your own phrasing come back at you, they have memorised a sentence, not learned a thing. Ask a narrower question and find the actual gap.

### The rules, all of them hard

1. **Never advance a rung without evidence written into the topic's Evidence list.** An un-evidenced check-off is the self-graded pass, [F-10 in FAILURE-MODES.md](../protocols/FAILURE-MODES.md#f-10--the-self-graded-pass), applied to somebody's education. You did the teaching, so you are the last one who should be trusted to certify that it landed. The evidence line is what makes the claim checkable by someone who was not there.
2. **Never advance on exposure.** Reading the chapter is not a rung. Watching you do it is not a rung. Saying "that makes sense" is not a rung.
3. **The Evidence list is append-only.** Never rewrite or tidy an old evidence line, including one that records a topic going backwards. The value of this file is that it is unedited. `none yet` is a placeholder rather than a line — the first real evidence replaces it, and after that nothing is ever replaced again.
4. **Last recalled and the rung box are editable in place**, because they describe the present rather than the past. Everything else in a topic block — chapter, known-when, quiz shape, demonstrate-by — is fixed. Do not reword them to match a session.
5. **Honest un-checking.** If a learner clearly no longer has a topic, move it back down the ladder, write an evidence line saying so, and tell them kindly and without drama. A tracker that only ever goes up is a tracker that lies, and a lying tracker makes you teach the wrong thing next week.
6. **One topic per session.** Depth over coverage. If they want to cover two, you cover one well and say why.
7. **Do not quiz a `[ ]` topic.** There is nothing there to recall. Use the moment for a curiosity question instead — show them something they did not know to ask for.

### The exact line formats

Two formats, used by this file, by [`.claude/skills/quiz/SKILL.md`](../.claude/skills/quiz/SKILL.md), and by anything else in the harness that writes here. This file owns these formats. Do not invent a third shape.

**Evidence line** — append one to the topic's Evidence list every time a rung changes, in either direction:

```
- `YYYY-MM-DD` `[rung]` — <what they actually said or did, quoted or closely paraphrased> — on: <the real work it happened on>
```

The middle field is the load-bearing one. "Understood the concept" is not evidence. "Said a done-check is 'something my colleague could check without asking me what I meant'" is evidence, because a stranger reading it can judge whether the rung was earned.

**Last recalled line** — overwrite in place whenever the topic comes up in a quiz or in passing:

```
**Last recalled:** YYYY-MM-DD — <what came back cleanly, and what was shaky>
```

`Last recalled` is how [/quiz](../.claude/skills/quiz/SKILL.md) decides what to ask about. If you never update it, spaced recall stops working and the same three topics get asked forever.

### Finding the entry point

Do not start at topic 1 by default. At the start of a first session:

- Read [`LEARNER.md`](LEARNER.md) first. If they already do something that clearly demonstrates a topic, say so and ask them to show you — that is a real `[x]`, earned before you met them.
- Otherwise start at the **lowest-numbered topic not at `[x]`**, which on a fresh copy of this file is topic 1. The worked example at the bottom of this file is marked `[x]` and is fictional — it is not part of the track and never counts as progress.
- If they ask to skip ahead, let them. Mark the skipped topics honestly as `[ ]`, and tell them which one is most likely to bite them and why. Skipping done-checks before loops is the usual expensive one.

### Two notes on the track itself

**The teaching order is not the file numbering.** Chapters are numbered for reference; this track is ordered for learning. Chapter 17 is taught twice and chapter 11 is not on the track at all — it is a planning document they should read when they are ready to plan, not a topic to be examined on.

**Topics 7 and 16 point at the same chapter on purpose.** Topic 7 is the principle — why a model is a poor judge of its own output. Topic 16 is the practice — actually running work past a second model as a habit. The principle is worth teaching early, in with verification where it belongs. The practice needs tools and setup and belongs later. Same chapter, two different rungs to earn.

---

## Foundations

### `[ ]` 1 · What the model actually is

- **Chapter:** [`curriculum/01-what-the-model-actually-is.md`](../curriculum/01-what-the-model-actually-is.md)
- **Known when:** you can say in one sentence what the model is doing when it answers, and explain why a confident wrong answer is expected behaviour of that mechanism rather than a malfunction.
- **Quiz shape:** "You got an answer recently that turned out to be wrong but sounded completely certain. Walk me through what was actually happening when it produced that — no jargon, as if to a colleague."
- **Demonstrate by:** taking a real answer they received for their own work, marking which parts are the kind of thing this mechanism invents, and naming the one claim they would check first and exactly how they would check it.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 2 · The context window

- **Chapter:** [`curriculum/02-the-context-window.md`](../curriculum/02-the-context-window.md)
- **Known when:** you notice a session going stale from its symptoms rather than from a warning, and you start a fresh one with a written handoff instead of pushing on.
- **Quiz shape:** "Think about the longest chat you had this month. Where did it start getting worse, what were the signs, and what would you do differently at that exact point now?"
- **Demonstrate by:** taking one of their own heavy sessions, writing the handoff, opening a fresh session with it, and showing that the new session picks up the work correctly with none of the weight.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 3 · Asking well

- **Chapter:** [`reference/PROMPT-PATTERNS.md`](../reference/PROMPT-PATTERNS.md)
- **Known when:** you can take one of your own vague requests, name what is missing from it, and predict how the output will change before you rerun it.
- **Quiz shape:** "Here is a request you sent earlier this week. Which piece is missing — audience, purpose, constraints, format, a model of good, or what to leave out — and which missing piece is costing you the most?"
- **Demonstrate by:** rewriting a request they actually sent for real work, running both versions, and naming the specific difference in the output rather than saying it was better.
- **Evidence:** none yet
- **Last recalled:** never

---

## The method

### `[ ]` 4 · The loop

- **Chapter:** [`curriculum/03-the-loop.md`](../curriculum/03-the-loop.md)
- **Known when:** you can describe a repeated piece of your own work as an input, a step, a check, and a stop — and say which part of it is currently missing.
- **Quiz shape:** "Where in last month's work would a loop have actually helped? Now tell me where one would have run all night and produced nothing you could keep — what is the difference between the two?"
- **Demonstrate by:** taking one of their own recurring tasks, writing it out as a bounded loop with a hard cap, running it once, and reporting what each pass produced.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 5 · Done-checks

- **Chapter:** [`protocols/DONE-CHECKS.md`](../protocols/DONE-CHECKS.md)
- **Known when:** you state a done-check before starting, in terms a stranger could evaluate, and you can tell when your own done-check is not actually checkable.
- **Quiz shape:** "Give me the done-check for the last thing you asked an AI to do. Now: how would a colleague who was not in the room test whether it was met?" Follow with a deliberately broken one — "make it clear and comprehensive" — and ask them to say what is wrong with it.
- **Demonstrate by:** writing the done-check for one of their real deliverables *before* it is produced, then holding the output against it and finding at least one gap they would otherwise have accepted.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 6 · Verification and evidence

- **Chapter:** [`curriculum/04-verification.md`](../curriculum/04-verification.md)
- **Known when:** you ask for evidence rather than a verdict by default, and you never let the thing that did the work be the thing that decides it is done.
- **Quiz shape:** "Something you sent out last month — who checked it? If the answer is the AI that wrote it, what would that check have been able to see, and what would it have been structurally unable to see?"
- **Demonstrate by:** running a real check on one of their own deliverables from a separate session that was not told who wrote it, and producing the met / not met / cannot tell table with quoted lines.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 7 · Cross-model verification

- **Chapter:** [`curriculum/17-many-models.md`](../curriculum/17-many-models.md) — the principle half
- **Known when:** you can explain why a model is a weak judge of its own output, where a different model helps, and why two models agreeing is not proof.
- **Quiz shape:** "Two different assistants gave you the same answer. How much more confident does that make you, honestly — and what kind of check would still beat both of them agreeing?"
- **Demonstrate by:** taking a real artifact of theirs, handing a second assistant the artifact and the criteria and nothing about how it was made, and reporting what came back and whether it changed the deliverable.
- **Evidence:** none yet
- **Last recalled:** never

---

## Building

### `[ ]` 8 · What a skill is

- **Chapter:** [`curriculum/05-skills.md`](../curriculum/05-skills.md)
- **Known when:** you can point at something you have now typed three times and say what the skill version of it would have to know.
- **Quiz shape:** "What did you retype from memory this week? What part of it is the same every time, and what part changes per run?"
- **Demonstrate by:** identifying a genuinely repeated task from their own week and splitting it out loud into the fixed part and the varying part, without help.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 9 · The skill library

- **Chapter:** [`curriculum/14-the-skill-library.md`](../curriculum/14-the-skill-library.md)
- **Known when:** you reach for the right skill in this harness at the right moment without scrolling a list to find it.
- **Quiz shape:** "You have just finished a report you are not sure holds up, and it is going to someone senior. Which skill do you reach for, and why that one rather than the two nearest alternatives?"
- **Demonstrate by:** using two different harness skills inside one real work session on their own material, and afterwards saying why each one was the right call at that moment.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 10 · Building your own skill

- **Chapter:** [`.claude/skills/skillify/SKILL.md`](../.claude/skills/skillify/SKILL.md)
- **Known when:** you have written a skill start to finish, used it more than once on real work, and sharpened it once from something you had to fix by hand.
- **Quiz shape:** "Your skill produced something you had to correct manually. Where does that correction go, and what happens if it goes in your head instead?"
- **Demonstrate by:** writing and saving a skill for one of their own repeated tasks, running it twice on real work, and folding one real workaround back into it — logged in [`SKILLS-BUILT.md`](SKILLS-BUILT.md).
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 11 · Memory and the second brain

- **Chapter:** [`curriculum/06-memory-and-second-brain.md`](../curriculum/06-memory-and-second-brain.md)
- **Known when:** you keep notes the AI reads and writes, with one fact in one place, and you load the router plus the one thing you need rather than everything.
- **Quiz shape:** "You told an AI something important three weeks ago that still matters. Where does that fact live now? What exactly would a brand-new session have to read to find it — and how long would that take it?"
- **Demonstrate by:** setting up their own notes file or files for a real ongoing piece of their work, then having a fresh session get fully up to speed from those files alone, with them watching.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 12 · Tools and connectors

- **Chapter:** [`curriculum/07-tools-and-mcp.md`](../curriculum/07-tools-and-mcp.md)
- **Known when:** you can say what a connector adds over pasting, and why connecting everything you own makes answers worse rather than better.
- **Quiz shape:** "Of the systems your work runs on, which one would genuinely earn a connection, and which one would you turn back off after a week? How would you tell the difference — what would you actually observe?"
- **Demonstrate by:** connecting or requesting exactly one tool for a real task of theirs, using it, and then saying concretely what it added that copying and pasting would not have.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 13 · Subagents and fan-out

- **Chapter:** [`curriculum/08-subagents-and-swarms.md`](../curriculum/08-subagents-and-swarms.md)
- **Known when:** you can write a worker instruction with one exact question and a reporting template, and you correctly choose one agent over five when the pieces are not independent.
- **Quiz shape:** "Take the biggest thing on your plate this week. Would you split it across workers? If yes, what is the exact question each one gets and what shape does its answer come back in? If no, what specifically makes it un-splittable?"
- **Demonstrate by:** fanning out on a real task of theirs where the pieces genuinely are independent, with a written reporting template, then judging honestly whether it beat doing it in one pass.
- **Evidence:** none yet
- **Last recalled:** never

---

## Craft

### `[ ]` 14 · The terminal

- **Chapter:** [`curriculum/16-the-terminal.md`](../curriculum/16-the-terminal.md)
- **Known when:** you can open it, tell where you are, move to a folder, run something, stop a runaway process, and read an error well enough to paste it somewhere useful — and it no longer frightens you.
- **Quiz shape:** "Someone hands you a command and says paste this. What do you ask before you run it? Which shapes of command would make you refuse outright even after an explanation?"
- **Demonstrate by:** on their own machine, opening a terminal, finding out where they are, moving to their own working folder, running one harmless command, and deliberately stopping a running process.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 15 · Git

- **Chapter:** [`curriculum/15-git.md`](../curriculum/15-git.md)
- **Known when:** you can say in one sentence what a commit is, and you commit before letting an AI change a lot of files because you understand what that buys you.
- **Quiz shape:** "An AI just changed nine of your files and the result is worse than what you had. What do you say to get back to this morning — and what had to be true beforehand for that to work at all?"
- **Demonstrate by:** putting one of their own real folders under version control, committing before an AI makes a change to it, and then rolling back a change they did not like.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 16 · Running many models side by side

- **Chapter:** [`curriculum/17-many-models.md`](../curriculum/17-many-models.md) — the practice half
- **Known when:** getting a second opinion from a different assistant is a habit on work that matters, and you hand it the artifact and the criteria without the reasoning that produced them.
- **Quiz shape:** "You want a second model to check this properly. What exactly do you paste in — and what do you deliberately leave out, and why does leaving it out matter?"
- **Demonstrate by:** running a real deliverable of theirs through a second assistant with a refutation prompt, then reporting what it caught, what it got wrong, and what both models missed.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 17 · Cost, model tiers, and effort

- **Chapter:** [`curriculum/09-cost-models-and-effort.md`](../curriculum/09-cost-models-and-effort.md)
- **Known when:** you choose model tier and effort deliberately, and can say why reaching for the strongest option every time is a bad default rather than a safe one.
- **Quiz shape:** "Of everything you did with AI this week, which should have run on the cheapest setting, and which one earned the expensive one? What made the difference?"
- **Demonstrate by:** taking one of their own recurring tasks, running it at two different tiers or effort levels, comparing the outputs themselves, and deciding which one it lives on from now on.
- **Evidence:** none yet
- **Last recalled:** never

---

## Judgment

### `[ ]` 18 · Safety, privacy, and the trust ladder

- **Chapter:** [`curriculum/10-safety-privacy-and-trust.md`](../curriculum/10-safety-privacy-and-trust.md)
- **Known when:** you know what must never go into a tool and act on it without checking first, and you automate the boring reversible thing before anything that matters.
- **Quiz shape:** "What in your work would you never paste into an assistant? Now give me the one-sentence rule you would hand a new colleague on their first day — one they could actually follow without a lawyer."
- **Demonstrate by:** writing their own do-not-paste list into [`LEARNER.md`](LEARNER.md) in their own words, and putting one real automation of theirs into propose-only mode before it is ever allowed to act.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 19 · Reading AI claims

- **Chapter:** [`curriculum/12-the-hype-ledger.md`](../curriculum/12-the-hype-ledger.md)
- **Known when:** you can take a claim you saw this week, say what would have to be true for it to hold, and name what evidence would settle it either way.
- **Quiz shape:** "Show me something about AI you read or were told recently. What is the actual claim underneath it, who benefits if you believe it, and what would change your mind?"
- **Demonstrate by:** taking a real claim from their own workplace or feed and writing the three-line verdict — what is supported, what is not, what would settle it — then acting on that verdict rather than filing it.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 20 · Curiosity

- **Chapter:** [`curriculum/13-graduation.md`](../curriculum/13-graduation.md)
- **Known when:** you ask for things you did not previously know were possible, and you generate your own next question instead of working through somebody's list.
- **Quiz shape:** "What did you want to ask for this month but assumed was not possible? What made you assume that — and was the assumption about the tool or about yourself?"
- **Demonstrate by:** bringing a request nobody suggested, that no chapter in this harness covers, and driving it to a working result on their own real work.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 21 · Knowing what situation you are in

- **Chapter:** [`protocols/SITUATIONS.md`](../protocols/SITUATIONS.md)
- **Known when:** you can name the situation you are in before you ask for help — and route it with the four questions (is the problem the goal, the information, the checking, or the conversation itself?) rather than by scrolling a catalogue for a match.
- **Quiz shape:** "Think of the last stretch of work with an AI that felt like wading. Which of the four questions would have caught it, and what would you have done differently in the first five minutes if you had named it then?"
- **Demonstrate by:** naming their own situation out loud, unprompted, while it is happening on their real work, and taking that situation's move before asking what to do.
- **Evidence:** none yet
- **Last recalled:** never

### `[ ]` 22 · Reviewing your own practice

- **Chapter:** [`protocols/REVIEW-ROUTINE.md`](../protocols/REVIEW-ROUTINE.md)
- **Known when:** a review of how you have been working happens on a cadence you chose for a stated reason, and each one ends with one thing done rather than a list of three.
- **Quiz shape:** "Say a review handed you three items and a fortnight later you had done none of them. What does that tell you — is it the cadence, the size of the items, or the routine not earning its slot? What would you change first, and how would you know it worked?"
- **Demonstrate by:** running a review over their own record, acting on item one the same day, marking it, and setting the recurring reminder at a cadence they can justify from what the review actually found.
- **Evidence:** none yet
- **Last recalled:** never

---

## Worked example — what a filled-in topic looks like

> **This block is an illustration of the format, not real history.** The learner, the dates,
> and the work are invented. Keep it as a reference, or delete it once several real topics
> have been filled in. Do not treat anything in it as a fact about the actual learner, and do
> not copy its rung into the real topic 5 above.
>
> **It is not state.** Everything below this line is outside the track. Never count it when
> deciding the entry point, never select it as a quiz candidate, never list it when they ask
> what they know so far, and never write into it. On a fresh copy of this file the track is
> entirely at `[ ]` even though this block says `[x]`.

### `[x]` 5 · Done-checks — EXAMPLE, fictional

- **Chapter:** [`protocols/DONE-CHECKS.md`](../protocols/DONE-CHECKS.md)
- **Known when:** you state a done-check before starting, in terms a stranger could evaluate, and you can tell when your own done-check is not actually checkable.
- **Quiz shape:** "Give me the done-check for the last thing you asked an AI to do. Now: how would a colleague who was not in the room test whether it was met?" Follow with a deliberately broken one — "make it clear and comprehensive" — and ask them to say what is wrong with it.
- **Demonstrate by:** writing the done-check for one of their real deliverables *before* it is produced, then holding the output against it and finding at least one gap they would otherwise have accepted.
- **Evidence:**
  - `2026-03-04` `[~]` — taught it against their Friday status roundup; contrasted "make it good" with a version naming every required source — on: the Friday roundup
  - `2026-03-04` `[>]` — explained it back as "a done-check is something my colleague could test on Monday without asking me what I meant by good", and gave their own example: every one of the four sources named, and a missing source listed as missing rather than dropped — on: the Friday roundup
  - `2026-03-11` `[x]` — wrote the done-check for that week's roundup before asking for a draft, unaided; the draft met three of four conditions and they caught the fourth themselves, which was the silently omitted source — on: the Friday roundup, week of 9 March
  - `2026-04-22` `[>]` — un-checked. Six weeks later, asked for a "thorough" competitor summary with no done-check stated, and did not notice until asked what "thorough" would be tested against. Moved back down a rung honestly; re-earned it the following session on the same task — on: the competitor summary
- **Last recalled:** 2026-04-22 — the definition is solid and comes out in their own words. Applying it under time pressure is where it slips. Quiz this one on application, never on definition.

---

## Notes for the AI on using the example

Three things that example is trying to show you.

**The evidence lines are specific enough to be argued with.** "Explained it back as 'something my colleague could test on Monday'" can be judged by a stranger. "Understood done-checks" cannot. If your evidence line could have been written without the session happening, it is not evidence.

**One entry per rung change, including the one that goes down.** The `2026-04-22` line is the most useful line in that topic, because it tells the next session exactly where the weakness is and stops them re-teaching the part that was never broken.

**Last recalled carries the diagnosis, not the score.** "The definition is solid, applying it under pressure is where it slips" is what makes the next quiz good. "Recalled successfully" is what makes the next quiz useless.

Related files: [`LEARNER.md`](LEARNER.md) for who they are and what they are working on, [`SKILLS-BUILT.md`](SKILLS-BUILT.md) for what they have built, [`DECISIONS.md`](DECISIONS.md) for what has already been ruled out, and [`.claude/skills/quiz/SKILL.md`](../.claude/skills/quiz/SKILL.md) for the recall pass that keeps this file honest.
