# Decisions

*A record of what was decided, why, and what was ruled out — so nothing gets relitigated six weeks later. The AI checks this file before proposing anything. Reading time: about 5 minutes.*

---

## For the AI: check this file before you propose

**Read this file before suggesting a tool, a workflow, an automation, a structure, or a way of working.** The learner may have already considered it and said no, and there is a reason written down here.

Re-proposing something that was rejected — with no acknowledgement that it was rejected — is one of the fastest ways to lose someone's confidence in you. It signals that nothing they told you stuck. It also wastes their time twice: once explaining the reasoning again, and once wondering whether they were wrong to reject it.

So:

- **If the thing you are about to propose appears in the Ruled out column of any decision below, do not propose it fresh.** Either drop it, or open with the fact that it was ruled out and say specifically what has changed since. "You ruled this out in April because of the cost; the free tier now covers your volume, which was the blocker" is a legitimate thing to raise. "Have you considered X?" is not.
- **If a decision is marked `Revisit when: <condition>` and that condition has now occurred, raise it.** That is the file working as designed. Say which decision, which condition, and what changed.
- **If you are proposing something genuinely new, say so** and check that it does not quietly contradict a standing decision.

**When a real decision gets made, write it down here immediately.** Not at the end of the session, not "if it seems important." The decisions that cause the most trouble later are the ones that felt too small to record at the time.

Rules for this file:

1. **Append only.** New decisions at the bottom. Never edit a past decision's reasoning to match what you now think — that destroys the record's only real value, which is showing what was known at the time.
2. **A decision is superseded, never overwritten.** If it changes, write a new entry and add a line to the old one: `SUPERSEDED BY: <date of the new entry>`. That single-line addition is the one edit permitted to a past entry.
3. **Record the reasoning as it was, including reasoning that later turned out wrong.** A decision made for a reason that did not hold up is the most educational entry in the file. Do not clean it up.
4. **"What was ruled out" is not optional.** A decision with no alternatives listed is not a decision — it is a default that nobody examined. If nothing was ruled out, write that explicitly and say whether alternatives were actually considered.
5. **Do not record preferences as decisions.** "Prefers short replies" belongs in [`LEARNER.md`](LEARNER.md). This file is for choices with consequences and alternatives.
6. **The entry template below is the only shape an entry takes.** If another part of the harness gives you a decision in a different shape, map it onto these fields. The field most often missing from an improvised shape is `RULED OUT`, which is the one that makes the entry worth keeping.

Related: [`LEARNER.md`](LEARNER.md) for who this person is and what they can do; [`SKILLS-BUILT.md`](SKILLS-BUILT.md) for what has been built, which is often the visible result of a decision recorded here.

---

## What belongs in this file

| Belongs here | Belongs elsewhere |
|---|---|
| Chose one tool over another, and why | How to use that tool (a skill) |
| Decided not to automate something, and why | A note that they find it boring ([`LEARNER.md`](LEARNER.md)) |
| Settled on a folder or note structure | The contents of those notes |
| Decided what will never be put into an AI tool | General privacy guidance ([the safety chapter](../curriculum/10-safety-privacy-and-trust.md)) |
| Rejected a proposed workflow after trying it | A skill that failed and was retired ([`SKILLS-BUILT.md`](SKILLS-BUILT.md)) |
| Chose a model tier or effort default for routine work | What model tiers are ([chapter 09](../curriculum/09-cost-models-and-effort.md)) |

A useful test: **would someone proposing the opposite six weeks from now need to know this?** If yes, it goes here.

---

## Entry template

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

---

## Decision log

*Append only. Newest at the bottom.*

---

### 2026-03-18 — EXAMPLE ENTRY, fictional

> **This entry illustrates the format. The learner, the situation and the dates are
> invented.** Delete it once there are real entries. Do not treat anything in it as a
> fact about the actual learner or as a recommendation about any real product.

```
DECISION: The Friday roundup stays a written instruction the learner runs by hand
  each week. It does not get put on a schedule to run unattended.

REASONING: The roundup goes to people whose opinion of the learner's work matters,
  and one of its four sources is unreliable — it is sometimes not updated until
  Friday afternoon. An unattended run would produce a confident roundup built on
  stale data, and nobody would be looking at it before it went out. The rule being
  applied: automate the boring, reversible, low-stakes thing first. This is
  reversible but it is not low-stakes, because a wrong roundup is seen by people
  before it can be corrected.

RULED OUT:
  - Scheduling it to run Friday morning — the stale-source problem, above.
  - Scheduling it with an alert when a source looks stale — rejected as premature.
    The learner has not yet run the manual version enough times to know what
    "stale" reliably looks like, so the staleness check would be guesswork
    dressed up as a rule.
  - Dropping the unreliable fourth source entirely — it is the one people ask
    about most.

DECIDED BY: The learner, after the AI proposed scheduling it.

REVISIT WHEN: The learner has run the manual version enough times to describe
  precisely what a stale fourth source looks like. At that point the staleness
  check stops being guesswork and the automation becomes reasonable.

REVISITED: (blank)
```

**Why this example is worth keeping until you have real entries:** it shows the two things that make an entry useful later. The reasoning names the principle being applied, not just the conclusion, so a future reader can tell whether the principle still fits. And the `RULED OUT` section records a rejected idea *with its specific defect*, which is what stops the same idea coming back in a new costume.

---

*Real entries start below this line.*
