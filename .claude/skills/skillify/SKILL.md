---
name: skillify
description: Turn something that just got done by hand into a reusable skill file, then test it and log it. Use when the learner says "make this a skill", "save this", "save what we just did", "turn what we just did into something reusable", "I do this every week", "I don't want to explain this again", "codify this", or when a task has now been done the same way more than once.
---

# /skillify — turn what just happened into something reusable

*Extracts the repeatable core of a piece of work, writes it as a skill, tests it once, and logs
it. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.
The concept behind this is taught in [05 Skills](../../../curriculum/05-skills.md).

---

## What you are making

A skill has three layers, and the third is the one people skip:

1. **Description** — one or two sentences in the frontmatter. This is checked against every
   request to decide whether to use the skill. Vague description, skill never fires.
2. **Instructions** — the numbered procedure to follow once the skill fires.
3. **Tools** — the checklists, templates, reference files, and scripts saved in the same folder.
   This is where the leverage is. A beautiful procedure with no tools is a prompt with extra steps.

---

## Step 1 — Establish what "just happened"

First read `progress/SKILLS-BUILT.md`. Two things live there that decide whether you should be
building at all: if a skill already covers this need, sharpen that one instead of adding a second
(two overlapping skills is worse than one blunt one, because neither gets improved), and the rule
of three says a task earns a skill on its third real occurrence. Earlier occurrences go in that
file's Candidates table with a note on what varied between them, and you stop there.

If the work happened in this session, say back the shape of it in three sentences and ask them to
correct you. If it did not, ask for one concrete run:

```
Walk me through the last time you did this, start to finish. What you started with,
what you did in order, what you handed over at the end. Concrete, not the tidy version.
```

Do not proceed on a description of the *category* of work ("reporting"). You need one real run.

---

## Step 2 — Separate the repeatable core from the one-off specifics

Out loud, build this table and show it to them. Getting this wrong is the main way skills come out
useless — either baked so hard to one example that they never fire again, or so generic they say
nothing.

| Element of what we did | Repeatable | One-off | Becomes |
|---|---|---|---|
| Pulling last month's numbers | yes | | Step 1, with the source as an input |
| The specific March figures | | yes | Nothing — the skill takes them as input |
| Checking totals against the source before writing | yes | | The done-check |
| Their preferred section order | yes | | A template file in the skill folder |

Rules for the split:
- Anything you had to be *told* during the run is an input or a reference file, not a hardcoded fact.
- Anything you got wrong during the run and were corrected on becomes an explicit instruction. That
  correction is the most valuable thing in the session.
- Anything a rule, a search, or plain code can do deterministically should be a script in the tools
  layer, not a paragraph asking the model to do it by hand. Same input, same output, no drift.

Ask them one question before drafting: **"What would you actually type when you want this?"** Their
literal phrasing goes into the description. Not your phrasing of it.

---

## Step 3 — Name it

Lowercase, hyphenated, verb-led where it reads naturally: `draft-client-update`,
`reconcile-invoices`, `prep-monday-standup`. Short enough to type.

Prefer several small skills that call each other over one large one. Small skills are easier to fix,
and an improvement to one lands everywhere it is used.

---

## Step 4 — Draft the three layers

Write to `.claude/skills/<name>/SKILL.md` using this structure. Then tell them how it actually gets
used in their setup, because a skill they cannot call is a file they will forget: in a tool that
reads a `.claude/skills/` folder, they invoke it by name; anywhere else, they open the `SKILL.md`
and paste it, or tell you to follow it. Same result, different plumbing. If their tool does neither,
say so now rather than after they have built three of them.

```markdown
---
name: <name>
description: <What it does in one clause. Then: "Use when the user says" plus three to
  six phrasings they would actually type, including the one they gave you in Step 2.>
---

# /<name> — <one-line purpose>

*<Italic subtitle: what this produces and roughly how long it takes.>*

## Inputs
- <What the skill needs before it can start. Ask for anything missing; do not guess.>

## Procedure
1. <Numbered, literal steps. Each one an action, not a topic.>
2. <...>

## Done-check
- <Objective conditions. What must be true for the output to count as finished.>
- <How it is checked, and by what evidence.>

## Stop
- <When to stop and hand back rather than keep trying. A cap on attempts, or a
  condition that means "this needs a human".>

## Files in this folder
- `<template-or-checklist.md>` — <what it is for>
```

