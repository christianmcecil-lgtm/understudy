---
name: verify-this
description: Independently check a piece of work before it is acted on or sent. Use whenever the user says "check this", "is this right", "verify this", "fact-check this", "before I send this", "did you make this up", "are you sure", "double-check", or asks whether something is safe to send, share, or act on. Also use before anything irreversible, client-facing, or containing numbers, dates, names, quotes, or citations.
---

# /verify-this — the independent check

*Checks a piece of work claim by claim and reports what holds, what does not, and what could not
be checked. Instructions for the AI, not the human: read time about 5 minutes.*

Independently check a target piece of work, claim by claim, and return a per-claim verdict with
evidence plus one overall recommendation. Follow
[the verification protocol](../../../protocols/VERIFICATION-PROTOCOL.md); this skill is the
invocable form of it.

**The prime rule: you are not the author right now. You are the checker.** Do not improve the
work. Do not rewrite it. Find what is wrong with it and report. If the work being checked is
something you wrote earlier in this conversation, that makes hostile framing more important, not
less.

## Step 0 — Identify the target

The target is whatever the user pointed at: the last thing you produced, a pasted block, a named
file, or a draft in progress. If it is genuinely ambiguous, ask one short question and stop. Do
not verify the wrong thing.

## Step 1 — List every load-bearing claim, explicitly

Write out a numbered list of the claims before checking anything. A claim is **load-bearing** if
the reader would do something different were it false.

Sweep for these specifically, because they are what gets invented:

- every number, total, percentage, amount, count
- every date, deadline, duration, ordering
- every name of a person, company, product, or team
- every quoted passage and every citation or link
- every statement about what a source says
- every claim about what will happen, what is required, or what is allowed
- every recommendation, and the assumption underneath it

Show this list to the user. It is the first useful output of the skill, and it is often the
moment they realise how many assertions were sitting inside two paragraphs.

## Step 2 — Classify each claim

Tag every claim with exactly one:

| Tag | Meaning |
| --- | --- |
| **`SOURCED`** | There is a specific source that states it, and you can name the source |
| **`INFERRED`** | Derived, combined, or reasoned from something else — not stated anywhere directly |
| **`UNCERTAIN`** | No traceable basis you can rely on: it came from general knowledge or from nothing, you are not confident, the sources disagree, or you filled a gap with a reasonable default. Say which, and name the default if you used one |

These three are the whole vocabulary — there is no fourth tag. They are defined in
[Verification](../../../curriculum/04-verification.md).

Anything you cannot honestly tag as `SOURCED` is not sourced. A vague recollection of having read
something is `UNCERTAIN`. Do not upgrade a tag because the claim feels obviously true.

## Step 3 — Pick the highest available tier per claim

Per claim, take the strongest check that is actually possible:

- **Tier 1, deterministic** — re-read the primary source, count it, search for the exact string,
  recompute by a second route, open the link, run the script on a known input. Preferred always.
  Look for a Tier 1 check before concluding a claim needs judgment; most factual claims have one.
- **Tier 2, independent judgment** — a fresh checker with no history, told to refute, scoring
  against stated criteria. For anything requiring judgment: soundness, completeness, tone,
  would-this-actually-work. **A different model is the strongest form of this and the one to
  prefer** — see the cross-model option below and
  [Many models](../../../curriculum/17-many-models.md).
- **Tier 3, structured self-review** — only for low-stakes, reversible claims, and only framed as
  an attempt to disprove.

State the tier used for each claim in the output. A check whose tier is not stated cannot be
weighed by the reader.

## Step 4 — Run the checks

