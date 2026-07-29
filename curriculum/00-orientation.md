# Orientation

*What this harness is, what it will and will not claim, and the one thing to do first. Read time: 12 minutes.*

---

## The honest frame

Most people use AI like a vending machine. Put in a question, get out an answer, be mildly
disappointed, go back to doing the work by hand. They get a little faster at writing emails
and summarizing documents, and then they plateau.

The plateau is not a skill problem. It is a shape problem. A vending machine has no memory of
your last purchase, no way to check whether what it handed you was any good, and no way to get
better at serving you. If that is the shape of your relationship with AI, you will get vending
machine results forever, no matter how clever your prompts get.

The shift is this:

> Most people use AI like a vending machine: put in a question, get out an answer, be mildly
> disappointed. The shift is learning to build a *system* around it — one that remembers, one
> that checks its own work, and one that you improve a little every time you use it. That is
> not a technical skill. It is a habit of mind. This harness is here to install the habit.

That is the whole thesis. Everything in these files is in service of it.

You do not need to be a programmer. You do not need to open a terminal, though it helps and
[Install](../INSTALL.md) will walk you through it if you want to. What you need is a willingness
to stop treating each conversation as disposable.

---

## What changes when you stop using it as a vending machine

Here is the same task, done both ways. The task: you have to produce a weekly status summary
for your team, pulling from your notes and last week's summary.

**Vending machine version.** You open a chat. You paste your notes. You type "write a weekly
status summary." You get something generic. You spend fifteen minutes fixing the tone, adding
the context it did not have, and correcting one thing it made up. Next week you do all of that
again, from scratch, with no accumulated improvement.

**System version.** The first time, you spend forty minutes with the AI building three things:
a file that describes what a good summary looks like for your team, a place where last week's
summary lives so the AI can read it, and a checklist the AI has to pass before it hands you a
draft. Every week after that, you say "run the weekly summary" and you get back a draft that
starts much closer to finished, that knows what happened last week, and that flags the parts it
was not sure about instead of inventing them.

The first week, the system version costs you more time than it saves. At some point it crosses
over, and after that every run is close to free. How long that takes depends entirely on how
often you do the task — which is the actual reason to start with something you repeat.

That is not a promise about hours saved. It is a description of a mechanism: work you codify
once gets reused, and work you retype every time does not.

---

## The five-layer picture

Everything people build with AI sits somewhere in this stack — five layers, numbered 0 to 4.
Read it bottom up. Layer 0 is the engine you sit on top of rather than one you build; the four
above it are yours, and the value concentrates in layers 1 and 2.

```
LAYER 4  Distribution   ->  share it so other people can use it
LAYER 3  Interface      ->  optional dashboard, buttons, a nice front end
LAYER 2  Memory & State ->  notes the AI reads and writes; your second brain   <- most of
LAYER 1  Skills & Loops ->  codified repeat work + verification loops          <- the value
LAYER 0  Engine         ->  the model itself (the thing that generates text)
```

| Layer | What it is | What it looks like day to day | Who obsesses over it |
|---|---|---|---|
| 0 — Engine | The model. The raw text-prediction machine. | Choosing a smarter or cheaper model for a task. | Everyone on social media |
| 1 — Skills & Loops | Repeat work written down as instructions the AI follows, plus a checking cycle so it grades its work before you see it. | "Run the weekly summary." "Verify this before you show me." | Almost nobody |
| 2 — Memory & State | Plain files the AI reads at the start and writes at the end. What it learned, what you decided, what your preferences are. | A folder of notes that quietly gets better. | Almost nobody |
| 3 — Interface | A dashboard, a set of buttons, a phone app over the top. | Clicking "run" instead of typing. | Demo videos |
| 4 — Distribution | Packaging it so a colleague can use it without you. | Handing someone a folder — like this one. | Consultants |

**The overwhelming majority of the value sits in Layer 1 and Layer 2.** That is a claim about
*priority*, not a measurement, and nobody should hand you a percentage for it. The honest
version is: the layers that look most impressive in a demo are the ones that matter least, and
the two boring middle layers are where your results actually come from. You can test that claim
against your own work in a month and disagree with it.

