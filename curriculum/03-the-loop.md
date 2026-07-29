# The Loop

*What a loop actually is, when you need one, and a fill-in-the-blank card you can copy for any task. About 20 minutes to read, and you can build your first loop in five.*

---

## The one-sentence version

A loop is what replaces **you** as the person who keeps prompting.

Right now, if you use AI like most people, the pattern looks like this: you ask, it answers, you read the answer, you notice it is wrong or thin, you type "no, more like this," it tries again, you read again. You are the engine. Every iteration costs you a turn of attention. The work stops the moment you look away.

A loop moves that job into the system. You define the goal once, you define how "done" gets checked once, and the AI runs the ask-answer-check-retry cycle itself until the check passes or it hits the stop you set.

That is the whole idea. Everything else in this file is about doing it without setting money on fire.

---

## The shape

Every working loop, no matter how simple or how elaborate, has the same four beats and a stop:

```
  reason  ->  act  ->  observe  ->  done-check?
    ^                                   |
    |                             no    |    yes
    +-----------------------------------+     |
                                              v
                                     stop, report to human
```

- **Reason** — decide the next step toward the goal.
- **Act** — actually do it. Edit the file. Search the web. Rewrite the paragraph.
- **Observe** — look at the result. Not at the intention, at the result.
- **Done-check** — compare the result against a stated standard. If it passes, stop and report. If it fails, go back to reason with what you learned.
- **Stop** — the cap that ends the run even when the done-check never passes. It is not optional; there is a whole section on it below.

The minimum viable version is even shorter: **trigger, action, stop condition.** If your instruction to an AI does not contain all three, you do not have a loop. You have a request.

Here is the shape in plain English, on an invented but ordinary office task, so you can see it move. The numbers below are made up for the illustration:

> **Goal:** every row in this 412-row contact list has a valid email and a company name.
>
> **Pass 1 — reason:** fastest path is a scan for blanks and malformed addresses first.
> **Pass 1 — act:** flags 61 rows with problems.
> **Pass 1 — observe:** 38 are missing a company; 19 have a typo pattern like `.con` or a double `@`; 4 are blank.
> **Pass 1 — done-check:** 61 bad rows remain. Standard is zero. Fail. Continue.
>
> **Pass 2 — reason:** typos are mechanical, fix those first.
> **Pass 2 — act:** repairs the 19 typo rows.
> **Pass 2 — observe:** re-runs the same scan. 42 bad rows remain.
> **Pass 2 — done-check:** fail. Continue.
>
> **Pass 3 — reason:** company names can often be derived from the email domain.
> **Pass 3 — act:** fills 33 companies from domains, leaves 5 it cannot infer.
> **Pass 3 — observe:** re-scan. 9 bad rows remain: 4 blank emails, 5 uninferable companies.
> **Pass 3 — done-check:** fail, but the remaining ones need a human decision.
>
> **Stop:** reports "403 rows clean, 9 rows need you: here they are."

Notice what the human did. The human wrote one paragraph at the start and read one paragraph at the end. The human did not write "no, keep going" three times.

Notice also that the loop ended honestly. It did not fabricate five company names to make the check pass. That behavior is not automatic — it comes from the way the done-check and the stop are written, which is most of what this file teaches.

---

## The two pillars

Everything that makes a loop work or fail sits in two places.

### Pillar 1: an objective goal

Objective means a stranger could look at the result and agree on whether you hit it, without asking you what you meant.

| Weak goal (subjective) | Strong goal (objective) |
|---|---|
| "Clean up this contact list" | "Every row has a non-blank company and an email matching a standard address pattern" |
| "Make this email sound better" | "The email is under 150 words, states the ask in the first two sentences, and contains no unexplained internal jargon" |
| "Research our competitors" | "For each of these five named competitors, produce pricing, positioning line, and any public change in the last 30 days, each with a source link" |
| "Tidy the budget spreadsheet" | "One header row, no merged cells, every amount column numeric, no duplicate line items, totals recomputed and matching" |

You can still run a loop on a subjective goal. It will just run longer, drift further, and stop for reasons you cannot audit. Sometimes that is the only option and you accept it consciously. It should never happen by accident.

