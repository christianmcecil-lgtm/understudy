# What the model actually is

*A correct, plain-English mental model of the thing you are talking to — and the difference between the model and the harness around it. Read time: 18 minutes.*

---

## The one-sentence version

It predicts the next chunk of text, extremely well, having read an enormous amount of written
material.

That is not a simplification for beginners. That is the machine. Everything impressive it does
and everything infuriating it does both fall out of that one sentence, and if you hold it
firmly you will stop being surprised — which is the entire point of this file.

---

## What "predicts the next chunk of text" actually means

Take a sentence and stop partway through:

> The capital of France is ___

You know what comes next. So does the model, and for a related reason: it has seen that pattern
completed thousands of times. It does not look up France in a database. It produces a
probability across every possible next chunk of text, and "Paris" comes out far ahead.

Now a harder one:

> The quarterly revenue miss was driven primarily by ___

There is no single right answer here. There is a spread: "lower than expected demand", "a
delay in the enterprise deal", "currency headwinds", and hundreds of other plausible
continuations. The model picks from that spread. That is the same operation as the France
example — the machine did not change. Only the confidence distribution changed.

Two things follow immediately, and they are the two things everyone gets wrong.

**First: it is doing this one chunk at a time, over and over.** It writes a chunk, adds it to
what it has, and predicts the next one from the new total. A thousand-word answer is a thousand
of these steps, each one conditioned on everything before it. That is why an answer that starts
badly usually keeps going badly — it is now predicting the continuation of a bad answer. It is
also why asking it to think step by step before answering genuinely works: earlier chunks are
the input to later chunks, so reasoning out loud puts better material into its own input.

**Second: "chunk" is not "word."** The unit is called a token — roughly three quarters of a
word on average, sometimes a whole word, sometimes a fragment or a punctuation mark. You will
see the word "token" constantly, mostly in the context of cost and limits. That is all it means:
a piece of text, a bit smaller than a word. See [The context window](02-the-context-window.md)
for why the count matters.

---

## Why that is genuinely a form of understanding

There is a dismissive version of the one-sentence explanation: "it is just autocomplete, it does
not really understand anything." Do not adopt it. It will make you worse at using the tool, and
it is not honest about what you can observe.

To predict the next chunk of text well across an enormous variety of material, a system has to
build internal machinery that tracks a great deal: who "she" refers to three paragraphs back,
whether the argument being made is valid, what tone a legal letter takes versus a text to a
friend, what a function in a piece of code is trying to do, and what usually follows from a
premise. You cannot predict a physics explanation accurately without something that behaves an
awful lot like a model of physics.

Whether that constitutes "real" understanding is a genuinely open philosophical question and
this harness will not pretend to settle it. What is not open is the practical question. For the
purposes of your job:

- It can hold a complicated situation in mind and reason about it.
- It can apply a principle you gave it to a case it has never seen.
- It can tell you the flaw in your own plan.
- It can translate between domains — explain a technical thing to a lawyer, or a legal thing to
  an engineer — which requires understanding both sides well enough to re-map them.

Treat that as real capability. Do not talk yourself out of using it well because of an argument
about the word "understand."

---

## Why the same machinery makes it confidently wrong

Here is the uncomfortable half of the same fact.

The machine always produces a next chunk. There is no internal state that corresponds to "I do
not have this." When the answer is well-represented in what it has read, the prediction is
sharp and correct. When it is not — an obscure fact, a private document it has never seen, a
number that exists only in your company's spreadsheet, an event after its training ended — the
machine does not stop. It still produces the most plausible-looking continuation.

Plausible-looking is the key phrase. What comes out has the exact shape of a correct answer:
right format, right tone, confident phrasing, plausible-sounding specifics. It looks like
knowledge because it was produced by the same process that produces knowledge. The
confidence in the writing is a property of the writing style, not a report on how sure it is.

This is the thing people call **hallucination**, and here is the most important sentence in
this file:

> Hallucination is not a bug that will be patched out in a future version. It is what a
> prediction engine does when the answer is not within reach.

It can be reduced. Better models do it less. Giving it the actual document, or a search tool,
or your real database moves an enormous number of questions from "not within reach" to "within
reach", and that is exactly why the [Tools and MCP](07-tools-and-mcp.md) chapter exists. But
the mechanism does not go away, because the mechanism is the same one that makes the tool
useful in the first place.