This matters because it tells you what to ignore. You will see a lot of content about which
model is best this month (Layer 0) and a lot of beautiful dashboards (Layer 3). Both are real.
Neither is where you should spend your first three months.

---

## The operating discipline

Ten ideas run through everything here. You do not need to absorb them now. They are listed so
you can see the shape of the thing, and so you know which file teaches each one.

| # | The idea | Taught in |
|---|---|---|
| 1 | Verification is load-bearing. Never let the worker grade its own work. Evidence before "done." | [Verification](04-verification.md) |
| 2 | A loop needs an objective done-check and a hard stop. A loop is only as good as its done-check. | [The loop](03-the-loop.md) |
| 3 | Deterministic before probabilistic. If a rule, a search, or plain code can do it, use that. | [The loop](03-the-loop.md) |
| 4 | Skills, not prompts. A prompt dies with the chat. A skill compounds. | [Skills](05-skills.md) |
| 5 | Memory lives outside the conversation, in plain files, one fact in one place. | [Memory and the second brain](06-memory-and-second-brain.md) |
| 6 | Context is a budget. Load the map plus the one thing you need. Never bulk-load. | [The context window](02-the-context-window.md) |
| 7 | Cost has two levers: which model, and how much effort you ask it to spend. | [Cost, models, and effort](09-cost-models-and-effort.md) |
| 8 | Curiosity is the actual skill. Knowing what to ask for is the bottleneck. | [Graduation](13-graduation.md) |
| 9 | Tag what you know versus what you inferred. Provenance on every AI-derived claim. | [Verification](04-verification.md) |
| 10 | Trust is earned in an empty parking lot, not on the highway. Automate the boring, reversible thing first. | [Safety, privacy, and trust](10-safety-privacy-and-trust.md) |

---

## The map: everything in this harness

### Curriculum — the teaching path

| File | What it teaches | Why you would read it |
|---|---|---|
| [00 Orientation](00-orientation.md) | This file. The frame, the map, the promises. | You are here. |
| [01 What the model actually is](01-what-the-model-actually-is.md) | A correct mental model of the thing you are talking to, in plain English. | So you stop being surprised by its failures. |
| [02 The context window](02-the-context-window.md) | Its short-term memory: how big, how it fills, what happens when it does. | This explains most of "why did it get worse partway through?" |
| [03 The loop](03-the-loop.md) | Goal, act, observe, done-check, stop. How to hand off work instead of prompting. | So you stop being the person who prompts every step. |
| [04 Verification](04-verification.md) | The spine of the whole harness. How to make the AI prove it, and never grade itself. | This is the single highest-return habit here. |
| [05 Skills](05-skills.md) | Turning a thing you do repeatedly into a reusable, improvable procedure. | This is how effort compounds instead of evaporating. |
| [06 Memory and the second brain](06-memory-and-second-brain.md) | Files the AI reads and writes. Routing. One fact in one place. | So it stops forgetting who you are every morning. |
| [07 Tools and MCP](07-tools-and-mcp.md) | How the AI reaches your real systems, and the order to try things in. | So it can act, not just advise. |
| [08 Subagents and swarms](08-subagents-and-swarms.md) | Delegation to specialists. Also: when not to. | So you can scale without scaling your bugs. |
| [09 Cost, models, and effort](09-cost-models-and-effort.md) | The two cost levers and how to route work between models. | So the good habits stay affordable. |
| [10 Safety, privacy, and trust](10-safety-privacy-and-trust.md) | What leaves your machine, what never should, and how to earn trust in stages. | Read this before you connect anything to work data. |
| [11 First 90 days](11-first-90-days.md) | A concrete sequence for a new job: week one, month one, quarter one. | Turns all of the above into a plan. |
| [12 The hype ledger](12-the-hype-ledger.md) | Claims circulating that are unsupported, and how to spot the next one. | So you can tell substance from noise on your own. |
| [13 Graduation](13-graduation.md) | Curiosity as the actual skill, and how to keep going without this folder. | The point of the whole thing. |
| [14 The skill library](14-the-skill-library.md) | A tour of every command and specialist in this folder, and how they chain together. | So you know what you already have before you build anything. |
| [15 Git](15-git.md) | An undo history for a whole folder, explained for someone who has never used it. | This is what makes it safe to let an AI change your files. |
| [16 The terminal](16-the-terminal.md) | What it is, the honest case for and against it, and the little you actually need. | So it stops being scary without you having to master it. |
| [17 Many models](17-many-models.md) | Why a second, different model catches what the first one cannot — and where that stops being true. | The other half of verification. |

