# 04 — Verification

*The one habit that separates people who get real value from AI from people who get plausible-looking garbage. Read time: 25 minutes. This is the most important chapter in the harness.*

---

## The whole chapter in one paragraph

An AI will hand you work that is confident, well-formatted, internally consistent, and wrong.
Not usually. But often enough that if you do not check, you will eventually put your name on
something that falls apart in front of someone who matters. The fix is not "be careful" and it
is not "use a better model." The fix is a *procedure*: never let the thing that did the work
decide whether the work is good, and never accept the word "done" without a receipt attached.
Everything else in this harness — skills, memory, loops, agents — is machinery for producing
output. This chapter is the machinery for trusting it.

If you read one chapter and skip the rest, read this one.

---

## 1. Why the AI cannot grade its own work

Start with the mechanism, because the mechanism tells you what to do.

When a model produces an answer, it does so from a particular context: the conversation so far,
the files it read, the assumptions it formed along the way. If it made an error, that error came
from somewhere — a misread line, a wrong assumption, a source it trusted too much, a step it
skipped because it seemed obvious.

Now ask that same session, in that same context, "is this correct?"

It is re-reading the same evidence, holding the same assumptions, with its own prior answer
sitting right there in front of it as the most recent and most heavily weighted thing in view.
**The context that produced the error also contains the reason the error looked right.** So the
self-check tends to reconstruct the same reasoning and arrive at the same conclusion. You have
not added a check. You have added a second vote from the same voter.

There is a second force stacked on top. Models are trained to be helpful and agreeable, and
"does this look good?" has an easy, pleasant, socially-correct answer. You are not asking a
neutral question. You are offering it a yes and waiting.

So the two rules fall straight out of the mechanism:

1. **Separate the checker from the worker.** A different session, ideally with a fresh context,
   given only the artifact and the criteria — not the reasoning that produced it. A different
   *model* is stronger still, for reasons in section 3.
2. **Ask it to refute, not to review.** Give it a job that only succeeds if it finds something.

This is not a Claude-specific quirk or a temporary limitation. It is what you should expect from
any system that generates text by continuing a context. Design around it.

> Honest framing: people online will tell you verification "doubles" or "triples" your quality.
> Those numbers are made up — nobody has run that study on your work. What is defensible is the
> mechanism: an independent reader with an instruction to find fault catches a category of error
> a self-check structurally cannot. That is a reason, not a multiplier. Treat any precise
> percentage claim about AI quality as marketing until you see the method. See
> [The hype ledger](12-the-hype-ledger.md).

---

## 2. Evidence before done

Here is the most useful sentence in this harness:

> **"Done" is not a claim. It is a receipt.**

An AI saying "I've completed the analysis" is a sentence. A sentence costs nothing to produce and
carries no information about whether the analysis exists, ran, or is correct. What carries
information is the *artifact*: the actual number, the actual quote, the actual link that opens,
the actual screenshot, the actual row count, the actual file path you can open yourself.

Get in the habit of never accepting the first kind and always demanding the second.

### The receipt table

| Instead of accepting | Demand |
|---|---|
| "I checked the sources." | The URL for each source, and the sentence you are relying on, quoted. |
| "The numbers add up." | The arithmetic shown, or the query, or the total printed. |
| "I updated the document." | The file path, and the before/after of the section you changed. |
| "There are 14 clients in that category." | The list of 14, by name. |
| "This matches the policy." | The policy clause, quoted, with where it lives. |
| "It works now." | What you ran, and the actual output it produced. |
| "I searched and found nothing." | What exact search terms were used, and where. |

Notice the pattern. Every right-hand cell is something you could, in principle, check yourself in
under a minute. That is the test for whether you have asked for a real receipt: **can a
non-expert falsify it quickly?** If not, it is not a receipt; it is a nicer-sounding claim.

### Exact phrasings to keep

Copy these. Use them verbatim. They are boring on purpose.

