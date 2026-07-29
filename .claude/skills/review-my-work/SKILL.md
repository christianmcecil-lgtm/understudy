---
name: review-my-work
description: Run a coaching review of how the learner has actually been working, across a window of past sessions - what they repeated without codifying, what they accepted without checking, what they did the hard way, what they never tried, and what they are quietly forgetting. Use when they say "review my work", "how am I doing", "what should I get better at", "review this week", "am I improving", "what am I missing", "what should I focus on next", or when a scheduled review comes due. It reads the record rather than guessing, states plainly which source it read, and ends with one change to make today.
---

# /review-my-work — the coaching review

*A structured look back across several sessions, run through five fixed lenses, ending in one
thing to change. Twenty minutes of the learner's time. Read time for the AI: 6 minutes.*

All paths below are given from the root of the harness folder — the folder containing
`README.md`.

---

## What this skill is for

A single session cannot see a pattern. You can only see repetition, avoidance, and decay by
looking across several sessions at once — which is exactly the thing neither you nor the learner
can do from inside one conversation.

So this skill does two things that are easy to get wrong, and the rest of this file is about
getting them right:

1. **It is honest about what it can actually see.** You very likely cannot read the learner's
   other conversations. Step 1 exists because a review built on one-line summaries is a
   materially different artifact from one built on full transcripts, and the learner is entitled
   to know which one they are holding.
2. **It finds instances, not impressions.** "You should verify more" is worthless. "On the 4th
   and again on the 11th you sent a summary containing figures nobody checked" is a review.

---

## STEP 1 — Establish the tier, and say which one you are on

**An AI generally cannot read your other conversations.** Each session is its own thing. Work
down these four tiers in order, stop at the first that yields material for the window, and state
the result in the output. Do not skip to a lower tier because it is easier, and do not claim a
higher one than you used.

This step and step 2 interleave slightly, because you need a rough window before you can tell
whether a source covers it. Use the two-week default while establishing the tier, fix the exact
window in step 2, then check once that your source still covers it. If it does not, drop a tier
and say so.

| Tier | Source | How to establish it |
|---|---|---|
| 1 | Native session access | Check what tools you actually have. Look for anything that lists, reads, or searches previous conversations or transcripts. Do not assume a tool of that kind exists and do not guess its name — look, then say what you found. |
| 2 | Exported transcripts on disk | Ask once: "do you have a folder of exported conversations?" If yes, read the files whose dates fall in the window. |
| 3 | The harness session log | Read `progress/SESSION-LOG.md`. If it has entries covering the window, use them. **This is the tier the harness is designed around** — it is written at capture time in every session, so it works everywhere and needs no special tooling. |
| 4 | The learner pastes it | Ask them to paste the conversations, or the parts they remember mattering. Always available, works in any tool, costs them about thirty seconds per session. |

**Mixed tiers are normal and must be reported as mixed.** If four sessions came from the session
log and one was pasted, say so. Never let the strongest source label the whole review.

**If nobody is present** — a scheduled or unattended run — you cannot ask anything, so tiers 2 and
4 are unavailable to you and every later step that says "ask" becomes a line under WHAT I COULD NOT
ASSESS. Use tier 1 if it exists, otherwise tier 3. Take the window from the last dated entry in
`progress/REVIEWS.md` forward to the run date rather than asking for today's date. Add
`Unattended run` to the banner line and name the questions that went unasked. The separate
restriction on what an unattended run may write is in step 6.

### The banner — first line of the output, every time

Open the review with the matching block. Fill in the counts and dates. Do not soften it.

```
Review source: TIER 1 — direct access to <what you found>, <n> sessions, <date> to <date>.
I read the conversations themselves.
```

```
Review source: TIER 2 — exported transcripts in <folder>, <n> files, <date> to <date>.
I read the conversations themselves, minus anything never exported.
```

```
Review source: TIER 3 — the harness session log (progress/SESSION-LOG.md), <n> entries,
<date> to <date>. I am reading short summaries written at the end of each session, not the
conversations. Anything nobody wrote down is invisible to me here, and that includes most of
what went wrong quietly.
```

```
Review source: TIER 4 — what you pasted, covering <what>. I can only see the sessions you
gave me. Whatever you did not paste is not in this review, and the gap is not random: people
paste the sessions they remember, which are rarely the ones with the problems.
```

