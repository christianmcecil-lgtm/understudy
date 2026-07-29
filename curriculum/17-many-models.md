# 17 — Many Models

*Why a second model catches what the first one cannot, where that stops being true, and exactly how to do it today with two browser tabs. Read time: 25 minutes. This is the most important chapter after [Verification](04-verification.md), and it is the other half of it.*

---

## The whole chapter in one paragraph

A model's mistakes are not random. They have a shape, inherited from what it read, how it was
trained, and the habits of expression it settled into. When you ask that same model to check its
own work, you are asking the shape to notice itself — and it cannot, because the thing doing the
checking is the same thing that produced the answer, running the same patterns over the same
material. A fresh session of the same model helps, because it drops the context and the prior
commitment. A **different** model helps more, because it does not share the shape at all: things
that sat comfortably inside one model's sense of what is plausible can stick out sharply to
another. That is the argument, and it is a mechanism, not a slogan. The honest limit follows in
the same breath: two models trained on overlapping material can be confidently wrong in the same
direction, so agreement raises your confidence without ever proving you right.

You will meet this chapter twice on the mastery track in `progress/MASTERY.md` — once early, as
the principle sitting next to verification, and once later, as the practice. This file is both.

---

## How this fits with chapter 4

[Verification](04-verification.md) gave you a hierarchy of **kinds of check**:

| Rank | Kind of check |
|---|---|
| 1 | Deterministic — a count, a search, a script, a total |
| 2 | Checkable external fact — a link that opens, a quoted primary source |
| 3 | Independent judgment with a rubric — a separate session scoring against written criteria |
| 4 | The same model saying "looks good" |

This chapter does not replace that. It opens up **rank 3** and shows you that "independent" is not
one thing — it is a scale, and most people who think they have separated the checker from the
worker have separated them by about an inch.

Everything here is about *how independent your checker actually is*. And the whole ladder still
ends where chapter 4 said it ends: at a deterministic check, which beats every model-based rung
combined.

---

# PART ONE — WHY THIS WORKS

## 1. A model's errors have a shape

Start where chapter 4 started: with the machine.

A model produces text by predicting what comes next, over and over, from everything it has read
before. What it finds plausible is a direct product of three things:

- **What it was trained on.** An enormous body of writing, with particular emphases, particular
  gaps, particular repeated claims, particular communities over-represented and others barely
  present.
- **How it was trained afterward.** The post-training that shapes it into an assistant teaches it
  what a good answer looks like — including things like being helpful, being agreeable, filling
  a request rather than pushing back on it, and producing output that reads as complete.
- **Its habits of expression.** Every model has tics. Preferred structures. A characteristic level
  of hedging. A tendency to reach for certain framings, certain analogies, certain formats. You
  will start to recognise them.

The consequence is the important part. **Its mistakes are not noise scattered evenly around the
truth.** They cluster. A given model will tend to overreach in the same *kinds* of places, hedge
in the same places, over-trust the same categories of source, and fill the same kinds of gaps
with the same kinds of confident-sounding filler.

That is what people are pointing at, loosely, when they say a model has a "personality." It is
not personality. It is a **plausibility landscape** — a map of what feels right to that machine —
and errors happen where the landscape and reality disagree.

Hold that phrase. The rest of the chapter is built on it.

## 2. Why self-checking re-runs the same patterns

Now ask that model to check its own work.

Chapter 4 gave you the context-level reason: the session that produced the error still holds the
assumptions that made the error look right, with its own answer sitting right there as the most
recent thing in view. That is real and it is the bigger effect in practice.

But there is a deeper one underneath, and it survives even when you clear the context.

**The generator and the evaluator are the same machinery.** When the model asks itself "is this
right?", the operation it actually performs is something like "does this text look like the sort
of text that is right?" — which is a plausibility judgment, made by the same plausibility
landscape that produced the text in the first place. The answer it generated is, by construction,
sitting near a peak on that landscape. That is *why* it got generated. So when the same landscape
is asked to evaluate it, the answer scores well.

This is not laziness and it is not the model being dishonest. It is a structural fact about
asking one system to be both the producer and the judge. A person who genuinely misremembers a
date will re-derive the same wrong date when they check, using the same memory. They are not
being careless. They are consulting the only source they have, twice.