```
Before you tell me this is done, show me the evidence. For each claim you made,
give me one of: the exact quote and its source link, the number and where it came
from, or the file path and the lines you changed. If you cannot produce evidence
for a claim, delete the claim and tell me you deleted it.
```

```
List every statement in what you just gave me that you cannot back with a source
I could open. Do not defend them. Just list them.
```

```
You said it works. What exactly did you run, and what exactly did it print?
Paste the real output, not a description of the output.
```

```
Give me the three weakest parts of what you just produced, ranked. For each one,
say what would have to be true for it to be wrong.
```

That last one is worth keeping in your head. "What would have to be true for this to be wrong"
converts vague unease into a checkable question.

---

## 3. The done-check hierarchy

Not all checks are equal. There is a clear ordering, and your job on every task is to push the
check **as far up this list as it will go**.

| Rank | Kind of check | What it looks like | Why it ranks here |
|---|---|---|---|
| 1 | **Deterministic** | A count, a search, a script, a total, a comparison that either matches or does not | No judgment involved. Same input, same answer, every time. Cannot be talked into agreeing. |
| 2 | **Checkable external fact** | A live link that opens to the claimed content; a quoted primary source; a real record in a real system | Judgment is involved only in reading. The fact exists outside the AI and outside you. |
| 3 | **Independent judgment with a rubric** | A different session, fresh context, scoring against named written criteria | Judgment, but constrained and separated. Reproducible enough to argue with. |
| 4 | **The same model saying "looks good"** | Exactly what it sounds like | Almost no information. This is the level most people stop at. |

Rank 4 is not worthless — it catches the occasional obvious blunder. But it is the floor, not the
standard, and it is where nearly everyone lives.

### Rank 3 has its own scale inside it

"A different session" is the minimum, not the goal. Weakest to strongest:

1. The same session, asked to check itself. This is rank 4 wearing rank 3's clothes.
2. A different session of the same model, fresh context, given the artifact and the criteria.
3. **A different model**, given the artifact and the criteria and told to refute it.

The third is the strongest check any model can give you, and the reason is mechanical: a model's
mistakes are patterned rather than random, so a fresh session of the same model still finds the
same things plausible. A different model has different patterns, so what slipped past one can
stick out to the other.

It is not a guarantee. Models trained on overlapping material can be confidently wrong in the same
direction, which is why rank 1 still beats any number of agreeing models. The full argument, that
caveat, and how to run a cross-model check today with two browser tabs are in
[Many models](17-many-models.md).

### How to climb the ladder

The skill is spotting that a level-3 or level-4 check can be *converted* into a level-1 or
level-2 one. Some conversions worth memorising:

- "Did you include all the regions?" -> "Print the list of regions you included, and the list from
  the source file. Show me any name in one and not the other." (3 -> 1)
- "Is the summary faithful?" -> "For each bullet in the summary, quote the sentence in the source
  it came from. Flag any bullet with no matching sentence." (3 -> 2)
- "Are these citations real?" -> "Open each link. Paste the page title and the sentence that
  supports my claim. Mark any link that 404s or does not contain the claim." (4 -> 2 — but see
  the warning about browsing in section 7, stage 2, before you trust the answer)
- "Does the tone work?" -> mostly stays at 3, and that is fine. Use a rubric (section 6).
- "Did the change break anything?" -> "List everything else in the file that reads from what you
  changed. For each, say whether it still works and how you know." (4 -> 2, and sometimes -> 1)

A useful mental habit: whenever you are about to accept a judgment, ask **"is there a count, a
search, or a link that would settle this instead?"** Surprisingly often there is, and it takes
one more sentence to ask for it.

This connects to a broader principle the harness repeats: prefer the deterministic mechanism over
the probabilistic one wherever the deterministic one exists. A search either finds the string or
it does not. That property is worth a lot.

---

## 4. Adversarial framing, not review framing

Two prompts. Same document. Radically different results.

