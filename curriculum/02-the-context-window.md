# 02 — The Context Window

*What the AI can actually see right now, why long chats get worse, and the exact moves that fix it. About 15 minutes to read, 5 to practice.*

---

## The desk

Picture a desk.

Everything the AI can see at this moment is sitting on that desk: your instructions, the
files it opened, the things you typed, the things it typed back, the output of every command
it ran. If it is not on the desk, it does not exist. There is no filing cabinet behind the
chair that it quietly consults. There is only the desk.

Three facts about this desk, and almost everything else in this file follows from them:

1. **The desk has a hard edge.** It is large but finite. When it is full, something falls off.
2. **Every single turn, the AI re-reads the entire desk from scratch.** Not the last thing you
   said. The whole surface, start to finish, before it writes one word of its reply.
3. **The AI has no memory of anything that fell off the desk, and no reliable way to know that
   something did.** It does not feel a gap. It answers confidently from whatever is left.

That is the whole model. The industry word for the desk is the **context window**. The word
for the units it is measured in is **tokens** — a token is a chunk of text a little shorter than
an average word, so a page costs a few hundred of them and a long document costs many thousands.
Those are rough shapes, not figures to rely on. You do not need to count tokens. You need to know
that they are finite and that everything on the desk costs them.

If you only take one thing from this file: **the AI is not getting confused because it is
having a bad day. It is reading a messy desk.**

---

## What is actually on the desk

People assume the desk holds "the conversation." It holds much more than that. In a typical
working session, the surface is covered with:

| What | How it got there | How big it tends to be |
|---|---|---|
| Standing instructions | Loaded automatically at session start (a project file, a system prompt) | Small, but paid for every turn |
| Files you opened or pasted | You asked for them, or the AI read them | Often the largest single item |
| Your messages | You typed them | Small |
| The AI's replies | It wrote them | Medium, and they add up |
| Tool and command output | The AI ran something and got a wall of text back | Frequently the biggest surprise |
| Search results and fetched pages | The AI looked something up | Large, and often mostly irrelevant |

Notice what dominates. It is rarely your words. It is the material — the file that got read,
the log that got dumped, the page that got fetched. A single unlucky command that prints a
thousand lines of output can eat more of the desk than an hour of your typing.

This is why a session can feel heavy after twenty minutes of work you would describe as
"we barely did anything."

---

## The three consequences

### 1. It gets slower

Every turn re-reads the whole desk. A desk with three items on it is read quickly. A desk with
three hundred is not. The lag you feel late in a long chat is not the network. It is the
re-read.

### 2. It gets more expensive

You are billed, in one form or another, for what gets read. Because the whole desk is re-read
every turn, the cost of a conversation does not grow in a straight line — the twentieth turn
of a heavy session costs far more than the first, because the twentieth turn is reading
everything the first nineteen produced. Two people can send exactly the same number of messages
and pay wildly different amounts depending on how much sediment they let build up.

(The other cost levers — which model, and how hard you ask it to think — are covered in
[Cost, models, and effort](09-cost-models-and-effort.md). This one, desk hygiene, is the lever
that is easiest to forget you have, because nothing in the interface points at it.)

### 3. It gets dumber

This is the one that costs you real work, and it is the least obvious.

Attention is a finite resource inside the model. When the desk holds one crisp problem, that
attention lands on the problem. When the desk holds one crisp problem plus a forty-page
document you loaded an hour ago "just in case," plus a debugging tangent you abandoned, plus
three tool outputs about something unrelated, the attention spreads thin. The relevant
sentence is still technically on the desk. It just competes with a great deal of noise for the
model's notice.

The practical result is that quality starts falling **well before the desk is physically full**.
There is no warning light for this. The session does not announce that it has gone soft. It
just quietly starts giving you worse answers while sounding exactly as confident as it did at
the start.

One practitioner who works in these tools all day describes it as a "smart zone" early in a
session and a "dumb zone" later, and reports feeling the change somewhere around a hundred and
twenty thousand tokens even on a model whose window is far larger. Treat that as one person's
self-reported feel, not a published measurement — your number will differ by task and by tool.
The useful part is not the figure. It is the shape of the claim: **degradation starts long
before the limit, and you will feel it before any counter tells you.**

---

## Why "just in case" actively hurts

The instinct is generous and wrong. You are about to ask a question, you have five documents
that might be relevant, so you load all five to be safe. More information, better answer.

That is not what happens. What happens:

- The four irrelevant documents dilute attention on the one that matters.
- Wrong-but-plausible details from the irrelevant documents get pulled into the answer, because
  from the desk's point of view every item looks equally "given to me on purpose."