**If you can spawn subagents:** spawn one checker per load-bearing claim when the claims are
separable facts, or one checker per dimension — accuracy, completeness,
would-this-actually-work, what-was-assumed — when the target is a single piece of work that has
to hold together. This harness ships two checkers written for this: the
[verifier](../../agents/verifier.md), which grades claims against sources, and the
[adversary](../../agents/adversary.md), which tries to prove them wrong. Dispatch those. Bound the
fan-out — group related claims so you spawn a handful of checkers rather than dozens, and name any
claim you did not dispatch a checker for. Give each checker the refutation prompt below,
unmodified, plus the claim and its evidence, and nothing else. Never hand a checker the
conversation that produced the work.
Require the structured verdict; an unstructured reply does not count. Majority refutation of a
claim means the claim fails, and a single refutation carrying real evidence also fails it.
Checkers report; they never fix. See
[subagents and swarms](../../../curriculum/08-subagents-and-swarms.md).

**If you cannot spawn subagents:** run degraded mode, and say in the output that you did.

- Do every Tier 1 check yourself. These lose nothing in degraded mode — re-reading a source and
  recomputing a total are exactly as strong either way. Do these first and do them all.
- For judgment claims, start a clean-slate pass: restate only the claim and only the evidence,
  with none of the surrounding conversation, and apply the refutation prompt to that. Label the
  result as degraded, not independent.
- If the work is client-facing, irreversible, or otherwise high-stakes, offer the user the
  fresh-chat handoff: prepare the block from
  [the verification protocol](../../../protocols/VERIFICATION-PROTOCOL.md) Part 5, tell them to
  paste it into a brand-new chat with no history, and ask them to paste the verdict back. That
  is genuinely Tier 2, and it costs one paste out and one paste back. Offer the cross-model
  version of it below first — a different assistant is a stronger checker than a new window of
  the same one, and it costs the user exactly the same two pastes.

## The refutation prompt

Hand this to every checker you dispatch or run yourself, verbatim. Fill in the two bracketed
fields and change nothing else. (The prompt for a checker the *user* pastes into a second
assistant is the one in the cross-model section below.)
Do not soften it — the hostility is what makes it work.

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

## The cross-model option

The strongest check available to a user sitting in a plain chat window: a **different** assistant,
from a different vendor, told to refute. It is not a different tier — it is the strongest form of
Tier 2, because a model trained differently does not share the first one's blind spots. The
mechanism and its limits are in [Many models](../../../curriculum/17-many-models.md).

Offer it whenever a claim needs Tier 2 and the stakes are client-facing, irreversible, or
something the user will be asked to defend. Say plainly what it costs: one paste out, one paste
back, about two minutes.

**Give the other model exactly two things: the artifact and the criteria.** Never the
conversation that produced the work, never your reasoning, never what you were worried about,
and usually not that an AI wrote it. The reasoning is the thing the check is trying to escape —
paste it and the second model reads the first one's argument, finds it coherent, and agrees. The
user has then paid for a second opinion and received an echo.

Hand the user this text to paste, with the two placeholders filled in:

```
You are reviewing a document written by someone else. I did not write it and I have
no stake in it being good. You have not seen how it was produced and you should not
ask — judge only what is on the page.

Your job is to find what is wrong with it. You are not allowed to conclude that it is
fine, and you are not allowed to soften a finding to be polite.

Find the three problems most likely to cause real damage if this is acted on. For each:
1. What is wrong.
2. The exact sentence or line it lives in, quoted.
3. What would have to be true for it to actually be correct.
4. What the author should do about it.

Then, separately and briefly:
- Every factual claim you cannot verify from the document itself.
- Every number that appears without a source.
- Anything the document treats as settled that is actually a judgment call.

Do not rewrite it. Do not fix anything. Report only.

CRITERIA IT MUST MEET:
[your 2-5 lines here]

DOCUMENT:
[paste the artifact only]
```

Write the criteria for the user rather than asking them to invent them — two to five lines
stating what the artifact has to be true or good for. That is the part most people leave out, and
without it the checker scores against a general sense of quality.

When the verdict comes back:

- Treat the findings as **candidates, not verdicts**. A model told to find three problems will
  find three, including on clean work.
- Settle anything settleable with a Tier 1 check before acting on it. Second models invent
  problems the same way first models invent facts.
- An objection to a deliberate choice the checker could not see is not a finding. It is the price
  of withholding the reasoning, and it is worth paying.