```
Is this good?
```

```
Find three things wrong with this. You are not allowed to say it is fine.
```

The first invites agreement, and you will usually get it, dressed up with a compliment and two
soft suggestions. The second sets a job that is only complete when problems exist on the page.

The reason is the same agreeableness pressure from section 1. **A question that permits a yes
tends to get one.** So write questions that do not permit a yes.

### Framings ranked, weakest to strongest

| Framing | What you tend to get |
|---|---|
| "Does this look right?" | Yes, with garnish. |
| "Any issues?" | Two cosmetic suggestions. |
| "Review this critically." | Slightly sharper garnish. |
| "Find three things wrong with this." | Three candidates, some of them real. |
| "Your job is to prove this is wrong. What is the strongest case against it?" | Genuine attack surface. |
| "A colleague is going to challenge this in a meeting. Write their strongest objection." | The objection you were not ready for. |

### Rules for adversarial checks

- **Give it a quota.** "Find three" beats "find any." A quota removes the option of finding none.
  You then triage the three yourself; if one is real, the quota paid for itself.
- **Forbid the escape hatch.** Add "you are not allowed to conclude it is fine" to prevent the
  polite exit.
- **Do not show it your reasoning.** Give the artifact and the criteria only. Paste your
  justification too and you have contaminated the fresh context with the exact assumptions you
  wanted tested.
- **Do not tell it you wrote it.** "Here is a draft I received" beats "here is my draft." You are
  removing a social cue, not lying to a person.
- **Separate finding from fixing.** The checker reports; it does not edit. A checker that fixes
  starts optimising for a clean-looking fix rather than an honest finding.

One caution, honestly stated: adversarial framing also produces *false* findings. A model told to
find three problems will find three, including on a flawless document. You are generating
candidate objections, not verdicts — your job is triage. If all three are trivial and nothing
lands, that is itself a signal.

---

## 5. Confidence and provenance: stop inferences from wearing a fact's clothes

The most dangerous sentences in AI output are not the wrong ones. They are the *plausible
inferences written in the same voice as the sourced facts*.

If a document says "the renewal window closed in March" and "the renewal window likely closed in
March, based on the pattern in the previous two contracts," you would treat those differently.
The problem is that AI output tends to flatten both into the first form. Uniform confident prose
is the default register, and it hides the seam between what was read and what was guessed.

The fix is cheap. Make it tag every claim. Three tags, and the same three everywhere in this
harness — every other file that talks about provenance means these.

```
Rewrite what you just gave me with a tag on every factual claim:

[SOURCED] — you read this in a document or page. Include the source.
[INFERRED] — you concluded it from something you read. Say from what.
[UNCERTAIN] — you are working from general knowledge rather than anything in front of
you, you are not confident, the sources disagree, or you filled a gap with a reasonable
default. Say which of those it is, and if it was a default, say what default you used.

Do not change the content. Only tag it. If a sentence mixes two kinds, split it.
```

Three bins is the whole vocabulary, and the third one is deliberately broad. A gap filled with a
sensible default sounds like the mildest item on the list. It is the most dangerous one, so it
goes in `UNCERTAIN`, where you will actually look at it.

Two things happen, and both are useful. First, you get a map of where the risk lives, so you can
spend your limited checking attention on the `[INFERRED]` and `[UNCERTAIN]` lines instead of
re-reading everything. Second, and more interesting: **the act of tagging often changes the
content.** A claim that cannot survive being labelled sourced gets downgraded, hedged, or dropped
during the rewrite. Sorting output into bins is a more constrained task than self-assessment,
which is why it works better than "how confident are you?" — the same reason a checklist beats
a vibe.

Keep the tags in anything that will be read later, especially anything that goes into your notes.
An untagged inference filed away today becomes a "fact you already established" three weeks from
now, and then it gets built on. That is how a set of notes quietly poisons itself.