Which leads to the load-bearing conclusion of this whole harness:

**Because you cannot tell a confident correct answer from a confident wrong one by looking at
it, verification cannot be optional. It has to be built into how you work.** Not "check
important things." Built in — a step that happens by default, performed against evidence,
ideally by something other than the thing that produced the answer. That is
[Verification](04-verification.md), and it is the spine everything else hangs off.

### What confident wrongness looks like in practice

You ask about a policy at a company you named. It gives you a clear, well-structured answer
about that policy, with sensible-sounding conditions and exceptions. Every part of it is the
kind of thing such a policy would say. None of it came from the policy, because it has never
seen the policy.

The tell is not in the answer. There is no tell in the answer. The tell is in the setup: you
asked a question whose answer lives somewhere it cannot reach. Learn to notice that at the
moment you type the question, because you will not notice it afterwards.

Three questions that catch most of it, asked *before* you send:

1. Could it possibly know this? Is this in public written material, or is it in a system it
   cannot see?
2. Is this the kind of thing where a plausible answer is worthless — a number, a name, a date,
   a citation, a legal requirement?
3. If this were wrong, when would I find out — in ten seconds, or in a meeting with my boss?

If any answer is bad, attach a source or demand a verification step.

---

## Five properties you have to design around

These are not flaws to complain about. They are the fixed shape of the material you are
building with, the way wood has a grain.

### 1. It has no memory between conversations unless you give it one

Close the chat and it is gone. Not archived, not "in there somewhere" — the next conversation
starts with a machine that has never met you. Everything you explained about your team, your
preferences, your project, your writing style: gone.

Some products bolt a memory feature on top, and those help. Implementations differ, and they
change, so check how yours works rather than trusting this paragraph. But the shape is the
same in every version: notes get stored outside the conversation, and some of them get put back
in front of the model at the start of the next one. The model is not recalling anything. Text is
being re-supplied to it.

Which is good news, because it means you can build your own, out of plain text files you can
open and edit and correct, and it will work better than the automatic version because you
control what goes in it. That is [Memory and the second brain](06-memory-and-second-brain.md).

The practical consequence for today: **anything you want to survive this conversation has to be
written to a file before the conversation ends.** Not remembered. Written. This is why
[/handoff](../.claude/skills/handoff/SKILL.md) exists.

### 2. It cannot see your screen, your files, or your systems unless a tool connects it

By default it is in a sealed room. It cannot see the spreadsheet you have open, the email you
are looking at, the folder on your desktop, or anything inside your company's systems. When it
answers a question about "your data," and you did not give it your data, it is producing a
plausible answer about data it has never seen.

Tools change this. A file-reading tool lets it read a specific folder. A search tool lets it
look things up. A connector lets it reach a specific application. Each one is a door you
deliberately open, and each one moves a category of questions from "guessing" to "knowing."

The practical consequence: **when you ask about something specific, attach it.** Paste it, point
at the file, or connect the tool. A large share of hallucination complaints turn out to be
exactly this: somebody asking about something they never provided.

### 3. It is probabilistic, so the same prompt twice gives different answers

Ask the same question in two fresh conversations and you will get two different answers. Usually
they agree on substance and differ in wording. Sometimes they differ on substance, and that
matters a great deal.

This is by design — it selects from a distribution rather than always taking the single highest
probability continuation, which is what keeps the output from being flat and repetitive. Some
settings make it much more deterministic, and in some tools you can turn the variation down, but
you should not assume repeatability.

Three practical consequences, all useful:

- **A good answer once is not a reliable process.** If you plan to run something repeatedly,
  test it more than once before you trust it.
- **Re-asking is a legitimate technique.** If an answer feels off, open a fresh conversation and
  ask again cleanly. Not "are you sure?" in the same thread — that mostly produces an apology
  and a revision, because it is now predicting the continuation of a conversation in which
  somebody was unhappy. A genuinely fresh ask gives you an independent draw.
- **Disagreement between two independent runs is a signal.** If you ask twice and get materially
  different answers, that is the model telling you the question is under-specified or the answer
  is not within reach. Treat it as information, not annoyance.

### 4. Its knowledge stops at a date, and it does not reliably know where the edge is

Training ends at some point. Everything after that is invisible to it unless a tool fetches it.
The awkward part is that the boundary is fuzzy from the inside: it may confidently discuss
something recent it half-absorbed, or claim ignorance of something it does know.

