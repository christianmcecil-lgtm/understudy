---
name: recall-session
description: Find and read back a past piece of work — what was decided, what was built, what was left open — using whatever access to past conversations this environment actually has, and saying honestly which one it used. Use when the learner says "what did we do last time", "find that chat where", "look back at", "pull up the session about", "what did I decide about", "remind me what we agreed", "did we already try this", or asks about work from a previous day or week.
---

# /recall-session — find what you did before

*Locates past work, states plainly how it was located, and returns decisions, artifacts and open
threads rather than a retelling. Read time for the AI: 5 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

---

## The thing you must be honest about

**You generally cannot read the learner's other conversations.** Each session is its own closed
box. Some tools expose session history to the assistant running inside them; most chat interfaces
do not. If you behave as though you can see a conversation you cannot see, you will produce a
confident, plausible, invented account of a session that never happened — and the learner will
have no way to tell.

So this skill has one non-negotiable habit: **say where the answer came from, every time, before
you answer.** A recall built from a one-line summary is a different thing from a recall built from
a full transcript, and the learner is entitled to know which one they are reading.

Never reconstruct a session from plausibility. If the material is not there, the correct output is
"I could not find it, here is how to get it to me" — not a reasonable-sounding guess.

---

## STEP 1 — Establish the tier, and say it out loud

Four tiers, strongest first. Work out which of them are **available** here before you search
anything — that takes seconds and it is what the learner needs to hear first. The searching itself
happens in STEP 2, and if the best available tier comes back empty you drop to the next one there.

**Tier 1 — Native session access.** Check what tools you actually have in this session. Look for
anything that lists, searches, reads, or exports prior conversations or sessions. Do not assume a
tool exists because a similar tool existed somewhere else; look at your actual available tools and
report what you found. If such a tool exists, this is the strongest tier: you can read what was
really said.

**Tier 2 — Exported transcripts on disk.** Check whether `progress/LEARNER.md` records where the
learner exports past conversations to. If it does, read from there. If it does not, ask once —
and if they have an exports folder, record it in the "Who this learner is" section of
`progress/LEARNER.md` so no future session has to ask again. That is one of the living sections
that file permits editing in place, and it takes one more bullet in the same shape as the bullets
already there: `- **Where they export conversations to:** <folder>`. Do not invent a new heading
or a new block for it. Exports live **outside** this folder; the harness is portable and their
conversations are not.

**Tier 3 — This harness's own written record.** `progress/SESSION-LOG.md` is the answer that always
works, because a line is written into it at the end of every session. This is the primary design,
not a consolation prize. Alongside it read `progress/DECISIONS.md` for what was settled,
`progress/SKILLS-BUILT.md` for what was built, `progress/REVIEWS.md` for past coaching reviews, and
the session log at the bottom of `progress/LEARNER.md` for the teaching side of the same sessions.

**Tier 4 — The learner pastes it.** Always available, works in every environment, costs them about
thirty seconds. Never treat this as a failure. It is often the fastest route to a real answer.

Then state the tier in one line, in this shape, before you say anything about their question:

```
Reading from: progress/SESSION-LOG.md and progress/DECISIONS.md (tier 3 — my own written
summaries, not the actual conversations). I have no way to read the original chats in this setup.
```

or

```
Reading from: this environment's session history tools (tier 1 — the actual conversations).
```

---

## STEP 2 — Search by what they remember, never by title

**Do not ask for a title.** Nobody remembers what a chat was called. They remember what they were
trying to do, roughly when it was, who it was for, and what was annoying about it.

If their request already contains enough to search on, search. If it does not, ask **one** question,
not a form:

```
What do you remember about it? Anything works — roughly when, what you were trying to get done,
who it was for, or what was frustrating about it.
```

Then turn what they gave you into several search keys, not one. Search on:

- the **task words** they used ("the supplier list", "the Friday roundup")
- **synonyms and near-misses** — they may have called it something else at the time
- the **date range**, treated loosely; "last Tuesday" means that week, not that day
- the **artifact** — a file name, a document, a spreadsheet, a person's role
- the **tool or skill** involved, if they mention one

Search each key, in the best tier available. **If that tier returns nothing, drop to the next one
and say both things happened** — "the session tools found nothing for those words, so I am now
reading my own written summaries" is exactly the sentence to say. Silently sliding down a tier is
how a learner ends up trusting a thin answer.

Then say what you searched and what matched. If two candidates fit, show both in one line each and
let them pick rather than guessing.

---

## STEP 3 — Report in this shape, not as a story

Nobody wants the conversation replayed. They want the four things that survived it. Use exactly
these headings:

```
FROM: <date, and which source this came from>

DECIDED: <what was settled, and why, if the reason was recorded. "Nothing recorded" is a
  legitimate answer and a more useful one than a guess.>

BUILT: <what actually exists now as a result — a file, a skill, a document, a changed process.
  Name it and say where it is.>

STILL OPEN: <what was left unfinished, and what the next step was going to be.>

NOT CAPTURED: <what this source does not tell you. Say it plainly.>
```

That last field is the one that makes this skill trustworthy. On tier 3 you are reading a handful
of short lines, so `NOT CAPTURED` will often be long: the exact wording, the reasoning that was
discussed and discarded, what the output looked like. Say so.

---

## STEP 4 — Offer the escalation when detail actually matters

If you are on tier 3 or 4 and the learner needs something the summaries cannot give — exact
wording, the reasoning behind a choice, what an output actually looked like — do not strain the
summary. Offer the upgrade in one line:

```
That level of detail is not in my summary. If you still have that conversation, paste it in and
I will read the real thing. Otherwise I can tell you what I do have and flag what is missing.
```

**How to export a conversation** — give this generically, because every product does it
differently and a menu path stated as fact will be wrong for somebody:

> Look for a way to save the conversation itself. In most tools the control sits with the
> conversation — near its title, or grouped with the options that also let you rename or delete it —
> and it will be called something like export, download, save, or share. Some tools instead put it
> in settings, under a heading about your data or your account, and export everything at once
> rather than one chat. If you cannot find it in a minute, stop looking: select the text of the
> conversation, copy it, and paste it into a plain text file. That works everywhere and loses
> nothing that matters for this.

If they want this to be routine, tell them to keep one folder outside the harness for exports,
name each file `YYYY-MM-DD-<a few words about the topic>`, and tell you where that folder is once
so it goes into `progress/LEARNER.md` and never has to be asked again.

---

## STEP 5 — Capture what was never captured

Recall almost always turns up something durable that nobody wrote down. Do not let it evaporate a
second time. Offer, in one line, and route it correctly:

| What surfaced | Where it goes |
|---|---|
| A real choice with alternatives, made and still standing | `progress/DECISIONS.md` |
| Something built that is not in the table | `progress/SKILLS-BUILT.md` |
| A fact about how the learner works, or a constraint they are under | `progress/LEARNER.md` |
| A session that has no line in the log at all | `progress/SESSION-LOG.md`, dated as best you can |

**Write it in the target file's own shape.** Each of those files defines its entry template in its
own header and states that the template is the only shape an entry takes there. Read that header
and use it rather than improvising: a session-log entry is the six-field block, a decision needs
its `RULED OUT` field, something built is a row in the Active skills table, and a fact about the
learner is a bullet in a living section. The field an improvised shape drops is always the one
that stops getting captured.

Backfilled entries are still **appended at the bottom**, never inserted back into the history.
They carry the date you believe the work happened rather than today's, and they say
`(backfilled <today's date> from recall — date approximate)` on the entry's title line, so the
out-of-order date reads as deliberate rather than as a mistake. A record that quietly pretends to
have been written at the time is a record you cannot trust later.

If the file cannot be written in this environment, say so and put the exact text in the chat for
them to paste.

---

## When you find nothing

Say it in one sentence and give them the next move. Do not pad, and do not offer a summary of what
the session "probably" covered.

```
Nothing in my written record matches that, and I cannot read past conversations in this setup.
Two options: paste the conversation if you still have it, or tell me what you remember and I will
help you rebuild the decision from scratch — which is often faster than finding it.
```

That second option is real advice, not a consolation. Re-deciding a small thing with a clear head
frequently costs less than a long hunt for what was decided before.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| You are about to describe a conversation you did not read | Stop. You are inventing. Go back to STEP 1 and state the tier. |
| The learner assumes you can see all their chats | Correct it kindly and immediately, once. It changes how they work with you from then on. |
| Three sessions look like plausible matches | Show all three as one line each and ask. Guessing wastes more time than asking. |
| The log line exists but is uselessly thin | Say so, and treat it as evidence that entries are being written too briefly. Point at the format in `progress/SESSION-LOG.md`. |
| They ask you to search "everything" | Ask for a window. An unbounded search on thin material produces confident noise. |

---

## Related

- [`progress/SESSION-LOG.md`](../../../progress/SESSION-LOG.md) — the record this skill reads, and why it exists
- [`protocols/SESSION-PROTOCOL.md`](../../../protocols/SESSION-PROTOCOL.md) — the capture step that fills it
- [`curriculum/06-memory-and-second-brain.md`](../../../curriculum/06-memory-and-second-brain.md) — why memory has to live outside the conversation
- [`.claude/skills/review-my-work/SKILL.md`](../review-my-work/SKILL.md) — the same tiers, used to review a stretch of work rather than find one session
