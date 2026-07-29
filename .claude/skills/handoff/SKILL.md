---
name: handoff
description: Close a long or degraded session by writing a purpose-built document that starts the next one clean. Use when the learner says "this session is getting long", "start fresh", "hand off", "make me a handoff doc", "write a handoff", "I'm going to open a new chat", "carry this over", or when the AI notices staleness signals and offers a handoff proactively.
---

# /handoff — end this session so the next one starts sharp

*Produces a short document containing only what the next session needs for one stated purpose,
plus the exact text to paste into the fresh session. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.
The reasoning behind this is taught in
[02 The context window](../../../curriculum/02-the-context-window.md) and the session mechanics
live in [Session protocol](../../../protocols/SESSION-PROTOCOL.md).

---

## Why this exists

A long conversation carries everything: the false starts, the abandoned approach, the file read
once and never used, the tangent about something else. All of it competes for attention every
turn. A handoff is not a summary of the session — it is a deliberate *forgetting*. You keep the
small slice that matters next and drop the rest on purpose.

This is not the same as compacting. Compacting summarises in place and keeps going, so the
sediment stays; a handoff forks a clean session with only the relevant slice. Compact when the
next thing continues the same debugging; hand off when the next thing deserves a fresh head.

---

## Offer it proactively when you see staleness signals

Do not wait to be asked. When two or more of these are true, say so and offer:

- You have re-read a file you already read earlier in the session.
- You contradicted something you said earlier, or the learner had to remind you of a decision.
- You are repeating advice you already gave.
- The session has drifted through two or more unrelated topics.
- A debugging attempt has cycled three times with no new information.
- The interface is warning that the context window is filling.
- The learner says any version of "you already told me that".

The offer, in one sentence, then wait:

> I think this session is past its best — I just re-read a file I already had and repeated
> myself. Want me to write a handoff so the next session starts clean? I need one thing from
> you first: what is the next session *for*?

---

## Step 1 — Require a purpose. Refuse without one.

**A handoff with no stated purpose is just a bloated summary.** It will contain everything,
because with no purpose there is no basis for leaving anything out, and it will start the next
session exactly as clogged as this one.

So: purpose is a required input. Ask for it plainly.

```
What is the next session for? One sentence, in the form "get X to Y" or
"decide whether to Z". If you tell me "continue this", I cannot write a
useful handoff - that is a request for a transcript, not a handoff.
```

Accept: "finish the client update skill and test it on March data." "Decide whether to keep the
notes in one file or split them." "Fix the reconciliation script so it handles refunds."

Do not accept, and say why: "continue", "keep going", "everything we did today", "you decide".
If they genuinely do not know what comes next, that is useful information — tell them the honest
answer is to end here and start the next session with `/learn` or `/grill-me` rather than carry
this one forward.

Once you have the purpose, use it as a filter on every single line you are about to write: does
the next session need this *for that purpose*? If no, it does not go in. Being ruthless here is
the whole value of the skill.

---

## Step 2 — Write the document

Use exactly these sections, in this order. Keep the whole thing short — if it runs past two pages
you have stopped filtering.

```markdown
# Handoff — <short topic>

## Purpose of the next session
<Their one sentence, verbatim.>

## Goal
<What "done" looks like for that purpose, stated so it can be checked. If there is an
objective done-check, put it here.>

## Current state
<Where things actually stand right now. What exists, what works, what is half-finished.
Facts only. No narrative of how we got here.>

## Decisions already made
<Each with its reason. This section exists so the next session does not reopen settled
questions. Format: "Chose X over Y because Z.">

## Explicitly ruled out
<What was considered and rejected, and why. Without this the next session will helpfully
suggest the thing that already failed.>

## Files and locations
<Pointers only - paths and one line on what each holds. Never paste file contents.>

## Open questions
<What is genuinely undecided, and who or what would settle it.>

## Immediate next action
<One action. Specific enough to start on without asking anything first.>
```

Rules for filling it in:

- **Pointers, not contents.** Name the file and say what is in it. The next session can read it
  if it needs it, and most of the time it will not. Pasting file contents into a handoff recreates
  the exact problem you are solving.
- **Decisions carry their reason.** "Chose X" invites relitigation. "Chose X over Y because Y
  broke on the January data" ends it.
- **Facts, not story.** Nobody needs the sequence of events. They need the current state.
- **One next action.** A list of five is a plan, and plans belong in the goal section. The next
  session needs one place to put its hands.

---

## Step 3 — Redact before you save

Read the document once more, specifically hunting for things that should not be written down:

- Passwords, API keys, tokens, connection strings. Never write these anywhere. Replace with
  `<credential - ask the human>`.
- Personal data about other people: names, addresses, health details, salary figures, anything a
  third party told them in confidence. Replace with a role: "the client", "the finance lead".
- Anything the learner's employer would not want sitting in a file. If you are unsure, ask.

If you replaced anything, tell them what and where in one line. See
[10 Safety, privacy, and trust](../../../curriculum/10-safety-privacy-and-trust.md).

---

## Step 4 — Save it outside the harness

**Do not write the handoff into this folder.** The harness is a teaching artifact that may be
handed to someone else; a handoff is their live work, and it may reference things that should
not travel. Keeping the two separate also means the harness stays clean enough to pass on.

Save it to a scratch location, named `handoff-<short-topic>-<date>.md`:

- Default: your environment's temporary directory, which is disposable by design. Resolve that
  path from the environment rather than typing a guess; if you cannot, ask the learner for a
  folder outside this one and use that.

Then tell them the full path, plainly, once. If your environment cannot write files at all, say
so honestly and output the document in the chat instead, telling them to save it themselves.

---

## Step 5 — Tell them exactly what to paste

End the session with this, filled in. Do not paraphrase it into advice — give them the literal
block to copy.

```
Open a new chat, then paste this:

---
Read the handoff document at <full path>. That is your starting context.

Then read only the files it points to that you actually need for the stated
purpose. Do not read the rest of my folder.

Confirm back to me in three lines: the purpose, the current state, and the
immediate next action. Then start on that action.
---
```

If Step 4 could not write a file and the document is in the chat instead, change the first line of
that block to "Read the handoff document I am pasting below" and put the document under it. The
paste block must never point at a path that does not exist.

Add one closing line about what is intentionally being left behind: "I am not carrying over the
tangent about the calendar tool or the first approach we abandoned. If either matters, say so now."

Before you stop, do the end-of-session capture the constitution requires: append one entry to the
session log in `progress/LEARNER.md`, using the entry template defined inside that file. The handoff
is disposable and lives outside this folder; the progress files are what survives it.

Then stop. Do not continue working in this session after writing the handoff — that is how the
handoff goes stale before it is used.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| They will not state a purpose | Do not write the document. Explain in one sentence why, and offer to end the session cleanly instead. |
| The handoff runs to four pages | You stopped filtering. Cut everything the stated purpose does not need, especially the story of how you got here. |
| You are tempted to paste a file into it | Put the path in instead. Always. |
| The next session immediately asks a question the handoff should have answered | Note it, and add that item to the template shape above so future handoffs cover it. |
| Several decisions were made and none were recorded anywhere durable | Before saving, add them to `progress/DECISIONS.md` as well, creating it with a `# Decisions` heading if it does not exist. The handoff is disposable; that file is not. |