Related principle, worth stating plainly: **mark AI-authored material as AI-authored when you
file it.** Not out of guilt. Because six months later you will want to know which of your notes
came from a source and which came from a model, and by then you will not remember.

---

## 6. When judgment is genuinely subjective: write the rubric first

Some questions have no deterministic answer. Is this email the right tone for a nervous client?
Is this summary useful to someone who missed the meeting? Is this proposal persuasive?

You cannot count your way out of these. But you can do much better than "does this seem good."

**Write a rubric.** Named criteria, each with what a good and bad version looks like. Then have a
*different* session score the artifact against it, without having seen the artifact get made.

A rubric does three things at once. It forces you to say what you actually want before you look
at the work, which is when your judgment is least biased. It makes the score reproducible enough
to disagree with. And it gives the checker something to fail against, which is what section 4 was
about.

### A rubric template

```
Score the attached draft against these criteria. For each: a score 1-5, the single
sentence from the draft that most supports the score, and the one change that would
move it up a point.

1. AUDIENCE FIT — reads as written for a busy person with no background in this,
   not for an insider. Bad: assumes context. Good: gives context in one clause.
2. LEADS WITH THE ANSWER — the thing the reader needs is in the first two sentences.
   Bad: builds up to it. Good: states it, then supports it.
3. NO UNSUPPORTED CLAIMS — every assertion is either sourced or visibly hedged.
4. ACTIONABILITY — the reader knows exactly what they are being asked to do, by when.
5. LENGTH DISCIPLINE — nothing that could be cut without losing meaning.

Do not give an overall score. Do not say it is good. Score each criterion separately,
and be harder on it than you think is fair.
```

Notes on making rubrics that work:

- **Three to six criteria.** More than that and the scoring becomes noise.
- **Each criterion needs a bad example**, not just a good one. "Clear" is not a criterion.
  "Does not use a term it has not defined" is.
- **Ban the overall score.** An overall score lets the checker average away a serious failure on
  one axis. You want to see the one 2 among the fours.
- **Ask for the supporting sentence.** This forces the score to be anchored to actual text and
  makes bluffing visible.
- **Reuse the rubric.** A rubric you keep is a small asset that compounds — it belongs in a
  skill. See [Skills](05-skills.md).

---

## 7. Worked example: verifying a piece of research, start to finish

This is the whole chapter applied to one realistic task. Follow the shape, not the specifics.

> **Read this as illustrative.** The task, the AI's output, and the findings below are a
> constructed example built to show the sequence of moves. The figures inside it are stand-ins,
> not real data about any real market. What is real is the procedure.

**The task.** You are new. Your manager asks for a short briefing on how competitors in your
sector handle a particular customer-onboarding step, to be used in a meeting Thursday.

### Stage 1 — Ask, with the receipt requirement built in from the start

Do not ask for research and then ask for sources afterward. Ask in a way that makes the
unsupported version impossible to produce.

```
Research how the four largest companies in [sector] handle [the onboarding step].
For each company:
- what they do, in two sentences
- the primary source (their own documentation, help centre, or filings) with a link
- the exact sentence from that source that supports your description
- a confidence tag: SOURCED, INFERRED, or UNCERTAIN

If you cannot find a primary source for a company, say so and leave that entry blank.
Do not fill gaps with what is typical for the industry. A blank is more useful to me
than a guess.
```

**What comes back, in shape:** four entries. Three with links and quotes. One marked
`UNCERTAIN — no primary source found; the description below is inferred from a third-party
comparison article.` Plus, in the example, a summary paragraph asserting a percentage about
industry adoption with no source attached.

That last item is the interesting one, and it is typical. The per-company discipline held because
you specified the format; the summary paragraph slipped back into unsourced confident prose
because you did not specify a format for it. **Structure is what holds; general instructions to
be careful do not.**

### Stage 2 — The yes-or-no checks first (ranks 1 and 2)

Before any judgment, do the checks that have a yes-or-no answer: does the link open, and is the
quoted string actually on the page.

