---
name: grill-me
description: Interview the learner about their actual working week to find what is worth automating, then produce a ranked shortlist of skills and loops to build. Use when they say "what should I automate", "help me figure out where AI fits", "audit my work", "audit my workflow", "I don't know what to build", "what could you take off my plate", "interview me about my job", or when they are stuck choosing what to build first.
---

# /grill-me — the workflow audit

*An interview that turns a vague "AI should help with something" into three specific things to
build, in order. Takes 20 to 40 minutes of real conversation. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

---

## The prime rule

**Interview. Do not lecture.** Your job in this skill is to ask, listen, and push. You are not
explaining what AI can do; you are finding out what their week actually looks like, because that
is where the answers are and they cannot see it from inside.

Hard constraints on how you ask:

- **One question at a time.** Ask, then stop. Never send a numbered list of five questions.
- **Plain text only.** No multiple-choice widget, no form, no checkbox list, no "pick A, B, or C".
  A menu limits them to options you thought of, which defeats the point of the interview.
- **No suggestions until the interview is over.** Not one. The moment you start proposing, they
  start agreeing with you instead of telling you things.
- **Probe anything they mention twice.** A repeat is a signal. Stop the sequence and dig: what
  exactly, how often, what makes it annoying, what happens if it is late.

If they have already run [/whats-possible](../whats-possible/SKILL.md), read its entry in
`progress/LEARNER.md` first — that is where it logs — and do not re-ask what it already covered. Go deeper on mechanics instead: not "what do you
do" but "what happens between the email arriving and the file being saved".

---

## Step 1 — The interview, in this order

Work through these in sequence. Follow tangents when they open up — the tangent is usually better
than your next scripted question — but come back and finish the list.

**1. Monday.** "Walk me through last Monday. Not a typical Monday — last Monday, hour by hour,
as best you remember." Concrete beats representative. If they give you job-description language,
ask what they actually had open on screen.

**2. What recurs.** "What did you do last week that you will also do this week?" Then: "and the
week before that?" Recurrence is the single strongest signal in this whole interview.

**3. What they dread.** "What is on your list right now that you keep pushing to tomorrow?" Dread
usually means either tedium (automatable) or ambiguity (not automatable, but a checklist helps).
Find out which.

**4. What they redo.** "What do you produce that comes back needing changes?" and "what do you
rewrite from scratch each time even though it is basically the same document?" Rework is invisible
to most people until they are asked directly.

**5. What they wait on.** "Where do you sit idle waiting for someone else, or for something to
finish?" Waiting often hides a status-chasing task that can be handed off entirely.

**6. What breaks.** "What went wrong in the last month, and what did it cost to fix?" Then: "was
that a one-off or does it happen?" Recurring breakage is a verification problem, not an automation
problem — note it as such.

**7. What only they know how to do.** "What would fall over if you were out for two weeks?" This
finds the undocumented procedure living in their head. Even if it never becomes automated, writing
it down is usually the highest-value thing in the session — so offer to do exactly that before the
session ends: take the steps in their words into a plain file they own, and say where you put it.

Two more worth asking once the rapport is there:

**8. The retyping question.** "What do you copy from one place into another by hand?"
**9. The dashboard question.** "What do you check regularly just to see whether anything changed?"

Throughout, when an answer is vague, push once and be specific about the vagueness:

> "Reports" is not something I can build for. Which report, for whom, from what source,
> how often, and what happens if it is wrong?

---

## Step 2 — Play it back before you analyse

Summarise what you heard in under ten lines and ask what you got wrong. People correct a wrong
summary far more readily than they volunteer a missing fact. Wait for the correction.

---

## Step 3 — The table

Now produce the analysis. One row per candidate task, drawn from what they said, in their words.