### Protocols — procedures the AI follows

| File | What it does |
|---|---|
| [Verification protocol](../protocols/VERIFICATION-PROTOCOL.md) | The exact steps for proving a piece of work is actually done. |
| [Done-checks](../protocols/DONE-CHECKS.md) | A library of objective finish conditions you can copy for your own tasks. |
| [Session protocol](../protocols/SESSION-PROTOCOL.md) | How a working session starts, stays clean, and hands off to the next one. |
| [Failure modes](../protocols/FAILURE-MODES.md) | The specific ways this goes wrong, and the fix for each. |
| [Teaching protocol](../protocols/TEACHING-PROTOCOL.md) | How the AI teaches you, and what evidence it needs before it marks anything learned. |
| [Situations](../protocols/SITUATIONS.md) | A catalogue of the spots you actually get stuck in, and the move for each one. |
| [Review routine](../protocols/REVIEW-ROUTINE.md) | How to make the coaching review happen again next month instead of once. |

### Reference — look things up

| File | What it does |
|---|---|
| [Glossary](../reference/GLOSSARY.md) | Every term in plain English, with no term defined using another undefined term. |
| [Prompt patterns](../reference/PROMPT-PATTERNS.md) | Copy-pasteable wording for the situations that come up constantly. |
| [Sources](../reference/SOURCES.md) | Where the ideas here came from, and which claims are one person's experience. |

### Progress — files that change as you learn

| File | What it does |
|---|---|
| [Mastery](../progress/MASTERY.md) | Your place on the course: every topic, and the evidence that you actually knew it. |
| [Learner](../progress/LEARNER.md) | What you have covered, what you are working on, what you found hard. The AI updates this. |
| [Skills built](../progress/SKILLS-BUILT.md) | A running list of the procedures you have codified. Your actual output from this. |
| [Decisions](../progress/DECISIONS.md) | Choices you made and why, so future-you does not relitigate them. |
| [Session log](../progress/SESSION-LOG.md) | One short entry per session, so a later conversation can see what an earlier one did. |
| [Reviews](../progress/REVIEWS.md) | The coaching reviews, dated, so you can see whether the same problem keeps coming back. |

### Commands — things you can type

These live in `.claude/skills/`. If your AI can read this folder, you can type these directly.
If it cannot, you can get the same effect by saying the plain-English version next to each one.

| Command | What it does | Plain-English version |
|---|---|---|
| [/whats-possible](../.claude/skills/whats-possible/SKILL.md) | Three questions about your actual job, five directions drawn from your answers, then finishes one of them with you. | "Ask me about my job and tell me what I could hand to you." |
| [/learn](../.claude/skills/learn/SKILL.md) | Runs the curriculum for you, in the right order, at your pace, checking you understood. | "Teach me this folder, one piece at a time." |
| [/verify-this](../.claude/skills/verify-this/SKILL.md) | Takes something the AI just produced and adversarially checks it. | "Now try to prove that answer is wrong." |
| [/skillify](../.claude/skills/skillify/SKILL.md) | Turns something you just did by hand into a reusable skill. | "Write down what we just did so we never redo it." |
| [/grill-me](../.claude/skills/grill-me/SKILL.md) | Interrogates you to extract what is in your head into files. | "Interview me until you understand how I do this." |
| [/handoff](../.claude/skills/handoff/SKILL.md) | Ends a long session cleanly and writes a document that starts the next one. | "Write me a handoff so the next session picks up here." |
| [/quiz](../.claude/skills/quiz/SKILL.md) | Checks what you still actually have, using your own work rather than definitions. | "Test me on the things you say I already know." |
| [/coach](../.claude/skills/coach/SKILL.md) | Drops the teacher into whatever you are already doing, for one short correction. | "Am I doing this the smart way? One suggestion, then back to it." |
| [/im-stuck](../.claude/skills/im-stuck/SKILL.md) | Works out what kind of situation you are in, teaches you the diagnosis, walks the first move. | "I do not know what to do next. Help me work out what is actually wrong." |
| [/review-my-work](../.claude/skills/review-my-work/SKILL.md) | Looks back across several sessions and names the one thing to change next. | "Review how I have been working lately and tell me what to fix." |
| [/recall-session](../.claude/skills/recall-session/SKILL.md) | Finds what you did before, and says honestly how it found it. | "What did we decide about that last week?" |

