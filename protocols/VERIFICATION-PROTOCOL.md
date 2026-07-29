# Verification Protocol

*The standing procedure the AI follows to check its own output before you ever see it. Written to be executed literally. Read time: 15 minutes.*

---

## What this file is

This is an operating procedure, not an essay. When this harness is loaded, the AI follows this
file without being asked. You do not have to remember to say "check your work." The checking is
supposed to be automatic, the way a seatbelt is automatic.

Two readers:

- **The AI** reads this as instructions. Every step here is written so it can be executed
  literally, with no interpretation required.
- **You** read this so you know what to expect, and so you can tell when the AI skipped a step.

The idea underneath it is simple and it is the single most load-bearing idea in the whole
harness: **never let the worker grade its own work.** The part of the system that produced an
answer is the worst possible judge of whether that answer is right, because it is judging using
the same assumptions that produced the answer. Every procedure below exists to put some
distance between the making and the checking.

The background and the reasoning live in [Verification](../curriculum/04-verification.md).
The catalog of what counts as a real check for each kind of work lives in
[Done-Checks](DONE-CHECKS.md). This file is the procedure that connects them.

---

## Part 1. When verification fires

Verification is not a mode you switch on. It fires automatically whenever any of the following
is true of the output being produced. The AI does not ask permission first. It verifies, then
reports what it verified.

| Trigger | Fires when | Why |
| --- | --- | --- |
| **Actionable claim** | The learner will do something differently because of it | A wrong claim becomes a wrong action |
| **Research output** | Anything gathered from outside the conversation | Sources get misread, mis-attributed, or invented |
| **A number** | Any figure, count, total, percentage, amount, rate | Numbers look authoritative even when guessed |
| **A date** | Any deadline, effective date, timeline, or ordering | A plausible date is trivial to produce and hard to spot as wrong |
| **A name** | Any person, company, product, team, or title | Wrong names damage trust instantly and visibly |
| **A quote** | Any words presented as someone else's words | A paraphrase presented as a quote is a fabrication |
| **A citation** | Any reference to a document, page, section, or link | Plausible-looking citations to nothing are common |
| **An external source** | Anything read from a web page, file, email, or system | The AI may have read something else, or nothing |
| **Human-facing output** | Anything being sent, posted, filed, or shown to another person | The cost of an error lands on someone else |
| **Irreversible action** | Anything that cannot be undone in one step | No second chance to catch it |
| **Code or a formula** | Any script, macro, or spreadsheet formula | It will run again later, on inputs you did not test |
| **A summary you have not read** | Any condensation of a source the learner has not read | You cannot spot what was dropped |

If more than one trigger fires, that does not change the procedure. It changes the tier — see
Part 2. Two or more triggers on the same output means Tier 3 is not acceptable.

**What does not fire verification.** Brainstorming. Drafting where you will review every line
yourself. Reformatting text you supplied. Answering a question about the conversation you are
already in. Verification has a cost in time and money, and spending it on throwaway output is
its own kind of waste.

---

## Part 2. The three-tier ladder

There are three ways to check something. They are not equally good. **Always climb as high as
the task allows** — take the highest tier that is actually possible for this piece of work, and
say which tier you used.

### Tier 1 — Deterministic

A check that either matches or does not, with no judgment involved. No opinion, no "seems
right." A machine, or a person with no expertise, could run it and get the same answer.

Examples of Tier 1 checks:

- Re-read the primary source and confirm the sentence is actually there.
- Count the rows, the items, the days. Compare to the number claimed.
- Search the document for the exact quoted string. It matches or it does not.
- Recompute the total a second way and compare the two results.
- Open the link. It resolves to the cited page or it does not.
- Run the script on an input where you already know the correct output.
- Look the value up in the system of record rather than in the AI's memory of it.

Tier 1 is the goal for anything factual. Many claims people treat as "matters of judgment" have
a Tier 1 check hiding in them. Before deciding a claim needs judgment, spend thirty seconds
looking for the deterministic version. **A claim that cannot be checked deterministically often
should not be asserted at all** — it should be marked uncertain instead.

### Tier 2 — Independent judgment

A separate reader, with a fresh context — **preferably running on a different model** —
instructed to refute, scoring against a written rubric. Use this when the question genuinely
requires judgment: is this argument sound, is this tone right for the recipient, did this
summary drop the thing that mattered, would this actually work.

Three requirements, all of them mandatory. A Tier 2 check that misses one of them is a Tier 3
check wearing a costume:

1. **Fresh context.** The checker must not have seen the conversation that produced the work.
   If it has, it inherits the same assumptions and will agree with itself.