### Pillar 2: a way to check

Not "will it check" — **what specifically does it look at, with what tool, and what result counts as pass.**

| The work | What checking actually means |
|---|---|
| A spreadsheet | Re-run a count of bad rows. The number is the check. |
| A document | Read it against a written rubric, quoting the line that satisfies each criterion. |
| A web page or app | Open it, look at it, click the thing, screenshot the result. |
| A research summary | Open every cited source and confirm the claim is actually in it. |
| An email draft | A separate pass grades it against your stated criteria and returns a score plus the specific edits. |

The most common reason loops fail, in the experience this harness is built on, is that the AI was given tools to **act** and no tools to **verify**. It writes and writes and never looks. Giving it the ability to look is usually the whole fix. See [Verification](04-verification.md) for the full treatment — it is the chapter this one leans on hardest.

---

## The reality check, stated bluntly

Two things you should hear before you get excited:

**1. Most tasks do not need a loop. They need the verification half.**

The dramatic part of a loop is the automation. The useful part is the checking. If you take one habit from this entire harness, take this one: after the AI produces something, make it check its own output against a stated standard and show you the evidence — before you read the output at all. That single move is available in a plain chat window, needs no setup, and will do more for your daily work than most of the loops you build.

Build a loop when the task genuinely requires multiple passes to get right. Do not build one for a task that requires one pass and a check.

**2. A loop is only as good as its done-check.**

A loop with a vague done-check does not produce vague results. It produces long, expensive, confident-sounding results that nobody can grade. The loop cannot be better than the standard you gave it, and it will happily spend hours discovering that.

And one calibration point: loops do not get you to perfect. They get you much closer on the first pass than you would be otherwise, and they take the "read it, complain, resend" cycle off your desk. Treat that as the promise. Anyone selling more than that is selling.

---

## Closed loops and open loops

This is the single decision that most determines what a loop costs you.

| | **Closed loop** | **Open loop** |
|---|---|---|
| The instruction | "Get *this specific thing* to *this specific state*" | "Go find what needs doing, and do it" |
| You can see the path | Yes, roughly | No, that is the point |
| Cost | Bounded and predictable | Unbounded until the stop hits |
| Failure style | Stops short, tells you why | Wanders into work you did not want |
| Use it | Nearly always | Only when budget genuinely does not matter to you |

**Closed is the default and the recommendation for everyone**, including people who are very good at this. A closed loop has a bounded goal, a path you could sketch on a napkin, and a clear evaluation at each step, so cost stays sane and failures are legible.

Open loops are not useless. They find things you would not have thought to ask for — a stale process, a duplicate report nobody needed, a customer nobody followed up with. That discovery is real. But an open loop reasons its way into territory you did not scope, spends tokens exploring, and can hand you back a pile of work you now have to evaluate. Reach for one when the exploration itself is the deliverable and the spend is genuinely irrelevant to you.

A safe middle ground worth knowing: run the open loop in **read-only, propose-only** mode. "Go through this folder, find everything that looks stale or duplicated, and give me a ranked list with reasons. Change nothing." You get the discovery, you keep the decisions, and the blast radius is zero. More on blast radius in [Safety, privacy, and trust](10-safety-privacy-and-trust.md).

---

## The hard stop is non-negotiable

Every loop gets a cap. A maximum number of passes, a maximum wall-clock time, or both. No exceptions, including for loops you are confident about — especially those.

Write it explicitly, in the instruction, in words the AI cannot interpret away:

```
Hard stop: maximum 5 passes. If the done-check has not passed after
pass 5, stop immediately. Do not start a sixth pass. Report what is
still failing and what you would try next.
```

Two reasons this matters, and only one of them is money.

**The money reason.** A model re-reads the accumulating conversation on every turn. A loop that runs for hours is not paying a flat rate per hour; the passes get more expensive as the history grows. Cost is covered properly in [Cost, models, and effort](09-cost-models-and-effort.md), but the intuition you need here is: long loops get more expensive per pass as they go, not less.

