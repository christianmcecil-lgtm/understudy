# Session Protocol

*How every working session in this harness runs, start to finish. Written for the AI to follow literally; readable by you in about ten minutes.*

This file is addressed to the AI. You can read it too, and you should — because once you
know the five phases, you can tell in one glance whether the AI is running the protocol or
improvising.

All paths below are given from the root of the harness folder — the folder containing
`README.md`.

The five phases:

| Phase | One-line job | Skipped when people are in a hurry |
|---|---|---|
| START | Load almost nothing. Find out what the task is. | Rarely |
| ORIENT | Restate the goal. Name the done-check. | Often |
| DURING | Work, surface assumptions, notice repetition. | Sometimes |
| PAUSE | Stop before anything irreversible. | Dangerously often |
| CAPTURE | Write down what was learned. | Almost always |

CAPTURE is the phase everyone skips, and it is the only phase that makes tomorrow's session
better than today's. A session without capture is a session you will repeat.

---

## Phase 1 — START

**Read exactly two files before anything else:**

1. `CLAUDE.md` at the root of this harness — the operating rules.
2. `progress/LEARNER.md` — what the learner has already done, what confused them, what to
   offer next.

Read nothing else yet. Not the curriculum. Not the reference folder. Not the whole progress
folder. You do not know what the task is, so you cannot know what is relevant, and anything
you load "just in case" costs attention you will want later.

**If `progress/LEARNER.md` is missing, empty, or still the unfilled template** — no facts about
the learner, no ticked checkpoints, no real session log entries — say so plainly and carry on
here. You will create it at CAPTURE. An empty tracker does **not** by itself mean first contact:
every properly ignited first session has one. The test for first contact is what *this session*
was told to read, and it lives in the first-contact section of [`CLAUDE.md`](../CLAUDE.md).
Apply that test, and hand off only if it says to.

**Then ask what the task is, or take it from the learner's first message.**

**Then load exactly ONE more file** — the single curriculum, protocol, or reference file the
task needs. Use this routing table:

| If the task is about... | Load this one file |
|---|---|
| "What could I even use this for?" | [Orientation](../curriculum/00-orientation.md) |
| Why the AI behaves the way it does | [What the model actually is](../curriculum/01-what-the-model-actually-is.md) |
| Long chats going bad, handoffs, loading less | [The context window](../curriculum/02-the-context-window.md) |
| Setting up a repeating task or an agent that runs on its own | [The loop](../curriculum/03-the-loop.md) |
| Checking work, catching errors, "is this right?" | [Verification](../curriculum/04-verification.md) |
| Turning a repeated task into something reusable | [Skills](../curriculum/05-skills.md) |
| Notes, files, remembering across sessions | [Memory and second brain](../curriculum/06-memory-and-second-brain.md) |
| Connecting the AI to other apps and data | [Tools and MCP](../curriculum/07-tools-and-mcp.md) |
| Running several agents, parallel work | [Subagents and swarms](../curriculum/08-subagents-and-swarms.md) |
| Spend, speed, which model, how hard it should think | [Cost, models and effort](../curriculum/09-cost-models-and-effort.md) |
| Privacy, permissions, what to automate first | [Safety, privacy and trust](../curriculum/10-safety-privacy-and-trust.md) |
| "Where do I start at my new job?" | [First 90 days](../curriculum/11-first-90-days.md) |
| "Is this claim I read online true?" | [The hype ledger](../curriculum/12-the-hype-ledger.md) |
| "Am I actually good at this yet?" | [Graduation](../curriculum/13-graduation.md) |
| Which skill or agent to reach for, and how they chain | [The skill library](../curriculum/14-the-skill-library.md) |
| Undoing a change, or protecting files before a big one | [Git](../curriculum/15-git.md) |
| Opening a terminal, running something, stopping it | [The terminal](../curriculum/16-the-terminal.md) |
| Getting a second opinion from a different assistant | [Many models](../curriculum/17-many-models.md) |
| Building a done-check | [DONE-CHECKS.md](./DONE-CHECKS.md) |
| Running a check on finished work | [VERIFICATION-PROTOCOL.md](./VERIFICATION-PROTOCOL.md) |
| Something went wrong and you want to name it | [FAILURE-MODES.md](./FAILURE-MODES.md) |
| They are stuck and cannot say what kind of stuck | [SITUATIONS.md](./SITUATIONS.md) |
| Making a review of their own practice recur | [REVIEW-ROUTINE.md](./REVIEW-ROUTINE.md) |
| A word or piece of jargon they do not know | [GLOSSARY.md](../reference/GLOSSARY.md) |
| "How do I phrase this?" — the wording of a request | [PROMPT-PATTERNS.md](../reference/PROMPT-PATTERNS.md) |
| Where a claim in this harness came from, and how much to trust it | [SOURCES.md](../reference/SOURCES.md) |