Two forces, then, stacked:

1. **Context contamination** — the reasoning that produced the error is still in view. Fixable by
   starting fresh.
2. **Shared plausibility landscape** — the evaluator's sense of "right" is the generator's sense
   of "right." *Not* fixable by starting fresh. Only fixable by changing the machine.

Almost everyone who has heard "use a fresh session to check" has fixed problem one and has never
been told problem two exists.

## 3. A fresh session of the same model: real, cheap, incomplete

Open a new chat. Paste in the artifact and the criteria, nothing else. Ask it to refute.

This genuinely works, and it is the single cheapest upgrade available to anyone reading this:
zero setup, zero cost beyond one more message, available in any tool on any device.

What it fixes:

- The prior answer is no longer in view, so it is not the thing being continued.
- The assumptions formed along the way are gone.
- The social commitment is gone — nothing in the new session has agreed to anything yet.
- The instruction can be adversarial from the first word, instead of arriving after a hundred
  turns of cooperative momentum.

What it does not fix: the landscape. Same model, same training, same tics, same blind spots. If
the original error was of the form *"this is the sort of thing that is usually true, so it is
true here"*, the fresh session runs the same reasoning and reaches the same comfortable place.

So: always do it. Never mistake it for independence.

## 4. A different model: what actually changes

A different model was trained on a different mixture of material, post-trained by a different
team with different judgments about what a good answer is, and settled into different habits. Its
plausibility landscape has peaks and valleys in **different places**.

That is the entire mechanism, and it is worth saying slowly: an error survives a check when it
sits somewhere the checker finds unremarkable. Move to a checker whose sense of "unremarkable" is
shaped differently, and some of those errors are now standing in the open.

You already believe this about people. You do not ask the person who drafted the contract to be
the only one who reads it — not because they are careless, but because they will read what they
meant. A second reader does not have the meaning in their head, so they see what is on the page.
Different training is the machine version of a different reader.

Some concrete places it shows up, described as categories rather than as claims about any
specific product:

- **One model reaches for a confident summary where another flags the ambiguity.** Different
  post-training, different default about whether it is better to answer or to say the question is
  underspecified.
- **One model's characteristic format hides a gap the other's format exposes.** If a model likes
  tidy parallel bullets, a missing case can quietly get absorbed into the parallelism. A model
  that prefers prose has to write the sentence, and the sentence is where the gap becomes visible.
- **They disagree about which sources are reliable**, because they read different amounts of
  different things.
- **They fill gaps differently.** When neither knows, they invent different plausible material —
  and two different inventions are easy to spot side by side, where one invention alone reads as
  a fact.

That last one is the highest-yield pattern in this whole chapter. **Where models disagree is a map
of where at least one of them is making something up.** You do not have to know which. You just
have to look there.

## 5. The independence ladder, weakest to strongest

Here it is in full. Push as far right as the stakes justify — and no further, because every rung
costs time.

One thing to fix in your head before you read the table, because it trips people: chapter 4's
**ranks** count *down* to the best check (rank 1 is the strongest), and this chapter's **rungs**
count *up* to it (rung 5 is the strongest). Two scales, opposite directions, same destination —
a check with no model in it. Rank 1 and rung 5 are the same thing.

| Rung | The check | What it actually removes | What it leaves untouched |
|---|---|---|---|
| 0 | **Same session, "does this look right?"** | Almost nothing | Everything. This is a second vote from the same voter, in the same room, holding the same notes. |
| 1 | **Same session, adversarial framing** ("find three things wrong; you may not conclude it is fine") | The agreeableness pressure and the permission to say yes | The context and the landscape. Still worth doing — it is one line and it sometimes lands. |
| 2 | **Fresh session, same model, artifact and criteria only** | The context, the prior answer, the accumulated assumptions, the social commitment | The plausibility landscape. Same blind spots, freshly applied. |
| 3 | **Different model, asked to review** | The landscape as well — genuinely different training, genuinely different tics | The politeness default. Asked to "review," most models still mostly agree. |
| 4 | **Different model, instructed to refute, given no sight of the reasoning** | Everything a model-based check can remove | Correlated error — see section 6. This is the ceiling for judgment-based checking. |
| 5 | **A deterministic check that involves no model at all** — a count, a search, a total, a link that either opens or does not | Judgment entirely | Nothing about the question you did not think to ask. But on the question you did ask, this is the end of the line. |

