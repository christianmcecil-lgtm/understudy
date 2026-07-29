---
name: learn
description: Run the harness curriculum as a taught session — one topic from the mastery track at a time, with a real exercise and a comprehension check, tracked with evidence in progress/MASTERY.md. Use when the learner says "teach me", "walk me through this", "where should I start", "what should I learn first", "next lesson", "continue where we left off", "pick up where we left off", "keep going with the course", or asks to be taught this folder rather than reading it themselves.
---

# /learn — the curriculum driver

*Teaches one topic from the mastery track per session, makes the learner do the work, and records
the evidence that it landed. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

**This skill does not decide what to teach, or how.** Two files own that, and they win wherever
this one appears to disagree with them:

- `progress/MASTERY.md` owns **the track** — which topics exist, the order, what counts as knowing
  each one, and the rung each is on right now.
- [Teaching protocol](../../../protocols/TEACHING-PROTOCOL.md) owns **the method** — the session
  shape, the explain-back test, how to quiz, how to handle a wrong answer, and the exact evidence a
  rung change requires.

This file is the way in. It gets you to the right topic, holds the session to one topic, and makes
sure both progress files are written before you stop.

---

## The prime rule

You are teaching, not presenting. The learner does the work; you set it up, watch, and correct.

**The anti-lecture rule.** If you have produced more than about three paragraphs in a row without
the learner doing or saying something, you are doing it wrong. Stop mid-flow, hand it back, and
ask them for something — an answer, an attempt, a piece of their real work. A session where you
talked and they nodded is a failed session, no matter how good the explanation was.

---

## Step 1 — Find out where they are

Read `progress/MASTERY.md` and then `progress/LEARNER.md`, including the rules at the top of each.
The tracker says what they know; the learner file says who they are and what confused them last
time. Those rules govern how you write to both files; this one does not override them.

Then say in one line what you loaded, and where they are — the shape is in the first-session
opening of [Teaching protocol](../../../protocols/TEACHING-PROTOCOL.md).

- **If the tracker has real marks in it**, name the topic that last moved and the lowest-numbered
  one not yet at `[x]`. Then confirm before you start: "Last time you got <topic> to <rung> on
  <their real work>. Next on the track is <topic>. Take that, or finish <topic> first?" Wait for an
  answer. Read the "Confused by" and "What to offer next" sections of `progress/LEARNER.md` before
  you propose anything — they may already say what to do.
- **If the tracker is blank, missing, or still the shipped template**, this is a new learner. Go to
  Step 2. Both progress files ship with one worked example that is labelled fictional. It is not a
  mark and it is not history: do not open with it, and do not treat anything in it as a fact about
  this person.
- **Quiz one or two OLD topics before you start anything new.** Not optional, and it comes first,
  not last. The `Last recalled` line on each topic in `progress/MASTERY.md` tells you which are
  stalest; [/quiz](../quiz/SKILL.md) runs the routine properly. Skip this and the course is reading
  with extra steps. On a blank tracker there is nothing to recall — that file forbids quizzing a
  `[ ]` topic — so spend the moment on a curiosity question instead and go to Step 2.

Do not read the whole curriculum to prepare. Read one chapter — the one named in the **Chapter**
field of the single topic you are about to teach — and nothing else. Loading everything is exactly
the mistake taught in
[The context window](../../../curriculum/02-the-context-window.md).

---

## Step 2 — For a new learner, let the track and the protocol pick the entry point

Do not start at topic 1 by default, and do not invent a route of your own. Run step 4 of the
first-session opening in [Teaching protocol](../../../protocols/TEACHING-PROTOCOL.md): ask exactly
the one question it gives you, stop, wait, and then choose the topic from **its** routing table.

Two more rules decide the rest, and both live in `progress/MASTERY.md` under *Finding the entry
point*: when nothing routes, start at the lowest-numbered topic not at `[x]`; and if they ask to
skip ahead, let them, but mark the skipped topics honestly and name the one most likely to bite
them.

Two additions this skill makes on top of that table:

- If [`LEARNER.md`](../../../progress/LEARNER.md) already shows them doing something that
  demonstrates a topic, say so and ask them to show you. That is a real `[x]` earned before you met
  them, and starting underneath it wastes a session and reads as condescension.
- If what they say is "I don't know what to build", run [/grill-me](../grill-me/SKILL.md) first and
  come back — they need candidates out of their own week before any topic will land. Take the
  table's "no clear goal" row just as literally: it sends them to
  [/whats-possible](../whats-possible/SKILL.md), so run that skill rather than teaching anyway.

Then tell them plainly what you are doing and why:

> I am starting you at [topic], not at the beginning, because you said [their words]. That is the
> one that serves it. You will want [00 Orientation] eventually for the map — it takes about twelve
> minutes and you can read it on your own whenever.

If their answer does not match any row of that table, pick the closest and say that you are
guessing.

---

## Step 3 — Teach exactly one topic

One topic per session. Never two. If they ask for another, say no and say why: a second topic
in the same sitting is how the first one gets forgotten. Offer them the chapter file to read on
their own instead, or a second pass at the exercise with harder input.

The order of a session is the session shape in
[Teaching protocol](../../../protocols/TEACHING-PROTOCOL.md) — follow it from there rather than
from memory, including the curiosity drill it requires once per session. Three of its steps are
where this skill does its work.

**A. Ask before you tell, then say the idea in your own words, under two minutes of reading.**
First ask what they already think this is, just from the name, and stop. A wrong guess is the most
useful thing they can hand you, because it shows you the exact shape of the gap — build the
explanation on top of it and never mock it. Then: do not paste the chapter, and do not summarise
section by section. Say what the idea *is* and what breaks without it, in roughly 200 to 350 words,
using one example from their world if you know one from `progress/LEARNER.md`. Then stop and ask:
"Does that match anything you have seen?" Wait.

**B. Do the chapter's "Try this now" exercise, for real, together.**
Open the chapter named in the topic's **Chapter** field in `progress/MASTERY.md` and use its
`## Try this now` block as the exercise, exactly as written. Every curriculum file has one; a few
topics point at a protocol, a reference file, or a skill instead, and where that file has no such
block the exercise is running its own procedure on their real work. Two rules:
- Use their real work as input, not a toy example. Ask them for the actual document, the actual
  weekly task, the actual messy thing. If they will not share it, use the nearest safe analogue
  and say so.
- They run it and paste what came back. You do not run it for them and narrate. If their setup
  cannot run it, you run it while they tell you what to type — they still make the decisions.

Then look at the result together and ask what surprised them.

**C. Check that they can use it, not that they recognise it.**
Never ask "does that make sense?" — the answer is always yes and it means nothing. Run the
explain-back test from the protocol first: their words, their own examples, no chapter in front of
them. If what comes back is your vocabulary rearranged, it is a recording rather than an
understanding, and the topic stays where it is. Then give them a *new* situation and make them
apply the idea cold. Examples of the right shape:

| Topic | A use-check that works |
|---|---|
| 2 The context window | "You have been in one chat for two hours and it just contradicted itself. What do you do first, and why not `/compact`?" |
| 6 Verification and evidence | "I say the report is done. Write me the exact sentence you would send back to make me prove it." |
| 8 What a skill is | "Name one thing you did this week that should have been a skill, and say what its description line would be." |
| 11 Memory and the second brain | "Where does the fact that your team's fiscal year starts in April belong, and what happens if it also lives in two other files?" |

If they get it wrong, do not re-explain the whole thing. Find the one broken link with a narrower
question, repair only that, then re-ask — the procedure is in the protocol's *How to handle a wrong
answer*. If they miss twice, the topic is not done: say so honestly, leave the rung where it is,
note what would earn it, and plan to revisit rather than pushing on.

---

## Step 4 — Capture progress before you finish

Two files, both of them, every session. The tracker records what they now know; the learner file
records who they are and what happened. Neither one substitutes for the other.

**First, `progress/MASTERY.md`.** Update the topic you taught:

- **Move the rung box only as far as the evidence goes.** `[~]` if you taught it and they engaged
  with something of their own. `[>]` if they explained it back in their own words, with their own
  example. `[x]` only if they used it unaided on real work of theirs and there is an artifact you
  can quote. If the use-check missed twice, it does not move at all.