### Agents — specialists the AI can call

These live in `.claude/agents/`. You will rarely call them yourself; the AI uses them.

| Agent | Its job |
|---|---|
| [Verifier](../.claude/agents/verifier.md) | Checks work against evidence. Does not care about your feelings or its own earlier answer. |
| [Adversary](../.claude/agents/adversary.md) | Actively tries to break a claim or a plan. Assumes it is wrong until it cannot be. |
| [Scout](../.claude/agents/scout.md) | Goes and finds things — in your files, in your systems, on the web — and reports back compactly. |
| [Teacher](../.claude/agents/teacher.md) | Explains and checks understanding. Runs the curriculum behind `/learn`. |
| [Reviewer](../.claude/agents/reviewer.md) | Reads a stretch of your past sessions through one lens and reports instances, not impressions. |

---

## How to read this

**You do not have to read it in order.** The numbering is a suggested path, not a lock. Files
01 through 04 are the foundation, and reading those four in order is genuinely worth it. After
that, jump to whatever your actual work needs.

**Better still: do not read it yourself.** Paste the ignition prompt from
[Bootstrap](../BOOTSTRAP.md), or type `/learn`, and the AI will run the curriculum for you — one
piece at a time, with exercises, checking that you understood before it moves on. It will track
where you are in [Mastery](../progress/MASTERY.md) so you can stop mid-way and pick up next week
without re-reading anything.

**The taught version is tracked, and you will be quizzed.** [Mastery](../progress/MASTERY.md) is
your report card: every topic on the course, and the evidence that you actually knew it. Nothing
gets marked as known because you read it. It gets marked when you have explained it back in your
own words and used it once on your own real work — both — which is the evidence-before-done rule
from [Verification](04-verification.md) turned on your own education. Expect the AI to bring back
things you covered weeks ago and ask you to use them, unprompted. Two things you can reach for at
any point, in any conversation: `/coach` pulls the teacher into whatever you are already doing for
one short correction and then hands the task straight back, and `/im-stuck` is for when you cannot
even name what is wrong — it works out which situation you are in and walks the first move with
you.

If you like reading, read. If you like being taught, be taught. Both paths land in the same
place. What does not work is skimming all eighteen files in one sitting and retaining none of it.

**Three suggested paths:**

| You have | Do this |
|---|---|
| 20 minutes | Run `/whats-possible`. Nothing else. |
| An afternoon | Read 01 through 04, then run `/whats-possible`, then build one small thing. |
| A first week at a new job | Go straight to [First 90 days](11-first-90-days.md) and follow it; it will pull in the other files as needed. |

---

## What this harness promises you

Four promises. They are also the standard you should hold this thing to — if it breaks one,
it is broken, and you should say so out loud to the AI so it can be fixed.

**1. It will not hype you.**
No invented statistics. No "10x your output." No claim that you must act now or fall behind.
Where a claim comes from one person's experience rather than evidence, the text says so in the
sentence. There is an entire file — [The hype ledger](12-the-hype-ledger.md) — devoted to
naming claims that circulate widely and are not supported. If a number appears anywhere in this
folder without a source, treat that as a bug.