Description-writing rules, because this is the part that decides whether the skill ever runs:
- Lead with what it does, then list trigger phrasings.
- Use their words, including the sloppy ones. If they say "do the Monday thing", that phrase goes in.
- Do not describe the mechanism, describe the request.
- Keep it to a couple of sentences. A description that tries to be the instructions gets ignored.

Then write the tools layer as real files in the same folder — a checklist, an output template, a
reference sheet of the rules the work has to satisfy, a script if code can do part of it. Reference
them by filename from the procedure. If you finish a skill with no files beside `SKILL.md`, say so
out loud and ask whether one of the steps should have become a template or a script.

---

## Step 5 — Test it immediately, on a fresh example

A skill that has never been run is a draft. Before you log it:

1. Ask for a different real example than the one it was built from.
2. Start clean — and you cannot honestly do that from inside the conversation that wrote the file,
   because you already know what it meant to say. Get a reader who does not, in this order:
   spawn a separate worker and give it only the `SKILL.md` and the new example (the role is
   described in `.claude/agents/verifier.md`); if your tool cannot spawn workers, ask the learner
   to open a fresh chat and paste in exactly those two things — no history, none of your reasoning
   — and bring the result back. Only if neither is possible, run it yourself, and say plainly in
   the conversation that the test was not independent and what that means for how much it proved.
   Whoever runs it follows the file literally, including the parts that feel obvious.
3. Note every place you had to improvise, guess, or ask a question the file should have covered.
4. Fix those in the file. Ambiguity you patched from memory is a bug the next run will hit.
5. Check the description would have fired: would you have picked this skill from the description
   alone, given the way they phrased the request? If not, rewrite the description, not the body.

Tell them honestly how the test went, including what broke.

---

## Step 6 — Log it

Append a row to the **Active skills** table in `progress/SKILLS-BUILT.md`, using that file's own row
template. Create the file with a `# Skills Built` heading if it does not exist. The row is:

```
| `skill-name` | What it does, in one or two sentences, concrete. | YYYY-MM-DD | 0 | (not yet sharpened) |
```

The usage count starts at 0 and is only ever incremented when you actually watch it get used. Never
estimate it — a guessed number there ruins the one signal that file exists to give.

The table has no column for three things that still matter, so say them in the conversation and put
the load-bearing ones into the `SKILL.md` itself: what the Step 5 test broke, what the skill does
not handle yet (that belongs in its `Stop` section), and the phrasings it fires on (that belongs in
its description). If the task was on the Candidates list, remove it from there when you promote it.

Also add a line to `progress/DECISIONS.md` if building it settled a question worth not reopening
(a naming convention, a source of truth, a format). Create that file with a `# Decisions` heading if
it does not exist.

---

## The sharpening rule

This is a standing rule, not a step in this skill. Apply it at the end of every later run of *any*
skill, including this one:

> Ask: was what just happened a one-time fix, or something this skill should handle forever?

If forever, open the skill file and update it before the session ends. The fastest wording to use:

```
Review the back-and-forth we just had and update the skill so this is handled
automatically next time and never comes up again. Show me the diff before you save.
```

When the change lands, add a dated note to that skill's Sharpened column in
`progress/SKILLS-BUILT.md`. That column is append-only: the history of how a skill got better is
what teaches the learner what sharpening actually is.

A skill that never changes after the day it was written is not compounding. One that absorbs a
correction each run gets meaningfully better over a month — that is the mechanism, and it only
works if the update happens while the correction is fresh.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| They ask to skillify something done once or twice | Say plainly it is early. Log it in the Candidates table in `progress/SKILLS-BUILT.md` now, with what varied between the runs, and build on the third — that is the point at which you can see which parts were incidental. |
| The procedure has no objective done-check | Do not ship it. Go back and ask what makes the output right or wrong. Without that, see [Done-checks](../../../protocols/DONE-CHECKS.md) for shapes that work. |
| The skill is turning into ten steps of judgment | Split it. Two skills that call each other beat one that nobody can debug. |
| The output involves anything sensitive | Check [10 Safety, privacy, and trust](../../../curriculum/10-safety-privacy-and-trust.md) before writing real data into the skill folder. Skills hold procedure, not payload. |
| The test run passes suspiciously easily | You reused context from the first run. Start over with a genuinely fresh example, or hand it to [/verify-this](../verify-this/SKILL.md). |