```
List every URL you cited. For each one: open it, and tell me (a) the page title,
(b) whether the sentence you quoted appears on that page word for word, and
(c) if not, what the page actually says on that point.
Mark each URL as VERIFIED, MOVED, or NOT FOUND.
```

**What comes back, in the example:** two verified. One where the quoted sentence does not appear
on the page word for word — the page says something adjacent but weaker. One link that resolves
to a general help-centre index rather than the specific article, so the claim is now unsupported.

This is the highest-value stage in the whole process, and no judgment was involved at any point.
You just made it go and look.

> **First, check that it can actually look.** Not every AI setup can open a web page. If yours
> cannot browse and you ask it to open a link anyway, it will not say "I cannot do that" as often
> as you would like — it will produce a page title and a quote that read exactly like a real
> check. That is this chapter's own worst failure mode aimed at you. So before you rely on stage
> 2, ask: `Can you open web pages in this session? Answer yes or no, then open
> [any URL you know the contents of] and tell me the first heading on it.` If the answer does not
> match what you know is on that page, the tool cannot browse, and every link in the document is
> yours to open yourself. That is still a rank-2 check. It is just your click instead of its.

### Stage 3 — The unsourced claim gets isolated (rank 2)

```
Your summary paragraph states a percentage for industry adoption. Where did that
number come from? Give me the source and the sentence. If it came from your general
knowledge rather than a document you read in this session, say that explicitly and
remove the number from the briefing.
```

**What comes back, in the example:** the number came from general knowledge, not from anything
read during the session. It gets removed. What replaces it is a sentence describing the direction
without the false precision.

Learn to spot this shape. **A specific number with no source attached is one of the most reliable
warning signs in AI output.** Numbers read as evidence, which is exactly why an unsupported one
does more damage than an unsupported adjective.

### Stage 4 — Fresh adversarial pass (rank 3, done properly)

New session. New context. It has not seen the research get made, and it does not know you
commissioned it.

```
Below is a briefing document someone is planning to present in a meeting on Thursday.
Your job is to find the three problems most likely to embarrass the presenter if a
well-informed person challenges them. You are not allowed to conclude it is fine.

For each problem: what is wrong, the exact sentence it lives in, and what the presenter
should say instead.

[paste the briefing only — not the prompts, not the sources, not this conversation]
```

**What comes back, in the example:** three findings. One is real and serious — the briefing
compares two companies on a metric they define differently, so the comparison is not meaningful.
One is real but minor — a date is stated as current when the source is over a year old. One is a
miss — the checker objects to a framing choice that is deliberate and correct.

One serious catch out of three. Do not read that ratio as a rate — it is what this constructed
example was built to show, not a measured yield. The point is the shape of the win: you are not
looking for a checker that is always right. You are looking for one that surfaces the objection
you would otherwise have met in the room. One real finding justifies the pass.

### Stage 5 — Fix, then re-verify only what changed

Send the two real findings back to the original session to fix. Then:

```
Show me the before and after for each of the two changes, and nothing else.
```

Small point, big habit: **verify the diff, not the whole document again.** Re-reading everything
is expensive, and it invites the AI to quietly rewrite parts you had already checked.

### Stage 6 — The honest residue

Last move before you put your name on it.

```
What in this briefing is still unverified, thin, or taken on faith? List it plainly.
Do not reassure me. I want to know what I am carrying into the room.
```

**What comes back, in the example:** the fourth company's entry is still inference from a
third-party article, not a primary source. That is fine — *now you know*, and you can say "I
could not confirm this one directly" in the meeting, which makes you look careful rather than
caught out.

The six stages add a modest amount of time to a task like this — you are mostly waiting on the AI
to go and look. The version without them is faster and hands you a document containing a broken
link, an invented percentage, and a comparison that does not hold. That trade is the entire value
proposition of this chapter.

---

## 8. The card: three questions to ask any AI output