2. **Refutation framing.** The checker is told to find what is wrong. See Part 3.
3. **A written rubric.** The checker scores against stated criteria, not against a general
   sense of quality. Without a rubric, "looks fine" is a valid answer, and it will be the
   answer most of the time.

#### The cross-model rung inside Tier 2

"Independent" is not one thing. Tier 2 has its own strength order, weakest to strongest:

- **A fresh session of the same model, asked to review.** Drops the context, the prior answer,
  and the accumulated assumptions. Keeps the model's characteristic blind spots, because the
  thing evaluating the answer is still the thing that produced it.
- **A different model, asked to review.** Drops the blind spots as well. A model trained
  differently finds different things unremarkable, so an error that sat comfortably inside one
  model's sense of what is plausible can stand out to another.
- **A different model, instructed to refute, given the artifact and the criteria and nothing
  about how the work was made.** This is the strongest check any model can give you.

**Prefer a different model whenever one is available**, and state in the report which of the
three was used. A check that does not say which one it was cannot be weighed.

The mechanism, at length, is in [Many models](../curriculum/17-many-models.md). The caveat that
travels with it, in one sentence: models trained on overlapping material can be confidently
wrong in the same direction, so cross-model agreement raises confidence and never establishes
correctness — which is why Tier 1 still outranks all of this.

### Tier 3 — Structured self-review

The same AI, in the same conversation, reviewing its own output. This is the weakest tier. It
catches careless errors and almost never catches confident ones, because a confident error is
by definition one the model believes.

Tier 3 is acceptable only for low-stakes, reversible, easily-inspected work. When it is used it
must be structured as **an attempt to disprove**, never as a general review. The prompt is never
"does this look right." The prompt is:

```
List every claim in what you just wrote that would be embarrassing if it were wrong.
For each one, state: where the claim came from, and what would have to be true for it
to be false. Then mark any claim you cannot trace to a source.
```

If that pass surfaces anything with a trigger from Part 1, stop and climb to Tier 1 or 2.

### Choosing a tier

| Situation | Minimum tier |
| --- | --- |
| Anything irreversible, or leaving the building | Tier 1 for facts, plus Tier 2 for judgment |
| Two or more triggers from Part 1 | Tier 2 |
| One trigger, reversible, you will read it yourself | Tier 1 if a deterministic check exists, else Tier 2 |
| No triggers, low stakes | Tier 3, or nothing |

When a Tier 1 check exists, use it even if you are also running Tier 2. They check different
things: Tier 1 checks whether the fact is right, Tier 2 checks whether the work is any good.

For the first row of that table — irreversible, or leaving the building — the Tier 2 check should
be the cross-model form wherever a different model can be reached, including by asking the human
to paste it into a second assistant. See Part 5, Option B.

---

## Part 3. The refutation frame

This is the part that makes verification work at all, and it is the part everyone skips.

A checker asked "is this correct?" will usually say yes. Not from laziness — from the ordinary
pull toward agreement. The fix is to change what the checker is being graded on. **The checker
is told to find what is wrong, and is judged on what it finds, not on agreeing.** Finding
nothing is a weak result for the checker, not a good result.

Hand a checker this text, verbatim. Fill in the two bracketed fields and nothing else.

```
You are a hostile checker. Your job is to find what is WRONG with the material below.
You are graded on the defects you find, not on whether you agree with it. Returning
"looks good" with nothing found is a failing result unless you can show the specific
checks you ran that came back clean.

MATERIAL TO REFUTE:
[paste only the claim or the output, with no surrounding conversation]

EVIDENCE SUPPLIED WITH IT:
[paste the source text, file excerpt, calculation, or link that the claim rests on -
 or write "none supplied"]

Do this, in order:
1. List every load-bearing claim in the material. Load-bearing means: if it were
   wrong, the reader would do something they should not do.
2. For each claim, try to break it. Check it against the supplied evidence. Where the
   evidence does not cover the claim, say so explicitly.
3. Flag anything that is asserted with more confidence than its evidence supports.
4. Flag anything that is an inference presented as a fact.
5. Name EVERY assumption made but never stated. Unstated assumptions are the most
   common failure and you are specifically looking for them.
6. State what you could NOT check, and why. This list must not be empty unless you
   genuinely verified every claim against a primary source.

Return exactly this structure:
  VERDICT: confirmed | corrected | demoted-to-uncertain | could-not-check
           (one overall verdict for the material - use the worst verdict
            appearing in PER-CLAIM below)
  PER-CLAIM: one line per claim - the claim, its own verdict, the evidence
  ASSUMPTIONS FOUND:
  COULD NOT CHECK:
  SINGLE BIGGEST RISK:

Do not rewrite or improve the material. You are not the author. Find the defects and
report them.
```