**The honesty reason.** A loop without a cap has no way to tell you it is stuck. It will keep generating plausible next steps forever, because generating a plausible next step is exactly what these systems are good at. The cap is what converts "stuck" from an invisible state into a report on your desk.

### The failure story

The shape of the disaster is always the same. Someone gives an agent an open-ended instruction: *"Keep improving this until it is perfect."* Or "keep going until you are 100% confident." Or "build me a full replacement for this piece of software, and don't stop until it's done." No pass cap. No time cap. No definition of perfect, because perfect is not a definition, it is a mood.

The run goes for hours. It looks productive the whole time — there is always output scrolling by, always a next step, always a refinement. Then a human comes back and finds: a large volume of work, no single artifact that passes any stated standard, no way to tell which pass made things better and which made things worse, and a bill.

Nothing failed loudly. That is what makes it expensive. The loop did exactly what it was told: it improved things, forever, because "perfect" never evaluates to true.

Versions of this get reported often enough to be worth naming: an open-ended build loop that kept running until a person noticed and killed it by hand. No duration or figure is claimed here, because none is measured. Treat it as a mechanism you can reason about rather than a statistic: **a done-check that can never return "yes" produces a loop that can never stop.** If you cannot state a condition that would make the loop end, you do not have a loop yet. You have a way to spend money.

The fix is two lines long. State a checkable condition. Cap the passes. Both go in the instruction, every time.

---

## The three shapes

There are exactly three loop shapes you need. Learn them in order and use the simplest one that covers the job.

### Shape 1: the solo loop

One agent. It reasons, acts, observes, checks its own work against your standard, repeats until done or capped.

**Use it for:** most work. Genuinely. One good instruction in one window covers the large majority of what you will ever need.

**The catch:** the worker is grading its own homework. That is acceptable when the done-check is mechanical — a count, a format, a pattern, a total that has to match. It is not acceptable when the check requires taste or judgment, because the same reasoning that produced the work will approve the work.

**Worked example — cleaning a messy contact list:**

```
Goal: every row in the attached contact list has a non-blank company
and an email that matches a standard address pattern.

Work in passes. After each pass, re-run the count of failing rows and
tell me the number before you continue.

Done when: the failing-row count is 0, OR the only remaining failures
are ones that require information you do not have.

Never invent a company name or an email address. If you cannot derive
it from data already in the file, leave it blank and list that row for me.

Hard stop: 5 passes. Then report.
```

The done-check here is a number. The AI cannot argue with a number, which is exactly why this is a good solo-loop task.

### Shape 2: maker and checker

Two roles. One does the work. A **different** one grades it, against a rubric, and hands back specific corrections. The maker revises. The checker re-grades. Repeat until the grade passes or the cap hits.

The checker must be a separate pass with fresh eyes on the output — not the same conversation that just spent twenty minutes convincing itself the draft was good. In a chat, this can be as simple as a second, clean conversation. In a tool with subagents, it is a separate agent. The mechanics are in [Verification](04-verification.md); the principle is: **never let the worker grade its own work when judgment is involved.**

**Use it for:** anything where "good" is a judgment call. Writing. Prioritization. Anything a human will read and form an opinion about.

**Worked example — drafting and grading a client email:**

```
Role 1 (maker): Draft an email to a client explaining that their
delivery date moves from the 14th to the 21st. Facts you may use are
in the attached note. Do not invent a reason.

Role 2 (checker): You did not write this draft. Grade it against these
five criteria, one line each, quoting the exact text that satisfies or
fails each one:
  1. The date change appears in the first two sentences.
  2. A reason is given and it appears in the source note.
  3. There is one clear next step with an owner.
  4. Under 150 words.
  5. No blame, no hedging phrases like "unfortunately it seems."
Score each pass or fail. If anything fails, say exactly what to change.
Do not rewrite it yourself.

Loop: maker revises using the checker's notes, checker re-grades.
Done when: all five criteria pass.
Hard stop: 3 rounds. If it has not passed by then, show me the latest
draft and the failing criteria.
```

The checker not rewriting is deliberate. A checker that rewrites stops being a checker and becomes a second maker with an opinion, and now nobody is grading.

### Shape 3: orchestrator with helpers