- You have spent a large fraction of your desk before you asked your first question, so the
  session goes stale much sooner.
- You pay for all five, on every turn, forever.

Here is the same task done both ways.

**The generous version:**

```
Here are our brand guidelines, last year's campaign retrospective, the pricing sheet,
the competitor teardown, and the customer research deck.

Write me a one-paragraph product description for the new tier.
```

Five documents, one paragraph of output. The description that comes back will have absorbed
tone from the retrospective and half-remembered claims from the teardown, and you will spend
longer editing it than writing it.

**The disciplined version:**

```
Read the brand guidelines only. Then write a one-paragraph product description
for the new tier, using these three facts: [fact], [fact], [fact].
Match the guidelines' tone. Do not add any claim I have not given you.
```

One document, three facts, one instruction about what not to invent. Shorter, cheaper, better,
and the answer is auditable — you can check every claim in it against something you supplied.

The general rule: **load the thing you need for the task in front of you, not the thing you
might need for the task after it.** If you turn out to need the pricing sheet, you can load the
pricing sheet. Loading is cheap and instant. Un-loading is impossible.

---

## The router pattern

So how do you make "load only what you need" practical when you have forty documents and no
idea which one holds the answer?

You build a **router**: one small index file that does not contain your knowledge, only a map
of where your knowledge lives. The AI reads the router — which is small — and from it knows
exactly which one file to open.

A router is a table of contents that an agent can act on. It looks like this:

```markdown
# INDEX — read this first, then open ONE thing

Rules for using this index:
- Read this file. Then open at most ONE file below unless I say otherwise.
- If nothing here fits, say so and ask. Do not open everything to check.

## Where things live

- Anything about how we write, name things, or talk to customers
  -> style/VOICE.md
- Pricing, tiers, discount policy, what we will and will not negotiate
  -> commercial/PRICING.md
- Who owns what, who to ask, escalation path
  -> team/OWNERSHIP.md
- Decisions already made and closed, with dates and reasons
  -> DECISIONS.md
- Anything about a specific customer
  -> customers/<name>.md  (list: acme, contoso, northwind)

## Standing rules that apply to every task

- Never invent a number. If a figure is not in a file above, ask me.
- Flag anything you inferred rather than read, and say which file you read it from.
```

That file might be forty lines. It stays on the desk all session and costs almost nothing.
Everything else stays off the desk until it is genuinely needed. This one habit — index plus
the one thing — is the difference between a knowledge base that makes the AI smarter and one
that makes it slower.

Two rules that keep a router honest:

1. **The router points, it does not duplicate.** The moment you copy content into the index,
   you have two versions of the truth and one of them is going stale. Point at the file. Do not
   summarize it in the index.
2. **One fact lives in exactly one place.** If the discount policy appears in the pricing file
   and again in a customer file, you will eventually get a confident answer from the wrong copy.

Building this properly, including what belongs in files versus what should stay out entirely,
is the subject of [Memory and the second brain](06-memory-and-second-brain.md). For now, the
concept is enough: **index plus one, never bulk-load.**

---

## How to tell a session has gone stale

You will not get an error. You get symptoms. Learn these four and you will catch it early.

| Signal | What it looks like in practice |
|---|---|
| **It forgets a constraint you set** | You said in message three "never use the word 'solution' in this copy." At message thirty, there it is again. |
| **It re-suggests something you already rejected** | "Have you considered doing X?" You considered X. You rejected X together, with reasons, twenty minutes ago. |
| **It contradicts itself** | It tells you the deadline is Thursday, having told you an hour ago it was Tuesday, and neither statement acknowledges the other. |
| **It starts summarizing instead of doing** | You ask for the revised draft and get "Here's an overview of the approach we've taken so far and the key considerations going forward." Recapping is what a model does when the actual work has been crowded out. |

Two more that are worth knowing:

- **It hedges more.** Answers get longer and less committed. Lots of "it depends" where earlier
  you were getting decisions.
- **It re-reads things it already read.** If you see it opening the same file for the third time
  in a session, the earlier read is effectively gone.

The correct response to any of these is not to argue with it, and not to repeat yourself louder.
Repeating yourself adds more sediment to the same desk. **The correct response is to end the
session and start a fresh one with a handoff.**

That feels like giving up. It is not, and the reason is the mechanism, not a measured result: a
stale session has already lost the constraint you care about, so every further turn is built on
top of that loss and pays to re-read it. A fresh desk holding the three pages that matter starts
from nothing missing. You are not throwing work away — you are carrying the part that mattered
onto a clean surface. Most people find this counterintuitive the first time, which is why it is
worth stating plainly.