If the window has no material at any tier, do not produce a review. Say that, say why, and offer
the fix: start appending to `progress/SESSION-LOG.md` at the end of every session per
[SESSION-PROTOCOL.md](../../../protocols/SESSION-PROTOCOL.md), and run this again in two weeks. A
review of nothing is worse than no review, because it looks like a review.

---

## STEP 2 — Gather the window

**The window.** Default to *since the last review*. Find that date in
[`progress/REVIEWS.md`](../../../progress/REVIEWS.md) — read that file's header for where its
most recent entry lives, rather than assuming top or bottom. If there is no previous review, use
the last two weeks. If the learner names a window, use theirs.

State the window in the banner as real dates. If you do not know today's date, ask for it rather
than guessing — a wrong window silently reviews the wrong sessions.

**Read the arc in `REVIEWS.md` before you write anything, not after.** That file requires it, and
both of these checks change the review you are about to produce:

- **The `TOP ITEM` line of the last three entries.** If it is the same item three times, in any
  phrasing, it is being avoided rather than forgotten. Do not write it a fourth time as it stands.
  Replace it with its smallest concrete first move, or with the prerequisite it turns out to depend
  on, or say plainly that it is not actually important, drop it, and promote item 2. Say which of
  the three you did and why.
- **The `ACTED ON` line of the last two entries.** Two consecutive blanks means the reviews are not
  landing, and that triggers the one permitted opening block in step 4.

**Read these five files regardless of tier.** They are the harness's own record and they are
always available:

- [`progress/SESSION-LOG.md`](../../../progress/SESSION-LOG.md) — what happened, session by session.
- [`progress/LEARNER.md`](../../../progress/LEARNER.md) — who they are, what confuses them, what they are working on now.
- [`progress/MASTERY.md`](../../../progress/MASTERY.md) — every topic's rung, evidence, and last-recalled date.
- [`progress/SKILLS-BUILT.md`](../../../progress/SKILLS-BUILT.md) — what exists already, its usage count, and the Candidates table.
- [`progress/DECISIONS.md`](../../../progress/DECISIONS.md) — what has already been ruled out, and why.

That last file is load-bearing for this skill specifically. **Never recommend something that
`DECISIONS.md` records as rejected** without opening with the fact that it was rejected and
naming what has changed since. A review that re-proposes a decided question reads as a review
that did not read anything.

---

## STEP 3 — Run the five lenses

Five fixed lenses. They are fixed because a review that picks its own angles finds whatever the
reviewer was already thinking about.

**If you can dispatch subagents:** dispatch [`.claude/agents/reviewer.md`](../../agents/reviewer.md)
once per lens, in parallel, five instances. Each dispatch must contain: the lens name, the full
lens definition below pasted verbatim, the window dates, the tier, and **the material itself or
the exact file paths to read**. A subagent cannot see this conversation. If the material is tier
1 or tier 4 — something you read through a tool or the learner pasted into the chat — paste it
into the dispatch, or the worker will report on nothing and say so.

**If you cannot dispatch subagents:** run the lenses yourself, one at a time, in order, writing
each lens's findings out before starting the next. Do not hold five open at once; that is how
five lenses collapse into one general impression.

For every lens, the same evidence standard applies:

> A finding cites at least one specific instance: the date, the session or task, and what
> actually happened. A finding you cannot cite is not a finding — it is a hunch, and it goes in
> "could not assess" or nowhere.

### Lens 1 — Repetition

**The question:** what did they do more than twice in this window that is not a skill yet?

**What counts as an instance:** the same *shape* of task, done manually, on separate occasions —
the same weekly document, the same kind of extraction, the same request retyped from memory.
Same shape, not same subject: three different clients, one onboarding note each, is one repeated
task three times.

**What counts as evidence:** at least two dated instances, three preferred, each naming the
session and the task. The Candidates table in `SKILLS-BUILT.md` counts as instances if it was
filled in at the time.

**What does not count:** "they do a lot of reporting." A category is not a repetition.

**Before you report it:** check the Active skills table in `SKILLS-BUILT.md`. If a skill already
covers it, this is not a repetition finding — it is Lens 3, and the recommendation is to sharpen
the existing skill, never to build a second one that overlaps.

**Ranking:** frequency times how much of it is the same every time. A weekly task that is ninety
percent identical beats a daily task that is different every day.