Three things to take from the table.

**The jump from rung 0 to rung 2 is free.** It costs one new chat window and one paste. If you
adopt nothing else from this chapter, adopt that.

**Rung 4 is the strongest thing a model can do for you.** Not "a very good model." Not "the newest
model." A *different* one, told to attack, working from the artifact alone.

**Rung 5 outranks all of it.** If the question is "did every client in the source list make it
into the summary," no amount of cross-model agreement beats printing both lists and comparing
them. Chapter 4 called this pushing the check up the hierarchy. This chapter's contribution is:
when you cannot get to rung 5, rung 4 is where you should be standing — and most people are
standing on rung 0.

---

## 6. The honest caveat: correlated error

This section is not a footnote. If you take the rest of the chapter and skip this, you will have
traded a loud failure mode for a quiet one.

**Different models are not independent.** They are trained on heavily overlapping material — much
of the same public writing, much of the same reference works, much of the same repeated claims.
Where that shared material is wrong, they can be wrong together, in the same direction, with the
same confidence, for the same reason.

The vocabulary for this is **correlated error**: two checkers failing in the same way because
their inputs overlapped. It is a real risk, not a theoretical one, and it is worst in exactly the
cases where you most want reassurance:

- **Widely repeated misinformation.** A claim that has been copied across thousands of pages will
  look right to anything that read those pages. Agreement here means "this is a popular belief,"
  which is not the same as "this is true."
- **Received wisdom in a field.** A rule of thumb that everyone in an industry states confidently
  and nobody has checked recently reads as consensus to every model.
- **Anything with a tidy, memorable, frequently-quoted form.** Compact claims travel. Travel
  creates repetition. Repetition creates plausibility. Plausibility is what a model is measuring.
- **Recent events, near or past the training cutoff.** Both models may be working from thin,
  early, or superseded material — and thin material is where confident agreement is cheapest.

So state the conclusion plainly and hold it:

> **Cross-model agreement raises your confidence. It does not establish correctness.**

And its corollary, which is the practical instruction:

> **A single deterministic check beats any number of agreeing models.**

Here is how to actually read the outcome of a cross-model check, which is more useful than a rule:

| What happened | What it tells you | What to do |
|---|---|---|
| Second model finds a real problem | You just avoided it | Fix it. This is the win, and one is enough to justify the pass. |
| Second model finds only cosmetic issues | Weak positive signal | Ship it if the stakes are low; go to a deterministic check if they are not. |
| Second model agrees enthusiastically and adds nothing | **Ambiguous, not reassuring** | Ask what would have to be true for it to be wrong. Then find one thing to check deterministically. |
| The two disagree flatly | At least one is wrong, and you have been handed the location | Go look. Do not pick a winner by vote. This is the most valuable outcome available. |
| Both hedge in the same place | Genuine uncertainty in the material, probably | Treat as `UNCERTAIN`, write it down as such, do not launder it into a fact. |

Note row three carefully. Warm agreement from a second model is the outcome that *feels* best and
carries the least information. Learn to be slightly suspicious of it. That is the whole skill in
this section.

And use the provenance vocabulary from [Verification](04-verification.md) when you record the
result: `SOURCED` when a check found the primary source, `INFERRED` when it survived cross-model
scrutiny but nothing external confirmed it, `UNCERTAIN` when the models split or both hedged. Two
models agreeing does not turn `INFERRED` into `SOURCED`. Only a source does that.

---

# PART TWO — HOW TO ACTUALLY DO IT

## 7. The two-tab method — zero setup, do it today

You do not need to install anything. You do not need a terminal. You need two browser tabs.

Most readers of this harness will never install a second command-line tool, and that is fine,
because this version captures most of the value.

