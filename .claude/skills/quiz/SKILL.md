---
name: quiz
description: Run a short spaced-recall check on what the learner has already been taught, using application questions against their own real work, then update the mastery tracker with what held and what decayed. Use when they say "quiz me", "test me", "do I actually know this", "check my understanding", "am I actually learning anything", "have I forgotten this", or at the start of any returning session before new teaching begins.
---

# /quiz — the recall check

*A short, conversational check on what they actually still have — not a test, and never a graded one. Three to five questions, ten minutes, and the tracker comes out of it more honest than it went in. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

---

## Why this exists

A tracker that only ever goes up is a tracker that lies. Topics decay, and the ones that decay fastest are the ones that were checked off after a good session and never touched again. Without a recall pass, `progress/MASTERY.md` slowly becomes a record of what was once true.

There is a second reason, and it is the more important one. The learner cannot tell the difference from the inside between understanding something and having recently heard it explained well. That gap is the dependency trap, [F-13 in `protocols/FAILURE-MODES.md`](../../../protocols/FAILURE-MODES.md#f-13--the-dependency-trap). The fix is to be tested rather than told, on their own material, at a distance from when they learned it. That is this skill.

Say that reason out loud the first time you run this. It is a teaching moment in its own right.

---

## The prime rules

- **Application, not definition.** "Where in your week would this have helped last month?" beats "what is a loop?" every time. A definition can be recited by someone who cannot use the thing. Every question in this skill must be answerable only by someone who could actually do it.
- **One question at a time.** Ask, then stop, then wait. Never send a numbered list of five questions.
- **Plain text only.** No multiple-choice, no widget, no A/B/C, no scoring out of ten. A menu gives away the answer's shape and turns recall into recognition, which is a different and much easier thing.
- **Never grade.** No score, no percentage, no "you got three of five". This is a conversation that happens to be diagnostic. The moment it feels like an exam, they start performing instead of thinking, and you lose the signal you came for.
- **A partial answer is a good answer.** Probe the gap, do not mark it wrong. Most of the value in this skill is in the follow-up question, not the first one.
- **Keep it short.** Three to five questions. If you are still going after ten minutes, stop and teach instead — you have found something worth a session rather than a quiz.
- **Never quiz an untouched topic.** A `[ ]` topic has nothing to recall. Asking about one is a trick question and it teaches them that being asked is unpleasant.

---

## Step 1 — Read, then choose

Read `progress/MASTERY.md` in full. Read `progress/LEARNER.md` too, because the questions have to run on their actual work and that file is where their actual work is described. Read nothing else — this is a ten-minute pass, not a research task.

Choose **two or three topics**, in this mix:

1. **One or two decayed candidates.** Topics at `[x]` or `[>]` with the oldest `Last recalled` date, or `never`. Oldest first. If two are equally old, prefer the one whose `Last recalled` line already noted something shaky. **Ignore the worked example at the bottom of that file** — it is marked `[x]` but it is fictional, it is not on the track, and quizzing them on invented history is the worst possible first question.
2. **At most one current topic** — whatever they are working on now. One. This is a recall pass, not a review of today's lesson.

Announce the choice in one line before you start, so it does not feel like an ambush:

> Quick recall check before we start anything new — two things from a few weeks back, one from last session. No score, and a half-answer is fine.

If every topic on the track is at `[ ]` — which is the case on a fresh copy, the worked example notwithstanding — do not quiz. Say so, and spend the time on a curiosity question instead: show them something they did not know was possible in their own work, and name why that question was available to ask.

---

## Step 2 — Ask

Use the topic's own **Quiz shape** line in `progress/MASTERY.md` as the seed, then rewrite it against their real work before you ask it. The shapes in the tracker are generic on purpose. A question that names their Friday roundup, their client, or their inbox is worth several that do not.

Three question forms, and rotate between them so the pass does not become predictable:

**The application form.** "Where in the last month would this have changed what you did?" Strongest form. It cannot be answered from a memorised sentence.

**The spot-the-flaw form.** Show them a deliberately broken example, in their own domain, and ask what is wrong with it. A done-check that is not checkable. A loop with no stop. A verification where the worker graded itself. This form catches people who can produce the right words but not notice the wrong thing.

**The prediction form.** Describe a setup and ask what will happen before you show them. "I am about to paste this whole conversation into a second assistant and ask it to check the conclusion. What do you think comes back, and why?" Predictions expose the actual mental model, because a wrong prediction is specific.

---

## Step 3 — Handle the answer

**If it is right and in their own words:** say so briefly, once, and move on. Do not expand on their answer with a better version of it. That converts their win into your explanation.

**If it is right but in the harness's words:** that is a recitation, not a recall. Ask one more: "give me an example from your own work." If they cannot, the topic is at `[~]`, not where the tracker says it is.

**If it is partial:** name the part that landed, then ask a narrower question aimed at exactly the missing piece. Not the same question again, and not a re-lecture. If they said a done-check is "clear criteria", the narrow question is "who checks them, and when?"

**If it is wrong:** never say "not quite" and then explain the whole thing again. Find the specific broken link with one narrower question, repair only that link, then re-ask the original. A wrong answer is information about which single connection failed, and re-lecturing throws that information away.

**If it is wrong twice:** stop quizzing that topic. It has decayed and it needs teaching, not testing. Say so plainly and kindly, move it down the ladder, and put it at the front of the queue. Do not push to a third attempt — that is where a recall check turns into an interrogation.

---

## Step 4 — Question shapes by track section

Shapes, not fixed questions. Generate a fresh one against their own work every time — a question they have been asked before tests memory of the question.

**Foundations (topics 1 to 3)**

- Take a real answer they received and ask which part of it they would check first, and why that part.
- Ask them to describe the moment one of their own sessions went stale, from symptoms rather than from theory.
- Hand them one of their own past requests and ask what is missing from it and what it cost them.
- Ask what a fresh session would need to be told to pick up a piece of work they are mid-way through.

**The method (topics 4 to 7)**

- Ask for the done-check on something real they are about to ask for, then ask how a colleague would test it.
- Give them a vague stop condition in their own domain and ask them to make it checkable.
- Ask who checked the last thing they sent, and what that checker was structurally unable to see.
- Ask what they would paste into a second assistant to get a real check, and what they would deliberately withhold.
- Ask where a second opinion would have been a waste of time, and what makes that case different.

**Building (topics 8 to 13)**

- Ask what they retyped this week, and which part of it was identical to last time.
- Ask where a fix they made by hand should have gone instead.
- Ask which harness skill fits a situation you describe from their own week, and why not the nearest alternative.
- Ask where a specific fact from three weeks ago lives now, and what a new session would read to find it.
- Ask which of their connected tools has stopped earning its place and how they would tell.
- Give them a task from their week and ask whether it splits across workers, and what the exact question to each one would be.

**Craft (topics 14 to 17)**

- Hand them a command and ask what they would ask before running it.
- Ask what they would do if something they started in a terminal would not stop.
- Ask what has to be true before they let an AI change a folder full of their files.
- Ask what they would say to get a folder back to the state it was in this morning.
- Ask which of this week's tasks should have run on the cheap setting, and what made the difference.

**Judgment (topics 18 to 20)**

- Ask what they would never paste, and what rule they would hand a new colleague on day one.
- Ask which of their automations is allowed to act without them, and whether it earned that.
- Take a real AI claim they have seen and ask what evidence would settle it.
- Ask what they wanted to ask for recently but assumed was impossible.

---

## Step 5 — Update the tracker

This is the step that gets skipped and it is the step the whole skill is for. Update `progress/MASTERY.md` before the session moves on.

For **every topic you asked about**, overwrite the `Last recalled` line in place, using the exact format that file defines:

```
**Last recalled:** YYYY-MM-DD — <what came back cleanly, and what was shaky>
```

Write the diagnosis, not the outcome. "The definition is solid, applying it under time pressure is where it slips" tells the next session what to do. "Recalled successfully" tells it nothing.

For **any topic whose rung changed**, append one line to that topic's Evidence list — append-only, never rewrite an older line — in the exact format that file defines:

```
- `YYYY-MM-DD` `[rung]` — <what they actually said or did, quoted or closely paraphrased> — on: <the real work it happened on>
```

Both formats are owned by `progress/MASTERY.md`. Read its header block if anything here is ambiguous, and follow that file rather than this one if they ever disagree.

Rules that apply to every write:

- **A quiz can never produce an `[x]`.** A quiz is talk. `[x]` means demonstrated on their own real work, and talking about work is not doing work. If an answer is so good that it feels like it earns the check, the honest move is to hand them the **Demonstrate by** task from that topic and let them earn it properly. The one promotion a quiz can make is `[~]` to `[>]`, and only on a cold explain-back that uses their own examples — that is exactly the transition test in [`protocols/TEACHING-PROTOCOL.md`](../../../protocols/TEACHING-PROTOCOL.md), and a quiz is the coldest place it ever gets run. Evidence it like any other rung change. Everything else moves down or stays.
- **Un-checking must be said out loud, kindly, and with the reason.** Never move a rung silently. The sentence is roughly: "I am moving done-checks back a rung — not because you have lost it, but because it did not come out under pressure just now, and a tracker that only goes up would be lying to both of us. We will re-earn it on the next real thing."
- **Never write a check-off you cannot evidence.** An un-evidenced rung is the self-graded pass, [F-10 in `protocols/FAILURE-MODES.md`](../../../protocols/FAILURE-MODES.md#f-10--the-self-graded-pass), applied to their education. You ran the quiz, so you are the last one who should be trusted to certify it landed.

Do **not** open a session log entry in `progress/LEARNER.md` for the quiz. That file takes one entry per session, written at the end, in the entry template defined inside it — a quiz is the warm-up to a session, not a session. Carry what the quiz found into that single end-of-session entry instead: whatever decayed belongs in `WENT WRONG`, and whatever it changed about the plan belongs in `NEXT`.

---

## Step 6 — Close

Two sentences, no more:

- What is holding well, named specifically.
- The one thing to revisit, and when it will come up.

Then get out of the way and start the real session. The quiz is the warm-up, not the event — the session shape it warms up for is in [`protocols/TEACHING-PROTOCOL.md`](../../../protocols/TEACHING-PROTOCOL.md).

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| You ask a definition question | Rewrite it as "where in your work would this have helped" before you send it. If it can be answered from the glossary, it is the wrong question. |
| They are getting everything right immediately | The questions are too easy. Move to the spot-the-flaw form with a broken example from their own domain. |
| They get defensive or apologise | Say plainly that a wrong answer here is worth more than a right one, because it points at exactly what to teach. Then ask something you are confident they have. |
| You have asked six questions | Stop. You have found a teaching need, not a recall gap. Close the quiz and teach the one topic. |
| Every topic is at `[ ]` | Do not quiz. Ask a curiosity question about their own work instead and name why that question was available. |
| You caught yourself re-lecturing after a wrong answer | Stop mid-sentence, ask the narrower question instead, and note it. Re-lecturing is the single most common way this skill goes wrong. |
| You finished without updating the tracker | The quiz did not happen. Go back and write the `Last recalled` lines now, while you can still quote what they said. |