One agent holds the goal and delegates parallel pieces to helpers, then pulls the results back together and checks them.

**Use it only when the work genuinely needs parallel specialists** — separate sources, separate skills, separate bodies of material that do not depend on each other. If the pieces are sequential, this shape adds coordination overhead and buys you nothing.

Be honest about the tax: every helper needs its own briefing, produces its own output, and the orchestrator has to reconcile results that may disagree. You are trading a bigger bill and more moving parts for wall-clock speed and coverage. Sometimes that trade is obviously right. Often it is not. Scaling a system you do not yet understand mostly scales its bugs. [Subagents and swarms](08-subagents-and-swarms.md) covers when this earns its keep.

**Worked example — a weekly competitor scan:**

```
Goal: a one-page brief covering what changed at these five competitors
in the last 7 days: [A, B, C, D, E].

Helpers: one per competitor. Each returns exactly this structure:
  - pricing change (yes/no + detail + source URL)
  - product or feature announcement (+ source URL)
  - notable public post or press item (+ source URL)
  - "nothing found" is a valid and expected answer
Each helper reads only public sources and never speculates about
motive or unannounced plans.

Orchestrator: merge into one page, sorted by how much it would change
our decisions this week. Mark every line as [confirmed] with its
source, or [inferred] with the reasoning that produced it.

Checker: open every source URL. Any claim not supported by its source
gets deleted, not softened. Report how many you deleted.

Hard stop: 1 pass per helper, 1 verification pass. Then report.
```

The `[confirmed]` versus `[inferred]` tagging is not decoration. When AI-produced material starts accumulating in your files, untagged inferences quietly become "facts" that later work builds on. Tag them at the point of creation. That habit is covered in [Memory and the second brain](06-memory-and-second-brain.md).

---

## The LOOP CARD

Copy this. Fill every line. If a line is blank, you are not ready to run.

```
LOOP CARD

GOAL
  (One sentence. Objective. A stranger could tell whether you hit it.)

DONE-CHECK
  (The exact condition that makes this stop. Prefer a number, a count,
   a pattern, or a rubric with pass/fail lines. If it is subjective,
   say so out loud here.)

TOOLS TO ACT
  (What it is allowed to touch or do: which file, which folder, which
   site, which app. Also what it must NOT touch.)

TOOLS TO VERIFY
  (How it will look at its own result: re-run the count, re-read
   against the rubric, open the source, take the screenshot. If this
   line is empty, the loop cannot work.)

HARD STOP
  (Max passes and/or max time. Non-negotiable. What to do when hit.)

WHERE MEMORY LIVES
  (The file or note it writes progress into after each pass, so a pass
   knows what earlier passes already did.)

WHO CHECKS
  (Same agent = fine for mechanical checks. Separate checker = required
   when the standard involves judgment. Name which one and why.)

REPORT
  (What lands on my desk at the end: the artifact, the pass log, and
   the list of things it could not do.)
```

A note on **where memory lives**, because it is the line people skip. A loop that keeps everything in the conversation forgets in a very specific way: as the conversation grows, early passes get squeezed out, and the loop starts redoing work it already did or contradicting decisions it already made. A one-page running note — "pass 3: fixed 19 typo rows, 42 remain, next is company backfill" — costs almost nothing and prevents the whole failure class. See [The context window](02-the-context-window.md) for why this happens and [Memory and the second brain](06-memory-and-second-brain.md) for where to put the note.

---

## Five worked loop cards for office work

None of these require code. Each one is copy-pasteable as an instruction.

### Card 1 — Cleaning a messy contact list