| Task | How often | What makes it painful | What a good version looks like | Proposed skill or loop |
|---|---|---|---|---|
| Weekly client status note | Weekly | Rewritten from scratch; last week's context is in a different tool | Draft arrives mostly written, knows what happened last week, flags anything it was unsure of | Skill: `draft-client-update`, with a template and a memory file |
| Chasing three teams for status | 2 to 3 times a week | Pure waiting; nothing thought-provoking about it | A summary of who has and has not replied, ready when they sit down | Loop: scheduled check with an objective done-check |
| Month-end reconciliation | Monthly | Manual, error-prone, and errors are expensive | Deterministic comparison, exceptions listed for a human | Script first, model only for the exceptions |

Rules for filling it in:
- "What a good version looks like" must be observable. If you cannot tell whether it happened, it
  is not a done-check and the thing is not ready to build. See
  [Done-checks](../../../protocols/DONE-CHECKS.md).
- If a task should *not* be automated, put it in the table and say so in the last column. Judgment
  calls, relationship work, anything where being wrong is expensive and hard to reverse, and
  anything their employer has not sanctioned belong in that group. An honest "do not build this"
  is a good outcome.
- If plain code, a rule, or a saved search does the job, say that instead of proposing a skill.
  Deterministic beats probabilistic when both work.

---

## Step 4 — Rank and recommend exactly three

Rank by **recurrence against build cost**. High recurrence and low build cost first. Impressiveness
is not a criterion and neither is how much they would enjoy it.

Then recommend exactly three, in order, and give a one-sentence reason for each that references
something they actually said. The shape:

> **Start with 1.** <task> — you do it every week, the inputs are already in files you control,
> and if the draft is bad you just do not send it. Low stakes, fast payback.
> **Then 2.** <task> — same shape, but it needs <the thing that has to exist first>, which
> number one gives you.
> **Then 3.** <task> — bigger, and worth doing only once the first two have earned it.

Add one line naming the flashiest thing they mentioned and why it is *not* on the list yet. That
sentence does more for their judgment than the three recommendations do.

The first one you pick should be boring, reversible, and low-stakes. Trust is earned in an empty
parking lot, not on the highway — see
[10 Safety, privacy, and trust](../../../curriculum/10-safety-privacy-and-trust.md).

---

## Step 5 — Offer to build it now

End with a direct offer, not a summary:

```
Want to build number one right now? Give me the last real example of it - the actual
document, the actual inputs - and we will do it by hand once, then run /skillify to
turn it into something you can call by name.
```

If they say yes, hand straight to [/skillify](../skillify/SKILL.md). Do not start a second
interview and do not re-explain the plan.

Log the shortlist in `progress/DECISIONS.md` so the next session does not re-derive it, creating
that file with a `# Decisions` heading if it does not exist. Then append one session-log entry to
`progress/LEARNER.md` recording that the audit was run and which three came out of it — use the
entry template defined inside that file, not a shape of your own, and follow its rules about what
may be edited in place.

---

## Between sessions: the friction log

Tell them this before you finish, in your own words.

The interview is limited by what they can remember on the spot, and the most automatable moments
are the ones that annoy them for eleven seconds and then get forgotten. A friction log fixes that.
It is not a project. It is one line, written in the moment, in whatever they already have open —
a note file, the back of a notebook, a message to themselves:

```
<date> - <what I was doing> - <what made it annoying> - <how long it took>
```

Three rules that keep it alive: write it *while* annoyed, never after; one line, never a paragraph;
no editing and no tidying. A week of that beats an hour of trying to remember.

Then: bring it to the next `/grill-me` and it becomes the agenda. Anything that shows up three
times in two weeks goes straight to [/skillify](../skillify/SKILL.md) without needing an interview
at all.

---

## Failure modes for this skill

| If this happens | Do this |
|---|---|
| You start suggesting during the interview | Stop, apologise briefly, ask the next question. The suggestion will still be there in Step 3. |
| They give job-description answers | Ask what was actually open on their screen at 10am last Tuesday. |
| Everything they name is high-stakes and irreversible | Say so directly and look for the boring adjacent task instead. Do not build the risky one first because it is the only one on the list. |
| They cannot think of anything | Ask what they complained about most recently, to anyone, about work. That question almost always produces something. |
| The list comes out at fifteen items | Good. Still recommend exactly three. A long list they cannot start is worse than three they can. |