Two rules about that text:

- **Do not soften it.** "Please review this and let me know if anything seems off" produces
  agreement. The hostility is load-bearing.
- **Do not include the conversation.** Paste the claim and the evidence only. Context that
  explains why the AI believed something will persuade the checker to believe it too.

---

## Part 4. The procedure when subagents are available

A subagent is a separate AI session the main AI can start, hand a task, and get an answer back
from. It has its own fresh context. That is exactly what Tier 2 requires. If your setup supports
them, this is the strong path. See
[Subagents and swarms](../curriculum/08-subagents-and-swarms.md) for what they are.

This harness ships two checkers already written for this job: the
[verifier](../.claude/agents/verifier.md), which grades claims against sources and reports what it
found, and the [adversary](../.claude/agents/adversary.md), which assumes the claim is wrong and
tries to prove it. Dispatch those rather than inventing a checker each time.

One honest note about subagents: they get a fresh context, but they usually run on the same
model as the session that produced the work, which puts them on the first rung of Tier 2 rather
than the third. If a different model is available to you — a second tool, a second vendor, or a
handoff the human can paste — prefer it, and say in the report which you had.

The procedure:

1. **Extract the load-bearing claims.** Write them out as a numbered list before checking
   anything. A claim is load-bearing if the reader would act differently were it false. This
   list is the unit of work — everything downstream is per-claim.

2. **Choose the split.** Two shapes work, and which one you use depends on the material:

   - **One checker per claim.** Use when the claims are factual and separable — numbers, dates,
     quotes, citations. Each checker gets one claim, its evidence, and the refutation prompt.
     Cheap, parallel, and the verdicts are unambiguous.
   - **One checker per dimension.** Use when the output is a single piece of work that has to
     hold together — a document, a plan, a recommendation. Run four checkers, one each on:
     **accuracy** (are the facts right), **completeness** (what is missing that should be here),
     **would-this-actually-work** (walk through it literally and find where it breaks), and
     **what-was-assumed** (list every unstated assumption and what happens if it is wrong).

   For work that is both factual and structural, run both shapes. They find different failures.

   **Bound the fan-out.** Do not spawn a checker for every line of a long list. Group related
   claims so you dispatch a handful of checkers rather than dozens, take the load-bearing claims
   first, and name in the report any claim you did not dispatch a checker for.

3. **Give every checker the refutation prompt from Part 3, unmodified**, plus the claim, plus
   the evidence. Never give a checker the conversation that produced the work.

4. **Require the structured verdict.** If a checker returns prose instead of the structure, that
   result does not count. Send it back once with the structure restated. If it comes back
   unstructured a second time, record it as could-not-check.

5. **Require the "could not check" list.** A checker that reports it verified everything with no
   gaps is reporting a suspicious result, not a clean one. Ask it directly: what did you take on
   faith? Every real check has a boundary.

6. **Count the verdicts.** If most checkers refute a claim, the claim fails — do not average the
   opinions and do not let the strongest-worded reply win. One checker refuting on solid evidence
   also fails the claim; evidence beats headcount. What never happens is a claim surviving
   because the author disagreed with the checker.

7. **Never let the checker fix it.** Checkers report. The author corrects. A checker that
   rewrites the work has taken authorship of it and can no longer check it.

**Cost note.** Checkers are usually cheap work — they read a small amount of text and return a
short structured answer, so a smaller and cheaper model is normally the right choice for them.
Reserve the expensive model for the original work and for genuinely hard judgment calls. See
[Cost, models and effort](../curriculum/09-cost-models-and-effort.md).

---

## Part 5. The procedure when subagents are not available

Most people reading this are in a plain chat window with no ability to spawn anything. The
degraded procedure is weaker, but it is real, and it catches a great deal. Do not skip
verification because the strong path is unavailable.

**Option A — the clean-slate message (the AI does this itself).**

In a new message, the AI restates **only** the claim and **only** the evidence, with none of the
surrounding conversation, and applies the refutation prompt from Part 3 to that. Then it answers
as the checker before returning to being the author.

This works because most of what makes self-review useless is the surrounding conversation: the
reasoning, the hedges, the earlier agreement, the sense of having already settled it. Stripping
that away removes a lot of the momentum. It does not remove all of it — the same model with the
same training is still doing the checking. Treat this as a strong Tier 3, not a real Tier 2.
Say so in the report: "checked in degraded mode, no independent context available."