If two rows both look right, pick the more specific one and say so. If none fit, say that
too and ask which direction to go rather than loading three files to cover your bases.

**Then say what you loaded, in one line, out loud.** Use this exact shape:

```
Loaded: CLAUDE.md, progress/LEARNER.md, curriculum/04-verification.md. Nothing else yet.
```

This line is not bookkeeping. It is teaching. The learner sees, every single session, that
a good answer came from three files and not thirty — and that is the habit the whole harness
is trying to install. Say it every time, even when it feels repetitive. Especially then.

**If the learner opens with a real question instead of a task**, answer it first, briefly,
then run START. Do not make someone sit through setup to get one answer.

---

## Phase 2 — ORIENT

Before doing any substantial work — before writing a document, changing files, running a
multi-step task, or starting anything that will take more than a couple of minutes — do
these two things and nothing else:

**1. Restate the goal in one sentence.**

Not a summary of what the learner said. A sentence that could be right or wrong, that they
can correct in five seconds. Write it as:

```
Goal, as I understand it: <one sentence>. Correct me if that is off.
```

Vague restatements are worse than none. "Help you with the report" is not a goal. "Produce a
two-page summary of the Q3 numbers for someone who has not seen them, in the format used
last quarter" is a goal.

**2. Name the done-check you intend to use.**

A done-check is the specific, observable thing that will be true when the work is finished.
Not "when it is good." Something you could hand to a stranger who would reach the same
verdict as you.

```
Done-check: <the observable condition>. I will show you <the evidence> when I claim it is met.
```

Examples of the difference:

| Not a done-check | A done-check |
|---|---|
| "Until the summary is good" | "Every number in the summary appears in the source file, and I can quote the line for each" |
| "Until the email reads well" | "Under 150 words, one ask, no jargon, and it survives being read aloud" |
| "Until the research is thorough" | "Five sources, each one opened and quoted, and at least one that disagrees with the others" |
| "Until the list is complete" | "Every item in the folder appears exactly once in the list, and the counts match" |

**If you cannot name a done-check, say so.** Out loud, in these words or close to them:

```
I cannot name an objective done-check for this yet. That usually means the goal is still
subjective. Can you tell me what you would look at to decide this was finished?
```

That is not a failure to be papered over. An un-checkable goal is the most common way a
session runs long and produces nothing usable — that is a principle drawn from practice, not
a measured result, but the mechanism is plain: nothing can end a task that has no end
condition. Surfacing it early costs one exchange. Discovering it late costs the session. See
[DONE-CHECKS.md](./DONE-CHECKS.md) for how to build one when the obvious check does not
exist.

**Skip ORIENT only for genuinely small things**: a definition, a quick lookup, a one-line
edit. If you are about to do more than about five minutes of work, ORIENT is not optional.

---

## Phase 3 — DURING

### Follow links as the task needs them, not before

You loaded one file at START. When that file points somewhere and you actually need what is
there, follow it and say so in one short line: `Following the link to DONE-CHECKS.md for the
subjective-goal case.` Load on demand. Never load a folder.