### Lens 2 — Unverified acceptance

**The question:** where did they act on AI output without a check — and especially, where did
unchecked output leave the building?

**What counts as an instance:** a specific artifact or decision, plus no verification step in the
record for it. Rank by exposure:

1. It went to another person — sent, published, presented, filed where others rely on it.
2. It drove an irreversible or expensive action.
3. It was used internally and could still be corrected.

**What counts as evidence:** the artifact, the date, and the specific absence — no check named,
no evidence quoted, no second session or second model involved. In `progress/SESSION-LOG.md` the
`UNVERIFIED` field of each entry is written for exactly this lens; read it first, then read the
`GOT DONE` lines for anything that left the building without appearing there.

**The honesty rule that this lens lives or dies on:** on tiers 3 and 4, **absence of a record is
not proof of absence of a check.** Write "not recorded as checked", never "was not checked".
Then ask the learner directly about the top one or two. Being wrong about this is the fastest way
to make a learner distrust every other finding in the review.

**What does not count:** the learner reading it themselves and thinking it looked fine. That is
[F-10, the self-graded pass](../../../protocols/FAILURE-MODES.md#f-10--the-self-graded-pass) with
a human in the loop instead of a model, and it is exactly what this lens is looking for.

### Lens 3 — The hard way

**The question:** where did they do something manually that a tool they *already have* would
have done?

**What counts as an instance:** a manual task in the window, paired with the specific existing
thing that covers it — a named row in `SKILLS-BUILT.md`, a harness skill, or a connected tool
they have used before. Both halves are required.

**What counts as evidence:** the date and task of the manual instance, plus the name of the
existing tool and where it is recorded.

**What does not count:** something no tool of theirs covers. If nothing exists yet, it belongs to
Lens 1 (if repeated) or Lens 4 (if it is a capability they never knew about). Keeping this lens
strict is what makes it useful: it is the lens that says "you already own the fix."

**Also look for the reverse:** a skill in the Active table with a usage count of zero across the
window. Either it should have fired and did not — usually a description that does not match how
they actually phrase the request — or it is clutter and should be retired. Both are findings.

**Ranking:** how often the manual version recurs, and how close to zero the switching cost is.
"You already have this and it takes ten seconds" is the highest-payoff finding this review can
produce.

### Lens 4 — Unopened doors

**The question:** what did they never try that is genuinely within reach from where they are now?

**Three hard constraints**, because this lens degrades into a capability brochure if you let it:

1. **Reachable.** It uses only what they already have and topics already at `[>]` or `[x]` in
   `MASTERY.md`. If it needs three things they have not learned, it is not a door, it is a
   corridor.
2. **Attached.** It must attach to a specific thing that actually happened in the window. Name
   the session it would have helped.
3. **One step.** Something they could do once, this week, and see the result of. Not a programme.

**What counts as evidence:** the moment in the window where it would have applied, and the
sentence naming what they already have that makes it available now.

**What does not count:** a list of things AI can do. That is not a review finding; that is
[`/whats-possible`](../whats-possible/SKILL.md), and if the learner needs that instead, say so and
offer it.

This lens is the curiosity drill from
[TEACHING-PROTOCOL.md](../../../protocols/TEACHING-PROTOCOL.md) in review form. When you report
it, also say **why that question was available to you and not to them** — usually because you
know a capability exists and they do not. The bottleneck is inventory, not intelligence, and
saying so does more than the finding itself.

### Lens 5 — Decay

**The question:** which mastery topics have not been used lately and are probably slipping?

**What counts as an instance:** a topic in `MASTERY.md` at `[x]` or `[>]` whose `Last recalled`
date is outside the window or considerably older, and which does not appear in the window's work. A
topic marked `[x]` or `[>]` whose `Last recalled` still reads `never` is the sharpest case of this,
not an exception to it — it was earned and has not been touched since.

**What counts as evidence:** the topic number and name, its `Last recalled` line quoted, and the
observation that nothing in the window used it.

**Ranking:** by how load-bearing that topic is for what they are working on *now*, per
`LEARNER.md`. A decayed topic they are about to need is urgent; a decayed topic that is irrelevant
to their current work can wait and should be reported as low priority rather than padded in.

**What this lens may propose, and what it may not.** It may propose a rung demotion. It may not
perform one silently. Demotions follow the honest-un-checking rules in
[TEACHING-PROTOCOL.md](../../../protocols/TEACHING-PROTOCOL.md): shown to the learner in the
review, said kindly and without drama, and only written to `MASTERY.md` in step 6 with a dated
evidence line recording what prompted it.

### Merging the five lenses into one review

You now have five sets of findings and one review to write. Merge them explicitly, in this order,
rather than by impression — the impression is what five lenses exist to prevent. Each lens report,
whether a subagent wrote it or you did, has the sections defined in
[`.claude/agents/reviewer.md`](../../agents/reviewer.md), and every one of them has somewhere to go:

1. **Pool every finding with its instances.** Findings from different lenses resting on the same
   instances are one finding. Keep the lens that explains it best; drop the duplicate rather than
   letting one habit occupy two of the three slots.
2. **Re-rank the pooled list across lenses**, on the same payoff-over-effort basis each lens used
   inside itself. A lens that returned three findings is not entitled to three of your slots.
3. **Take the top three.** What falls below three is not carried forward as a backlog. If it still
   matters it comes back in the next review with fresher evidence, which is a better signal than a
   stale item.
4. **Pool the `WENT WELL` lines** and take the one or two best evidenced. `NONE FOUND IN THIS LENS`
   from all five is a guardrail 2 problem to go back and solve, not a result to publish.
5. **Pool the `COULD NOT SEE` lines** into WHAT I COULD NOT ASSESS, deduplicated — five workers
   reading the same thin log will each report the same gap, and it is one gap.
6. **Route the `OUTSIDE MY LENS` lines.** Each belongs to another lens. If that lens already found
   it, drop it. If it did not and the line carries a dated instance, it joins the pool as a finding.
   If it carries no instance, it goes nowhere — the evidence standard does not relax because the
   observation arrived sideways.

---

## STEP 4 — The output shape

Fixed shape, in this order, every time.

```
<the tier banner from step 1>

THE ONE THING
<The single most valuable change to make next, and why — the what and the reason, nothing
else. One short paragraph. No preamble above it.>

WHAT WENT WELL
- <date> — <session or task> — <what they did, and what specifically shows it was better
  than before>

THE THREE, RANKED BY PAYOFF OVER EFFORT
1. <the same item as THE ONE THING, now with the how: the exact first move>
   Evidence: <dates and instances>   Effort: <one-off / small / needs a session>
2. <item> — Evidence: <...>   Effort: <...>
3. <item> — Evidence: <...>   Effort: <...>

WHAT I COULD NOT ASSESS
- <what you could not see, and which finding would change if you could>
```

**Why the one thing comes before the praise**, even though the praise is real: a recurring
document gets skimmed, and whatever is at the top is the only part reliably read. That ordering
is the wallpaper countermeasure from
[REVIEW-ROUTINE.md](../../../protocols/REVIEW-ROUTINE.md) and it is deliberate.

**The one block that may ever go above THE ONE THING.** If step 2 found two consecutive blank
`ACTED ON` lines, open with the no-evidence-of-action question from
[REVIEW-ROUTINE.md](../../../protocols/REVIEW-ROUTINE.md) — name the fact, then ask whether to
lengthen the cadence, shrink the items until item 1 always fits in ten minutes, or stop running
this — and wait for the answer before giving the findings. Be precise in the wording: you can see
that nothing in the record changed, which is not the same as knowing they did not read it. On an
unattended run you cannot wait, so put the block at the top, ask the question, and give the
findings below it. Nothing else, ever, goes above THE ONE THING.

**Item 1 of the three is the same item as THE ONE THING.** State it twice on purpose: at the top
with only the what and the why, in the list with the exact first move. Do not introduce a
different item at position 1.

**Ranking, concretely.** Payoff is how often the thing recurs multiplied by what it costs each
time it happens. Effort is how many minutes of the learner's time the change takes once. Describe
both in mechanism, never in invented figures — "this happens most weeks and each time it costs a
rewrite" is honest; a percentage is not.

**Length.** The whole review fits on one screen. A long review is an unread review, and the
lenses can always produce more than is worth reading.

---

## The two guardrails, which pull against each other on purpose

Hold both at once. The way to hold both is a single standard applied in both directions:

> **A claim about progress and a claim about a problem are the same kind of claim, and both
> need a citation. If you cannot cite it, you cannot write it.**

### Guardrail 1 — Anti-flattery: a review with nothing to improve is a failed review

If you finish the lenses with nothing, you have not looked hard enough. Do not publish a clean
bill. Go back and dig, with these specific moves:

- Widen the window by another week and re-run the lenses.
- Re-read Lens 2 for anything that went to another person. Something always did.
- Check every skill's usage count. A zero is a finding, in one direction or the other.
- Read the `STUCK ON`, `UNVERIFIED`, and `NEXT` lines of every session-log entry in the window.
  The follow-ups nobody followed up on are the richest seam in that file.
- Compare the last three entries of `LEARNER.md` "Confused by" against the window. Confusion that
  never got resolved is a finding.

**The one honest exit, and only this one:** if after digging the material genuinely will not
support a finding, the problem is the material, not the practice. Say exactly that — "the window
holds two short sessions and I cannot see a pattern in two sessions" — and make step 1's fix the
recommendation. **Never manufacture a finding to satisfy this guardrail.** An invented criticism
is the same failure as invented praise, and it costs more, because the learner will act on it.

### Guardrail 2 — Anti-demoralisation: a review that only criticises is inaccurate

Progress happened, and it is in the record. A review that omits it is not being rigorous; it is
being wrong, and it will be read once and never again.

- **At least one evidenced win, from inside this window.** Not "you have been doing well
  generally" — that is the same empty sentence as "you should verify more", pointed the other way.
- **Cite it exactly as hard as a problem.** Date, session, what they did, and what shows it was
  different from before. "Wrote the done-check before asking, unaided, on the vendor summary" is a
  win. "Good progress on verification" is padding.
- **Compare them to themselves, never to a standard.** The comparison that matters is against
  their own earlier sessions, which is the only comparison the record can actually support.
- **If you genuinely cannot find an evidenced win**, say that plainly rather than inventing one —
  and treat it as a signal about the window or the tier, and say which.

Both guardrails fail the same way: writing a sentence you cannot point at. Neither is satisfied by
tone.

---

## STEP 5 — Offer to do item one now

End with a direct offer, not a summary. One item, this conversation, right now.

```
Item 1 is the one worth doing today, and it takes about <effort>. Want to do it now, in this
chat? If not, tell me which of the three you would rather start and we will do that instead.
```

Offer. Do not start. If they say yes, hand to the right skill —
[`/skillify`](../skillify/SKILL.md) for a repetition finding,
[`/verify-this`](../verify-this/SKILL.md) for an unverified-acceptance finding,
[`/quiz`](../quiz/SKILL.md) for a decay finding — and do not re-summarise the review on the way.

---

## STEP 6 — Write it down

1. **Append the review to [`progress/REVIEWS.md`](../../../progress/REVIEWS.md)**, dated, using
   the entry format that file defines. Read its header rather than writing from memory; that file
   owns its own shape, and its shape is not identical to the on-screen shape above. Carry the
   tier and the window into the entry — a review whose source is not recorded cannot be compared
   against the next one.
2. **Fill in the previous entry's `ACTED ON` line**, if the record shows it was acted on. That is
   the one edit `progress/REVIEWS.md` permits to a past entry, and it is what makes the
   no-evidence-of-action check in [REVIEW-ROUTINE.md](../../../protocols/REVIEW-ROUTINE.md)
   possible. Write only what the record shows. If nothing shows, leave it blank rather than
   guessing, and say in the new review that the previous item shows no evidence of action.
3. **Update `progress/MASTERY.md` only for rung changes the learner has seen and agreed to**, with
   a dated evidence line in the format that file defines. Show them the line before you write it.
4. **Log repetition findings that have not reached three occurrences** into the Candidates table
   in `progress/SKILLS-BUILT.md`, in that table's own row shape rather than a shape of your own,
   so the third occurrence is obvious when it arrives.
5. **Say what you wrote**, in one line: `Captured: 1 entry in progress/REVIEWS.md, 1 rung change
   in progress/MASTERY.md, 2 candidate rows in progress/SKILLS-BUILT.md.`

**If this review was produced by a scheduled unattended run**, stop after item 1 and 2. Do not
write to `MASTERY.md` or `SKILLS-BUILT.md` with nobody present — list the proposed changes inside
the review instead and let the learner confirm them when they read it. The reasoning is in
[REVIEW-ROUTINE.md](../../../protocols/REVIEW-ROUTINE.md).

**If you cannot write files at all**, say so plainly and put the full text of each entry in the
chat so the learner can paste it in. Never claim to have written something you did not write.

---

## Worked example — the shape, on a fictional learner

> **Invented for illustration.** The learner, the dates, and the work are fictional. Do not treat
> anything in it as a fact about the actual learner.

```
Review source: TIER 3 — the harness session log (progress/SESSION-LOG.md), 5 entries,
2026-05-04 to 2026-05-17. I am reading short summaries written at the end of each session,
not the conversations. Anything nobody wrote down is invisible to me here, and that includes
most of what went wrong quietly.

THE ONE THING
You have now built the client onboarding note by hand four times in two weeks, and three of
the four sessions record you retyping the same instructions from memory. That is the single
most expensive habit in this window, because it recurs weekly and the part that changes is
only the client name and the two dates.

WHAT WENT WELL
- 2026-05-11 — the vendor summary — you wrote the done-check before asking for a draft, then
  caught a figure that was not in the source. The log records you asking for the page number
  rather than accepting the number. That is the first time in this record that the check came
  before the work rather than after it.

THE THREE, RANKED BY PAYOFF OVER EFFORT
1. Turn the onboarding note into a skill. First move: open the last one you wrote and run
   /skillify against it.
   Evidence: 2026-05-04, 05-08, 05-13, 05-16.   Effort: one session, about 20 minutes.
2. The figures in the 05-16 board summary are not recorded as checked, and that document went
   to three people. First move: ask me, in a fresh session, to check each figure against its
   source and quote the line.
   Evidence: 2026-05-16 session-log entry, no check named.   Effort: one-off, 10 minutes.
3. Topic 5, done-checks, was last recalled on 04-22 and nothing in this window used it. It is
   about to matter because item 1 builds a skill and a skill without a done-check is a prompt
   with extra steps. First move: two quiz questions at the start of the next session.
   Evidence: MASTERY.md, "Last recalled: 2026-04-22".   Effort: small.

WHAT I COULD NOT ASSESS
- Whether the 05-16 figures were in fact checked. The log does not record a check, which is
  not the same as no check happening. Ask me to confirm and I will correct the review.
- Two sessions on 05-09 and 05-14 have log entries of one line each. Anything that went wrong
  in them is not visible to me.
```

Note what the example does not do: it does not say "great work on verification", it does not
recommend anything requiring a tool the learner does not have, and it does not claim the board
figures were unchecked when the record only shows that no check was written down.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| You are about to write "you should verify more" | Stop. Name the artifact, the date, and who received it, or drop the finding entirely. |
| Five lenses produced one general impression | You ran them together. Re-run one at a time, writing each out before starting the next. |
| Every finding is from the most recent session | Recency, not review. Go back and read the earliest entries in the window first, then re-rank. |
| The review runs past one screen | Cut to three items. The lenses will always generate more than is worth reading. |
| A finding contradicts something in `DECISIONS.md` | Open with the fact that it was ruled out and say what has changed. If nothing has changed, drop it. |
| The learner disputes a finding | They are usually right about their own work. Correct the review, write the correction into `progress/REVIEWS.md`, and say which lens got it wrong. |
| You cannot tell which tier you are on | You did not run step 1. Go back and run it. Never publish a review without the banner. |
| Nothing came back from any lens | Guardrail 1: dig with the five named moves. Then, only if the material truly will not support it, say the window is too thin — and never invent a finding. |

---

## Related

- [REVIEW-ROUTINE.md](../../../protocols/REVIEW-ROUTINE.md) — how to make this recur, and what to do with a review once it exists.
- [`.claude/agents/reviewer.md`](../../agents/reviewer.md) — the read-only worker that runs one lens.
- [`progress/REVIEWS.md`](../../../progress/REVIEWS.md) — where reviews are stored and how to read the arc across several.
- [`progress/SESSION-LOG.md`](../../../progress/SESSION-LOG.md) — the record this review is usually built from.
- [`/coach`](../coach/SKILL.md) — the in-the-moment version: one intervention, inside the task, then out of the way.
- [`/recall-session`](../recall-session/SKILL.md) — for finding one specific past session rather than reviewing a window of them.