**Option B — the fresh-chat handoff (you do this, and it is genuinely Tier 2).**

The AI prepares a self-contained block. You paste it into a brand new chat with no history —
**and where you can, into a different assistant from a different vendor, not just a new window
of the same one.** A new window drops the context; a different model drops the blind spots too.
Then you paste the verdict back.

It costs one paste out and one paste back, and it is the cheapest way to get a genuinely
independent reader. Use it for anything going to a client, a boss, or a system you cannot easily
undo. Say in the report which you got — different model, or fresh window of the same one.

The block the AI prepares, verbatim:

```
You are checking a piece of work produced by someone else. You have no history with
it and no stake in it being right. Your job is to find what is wrong. You are graded
on the defects you find. "Looks good" with nothing found is a failing answer unless
you name the specific checks you ran.

THE CLAIMS TO CHECK:
[numbered list of the load-bearing claims, one per line, no commentary]

THE EVIDENCE BEHIND THEM:
[the source text, figures, excerpts, or links - or "none supplied" where there is none]

For each numbered claim, return one line:
  [number] VERDICT: confirmed | corrected | demoted-to-uncertain | could-not-check
           EVIDENCE: what you checked it against, specifically
           NOTE: the correction, or the reason it could not be checked

Then return:
  ASSUMPTIONS THE AUTHOR MADE WITHOUT SAYING SO:
  WHAT I COULD NOT CHECK, AND WHY:
  THE SINGLE THING MOST LIKELY TO BE WRONG HERE:

Rules: do not rewrite the work. Do not be agreeable. If a claim has no evidence
behind it, that is a finding - report it as could-not-check rather than assuming it
is fine. If the evidence supports something narrower than the claim, say exactly how
much narrower.
```

**Option C — the deterministic fallback.** When neither A nor B is available, Tier 1 still is.
Open the source and re-read it. Recount the list. Recompute the total by a different route. Click
the link. Deterministic checks need no second AI at all, and they are the strongest tier anyway.

---

## Part 6. The verdict format

Every verification returns one of exactly four verdicts per claim, with evidence attached. No
other verdicts exist. "Probably fine" is not a verdict.

| Verdict | Meaning | What must be attached |
| --- | --- | --- |
| **confirmed** | Checked against evidence and it holds | The specific evidence: the source line, the recount, the link that resolved |
| **corrected** | Was wrong, now fixed | The original claim, the corrected claim, and what showed it was wrong |
| **demoted-to-uncertain** | Cannot be established either way, so it is no longer asserted as fact | What was tried, and how the claim is now worded instead |
| **could-not-check** | No check was possible or none was run | Why — no source, no access, no time, out of scope |

Rules that go with the format:

- **A verdict with no evidence attached is not a verdict.** "Confirmed" on its own is a claim
  about a check, not a check.
- **Demoted is a success, not a failure.** A claim moved from "the deadline is the 14th" to "I
  could not confirm the deadline; the source I have does not state one" has made the output more
  useful, not less.
- **could-not-check is reported to the human every time.** It never gets quietly dropped, and it
  never gets rounded up to confirmed because everything else passed.
- **The final output carries the marks.** Anything demoted or could-not-check stays visibly
  flagged in the delivered work, not just in the verification report. The reader of the document
  is the person who needs to know.
- **Where the delivered work tags claims by provenance, the tags are exactly three:**
  `SOURCED`, `INFERRED`, `UNCERTAIN`, as defined in
  [Verification](../curriculum/04-verification.md). Provenance is not a verdict — it says where a
  claim came from, while the four verdicts above say what happened when it was checked. Surviving
  a cross-model check does not turn `INFERRED` into `SOURCED`. Only a source does that.

---

## Part 7. Escalation when verification fails

Verification failing is the system working. Here is what happens next, and there is a hard stop
in it on purpose.

1. **First failure: correct and re-verify, once.** Fix the specific defect the checker named. Do
   not rewrite everything around it. Re-run the same check — same tier, same rubric, and a
   different checker so it is not marking its own feedback. A different model is the best
   version of that; a fresh session is the minimum.

2. **Second failure: stop.** Do not attempt a third pass. Two failed checks on the same claim
   means the problem is not a wording error, it is that the claim cannot be supported with what
   is available. A third attempt does not find new evidence; it finds new phrasing that gets past
   the checker, which is worse than failing.

3. **Report the uncertainty plainly to the human.** In the delivered work, not in a footnote. The
   wording is close to this, and it is not an apology:

   > I could not verify this: [the claim]. I checked [what was checked] and it did not hold
   > because [reason]. I have left it out / marked it as unconfirmed. To resolve it you would
   > need [the specific thing that would settle it].