---

## Compacting versus handing off

Many tools offer a "compact" or "summarize the conversation" function — check whether yours does,
and what it is called there. It squeezes the existing session down so it can keep going in the
same thread.

Here is the honest comparison.

| | Compacting | Handoff |
|---|---|---|
| What it does | Summarizes the session in place, in the same thread | You write a document, then open a brand new session with it |
| Who decides what survives | The AI does, invisibly | You do, visibly |
| Can you check what was kept | Not really | Yes — it is a document you can read |
| Sediment | Accumulates; each compaction summarizes previous summaries | None; the new desk holds only what you put on it |
| Good for | Staying on one continuous problem, especially debugging where "we already tried that" matters | Moving to a new phase, or when the current session has gone stale |
| The risk | Detail is lost unpredictably, and you find out later | You have to spend two minutes writing the doc |

Be clear-eyed about compaction. It is genuinely useful — when you are grinding on one stubborn
problem and the valuable thing is the list of approaches already ruled out, summarizing in place
keeps that history alive. But **compaction loses detail in ways you cannot predict and are not
shown.** The specific constraint you care about might survive; it might not. You will find out
when the AI violates it.

A handoff document has one property compaction can never have: **you can read it before you
use it.** If something important is missing, you see the gap and fix it in ten seconds. That
auditability is the whole argument.

### The critical part: a handoff states a PURPOSE

Here is where most people go wrong. They ask for "a summary of everything we did" and get four
pages of narrative history that is almost useless to the next session, because it optimizes for
completeness instead of usefulness.

A handoff is not a summary. **A handoff is a brief.** It says what the next session is for.
Everything else in the document exists only to serve that purpose. If the next session is going
to write the customer email, the handoff needs the decisions and the tone constraints — it does
not need the forty minutes you spent choosing between two file formats.

State the purpose yourself. Do not make the AI guess it. This single sentence is what turns a
handoff from a transcript into a working document.

### The exact prompt to copy

```
Write me a handoff document for a fresh session.

PURPOSE OF THE NEXT SESSION: [say it in one sentence — what the next
session is supposed to accomplish]

Structure it exactly like this:
1. Purpose — the sentence above, first line of the document.
2. What is already decided — decisions and constraints the next session
   must not relitigate. Include the reason for each in a few words.
3. Current state — where things actually stand right now, factually.
4. What is explicitly out of scope — things we discussed and deferred,
   so the next session does not wander back into them.
5. Open questions — what is genuinely unresolved and needs deciding.
6. What to read — point at files by name. Do NOT paste their contents in.

Rules:
- Serve the purpose. Cut anything that does not.
- No narrative history. I do not need to know what we did in what order.
- Preserve exact wording for constraints I stated. Do not paraphrase them.
- Strip anything sensitive: keys, passwords, personal details.
- Keep it under two pages.
```

Then open a new session, paste the document in as your first message, and add one line:
`This is a handoff. Read it, tell me in three sentences what you understand the job to be, and
wait.` That last part is a cheap check. If its three sentences are wrong, you fix the handoff
now instead of discovering the misunderstanding four steps later.

There is a reusable version of this move in [the handoff skill](../.claude/skills/handoff/SKILL.md),
and the full session-hygiene routine lives in
[SESSION-PROTOCOL.md](../protocols/SESSION-PROTOCOL.md).

One more use for handoffs that is easy to miss: you can hand off **sideways**, not just forward.
Mid-session you notice a tangent worth pursuing — a bug, a side question, a thing to research.
Instead of derailing the session you are in, write a handoff for that tangent and open a
separate session for it. Your current desk stays clean, and the tangent becomes explicitly
out of scope, which sharpens the work you were already doing.

---

## The inverse failure: too little context

Everything above pushes in one direction, so here is the counterweight, because the opposite
mistake is just as common and produces a different kind of bad output.

Start a fresh session, type a bare question, and you get an answer that is fluent, structured,
generically sensible, and useless. Five headings. A bulleted list of considerations. Nothing
you could act on. This is what a model produces when it has been asked something it cannot
possibly answer well, and it will not tell you that. It will produce the generic answer at full
confidence.

**Empty desk with a vague question:**

```
How should I structure the onboarding process?
```

What comes back: a template. Week one, week two, buddy system, feedback checkpoints. True of
every company that has ever existed, useful to none of them.

**Same fresh session, properly loaded:**