**The setup:** two different assistants, from two different vendors, open side by side. If the
second one has a free tier, that is fine for this — the checker is reading one page and finding
fault, which is not a task that needs the strongest available engine. If you only have access to
one vendor today, do this with a fresh session of the same one. That is rung 2 rather than rung 4,
it is worth doing, and section 3 is honest about what it does not fix.

**The loop:**

1. Do the work in tab one, however you normally would.
2. When you have an artifact, get it into a clean form you can paste — the memo, the summary, the
   list, the plan, the code.
3. Write down the **criteria**: what this thing has to be true or good for. Two to five lines.
4. Go to tab two. Paste the refutation prompt below as one message, with your criteria and the
   artifact filled into the two placeholders at the bottom of it.
5. Read the findings as *candidates*, not verdicts. Triage them yourself.
6. Take the real ones back to tab one to fix. Then verify only what changed.

### The prompt to paste

Keep this. It is the workhorse of the chapter.

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

Three details in that prompt are doing real work, and it is worth knowing which:

- **"Written by someone else."** Removes the social cue that you want it to be good. You are not
  lying to a person; you are declining to hand a machine an irrelevant reason to be nice.
- **"You have not seen how it was produced and you should not ask."** Blocks the most common way
  people wreck their own check — see the next section.
- **"Find the three."** A quota. "Find any" permits zero. This is the same rule as chapter 4's
  adversarial framings, and it matters more here, because a fresh model with no context is exactly
  the kind of reader who will politely conclude it looks reasonable.

## 8. Paste the artifact and the criteria. Never the conversation.

This is the single most commonly botched part, and it is worth its own section because it undoes
everything else.

**The reasoning that produced the artifact is the thing you are trying to escape.** If you paste
the conversation — your prompts, its explanations, the justifications it gave along the way — you
have imported the original plausibility landscape into the second model by hand. It now reads
your first model's argument, finds it coherent (it *is* coherent; that was never the problem), and
agrees. You have paid for a second opinion and received an echo.

Give the checker exactly two things:

1. **The artifact.** The finished thing, on its own.
2. **The criteria.** What it must be true or good for.

Withhold: how it was made, why choices were made, what you were worried about, what the first
model said about its own work, and — usually — that an AI made it at all.

### Worked example: a bad handoff and a good one

Constructed illustration. The scenario is invented to show the shape; the point is the difference
between the two handoffs, not the subject matter.

**The situation.** You have used an assistant to produce a one-page recommendation: which of three
suppliers your team should use for a recurring service. It contains a comparison table, a
recommendation, and a short justification.

**The bad handoff** — what most people do:

```
I asked Assistant A to compare three suppliers for us and it recommended Supplier B.
Here's the whole conversation. Its reasoning was that B has better response times and
the price difference is small enough not to matter, and honestly that matches what I
was expecting. Can you sanity check this?

[pastes the entire chat, including the prompts and the model's explanations]
```

Count what went wrong in five lines:

- It named the conclusion up front, so everything after is read as evidence for a stated position.
- It supplied the reasoning, so the second model evaluates the argument rather than the situation.
- It said "that matches what I was expecting," which tells the checker what answer pleases you.
- "Sanity check" is a request for reassurance. It permits a yes, so it will get one.
- The whole chat is in view, so the second model is now working inside the first one's frame.

The reply will be a paragraph agreeing that B looks like a reasonable choice, plus one soft
suggestion about confirming pricing. You will feel verified. Nothing was verified.

**The good handoff:**

```
You are reviewing a supplier recommendation written by someone else. I did not write
it and I have no stake in which supplier wins. Judge only what is on the page.

Find the three problems most likely to cause real damage if this recommendation is
acted on. You are not allowed to conclude it is fine. For each: what is wrong, the
exact sentence it lives in, what would have to be true for it to be correct, and what
should be done about it.

Then separately: every claim in it you cannot verify from the document itself, and
every number without a source.

CRITERIA:
- The comparison must compare the three suppliers on the same terms.
- Every figure must have a stated source.
- The recommendation must follow from the comparison, not from anything unstated.
- Risks and downsides of the recommended option must be present, not just its upsides.

DOCUMENT:
[the one-page recommendation only]
```