4. **Never resolve a failed verification by lowering the tier.** Dropping from Tier 1 to Tier 3
   because Tier 1 said no is the exact failure this protocol exists to prevent. The check does
   not get easier because you did not like the answer.

---

## Part 8. Honest reporting

Every verification report ends with what was **not** checked. Every one. This is not a formality
and it is not padding.

The reasoning: a check has a boundary, always. The checker read some things and not others,
followed some links and not others, tested some inputs and not others. When that boundary is
stated, you know exactly how much weight the "confirmed" verdicts carry. When it is hidden, you
have to assume the boundary is exactly where you would have wanted it, which is a guess.

So: **a verification that claims to have checked everything is itself suspect.** It means either
the material was trivially small, or the checker did not look at where its own limits were. Ask
which.

The closing block of every verification looks like this:

```
CHECKED:      [what was actually verified, and against what]
NOT CHECKED:  [what was skipped, and why]
TAKEN ON FAITH: [what was assumed true without testing]
INDEPENDENCE: [which checker was used: same session / fresh session of the same model /
               a different model asked to review / a different model told to refute]
CONFIDENCE:   [high / medium / low] because [the specific reason]
```

Related failure patterns, including what a verification theatre looks like from the outside, are
cataloged in [Failure modes](FAILURE-MODES.md).

---

## Part 9. A worked example

You ask for a one-page brief on a vendor before a meeting. The AI produces it. Six things in it
trip a trigger from Part 1: the vendor's founding year, the name of its head of sales, a figure
for its headcount, a quoted line from its documentation, a claim about its refund window, and a
recommendation about which plan to choose.

What the protocol does with that, in order:

1. Six claims listed explicitly, numbered.
2. Tiers assigned. Founding year, headcount, the quote, and the refund window all have Tier 1
   checks — the source can be opened and read. The head of sales has a Tier 1 check only if a
   current source exists; if the only source is undated, it is Tier 2 at best. The plan
   recommendation is judgment, so Tier 2.
3. Checks run. With subagents: one checker per factual claim with the refutation prompt, plus a
   dimension checker on the recommendation. Without: the fresh-chat block from Part 5, pasted
   once, covering all six.
4. Verdicts come back. Founding year confirmed with the source line. Headcount
   demoted-to-uncertain — the source gives a range and a stale date. The quote corrected — it was
   a paraphrase, and the actual wording is narrower. Refund window could-not-check, because the
   terms page was not accessible. Head of sales confirmed against a dated page. Recommendation
   corrected — the checker found it assumed a usage volume nobody stated.
5. The delivered brief carries the marks. The headcount now reads as a range with its date. The
   quote is the real quote. The refund window says it could not be confirmed and names where to
   look. The recommendation states the volume assumption out loud.
6. The report ends with what was not checked: the terms page, and whether the pricing shown is
   current for this region.

That brief is shorter on confident-sounding facts than the first draft was, and it is the one you
want to walk into the meeting with.

---

## Try this now

Take something an AI wrote for you in the last week — an email, a summary, a set of notes. Open
a **new** chat, with no history — and where you can, a different assistant rather than a new
window of the same one — and paste this:

```
You are a hostile checker. Your job is to find what is WRONG with the material below.
You are graded on the defects you find, not on whether you agree with it. "Looks good"
with nothing found is a failing answer unless you name the specific checks you ran.

MATERIAL TO REFUTE:
[paste the thing here]

EVIDENCE SUPPLIED WITH IT: none supplied

For each load-bearing claim, return one line:
  VERDICT: confirmed | corrected | demoted-to-uncertain | could-not-check
  EVIDENCE: what you checked it against
  NOTE: the correction, or why it could not be checked

Then return:
  ASSUMPTIONS THE AUTHOR MADE WITHOUT SAYING SO:
  WHAT I COULD NOT CHECK, AND WHY:
  THE SINGLE THING MOST LIKELY TO BE WRONG HERE:

Do not rewrite the work. Do not be agreeable.
```

Note how much of it comes back as could-not-check. That is not the checker being unhelpful.
That is the actual evidence base of the original, made visible for the first time.

---

## What you should now be able to do

- Recognise, without being told, which parts of an AI's output require checking before you act
  on them, and which do not.
- Ask for the highest tier of check a piece of work allows, and know when a "check" you were
  offered was actually the weakest tier in disguise.
- Run a genuine independent check with nothing but a second chat window and a pasted prompt.
- Read a verification report and tell the difference between one that found nothing and one that
  did not look — because a real one always tells you where it stopped.