```
LOOP CARD: contact list cleanup

GOAL
  Every row in the attached contact list has a non-blank company and an
  email that matches a standard address pattern, with no duplicate people.

DONE-CHECK
  Failing-row count = 0, where a row fails if: email is blank or
  malformed, company is blank, or the same person appears twice.
  Report the count after every pass.

TOOLS TO ACT
  The contact list file only. Work on a copy; leave the original
  untouched. Do not contact anyone. Do not look anyone up online.

TOOLS TO VERIFY
  Re-run the same three checks (email pattern, blank company,
  duplicate name+email) and report the raw counts, not a summary.

HARD STOP
  5 passes. If the count is not 0, stop and hand me the remaining rows.

WHERE MEMORY LIVES
  A running note: pass number, what was changed, count before, count
  after. Append, never overwrite.

WHO CHECKS
  Same agent. The check is a count, so self-grading is acceptable here.

REPORT
  The cleaned file, the pass log, and a list of rows that need a human
  decision with the reason each one needs it.

RULE
  Never invent a company, an email, or a name. Blank is a correct
  answer. A fabricated value is a wrong answer that looks like a right one.
```

### Card 2 — Drafting and grading a client email

```
LOOP CARD: client email, maker-checker

GOAL
  A sendable email telling the client the delivery date moves from the
  14th to the 21st, using only facts in the attached note.

DONE-CHECK
  All five rubric criteria pass:
  1. Date change stated in the first two sentences.
  2. Reason given, and it appears verbatim in the source note.
  3. Exactly one next step, with a named owner and a date.
  4. Under 150 words.
  5. No blame, no vague hedging ("it seems", "there may have been").

TOOLS TO ACT
  Write the draft. Do not send it. Do not open my mail client.

TOOLS TO VERIFY
  A separate grading pass that quotes the exact sentence satisfying or
  failing each criterion, marks pass/fail, and lists required changes.
  The grader does not rewrite.

HARD STOP
  3 maker-checker rounds. Then show me the best draft plus what still fails.

WHERE MEMORY LIVES
  Keep every draft version numbered, so I can see what changed and ask
  for an earlier one back.

WHO CHECKS
  Separate checker. The standard is judgment-based, so the writer
  cannot be trusted to grade it.

REPORT
  Final draft, rubric scorecard, and the diff between round 1 and final.
```

### Card 3 — Weekly competitor scan

```
LOOP CARD: weekly competitor scan

GOAL
  A one-page brief on what changed at [competitor A, B, C, D, E] in the
  last 7 days, ranked by how much it would change our decisions this week.

DONE-CHECK
  Every competitor has all four slots filled (pricing / product /
  public post / nothing-found), AND every factual line carries a working
  source URL, AND every line is tagged [confirmed] or [inferred].

TOOLS TO ACT
  Public web only. No paid databases, no logged-in accounts, no
  contacting anyone. If a source is behind a login, mark it unavailable.

TOOLS TO VERIFY
  Open each cited URL and confirm the claim appears there. Any claim
  the source does not support is deleted, not reworded. Report the
  number deleted.

HARD STOP
  One research pass per competitor plus one verification pass. No
  re-research. Total time cap: 45 minutes.

WHERE MEMORY LIVES
  A dated file per week in the same folder, so next week's run can
  diff against last week's and say what is genuinely new.

WHO CHECKS
  Separate verification pass, because the researcher will believe its
  own sources.

REPORT
  The one-pager, the deletion count, and an explicit "nothing found for
  X" line where that is the truth. Silence is not the same as nothing
  happening, and I want to know which one I am looking at.
```

That last line matters more than it looks. A scan that returns nothing because there was nothing, and a scan that returns nothing because it could not reach the sources, look identical on the page and mean opposite things.

### Card 4 — Meeting notes into tracked commitments

```
LOOP CARD: notes to commitments

GOAL
  Turn the attached meeting notes into a list of commitments, where a
  commitment = who / what / by when, plus the exact quote it came from.

DONE-CHECK
  Every item has all four fields filled, AND every quote appears
  word-for-word in the source notes, AND the "unclear" bucket is
  explicitly listed rather than silently dropped.

TOOLS TO ACT
  The notes file only. Do not email anyone. Do not create calendar
  entries. Do not assign anything to anyone outside the meeting.

TOOLS TO VERIFY
  For each commitment, search the source notes for its quote and
  confirm an exact match. Any item whose quote cannot be found exactly
  moves to the "unclear" bucket. Report how many moved.

HARD STOP
  2 passes. Then report.

WHERE MEMORY LIVES
  Append to a running commitments file, so next week's meeting can be
  checked against what was promised last week.

WHO CHECKS
  Same agent is fine: the check is exact-text matching, which is
  mechanical.

REPORT
  Three lists: clear commitments, unclear items needing a human, and
  anything that sounded like a commitment but had no owner or no date.

RULE
  A missing owner is a finding, not a problem to solve by guessing.
  Never assign an owner who did not say the words.
```