- Enthusiastic agreement that adds nothing is **ambiguous, not reassuring**. If the stakes are
  high, go find a deterministic check anyway.
- Record the mode in Step 6 as `cross-model`, and name the correlated-error limit if the user
  treats agreement as proof: two models trained on overlapping material can be wrong in the same
  direction, so agreement raises confidence and never establishes correctness.

If no second assistant is available, say so rather than implying the check was stronger than it
was, and fall back to the fresh-chat handoff in Step 4.

## Step 5 — Return the verdict table

One row per claim. Four verdicts exist and no others. Every row carries its evidence; a verdict
with no evidence attached is not a verdict.

```
| # | Claim | Tag | Tier | Verdict | Evidence |
|---|-------|-----|------|---------|----------|
| 1 | ...   | SOURCED | 1 | confirmed | the exact line, count, or result that settled it |
```

| Verdict | Use when |
| --- | --- |
| **confirmed** | Checked against evidence and it holds |
| **corrected** | Was wrong; the corrected version is shown |
| **demoted-to-uncertain** | Cannot be established either way, so it is no longer asserted as fact |
| **could-not-check** | No check was possible or none was run — say why |

## Step 6 — State plainly what could not be checked

Always. Never omit this section, and never let it be empty unless every single claim was verified
against a primary source — which is rare enough that you should re-examine the claim that it
happened.

```
CHECKED:         [what was verified, and against what]
NOT CHECKED:     [what was skipped, and why]
TAKEN ON FAITH:  [what was assumed true without testing]
MODE:            [cross-model / subagent checkers / degraded single-context / deterministic only]
```

A verification that reports it checked everything is itself suspect. Say where you stopped.

## Step 7 — Show corrections next to the originals

For anything corrected, show both. Never silently swap in the fixed version — the user needs to
see what the original said in order to calibrate how much to trust the next draft.

```
ORIGINAL:  "the renewal date is 14 March"
CORRECTED: "the renewal date is 4 March"
WHY:       the contract, clause 8, states 4 March; 14 March appears nowhere in it
```

## Step 8 — One overall recommendation

End with exactly one of these three lines, and nothing hedged around it:

- **SAFE TO SEND** — every load-bearing claim confirmed or explicitly marked, nothing
  could-not-check that matters to the reader's decision.
- **NEEDS THE MARKED FIXES** — specific defects found, listed above, fixable. Name them again in
  one line each so the user can act without scrolling.
- **DO NOT SEND** — something load-bearing is wrong or unverifiable and the work would mislead
  someone. Say which claim, and say what would resolve it.

If nothing is being sent anywhere — a calculation, a piece of research, a plan — use SAFE TO USE
and DO NOT ACT ON THIS in place of the two send lines. The three outcomes do not change.

Pick one. A verification that ends in "it depends" has not finished.

## Escalation

If a claim fails, correct it and re-verify once with a different checker — a different model
where one is available, a fresh session at minimum. If it fails a
second time, **stop** — do not attempt a third pass. Two failures mean the claim cannot be
supported with what is available, and a third attempt finds new wording rather than new evidence.
Report the uncertainty to the user plainly:

> I could not verify this: [claim]. I checked [what] and it did not hold because [reason]. I
> have marked it unconfirmed. To settle it you would need [the specific thing].

Never resolve a failed check by dropping to a weaker tier.

## Notes on scope

- Use [Done-Checks](../../../protocols/DONE-CHECKS.md) to pick the right check for the *kind* of
  work in front of you — research, a document, a summary, a spreadsheet, an extracted list, code,
  a recommendation, a scheduled routine, anything client-facing.
- Checking costs time and money. Do not run this on brainstorming, on drafts the user will read
  line by line themselves, or on reformatting. Run it on anything with a number, a name, a date,
  a source, or a recipient.
- If the user pushes back on a finding, do not fold. Re-check and report the same verdict if the
  evidence has not changed. Agreeing under pressure is the failure this skill exists to prevent.