Same second model. Different question. Now it has no conclusion to defend, no reasoning to find
coherent, no signal about which answer you want, and a quota it must fill. In this constructed
example it comes back with: the three suppliers are compared on response-time figures that two of
them define differently, so the column is not a like-for-like comparison; one price is stated
without a source; and the recommended option's one real downside is mentioned in a subordinate
clause and never weighed.

The first finding is the kind that gets caught in a meeting by someone who knows the industry.
That is the whole return on the exercise.

**The rule, in one line:** hand over the *what*, never the *why*.

## 9. Reading what comes back

A second model told to find three problems will find three, including on flawless work. You are
generating candidate objections, not verdicts. Your job is triage, and it takes about a minute:

- **Is it checkable?** If a finding can be settled by a count, a search, or opening a link, settle
  it. That is a rung-5 check falling into your lap — take it.
- **Does it survive contact with the source?** Go look at the underlying material before you act
  on it. Second models invent problems the same way first models invent facts.
- **Is it disagreement or is it error?** A checker objecting to a deliberate choice you made for
  reasons it cannot see is not a finding. It is the cost of withholding context, and it is a cost
  worth paying.
- **If all three are trivial**, that is itself a signal — a weak positive one. Note it, and if the
  stakes are high, go find a deterministic check anyway.

Do not send the findings straight back to the first model with "fix these." Read them first. You
are the one accountable for the artifact, and a checker that is wrong twice will happily talk a
compliant first model into making the work worse.

## 10. The step up: two command-line agents, one folder

If you do work in files — documents, spreadsheets, code, anything living in a folder on your
machine — there is a stronger version of this. It costs more setup, and it buys you something the
two-tab method structurally cannot reach.

Read [The terminal](16-the-terminal.md) first if the command line is new to you. You need much
less of it than you think.

**The pattern, in general terms:** several vendors ship command-line agents — assistants that run
in a terminal window, sit inside a folder, and can read and change the files in it. They are
broadly interchangeable for this purpose. You run **two of them from different vendors, pointed at
the same folder**: one does the work, the other reads the result as an independent auditor and is
not allowed to change anything.

That last constraint is the whole design. The auditor's only possible output is a report, so it
cannot quietly "fix" a finding into something that looks clean, and it cannot damage the work
while reviewing it. Finding and fixing stay separate — the same rule as chapter 4, enforced by
permissions rather than by asking nicely.

### Do not trust a tool list written here

Specific products, their names, their install commands, their permission flags, and their
capabilities change on a timescale of weeks. Anything printed in this file would be wrong by the
time you read it, and a confidently wrong instruction is worse than none — the same position
[Cost, models and effort](09-cost-models-and-effort.md) takes about prices.

So ask, live. Paste this into any current assistant:

```
I want to run two different command-line AI coding agents from two different vendors
on the same folder on my machine. One does the work; the second one only reads and
reviews, with no ability to write files or run commands that change anything.

Tell me, for right now:
1. Which command-line agents are currently available from different vendors, and what
   it costs to run each at a low level of use.
2. For each, the exact way to start it in read-only or plan-only mode — the real flag
   or setting name, not a description.
3. Whether any of them can be told to review a folder without ever writing to it, and
   how you would confirm that it actually cannot write.
4. What operating system differences I need to know about. I am on [your OS].

Give me the install command for each. If you are not sure something is current, say so
rather than guessing.
```

Then verify the answer the way this harness verifies everything: the tool either starts or it
does not, and the auditor either can write a file or it cannot. Test that on a scratch folder
before you rely on it.

### The read-only auditor pattern, concretely

1. **Put the folder under version control first.** A commit before the working agent starts is
   your floor to fall back to. See [Git](15-git.md). This is not optional if an agent is going to
   change more than a file or two.
2. **Terminal window one: the working agent.** It does the task in the folder, normally.
3. **Terminal window two: a different vendor's agent, same folder, read-only.** Start it in
   whatever mode that tool provides for reading without writing. Confirm the restriction by asking
   it to create a throwaway file and watching it fail.
4. **Give the auditor the review job, not the task.** It should not know how the change was made
   or why. Something close to:

```
You are reviewing changes made to this folder by someone else. You cannot modify
anything, and you should not try.

Read the current state of the files and the most recent change. Tell me:
1. The three most likely ways this change is wrong or incomplete. Quote the exact
   lines. You are not allowed to conclude it is fine.
2. Anything elsewhere in the folder that depends on what changed, and whether it still
   works. Name the files.
3. Anything the change claims to do that you cannot confirm it actually does.

Report only. Do not propose a rewrite.
```

5. **Triage the report yourself**, then take the real findings back to window one.

Point 2 in that prompt is where this pattern earns its keep and the two-tab method cannot follow.
The auditor can read the *whole folder*, so it can answer "what else touches this?" — the silent
side-effect failure from chapter 4's gallery. Pasting an artifact into a browser tab can never
catch that, because the rest of the folder was never in the conversation.

A note on cost and honesty: this is more setup, more windows, and more money than two tabs. It is
worth it for work that lives in files and gets built on. It is overkill for a memo.

## 11. When it is worth it

The decision rule is keyed to **stakes and reversibility** — not to how important the work feels
while you are doing it. Those come apart constantly. The thing you spent all afternoon on is not
automatically the thing most in need of a second model.

| The work | Check level |
|---|---|
| Brainstorming, exploring, thinking out loud | Nothing. Do not verify a brainstorm. |
| Something only you will read and act on, easily undone | Rung 1. One adversarial line in the same session. |
| Anything leaving your hands with a name, number, date, or link in it | Rung 2 minimum — fresh session — plus rung 5 on every fact. |
| Client, executive, public, or anything you will be asked to defend | Rung 4. Different model, told to refute, artifact only. |
| Irreversible, or touching a real system, real money, or real people | Rung 4 **and** rung 5 **and** a human who is not you. |

The rule of thumb, borrowed from chapter 4 and still correct: **verify in proportion to how hard
it would be to take back.**

One addition specific to this chapter. There is a fourth trigger beyond stakes and
reversibility — **novelty**. When you are working somewhere you cannot personally judge the
output, you have lost your own ability to sanity-check, which is the layer everything else was
sitting on. That is the moment to bring in a different model, even for work that is otherwise low
stakes. A new job is full of these moments. That is a large part of why this chapter is in the
harness.

## 12. Rotate the checker, and learn the blind spots

One habit turns this from a procedure into a skill: **rotate which model does the checking.**

Do not settle permanently on one work model and one checker model. Swap them. Use a third when you
have access to one. Over a few months of doing this on your own real work, something useful
happens — you start to recognise the characteristic shapes:

- which one over-claims when it does not know, and which one hedges everything into mush
- which one is better at spotting a structural flaw versus a factual one
- which one writes beautifully and reasons less carefully, and which is the reverse
- which one quietly drops the qualifier that mattered
- which one you personally are most likely to be fooled by, because its style matches your taste

That last one is the real prize. **You have blind spots too**, and they interact with the model's.
The model whose output you find most convincing is the one you check least carefully, which makes
it the most dangerous one for you specifically. You cannot notice that from the inside. You notice
it by rotating and watching which errors got past you.

Write these down as you find them. A few lines in your notes — see
[Memory and the second brain](06-memory-and-second-brain.md) — under a heading like "what each
model gets wrong on my work." Mark them `INFERRED`, because they are your pattern-matching from a
handful of cases, not measured results, and models change under you when they are updated. Revisit
the list occasionally and delete what no longer holds.

This is one of the few genuinely durable AI skills. Specific products change. The habit of knowing
what your tools are bad at does not.

## 13. Ways this goes wrong

Five failures worth recognising on sight.

**Pasting the conversation.** Covered in section 8, and it is far and away the most common. You
imported the reasoning you were trying to escape. The tell: the second model's reply summarises
your first model's argument approvingly.

**Treating agreement as proof.** Section 6. Two models agreeing is a weak positive signal that
gets weaker the more widely-repeated the claim is. The tell: you feel relieved and stop looking.

**Vote counting.** Asking three models and going with the majority. Truth is not a poll, and
correlated error means the majority can be correlated too. When models disagree, that is a *place
to go and look*, not a ballot to count.

**Using the strongest model as the checker and assuming that settles it.** Strength is not
independence. A strong model that shares training material with the first one shares the blind
spot. Different beats strong for this job.