### Card 5 — Tidying a spreadsheet

```
LOOP CARD: spreadsheet tidy

GOAL
  The attached spreadsheet is machine-readable: one header row, no
  merged cells, no blank spacer rows, every amount column numeric, no
  duplicate line items, totals recomputed and matching the detail rows.

DONE-CHECK
  All six conditions true, each reported as its own pass/fail line with
  the count that proves it. "Totals match" means the recomputed total
  equals the stated total to the cent.

TOOLS TO ACT
  Work on a copy. Never overwrite the original. Do not change any
  underlying amount. Formatting and structure only.

TOOLS TO VERIFY
  Re-check all six conditions from scratch after each pass and print
  the six-line result table. Recompute totals from the detail rows
  rather than trusting the total cell.

HARD STOP
  4 passes. Then report which conditions still fail and why.

WHERE MEMORY LIVES
  A change log listing every structural edit made, so I can reverse
  any single one.

WHO CHECKS
  Same agent for the six mechanical conditions. If a number does not
  reconcile, stop and escalate to me rather than adjusting anything.

REPORT
  The tidied copy, the six-line check table, the change log, and any
  cell where the stated value and the computed value disagree.
```

The escalation rule in the last card is the one worth stealing for everything else. A loop should never resolve a discrepancy in the underlying data on its own initiative. It surfaces it. You decide.

---

## How loops go wrong

Short list, worth re-reading before you launch anything unattended. The longer version lives in [Failure modes](../protocols/FAILURE-MODES.md).

| Failure | What it looks like | The fix |
|---|---|---|
| No stop condition | Runs for hours, always "improving" | A checkable done-check plus a pass cap |
| Done-check that grades itself | Everything passes on pass 1 | Separate checker for anything judgment-based |
| Tools to act, none to verify | Confident output, never inspected | Name the verify tool explicitly on the card |
| Goal drifts | Ends up solving a different problem | Restate the goal at the top of every pass |
| No memory between passes | Redoes work, contradicts earlier decisions | A running note it appends to each pass |
| Gaps filled with invention | Plausible values that are not real | "Blank is a correct answer" as a written rule |
| Scope creep on write access | It changed something you did not expect | Say what it may touch, and what it may not |

---

## Try this now

Pick something you did more than once last week. Then paste this, filling the two bracketed spots:

```
I want to build a loop for this task: [describe the task in one or two
plain sentences]. My rough goal is [what a good result looks like to me].

Do not start the work yet. First, interview me until you can fill in
every line of this card, and tell me plainly which lines I am being
vague about:

GOAL (objective, a stranger could grade it)
DONE-CHECK (the exact condition that makes this stop)
TOOLS TO ACT (what you may touch, and what you may not)
TOOLS TO VERIFY (how you will look at your own result)
HARD STOP (max passes, max time, what to do when hit)
WHERE MEMORY LIVES (the note you append to after each pass)
WHO CHECKS (you, or a separate checker, and why)
REPORT (what lands on my desk)

Then tell me honestly: does this task actually need a loop, or does it
just need one good pass plus verification? If it is the second one, say
so and do not build me a loop.
```

That last paragraph is doing real work. An AI asked to build a loop will build you a loop. Asking it to argue against itself first is how you avoid over-engineering a task that needed one careful pass.

---

## What you should now be able to do

- Describe any task as reason, act, observe, done-check, and stop — and notice immediately which of those five parts your instruction is missing.
- Write a done-check that is objective enough to be graded by someone other than you, and say out loud when you are settling for a subjective one.
- Choose deliberately between a solo loop, a maker-checker pair, and an orchestrator with helpers, instead of reaching for the most elaborate one.
- Fill in a LOOP CARD for real work you do, with a hard stop you will actually enforce, and recognize the tasks that need [Verification](04-verification.md) rather than a loop at all.