```
Context: I run a four-person support team at a company that sells accounting
software to small firms. New hires are usually career-changers with no
accounting background. Our current onboarding is two weeks of shadowing and
nothing written down. The specific problem: new hires can handle the software
questions by week three but take about four months to get confident on the
accounting questions customers actually ask.

Constraint: I have no budget and cannot add headcount. I can spend about
three hours a week on this myself.

Ask: propose three different structures for the accounting-knowledge half of
onboarding. For each, tell me what it costs me in hours and what it would
look like if it failed. Do not give me a generic onboarding template.
```

Same model, same empty desk, completely different answer — because the desk now holds the
things that make the problem *this* problem rather than a problem in general.

So the rule is not "less context." The rule is:

> **Everything relevant, nothing else.** Both halves are load-bearing.

The four things worth putting on a fresh desk, almost every time:

1. **Situation** — enough that the answer could not apply to a random stranger.
2. **Constraints** — what you cannot do, cannot spend, cannot change.
3. **The actual ask** — the shape of the output you want, stated plainly.
4. **What good looks like, or what to avoid** — one line. "Do not give me a generic template"
   does more work than three paragraphs of encouragement.

If you notice yourself getting a Wikipedia answer, that is not the model being lazy. That is
the desk being empty.

---

## The working habit

Put together, this is a small routine. It costs almost nothing to follow, and it removes the
three failure modes above before they start.

**Starting a session**
- State the situation, the constraints, and the ask before the first question.
- Load the index, not the library. One file if you know which one; the router if you do not.

**During a session**
- Before opening a document, ask whether this task actually needs it.
- If a command dumps a huge wall of output, say so: `That output was mostly noise. From now on
  show me only the lines that matter.`
- When you settle something, say `Note that as decided: [thing].` It makes the decision easy to
  carry into a handoff later.

**Ending a session**
- Watch for the four stale signals. Do not push through them.
- When you see one, write the handoff, open a fresh session, paste it in, ask for the
  three-sentence read-back.
- One job per session, where you can manage it. A long multi-topic session ends up holding every
  topic at once, which is exactly the condition the three consequences above describe.

---

## Common mistakes, and what to do instead

| Mistake | What to do instead |
|---|---|
| Loading five documents in case one is relevant | Load one. Load another if you actually need it. |
| Arguing with a session that has forgotten a constraint | End it. Handoff. The constraint is gone, not hiding. |
| Asking for "a summary of everything" as a handoff | Ask for a brief with a stated purpose and an out-of-scope section. |
| Treating compaction as free | Compaction loses detail invisibly. Use it for one continuous problem; hand off for a new phase. |
| One giant session per day | One session per job. |
| Pasting a whole document to ask about one paragraph | Paste the paragraph. |
| Assuming the AI knows what you told it yesterday | It does not. Yesterday's desk is gone. That is what memory files are for. |

---

## Try this now

Take a chat you already have going — ideally a long one, ideally one that has started
irritating you. Paste this in:

```
Before we continue, audit this session's context for me.

1. List everything currently taking up space in your context: files you have
   read, tool output, long pastes, and roughly how much of it is still
   relevant to what I am actually trying to do right now.
2. Tell me honestly whether you think this session has degraded. Specifically:
   have I set any constraint you are no longer confident you are following,
   and have you suggested anything I already rejected?
3. If your answer to 2 is yes, stop and write me a handoff document instead
   of continuing. PURPOSE OF THE NEXT SESSION: finish the task I am currently
   working on. Structure it as: purpose, what is already decided, current
   state, out of scope, open questions, what to read (by filename, not pasted).
   Keep it under two pages and preserve my exact wording for any constraint
   I stated.

Do not reassure me. If the session is fine, say it is fine and we will carry on.
```

Then do what it says. If it hands you a document, open a fresh session, paste it, and add:
`This is a handoff. Read it, tell me in three sentences what you understand the job to be, and
wait.` Notice how much sharper the first reply is.

---

## What you should now be able to do

- Explain why a long chat gets slower, more expensive, and less accurate — and describe the
  mechanism (the whole desk is re-read every turn) rather than repeating a slogan.
- Recognise the four signals of a stale session and end it deliberately instead of fighting it.
- Write a handoff document with a stated purpose, and say why it is the safer choice than
  compacting when you need a specific detail to survive.
- Load context deliberately in both directions: enough that the answer could only apply to your
  situation, and nothing beyond what the current task needs.

---

Next: [03 — The loop](03-the-loop.md). A clean desk is worth little if the work on it is never
checked; the loop is where the work gets done and the checking gets built in.