Keep this where you can see it. Applies to research, drafts, summaries, code, plans, anything.

```
+-------------------------------------------------------------------+
|  THREE QUESTIONS FOR ANY AI OUTPUT                                 |
|                                                                    |
|  1. HOW WOULD I KNOW IF THIS WERE WRONG?                           |
|     If you have no answer, you have no verification -- you have    |
|     a feeling. Find the check before you accept the output.        |
|                                                                    |
|  2. WHAT IS THE RECEIPT?                                           |
|     The link, the quote, the count, the file path, the output.     |
|     Not the claim. If you cannot check it in a minute, it is not   |
|     a receipt.                                                     |
|                                                                    |
|  3. WHO CHECKED IT, AND WERE THEY THE ONE WHO WROTE IT?            |
|     If the writer is the checker, nobody checked it. Fresh         |
|     context, instruction to refute, no sight of the reasoning.     |
+-------------------------------------------------------------------+
```

If you only ever do question 1, you are already ahead of most people using these tools.

---

## 9. Failure gallery

Four failures you should be able to recognise on sight. These are the shapes that recur.

### The confident wrong citation

**What it looks like:** a source, an author, a title, a year, a page number. Formatted correctly,
completely plausible. It does not exist — or it exists and says something different, or it exists
and simply does not contain the sentence attributed to it.

**Why it happens:** a well-formed citation is a *pattern*, and producing text that fits a pattern
does not require checking facts about the world.

**The tell:** you cannot open it in one click, or you open it and the quoted sentence is not on
the page.

**The check:** rank 2. Open every link. Search the page for the quoted string. Boring, and the
highest-yield check available to a non-technical person.

### The code that compiles and silently breaks something else

**What it looks like:** you asked for a change. The change was made. It works. Three weeks later
a report comes out wrong, because the thing that got changed was also being read by something
nobody mentioned.

**Why it happens:** the AI verified what you asked about. "It works" meant "the thing I was
looking at works."

**The tell:** the verification only ever exercised the new behaviour.

**The check:** ask what *else* touches what changed. "List everything that reads from or depends
on what you just modified. For each, tell me whether it still behaves the same and how you know."
Then check the running system, not the description of the change. This shape is not limited to
code — it appears whenever you edit a shared spreadsheet, a template, or a process document.

### The summary that drops the one caveat that mattered

**What it looks like:** a genuinely accurate summary in which every sentence is true. The source
said the approach works *provided the data is cleaned first*. The summary says the approach works.

**Why it happens:** summarising is compressing, and compression drops qualifiers before it drops
claims. Qualifiers are grammatically peripheral. They are also, frequently, the entire point.

**The tell:** the summary is more confident than the source. If the original hedged and the
summary does not, something was thrown away.

**The check:** "List every condition, exception, caveat, or limitation in the source, whether or
not it made it into the summary. Then tell me which ones you dropped and why." Ask this of any
summary you are going to act on.

### The plausible statistic with no source

**What it looks like:** a sentence of the form "roughly 40% of firms in this space have moved to
the newer model" — that figure is invented here purely as an illustration, which is the point. No
citation. Reads like something you have heard before. It may even be approximately true.

**Why it happens:** a number in that slot is what the sentence pattern expects. It is generated
to fit, not retrieved to report.

**The tell:** precision without provenance. Especially round-ish numbers in summary paragraphs,
and in the parts of a document where you did not impose a format.

**The check:** "Every number in this document: where did it come from? Anything you cannot source
to a document you actually read, remove it and tell me you removed it." Then confirm the
survivors have links that open.

**And it is contagious.** An unsourced number that gets into your notes becomes a sourced number
next month, because the source is now your notes. Kill it at ingest. That is why section 5 exists.

---

## 10. Proportion: when not to do all this

Verification has a cost, and pretending otherwise is its own kind of dishonesty. Scale the check
to the stakes and the reversibility.

