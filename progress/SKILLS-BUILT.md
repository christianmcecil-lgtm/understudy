# Skills Built

*Every skill built for this learner, what it does, how often it actually gets used, and how it has been sharpened. The AI reads this before proposing a new skill and updates it after every use. Reading time: about 5 minutes.*

---

## For the AI: what this file is for, and the habit it enforces

A skill is a written instruction saved somewhere the AI reads, so a piece of repeated work is done the same good way every time instead of being retyped from memory. A prompt dies with the chat. A skill compounds. That is the whole reason this file exists.

But a skill only compounds **if it gets sharpened.** A skill written once and never touched again is a snapshot of what you knew the day you wrote it, and every time it produces a slightly disappointing result and someone silently works around it, the skill gets a little less true. The workaround is the signal. Fold it back in.

So there are two habits, and both live here:

**Habit one — before you build anything new, read this file.** If a skill here already covers the need, sharpen it instead of building a second one. Two skills that overlap is worse than one blunt skill, because now nobody knows which to use and neither gets improved.

**Habit two — after any skill is used, update its row.** Increment the usage count. If the output needed manual fixing, that fix belongs in the skill, not in the learner's head. Write what changed in the Sharpened column, with the date.

Rules for this file:

1. **Usage counts are observed, not estimated.** Increment when you see it used. If you do not know, write `unknown` — never a guess. A made-up number here corrupts the one signal this file exists to give.
2. **A skill with zero uses after a month is a candidate for deletion, not for improvement.** Say so plainly. Most people's real problem is too many unused skills, not too few skills.
3. **The Sharpened column is append-only.** Newest note last, each dated. Do not overwrite the history of how a skill got better — that history is what teaches the learner what "sharpening" means.
4. **Retire, do not delete.** Move dead skills to the Retired section at the bottom with a reason. A skill that failed teaches something.
5. **Never claim a skill saves a specific amount of time** unless the learner timed it and told you. Describe what it does. Do not invent a figure.
6. **Every skill is one row in the Active skills table, in the shape of the row template below.** If another part of the harness hands you a skill written up as a block of bullets, convert it into a row before you write it here. A block has no `Used` cell to increment and no `Sharpened` cell to append to, so a skill logged that way silently drops out of the two habits this file exists to enforce.

Related: capability checkpoints live in [`LEARNER.md`](LEARNER.md); the reasoning behind why a skill exists in its current shape often lives in [`DECISIONS.md`](DECISIONS.md). The full method for turning a repeated task into a skill is in [Skills](../curriculum/05-skills.md), and the harness ships a skill that does the conversion for you at [`../.claude/skills/skillify/SKILL.md`](../.claude/skills/skillify/SKILL.md).

---

## The rule of three

Do not build a skill the first time a task appears. Do not build one the second time.

On the **third** time, build it — you now know which parts are stable and which parts change per run, and that distinction is the entire difference between a useful skill and a rigid one that gets abandoned.

Log the first two occurrences in the Candidates section below so the third one is obvious when it arrives, instead of being retyped from scratch and forgotten again.

---

## Active skills

| Skill | What it does | Built | Used | Sharpened |
|---|---|---|---|---|
| `weekly-roundup` *(EXAMPLE — fictional, delete once real rows exist)* | Takes the four weekly sources and produces the Friday status roundup. Enforces: every section names its source, no section is silently empty, anything unavailable this week is listed as unavailable rather than dropped. | 2026-03-11 | 6 | **2026-03-18:** added "list unavailable sources explicitly" after a run produced a smooth three-source summary that read as complete. **2026-04-02:** added a fixed section order, because the order kept changing week to week and made the roundup hard to skim. **2026-04-29:** removed the "add a short executive summary" step — the learner rewrote it by hand every single time, which meant the skill was doing work that had to be undone. |

*Row template — copy this line:*

```
| `skill-name` | What it does, in one or two sentences, concrete. | YYYY-MM-DD | 0 | (not yet sharpened) |
```

---

## Candidates: tasks seen once or twice

*The waiting room for the rule of three. When a line reaches three, build it and move it up.*

| Task | Seen | Dates | What varies between runs |
|---|---|---|---|
| `<the repeated task>` | 1 | `<date>` | `<what changes each time — this becomes the skill's input>` |

The last column is the one that matters. A task where nothing varies should probably not be a skill at all — it should be a saved document or a template. A task where everything varies is not yet a task; it is a category, and it needs splitting.

---

## Sharpening prompts

Two things to run, and when.

**After any use where the output needed manual fixing** — the highest-value moment, and the one most often skipped:

```
I just used the [skill name] skill and had to fix the output by hand.

Here is what I changed after it ran: [paste or describe the fix]

Update the skill so that fix is not needed next time. Then show me a diff of
what you changed in the skill file and why. Do not change anything unrelated.
Then add a dated line to the Sharpened column in progress/SKILLS-BUILT.md.
```

**Periodically, when the list has grown** — a pruning pass, not an improvement pass:

```
Read progress/SKILLS-BUILT.md.

For each skill, tell me:
1. Its usage count, and whether that count is observed or unknown.
2. Whether any two skills overlap enough that they should be merged.
3. Which skills have never been sharpened, and what specifically in each one
   you would sharpen based on how it is written.
4. Which skills should be retired. Recommend retirement for anything unused —
   do not soften it. An unused skill is clutter I am paying attention for.

Do not build anything. Do not edit any skill. Report only.
```

Note that the second prompt is read-only on purpose. Pruning decisions belong to the learner.

---

## Retired skills

*Moved here, not deleted. The reason a skill died is often more instructive than the skill was.*

| Skill | What it did | Retired | Why |
|---|---|---|---|
| `<name>` | `<what it did>` | `<date>` | `<never used / superseded by X / the underlying task went away / it was doing work that always got undone>` |