**Letting the checker fix things.** The moment your checker starts editing, it begins optimising
for a clean-looking fix instead of an honest finding, and you have lost the separation you built
the whole arrangement to get. Checker reports. Worker fixes. You decide.

## 14. Where the machinery lives

- **[VERIFICATION-PROTOCOL.md](../protocols/VERIFICATION-PROTOCOL.md)** — the standing procedure,
  with the cross-model rung built into the tier ladder. Point your AI at it directly.
- **[DONE-CHECKS.md](../protocols/DONE-CHECKS.md)** — the catalog of what counts as proof of
  finished, by kind of work. Use it to find the checks that need no model at all.
- **[FAILURE-MODES.md](../protocols/FAILURE-MODES.md)** — the full gallery of failure shapes.
- **[verify-this](../.claude/skills/verify-this/SKILL.md)** — the skill that runs a verification
  pass for you, including the cross-model option and the exact text to paste elsewhere.
- **[adversary](../.claude/agents/adversary.md)** — the adversarial checker role. Strongest when
  it runs on a different model from the one that produced the work.
- **[Verification](04-verification.md)** — the parent chapter. Read it first if you have not.
- **[Subagents and swarms](08-subagents-and-swarms.md)** — fan-out and independent checkers inside
  one tool, which is a different axis of independence from this chapter's.
- **[The hype ledger](12-the-hype-ledger.md)** — for the marketing claims about which model beats
  which, all of which you should treat as unsupported until you see the method.

---

## Try this now

Take something an AI produced for you this week that you actually care about — a summary, a plan,
a recommendation, a draft you sent or nearly sent. If you have nothing, spend two minutes making
one on a topic you already know well, so you can judge the findings yourself.

Open **a different vendor's assistant** in a second browser tab. Not a new chat with the same one.
A different one. A free tier is fine if it has one. If you genuinely cannot get to a second
vendor right now, use a brand new chat with the same one and do the exercise anyway — you will see
a weaker version of the same effect, and you will have done rung 2 today instead of nothing.

Paste this as one message, with your criteria and the artifact filled into the two placeholders at
the bottom — the artifact alone, no conversation, no reasoning, no mention that an AI made it:

```
You are reviewing a document written by someone else. I did not write it and I have no
stake in it being good. You have not seen how it was produced and you should not ask.
Judge only what is on the page.

Find the three problems most likely to cause real damage if this is acted on. You are
not allowed to conclude it is fine, and you are not allowed to soften a finding.

For each: what is wrong, the exact sentence it lives in quoted, what would have to be
true for it to be correct, and what the author should do about it.

Then separately and briefly: every claim you cannot verify from the document itself,
every number without a source, and anything treated as settled that is a judgment call.

Do not rewrite it. Report only.

CRITERIA IT MUST MEET:
[2-5 lines: what this thing has to be true or good for]

DOCUMENT:
[paste the artifact only]
```

Now do the comparison that teaches the lesson. Go back to the **original** session and ask:
`Find the three biggest problems with what you gave me.` Put the two answers side by side.

Look for one specific thing: **a finding the second model made that the first one did not, even
when explicitly asked.** That is the plausibility landscape, visible on your own work. Once you
have seen it, you will not need to be persuaded of this chapter again.

Then write one line in your notes about what the second model caught, and check it against the
source before you believe it.

---

## What you should now be able to do

- Explain from the mechanism — not from folklore — why a model cannot reliably grade its own work,
  why a fresh session fixes the context problem but not the plausibility problem, and why a
  different model is the only thing that fixes the second.
- Place any check you are running on the independence ladder from rung 0 to rung 5, and push it at
  least one rung further right before you accept the output.
- Run a real cross-model check today with two browser tabs: artifact plus criteria, refutation
  framing, no conversation leaked, findings triaged rather than obeyed.
- Say out loud why agreement between two models is weaker evidence than one deterministic check,
  and recognise correlated error when a claim is popular, memorable, and everywhere.
- Describe the read-only auditor pattern well enough to ask your AI to set it up for you — and
  know to ask what tools are current rather than trusting any list, including this one.