**2. It will make the AI show you evidence.**
The default here is that "done" means proven, not asserted. When the AI tells you it finished
something, the harness expects it to show you what it checked and how. When judgment is
involved, a separate checker — one that did not do the work — looks at it. You will get used to
asking "show me" and getting a real answer. See [Verification](04-verification.md).

**3. It will teach curiosity, not recipes.**
Recipes go stale within months in this field. The questions do not. Every file here is trying
to give you a way of thinking you can apply to a tool that does not exist yet, rather than a
list of buttons to press in an app that will change next quarter. The measure of success is not
that you memorized this folder. It is that six months from now you ask for things nobody told
you to ask for.

**4. It will get better as you use it.**
This is a live folder, not a book. The AI writes into `progress/` as you go. When you codify
something, it lands in [Skills built](../progress/SKILLS-BUILT.md). When you find a rough edge
in the teaching, you can tell the AI to fix the file, and it will. The version you hand to
somebody in a year should be better than the one you received.

---

## What it does not promise

Honesty cuts both ways.

- **It will not make you a programmer.** It will make you effective without becoming one. Some
  of what you build will still be worth handing to an engineer.
- **It will not work equally well for every job.** If your work is mostly physical, mostly
  in-person, or mostly governed by rules you are not allowed to automate, the honest answer is
  that Layer 1 and Layer 2 apply to a smaller slice of your day. Run `/whats-possible` and find
  out which slice.
- **It does not know your company's policy.** Before you connect any AI to real work data, read
  [Safety, privacy, and trust](10-safety-privacy-and-trust.md) and then check with whoever owns
  that decision where you work. This folder cannot give you permission.
- **Parts of it will go stale.** Model names, prices, and product features change fast. The
  principles are written to outlive them, and the files flag which parts are dated.

---

## The fastest thing you can do right now

Type this:

```
/whats-possible
```

It runs a short interview — three questions about your actual work: what you do day to day, what
part of the week you dread, what you wish you had more time for. Then it shows you five
directions built out of your own answers rather than out of generic AI examples, names one thing
next to your choice that you did not know to ask for, and finishes one small real piece of work
with you before the conversation ends. You come away holding a result, not a plan.

Do that before you read anything else. Two reasons:

1. **It calibrates everything after it.** The rest of the curriculum lands very differently when
   you already have three concrete things from your own job in your head.
2. **It answers the question you actually have.** You do not really want to know how a context
   window works. You want to know what this thing can do for you. Start there, and the
   mechanics become interesting because they are in the way of something you want.

If your AI cannot run slash commands, paste the prompt in the next section instead. It does the
same job.

---

## Try this now

Copy this whole block into your AI and send it.

```
Read these three files from the folder I have given you, in this order: README.md,
CLAUDE.md, then curriculum/00-orientation.md. Nothing else yet.

Then run /whats-possible on me here, in this conversation. Do not hand me off to
a new session first - I have asked for three files, not the whole folder. If you
cannot run slash commands, open .claude/skills/whats-possible/SKILL.md and follow
it literally.

Follow that file exactly, including its limits:
- Ask me its three questions, one at a time, and wait for each answer.
- Ask about what I actually did last week, not what my job description says.
- Push back once when my answer is vague. "Reports" is not an answer; ask what
  report, for whom, from what source, how often.
- Do not give me a plan. Show me the five doors in my own words, name one thing
  next to what I pick that I did not know to ask for, and then actually finish
  one small real piece of work with me before this conversation ends.
- End with the receipt: what you checked it against, and what you could not
  confirm.
```

If you have never used this AI before and are not sure it can read the folder at all, send this
one line first and see what comes back:

```
List every file in the folder I gave you, then tell me in two sentences what it is for.
```

---

## What you should now be able to do

- Explain, in your own words, why using AI as a question-answering machine plateaus, and what
  a system around it adds that a better prompt cannot.
- Name the five layers, 0 to 4, say which two carry most of the value, and use that to decide
  what to ignore when someone shows you an impressive demo.
- Navigate this folder deliberately — pick the file that matches your question instead of
  reading straight through, and hand the driving to `/learn` when you would rather be taught.
- Hold this harness to its four promises, and say so when a file breaks one.