| Situation | Check level |
|---|---|
| Brainstorming, throwaway drafting, thinking out loud | None. Do not verify a brainstorm. |
| Something only you will read and act on | Question 1 from the card. Ten seconds. |
| Anything with a name, number, date, or link in it that leaves your hands | Rank 1-2 checks on every fact. Non-negotiable. |
| Anything going to a client, an executive, or a public channel | Full sequence, including a fresh adversarial pass. |
| Anything irreversible, or affecting a real system or real money | Full sequence, plus a human who is not you. |

The rule of thumb: **verify in proportion to how hard it would be to take back.** A wrong idea in
a brainstorm costs nothing. A wrong number in a board deck costs your credibility, and you get
one of those.

---

## 11. The machinery

This chapter is the *why* and the *how you say it*. The runnable procedure lives elsewhere in
the harness so you can hand it to an AI directly:

- **[VERIFICATION-PROTOCOL.md](../protocols/VERIFICATION-PROTOCOL.md)** — the standing procedure:
  worker/checker separation, the adversarial pass, the receipt requirement, what the checker is
  and is not allowed to do. Point your AI at this file and it will run the sequence.
- **[DONE-CHECKS.md](../protocols/DONE-CHECKS.md)** — the catalogue of done-checks by task type,
  with the hierarchy from section 3 applied to specific kinds of work.
- **[FAILURE-MODES.md](../protocols/FAILURE-MODES.md)** — the fuller gallery, including failure
  shapes not covered here.
- **[The loop](03-the-loop.md)** — why a loop is only as good as its done-check, and why an
  unverifiable done-check produces a loop that runs for hours and delivers nothing.
- **[Skills](05-skills.md)** — how to turn a verification you keep repeating into something that
  runs itself.
- **[PROMPT-PATTERNS.md](../reference/PROMPT-PATTERNS.md)** — the phrasings from this chapter in
  copy-paste form, alongside the rest.

---

## Try this now

Take something an AI produced for you in the last week — any research, summary, or draft. If you
have nothing to hand, make one first: ask any AI for a half-page briefing on a topic you already
know well, and ask it to include specific figures and sources. That takes two minutes and works
better for this exercise, because you will be able to judge the findings yourself.

Then open a **brand new chat** (this matters: fresh context, no memory of how it was made) and
paste this, followed by the artifact:

```
Below is a document someone is planning to send to their manager tomorrow. I did not
write it and I have no stake in it being good.

Your job is to find the three problems most likely to embarrass them if a well-informed
person challenges it. You are not allowed to conclude it is fine, and you are not
allowed to soften your findings.

For each of the three:
1. What is wrong.
2. The exact sentence it lives in, quoted.
3. What would have to be true for it to actually be correct.
4. What they should do about it.

Then, separately: list every factual claim in the document that you cannot verify from
the document itself, and every number that appears without a source.

Do not rewrite the document. Do not fix anything. Report only.

---
[paste the document here]
```

Read the three findings. Some will be wrong; ignore those. Notice the one that lands — and notice
that the session which produced the original never mentioned it.

Then do the second half, which takes one minute: go back to the *original* session and ask
`Was there anything wrong with what you gave me?` Compare the two answers. That comparison is the
lesson, and you will not forget it once you have seen it on your own work.

---

## What you should now be able to do

- Explain, from the mechanism rather than from folklore, why a session cannot reliably check its
  own work — and set up a separate checker with a fresh context and an instruction to refute.
- Refuse "done" as a claim and ask for the specific receipt that would settle it: the link, the
  quote, the count, the path, the actual output.
- Look at any done-check and say which rank it is on the hierarchy, then push it up at least one
  level by converting a judgment into a count, a search, or a source.
- Spot the four recurring failure shapes — the fake citation, the silent side effect, the dropped
  caveat, the unsourced statistic — before they leave your hands, and tag every AI-derived claim
  as sourced, inferred, or uncertain so the next reader (usually you) knows what they are holding.