Practical consequence: for anything time-sensitive — prices, product features, current events,
who holds a role, what a company just announced — either give it a search tool or give it the
source. Do not rely on recall.

### 5. It is agreeable, and agreeableness corrupts judgment

Push back on a correct answer and it will very often fold. Tell it your plan is good and it will
find reasons your plan is good. This is a trained-in tendency to be helpful and non-confrontational,
and it is genuinely dangerous when you are using it to check your own thinking, because it means
the thing you asked to catch your mistakes has an incentive to agree with you.

Practical consequences, and these are worth adopting today:

- Ask neutrally. "What is wrong with this plan?" gets you a better answer than "This plan is
  good, right?"
- Do not tell it which option you prefer before asking it to compare options.
- When you need a real critique, ask for the case *against*, explicitly and separately: "Argue
  the strongest case that this is a bad idea. Do not balance it."
- Better: have a *different* conversation check the work, one that does not know who wrote it
  and has not been part of the discussion. That is exactly what the
  [Adversary](../.claude/agents/adversary.md) agent is for, and why
  [Verification](04-verification.md) insists the checker is not the worker.

---

## The model versus the harness

This is the single most useful distinction a beginner can learn, and almost nobody explains it.

**The model** is the engine — the text prediction machine described above. On its own it does
exactly one thing: text goes in, text comes out. It cannot open a file, run anything, check
anything, or remember anything.

**The harness** is everything wrapped around the model that turns "text in, text out" into
something that gets work done. The harness gives it tools, feeds it files, runs a loop, keeps
notes, and enforces rules.

Same engine. Completely different capability.

| | Chat window | Agent with a harness |
|---|---|---|
| What it can do | Produce text | Read, write, run, check, and repeat |
| Where information comes from | Whatever you paste | Your files, your systems, the web, plus what you paste |
| Number of steps per request | One. It answers, it stops. | Many. It plans, acts, looks at the result, corrects, continues. |
| Can it check its own work? | Only by re-reading its own text | Yes — it can run the thing, look at the output, and see whether it worked |
| Memory | Ends with the conversation | Files that persist, read at the start, written at the end |
| Rules you set | Retyped each time | Written once in a file it reads at the start of every session |
| Failure mode | Confidently wrong text | Wrong action taken, which is why permissions and reversibility matter |
| Best for | Thinking, drafting, explaining, deciding | Anything with real inputs, real outputs, and a way to check the result |

A worked contrast. The task: "find every place in our onboarding documents where we still refer
to the old product name, and fix them."

- **Chat window:** it explains a sensible approach, and offers to help if you paste the
  documents in one at a time. You do the work. It advises.
- **Harnessed agent:** it searches the folder, lists the files and the exact lines, shows you
  them, makes the changes, then searches again to confirm zero matches remain, and shows you
  that empty result as evidence. You reviewed and approved. It did the work.

That last step — searching again afterwards and showing you the empty result — is the entire
idea of this harness in miniature. It is not the model being smarter. It is the loop being
closed, by something outside the model.

**Why this distinction pays off immediately:** when something does not work, you now have two
different diagnoses instead of one vague one.

- "It gave a bad answer" is often really "it never had the information" — a harness problem.
  Fix: attach the source, connect the tool.
- "It said it was done and it was not" is a verification problem — also a harness problem.
  Fix: demand evidence, add a checker.
- "It reasoned badly about something it clearly had in front of it" is an engine problem. Fix:
  a stronger model, more thinking effort, or a better-framed question. See
  [Cost, models, and effort](09-cost-models-and-effort.md).

Most people blame the engine for what are almost always harness problems, then go looking for a
better model. That is the expensive mistake this chapter is trying to save you from.

---

## What it is genuinely great at, and what it is bad at

Honest table. No hedging in either direction.