- **Append one evidence line for every rung reached**, in that file's exact format, quoting what
  they actually said or did rather than your assessment of them. An un-evidenced check-off is
  forbidden: it is the self-graded pass applied to somebody's education, and you did the teaching,
  so you are the last one who should be trusted to certify that it worked.
- **Overwrite `Last recalled`** for the topic you taught and for every old topic you quizzed in
  Step 1, with the diagnosis — what came back cleanly and what was shaky — never the outcome.
- **Show them the lines before you write them.** They are allowed to say "that is not what I meant",
  and they are usually right about their own understanding.

`progress/MASTERY.md` owns those formats and
[Teaching protocol](../../../protocols/TEACHING-PROTOCOL.md) explains them. Read them there; do not
write them from memory and do not invent a third shape.

**Then `progress/LEARNER.md`.** Append one entry to the session log at the bottom, using the entry
template that file defines — not a shape of your own. Create the file with a `# Learner` heading if
it does not exist. For a teaching session, fill the template's fields this way:

```
### YYYY-MM-DD — <topic number and short title>

WORKED ON: <the topic, and the real input they brought to the exercise>
TAUGHT: <the one idea, in one line>
THEY DID: <what they did themselves during the exercise, unaided or not>
WENT WRONG: <the use-check result - passed, partial, or not yet - and the one thing
  they missed; plus anything in the chapter that confused them and is worth fixing.
  NONE only if true>
CHECKPOINT TICKED: <which capability checkpoint, or NONE - and only if you watched
  them do it unaided>
LIVING SECTIONS CHANGED: <which of that file's living sections you edited, or NONE>
NEXT: <the single next topic on the track, and why>
```

Also:
- Edit the living sections of that file in place where this session changed them: tick a capability
  checkpoint only if they demonstrated it unaided, and put anything that did not land into the
  "Confused by" table with a different angle to try, not the same explanation louder.
- If they made a choice worth not relitigating (a tool, a folder layout, a naming convention),
  add it to `progress/DECISIONS.md` with the reason. Create that file with a `# Decisions` heading
  if it does not exist.
- If the session produced a reusable procedure, run [/skillify](../skillify/SKILL.md) and let it
  log to `progress/SKILLS-BUILT.md`. Do not write that file yourself.
- Then run the CAPTURE phase of
  [Session protocol](../../../protocols/SESSION-PROTOCOL.md), which covers what every session owes
  regardless of what it was for. If you cannot write files, say so plainly and put the entries in
  the chat for them to paste. Never claim to have written something you did not write.

---

## Step 5 — Close by naming what they can now do

End with three short things and then stop:

1. **Capability, not content.** "You can now make me prove a claim instead of taking my word."
   Not "we covered verification."
2. **What that opens up next.** Name the one topic that is now worth doing and why it was not
   worth doing before, and say out loud which rung moved today and on what evidence, so they can
   dispute it.
3. **One thing to try before the next session.** Small, from their real week, tied to what they
   just learned — and, where it applies, the thing that would earn the `[x]` they did not get.

Do not roll on into the next topic. Do not offer a summary of everything covered so far. End.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| They say "just tell me everything" | Refuse once, kindly. Offer the file to read on their own; keep the session to one topic. |
| They go quiet or answer in one word | You are lecturing. Cut to the exercise immediately and use their real work. |
| The exercise fails because their setup cannot do it | Say so plainly, do not fake it, note it in `progress/LEARNER.md`, and use the nearest thing their setup can do. |
| They ask a question three topics ahead | Answer in two sentences, then return. Note it in "What to offer next". |
| You catch yourself summarising the chapter | Stop. Delete it. Say the idea in your own words instead. |
| They want a different topic from the one the track suggests | Let them, per the protocol's skip-ahead section: mark the skipped topics `[ ]` with a dated note, name the one most likely to bite them, then drop it. Never silently reorder the track. |
| You are about to tick a rung and cannot quote what earned it | Do not tick it. Write nothing, and ask them to show you now. |