If you find yourself with more than about four files in play, stop and ask whether the task
has quietly become two tasks. It usually has. See
[The over-connected desk](./FAILURE-MODES.md#f-08--the-over-connected-desk) for what this
looks like from the outside.

### Surface assumptions as you make them

Every non-trivial task requires filling in something the learner did not specify. You will
fill it in either way — the question is whether they see it. Mark each one inline, in
brackets, at the moment you make it:

```
[Assuming: the audience is internal, so I am not defining the acronyms.]
[Assuming: last quarter's format, since you referenced it. Say if you want a different one.]
```

Do not batch assumptions into a list at the end. By then the work is built on them and the
learner has to unpick rather than redirect.

Tag anything you did not read directly. If a claim came from your general knowledge rather
than from a file or a source you opened this session, say so:

```
[From general knowledge, not checked against a source — worth verifying if it matters.]
```

### Notice repetition across sessions and offer to build a skill

At START you read `progress/LEARNER.md`. If the task in front of you resembles something in
there, read `progress/SKILLS-BUILT.md` before you say anything — a skill for it may already
exist, in which case sharpen that one rather than building a second. If none exists, say so
and offer:

```
This is the third time you have asked for something in this shape. That is the point where
a skill pays for itself. Want me to write one? It would take about ten minutes and every
future version of this task would start from it instead of from scratch.
```

The threshold is the third occurrence. Twice is a coincidence. Three times is a pattern, and
a pattern that is not codified is a tax you pay forever. On the first and second occurrence,
do not offer — log the sighting in the Candidates table in
[SKILLS-BUILT.md](../progress/SKILLS-BUILT.md) so the third one is obvious when it arrives.
Do not build the skill unprompted — offer it, and build it if they say yes. If they do say
yes, follow [Skills](../curriculum/05-skills.md) and record the result in
[SKILLS-BUILT.md](../progress/SKILLS-BUILT.md).

### Watch for staleness and offer a handoff instead of pushing on

You re-read the entire conversation every turn. As it grows, everything in it competes for
your attention, including things that were superseded an hour ago. You will not feel this
happening. That is exactly why it needs a checklist rather than a judgment call.

**Staleness signal checklist.** Run it whenever the session has been going a while, and
always after a long stretch of back-and-forth:

- [ ] You suggested something the learner already rejected in this session.
- [ ] You contradicted a constraint that was stated earlier in this session.
- [ ] You asked for a file you already read.
- [ ] You re-derived a decision that was already made and recorded.
- [ ] You referred to something "as mentioned earlier" that was never mentioned.
- [ ] Your summaries are getting vaguer, and your hedging is going up.
- [ ] Your edits or suggestions have drifted outside the area the learner named.
- [ ] The learner has re-explained the same goal more than twice.
- [ ] Every reply now opens with a long recap before it says anything new.

**The handoff trigger.** Offer a handoff when **any one** of these is true:

- Three or more boxes above are checked.
- Either of the first two conditions has happened twice in this session. (Re-suggesting a
  rejected idea, or contradicting a stated constraint, are the hard signals. They mean
  earlier context is no longer steering you.)
- The next phase of work needs a different set of files than the ones in play. A clean start
  is cheaper than carrying the old ones along.
- The learner says any version of "you seem to have forgotten."

Do not push on and hope. Say it plainly:

```
I am showing staleness signals: <name the specific ones>. Rather than push on, I recommend
a handoff — a fresh session with a short document holding only what matters. Want me to
write the handoff document now?
```

**What a handoff document contains** (write it into the chat so the learner can paste it
into a new session; the harness ships a skill that does this for you — invoke `/handoff`, or
read `.claude/skills/handoff/SKILL.md` and follow it if your tool has no slash commands):

1. The goal, in one sentence.
2. The done-check.
3. What is finished, each with the evidence that it is finished.
4. What is not finished, and what the next step is.
5. Constraints and decisions already made — especially anything already rejected, so the
   fresh session does not re-suggest it.
6. The exact list of files the next session should load. Short.
7. Open questions for the learner.

Nothing else. A handoff document that includes the whole conversation is not a handoff; it
is the same stale session in a new window. The reason a handoff works at all is that it is
small.

---

## Phase 4 — PAUSE before anything irreversible

Stop and wait for an explicit yes before doing any of these:

- Deleting anything, or overwriting a file that is not backed up.
- Sending anything to another person — email, message, calendar invite, comment, reply.
- Publishing or changing anything other people can see.
- Spending money, or agreeing to terms.
- Changing settings, permissions, or anything that persists after the session ends.
- Sharing data with a service or a person who did not already have it.
- Anything that will still be running after this conversation ends.

The pause has a required shape. Three lines, then stop:

```
About to: <the exact action, with the exact target>
Cannot be undone: <what specifically is unrecoverable>
Reversible alternative: <the draft / copy / dry-run version, if one exists>

Say go and I will do it.
```

Then actually stop. Do not do the thing and describe the pause afterwards. Do not treat
"sounds good" about the plan as approval of the action — approval is per-action, and it does
not carry forward to the next one.

If there is a reversible version, offer it first and default to it. Draft rather than send.
Copy rather than overwrite. Propose rather than apply. The reversible path costs one extra
exchange and removes an entire class of bad afternoons. More on where this line sits:
[Safety, privacy and trust](../curriculum/10-safety-privacy-and-trust.md).

---

## Phase 5 — CAPTURE (the end of every session)

**There is no automatic memory.** When this conversation closes, everything in it is gone.
Not compressed, not archived somewhere you can retrieve — gone. The next session starts from
the files on disk and nothing else.

This is the single most misunderstood thing about working with AI, and it is why most people
plateau. They have a hundred good sessions and no accumulated system, because each one
started from zero. Capture is an explicit act. If nobody writes it down, it did not happen.

The good news is that it takes about two minutes.

At the end of every session — or when the learner says they are done, or before a handoff —
do all four of these that apply. The first two always apply. Show the entries in the chat
before writing them, so the learner can correct anything you got wrong about their own
experience.

### 5a. Always: append to `progress/LEARNER.md`

Append one entry to the **Session log** at the bottom of that file, below the line that says
real entries start there. Never edit or overwrite an earlier log entry — this file is a
record, and a record you rewrite is not a record. The one exception is the five living
sections near the top (Who this learner is, Capability checkpoints, Working on now, Confused
by, What to offer next); those describe the present, so you edit them in place and note the
change in the entry. If that file lists a different set, it wins — count them there.

`progress/LEARNER.md` carries the authoritative template. It is this shape:

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

If the template in `progress/LEARNER.md` has been changed since, that file wins. Read it,
do not write from memory.

Write what is true, including when the session went badly. An entry saying "confused by all
of it, we should try a smaller example next time" is more useful than one that says the
session went well. This file is the only thing that makes the next session smarter than this
one, and a flattering record makes it dumber.

### 5b. Always: append to `progress/SESSION-LOG.md`

Two files, two jobs, and they are not substitutes. `progress/LEARNER.md` is about **the
person** — what they can do now, what confused them, what to teach next.
`progress/SESSION-LOG.md` is about **the work** — what was attempted and when, so a later
session can find it again and a review can see the shape across several weeks. Do not paste
the same paragraph into both.

Everything backward-looking in this harness reads this file. `/recall-session` searches it to
find a past piece of work; `/review-my-work` reads a run of entries to see what you repeat and
what you accept without checking. Both degrade to guessing when entries are missing. This is
the step that makes them work, and it is the one nobody treats as important until the week
they need it.

Append one entry at the bottom, newest last, never editing an earlier one.
[`progress/SESSION-LOG.md`](../progress/SESSION-LOG.md) carries the authoritative format. It is
this shape:

```
### YYYY-MM-DD — <title in about five words>

TRIED TO: <what the learner set out to do, in their terms>
GOT DONE: <what actually exists now that did not before. Be concrete. "Partly" is a real answer>
USED: <skills, tools, connectors, files touched — comma separated, no prose>
STUCK ON: <what fought back, confused, or took three attempts. NONE only if true>
UNVERIFIED: <anything accepted without a check, especially anything that went to another person>
NEXT: <the single most useful follow-up, or NONE>
```

Six fields, one line each, under a minute to write. **A heavyweight format is a format that
gets skipped**, and a skipped log silently disables everything that reads it. If a field is
running to a paragraph, the depth belongs in one of the other files and this line should point
at it instead.

`UNVERIFIED` is the field that earns this file its keep and the one you will be tempted to
leave blank. `NONE` is allowed only when nothing was accepted without a check, and on most
sessions that is not true. It is the only place in the harness where "I took its word for it"
gets written down at the moment it happens, rather than reconstructed later once it has already
cost something.

Write the entry even when the session was short, unfinished, or went badly. A log that only
holds good days cannot show a pattern, and patterns are the reason it is read.

### 5c. If a skill was built: add a row to `progress/SKILLS-BUILT.md`

Add one row to the **Active skills** table in that file. The row template lives there; it is
this shape:

```
| `skill-name` | What it does, in one or two sentences, concrete. | YYYY-MM-DD | 0 | (not yet sharpened) |
```

The columns are Skill, What it does, Built, Used, Sharpened. The Used count is observed, never
estimated — a new skill starts at 0. If a skill already in that table was used this session,
increment its count and, if its output needed fixing by hand, add a dated note to the
Sharpened column saying what changed.

A skill with no done-check is a prompt with extra steps. The "What it does" column is where the
done-check belongs: say what the skill enforces, not just what it produces. If it enforces
nothing checkable yet, write that plainly in the cell rather than leaving it implied.

### 5d. If a real decision was made: append to `progress/DECISIONS.md`

A real decision is one where a reasonable person could have chosen differently, and where
reversing it later would cost something. Choosing a file naming convention is a decision.
Choosing a word in a sentence is not.

Append to the **Decision log** at the bottom of that file, using its template:

```
### YYYY-MM-DD — <the decision in one line, stated as a decision>

DECISION: <what was decided, specifically enough to act on>
REASONING: <why — the actual reason, including any reason that is uncomfortable>
RULED OUT: <the alternatives considered, and the specific reason each lost.
  If none were considered, say so — that is itself worth knowing.>
DECIDED BY: <the learner / jointly / the AI proposed and the learner accepted>
REVISIT WHEN: <the condition that should reopen this, or "not planned">
REVISITED: <blank until it happens, then: date and what changed>
```

The `REVISIT WHEN` field is the one that earns its keep. Decisions made under one set of
conditions get quietly carried into conditions where they no longer make sense, and without
a written trigger nobody notices. `RULED OUT` is the second: a rejected option recorded with
its specific defect is what stops that option coming back in a new costume.

### 5e. Say what you wrote

One line, so the learner can see the system growing:

```
Captured: 1 entry in progress/LEARNER.md, 1 in progress/SESSION-LOG.md, 1 row in progress/SKILLS-BUILT.md. Nothing in DECISIONS.md this session.
```

### If you cannot write to the files

Some setups are read-only. If a write fails, say so plainly and put the exact text of each
entry in the chat so the learner can paste it in themselves. Never silently skip capture,
and never claim to have written something you did not write.

---

## The whole protocol, on one card

Print this, or tell the AI to echo it at the start of a session.

```
START    Read CLAUDE.md + progress/LEARNER.md. Find the task. Load ONE more file. Say what you loaded.
ORIENT   Restate the goal in one sentence. Name the done-check. No done-check, no start.
DURING   Follow links on demand. Bracket every assumption. Third repetition, offer a skill.
         Run the staleness checklist. Any hard signal, offer a handoff.
PAUSE    Before anything irreversible: what, what cannot be undone, the reversible option. Then stop.
CAPTURE  Append to progress/LEARNER.md AND progress/SESSION-LOG.md, every session, both.
         Skill built, add to SKILLS-BUILT.md. Real decision, DECISIONS.md.
         There is no automatic memory. Capture or it is gone.
```

## Try this now

Paste this at the start of your next session with the AI, before anything else:

```
Read CLAUDE.md and progress/LEARNER.md, and nothing else yet.

Then tell me three things:
1. What you loaded, and what you deliberately did not load.
2. Based on LEARNER.md, what you would offer me next and why.
3. One question you need answered before you could name a done-check for it.

Do not start any work until I answer question 3.
```

If it starts working anyway, stop it and point it back at this file. An AI that skips ORIENT
is an AI that is about to produce something you cannot check.

## What you should now be able to do

- Tell within thirty seconds whether a session is being run properly, by checking two things:
  did it say what it loaded, and did it name a done-check.
- Name the specific signals that mean a session has gone stale, instead of vaguely feeling
  that it "got worse," and ask for a handoff before the session wastes an hour.
- Recognise an irreversible step before it happens and insist on the three-line pause.
- End a session with a written record that makes the next one start further along — and
  explain to someone else why nothing is remembered unless it is written down.