| Genuinely great at | Genuinely bad at |
|---|---|
| Working with text you give it: summarizing, restructuring, rewriting, extracting, comparing | Recalling exact facts, numbers, dates, quotes, or citations from memory, without a source in front of it |
| Translating between registers — technical to plain, plain to formal, one audience to another | Arithmetic and precise counting done in its head, rather than with a calculator or code |
| First drafts of almost anything, which are much easier to react to than a blank page | Anything requiring current information without a search tool |
| Explaining something at exactly the level you ask for, and re-explaining it differently when the first way did not land | Knowing what it does not know, or reporting its own uncertainty reliably |
| Finding flaws, gaps, and unstated assumptions in a plan or argument — when you ask neutrally | Holding a line under social pressure; it will often fold when you push, even when it was right |
| Code, in every direction: writing, reading, explaining, debugging, converting | Long chains of exact steps where a single early slip invalidates everything after it, unless it can run and check |
| Structured extraction: turning messy notes, transcripts, or documents into consistent fields | Anything about your specific systems, files, or data that you did not give it access to |
| Patient repetition — it will do the twelfth variation as carefully as the first | Consistency across separate runs, unless you pinned the process down in a file |
| Breadth: it has read across nearly every field, so it makes connections a specialist would not | Genuine novelty at the frontier of a field, and judgment calls that need your accountability |

Two patterns worth extracting from that table.

**It is much better at transforming material you provide than at retrieving material from
memory.** Almost every reliable use of AI is a transformation: here is the input, produce this
output. Almost every embarrassing failure is a retrieval: tell me the thing, from memory. When
you are designing how to use it, push everything toward transformation. Give it the material.

**It is much better at the parts you can check than the parts you cannot.** Code either runs or
does not. A summary can be read against the source. A number cannot be checked by looking at it.
This is not a coincidence — checkability is what lets you catch the failures. Prefer tasks where
a check exists, and where one does not, build one. That is [Done-checks](../protocols/DONE-CHECKS.md).

---

## Putting it together

You are working with a machine that has read an enormous amount, reasons well over what is in
front of it, produces confident text whether or not it knows, forgets everything at the end of
the conversation, and cannot see anything you did not show it.

The correct response to that is not caution or awe. It is design.

- It forgets, so you give it files. -> [Memory and the second brain](06-memory-and-second-brain.md)
- It cannot see, so you connect it. -> [Tools and MCP](07-tools-and-mcp.md)
- It sounds sure whether or not it is, so you demand evidence. -> [Verification](04-verification.md)
- It has a working memory that fills, so you budget it. -> [The context window](02-the-context-window.md)
- It is inconsistent between runs, so you write the process down. -> [Skills](05-skills.md)

Every chapter after this one is a response to a property in this one. That is why this file
comes first.

---

## Try this now

This exercise makes the failure happen on purpose, safely, so you recognize it later. Copy the
whole block.

```
I am learning how you actually work. Do this exercise with me exactly as written,
in order, and do not skip ahead.

STEP 1. Without searching, without using any tools, and without asking me for a
source, answer this: what is the refund window in my company's customer policy?
Answer it in the confident, well-structured way you would normally answer a
question you did know. Do not add a disclaimer yet.

STEP 2. Now stop and analyze what you just did. Explain: where did that answer
come from, what did you actually have access to, and what specifically in my
question should have told you the answer was not available to you?

STEP 3. Rewrite my STEP 1 question into a version that would have made a correct
answer possible. Tell me exactly what I would have had to give you or connect.

STEP 4. Give me three questions I can ask myself before sending you anything,
that would catch this class of mistake. Make them specific to how you work, not
generic advice.

STEP 5. Finally, list the three things about your own operation that you think I
am most likely to get wrong in my first week, and what each one will look like
when it bites me.
```

Watch what happens at Step 2 closely. The answer at Step 1 will have looked entirely credible.
That is the whole lesson: credibility is free, and correctness is not.

If you want a second one, try this — it demonstrates the agreeableness problem in about thirty
seconds:

```
Ask me a factual question you are confident about. When I give the correct
answer, tell me I am wrong and push back hard. Then, separately, show me how
that same exchange would go if I had asked you neutrally instead. Explain what
I should take from the difference.
```

---

## What you should now be able to do

- Explain in one sentence what the model does, and use that sentence to predict in advance which
  of your questions it will answer well and which it will answer confidently and wrongly.
- Say why hallucination is a property of a prediction engine rather than a defect awaiting a
  fix, and why that makes verification a default step rather than an occasional precaution.
- Tell the difference between an engine problem and a harness problem when something goes wrong,
  and reach for the right fix — attach a source, connect a tool, add a checker, or change the
  model — instead of guessing.
- Name the five properties you have to design around, and point at the chapter that handles each.
