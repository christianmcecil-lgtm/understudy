# Glossary

*Every word this harness uses, in plain English, alphabetical. Skim in 10 minutes; come back whenever a term stops you.*

Nothing here assumes you have written code. Each entry is one or two sentences of plain
meaning, a "why you care" line where the term actually changes how you work, and a link to
the file that teaches it properly.

If you only internalise five, make them these: **context window**, **done-check**,
**verification**, **skill**, **provenance**. The rest hang off those.

---

## A

### Adversarial reviewer
A second AI whose only job is to attack the first one's work: find what is wrong, missing,
or taken on faith. It is not asked to be fair, only to be hard to satisfy.
*Why you care:* asking a fresh instance to tear apart what the last one produced costs you one
prompt, and it catches things the original will not catch about itself.
Taught in: [Verification](../curriculum/04-verification.md)

### Agent
An AI that is given a goal and allowed to take steps toward it on its own: read a file, run
a search, write a document, check the result, try again. A chatbot answers; an agent acts.
*Why you care:* the difference between "AI gave me a paragraph" and "AI did the task" is
almost entirely this one distinction.
Taught in: [The loop](../curriculum/03-the-loop.md)

### Artifact
Anything the AI produces that outlives the conversation: a file on disk, a document, a
spreadsheet, a rendered page. The opposite of an answer that scrolls away.
*Why you care:* work that lands in a file compounds. Work that lands only in a chat window
is gone the moment you close the tab.
Taught in: [Memory and the second brain](../curriculum/06-memory-and-second-brain.md)

---

## B

### Bootstrap (ignition prompt)
The block of text you paste into a brand new conversation to turn it into your teacher. It says
where this folder is, names the few files to read first, and tells the session to pick up the
course where you left it.
*Why you care:* it is the whole setup. The session that just read this entire folder is already
full of it; a fresh one loading four files is cheaper, sharper, and starts by asking you a question
instead of lecturing.
Taught in: [Bootstrap](../BOOTSTRAP.md)

### Branch
A movable label pointing at one snapshot of a folder's history, so work can go two ways at once
without either side destroying the other. Making one costs almost nothing — it writes a label, it
does not copy your files.
*Why you care:* you will hear the word long before you need to make one, and knowing it is just a
label is what stops it sounding expensive or dangerous.
Taught in: [Git](../curriculum/15-git.md)

---

## C

### Checkpoint
A saved snapshot of the state of your work before the AI changed it, so you can rewind to
it. Some tools take these automatically before each edit; version control (see **worktree**)
provides a sturdier version of the same idea.
*Why you care:* it converts "the AI might wreck my file" from a real risk into an
inconvenience. Reversibility is what lets you be brave.
Taught in: [Safety, privacy and trust](../curriculum/10-safety-privacy-and-trust.md)

### Coaching review
A periodic look back at how you have actually been working — what you repeated without codifying,
what you accepted without checking, what you did the hard way, what you never tried — ending in one
ranked list and one thing to do today.
*Why you care:* habits form quietly and skills decay quietly. A standing review is what catches the
thing you have been doing by hand for a month without noticing.
Taught in: [Review routine](../protocols/REVIEW-ROUTINE.md)

### Command-line agent
An AI agent you run in a **terminal** rather than in a browser tab, pointed at a folder on your
machine, able to read and change files and run commands. Several vendors ship one, and which is
best changes often enough that it is not worth memorising.
*Why you care:* this is where the most capable tooling lives, and where you can point two different
vendors' agents at the same folder — one working, one checking.
Taught in: [The terminal](../curriculum/16-the-terminal.md)

### Commit
A snapshot of an entire folder at one moment, saved with a message saying what changed and why. The
history is a chain of those snapshots, and committing only ever adds one.
*Why you care:* committing before you let an AI change a lot of files is what turns "it wrecked my
work" into "put it back the way it was this morning."
Taught in: [Git](../curriculum/15-git.md)

### Compaction
Squeezing a long conversation down to a summary so the session can keep going. The old
detail is replaced by a shorter recap of it.
*Why you care:* compaction keeps you working but loses fidelity, and each pass loses a
little more. When the next phase deserves a clean start, a **handoff** beats a compaction.
Taught in: [The context window](../curriculum/02-the-context-window.md)

### Connector
A prepackaged integration you switch on inside an AI product so it can reach an outside
service (your email, your drive, your notes app). Under the hood most connectors are **MCP**
servers with the setup already done for you.
*Why you care:* every connector you enable is both new capability and new surface area for
mistakes and for **prompt injection**. Turn on what you use; turn off what you do not.
Taught in: [Tools and MCP](../curriculum/07-tools-and-mcp.md)

### Context rot
The quality slide that happens as a conversation grows long: the model starts missing things
it was told earlier, repeats itself, or drifts off the instructions.
*Why you care:* when an AI suddenly seems dumber, the usual cause is a bloated conversation,
not a bad model. The fix is a fresh session, not a better prompt.
Taught in: [The context window](../curriculum/02-the-context-window.md)

### Context window
Everything the model can see at once: your instructions, the conversation so far, the files
it has read, the results of the tools it ran. It is working memory, and it is finite.
*Why you care:* this is the single most useful mental model in the whole harness. Almost
every "why did it forget / why is this expensive / why did it get worse" question is a
context-window question.
Taught in: [The context window](../curriculum/02-the-context-window.md)

### Correlated error
Two checkers being wrong in the same direction because the cause of the mistake is shared —
overlapping training material, or the same widely repeated falsehood.
*Why you care:* it is the ceiling on **cross-model verification**. Two models agreeing raises your
confidence; it does not prove you are right, and one deterministic check still beats any number of
agreeing models.
Taught in: [Running many models](../curriculum/17-many-models.md)

### Cross-model verification
Having work checked by a *different* model from the one that produced it, rather than by the same
model in a fresh conversation.
*Why you care:* a model's errors are patterned rather than random, so it finds its own output
plausible for exactly the reasons it produced it. A different model does not share those patterns,
which is why things that slipped past the first one can stick out to the second.
Taught in: [Running many models](../curriculum/17-many-models.md)

---

## D

### Deterministic (versus probabilistic)
Deterministic means the same input always produces the same output: a rule, a search, a
calculation, a script. Probabilistic means the output varies: anything the model generates.
*Why you care:* if a rule or a search can do the job, use it. Reserve the model for real
judgment. Deterministic steps are cheaper, faster, and cannot drift.
Taught in: [The loop](../curriculum/03-the-loop.md)

### Done-check
The objective test that decides whether a task is finished. "Until the page loads with no
errors" is a done-check. "Until it looks good" is not.
*Why you care:* a loop is only as good as its done-check. Vague criteria are the usual reason
automated runs burn time and produce nothing usable.
Taught in: [Done-checks](../protocols/DONE-CHECKS.md)

---

## E

### Effort level
A setting that controls how much thinking the model spends on a task, separate from which
model you picked. Low effort answers fast; high effort deliberates.
*Why you care:* cost has two dials, not one. Routing routine work to low effort on a capable
model is often a better trade than dropping to a weaker model.
Taught in: [Cost, models and effort](../curriculum/09-cost-models-and-effort.md)

### Evidence (receipt)
The concrete proof that something was actually done: the pasted output, the screenshot, the
file path, the quoted line, the query result. Not the AI's summary of what it did.
*Why you care:* "Done." is a claim. A receipt is a fact. Demanding receipts costs you one
sentence and is the verification habit to build first.
Taught in: [Verification protocol](../protocols/VERIFICATION-PROTOCOL.md)

### Explain-back
Saying an idea back in your own words, as you would to a coworker who has never heard of it, with
the file closed.
*Why you care:* it is the test that separates recognising an idea from holding it, and the tell is
whose examples you reach for. Your own clients and your own weekly report mean you own it; the
harness's words rearranged mean you memorised a sentence.
Taught in: [Teaching protocol](../protocols/TEACHING-PROTOCOL.md)

---

## F

### Fan-out
Splitting one job into several pieces and giving each piece to its own AI working in
parallel, then collecting the results.
*Why you care:* fan-out is genuinely good for reading and researching (many readers, no
collisions) and genuinely dangerous for writing (two writers editing the same thing is how
you lose an evening).
Taught in: [Subagents and swarms](../curriculum/08-subagents-and-swarms.md)

### Friction log
A running note of the moments where working with your AI was annoying, slow, or wrong. Later
you read the log and turn the repeating entries into **skills** or rules.
*Why you care:* it converts irritation into system improvement. Your own frustration is the
best backlog you will ever have.
Taught in: [Your first 90 days](../curriculum/11-first-90-days.md)

### Frontier model
The current top tier of the largest AI providers: the most capable, most expensive models
available at any given moment. The membership of that tier changes constantly.
*Why you care:* frontier tools assume frontier engines. Advice tuned for the top tier often
does not survive being pointed at a smaller or local model.
Taught in: [What the model actually is](../curriculum/01-what-the-model-actually-is.md)

---

## H

### Hallucination
When the model produces something fluent, confident, and false. It is not lying; it is
completing a pattern, and a plausible completion is not always a true one.
*Why you care:* fluency is not evidence. This is the reason the entire harness is organised
around checking rather than trusting.
Taught in: [What the model actually is](../curriculum/01-what-the-model-actually-is.md)

### Handoff
Deliberately ending a heavy session and starting a fresh one, carrying across a purpose-built
document that holds only the slice the next session needs.
*Why you care:* it is the clean alternative to letting a session rot. The new session starts
sharp instead of inheriting hours of sediment.
Taught in: [Session protocol](../protocols/SESSION-PROTOCOL.md)

### Harness
The software wrapped around the model that lets it read files, run commands, use tools, and
loop. The model is the engine; the harness is the car around it.
*Why you care:* most of what feels like "the AI got better" is actually the harness getting
better. It also means the engine is swappable.
Taught in: [Orientation](../curriculum/00-orientation.md)

### Headless
Running an AI task with no human watching: you state the job, it runs to completion, output
goes to a file or a message. The opposite of sitting in a chat.
*Why you care:* this is how scheduled and overnight work happens. It is also where a weak
**done-check** does the most damage, because nobody is there to stop it.
Taught in: [The loop](../curriculum/03-the-loop.md)

### Hook
A small script that fires automatically at a fixed moment: before a command runs, after a
file is saved, when a task finishes. It is a rule, not a request, so the AI cannot talk its
way out of it.
*Why you care:* hooks are deterministic guardrails that consume no thinking budget. Anything
you find yourself telling the AI every single session is a candidate for a hook.
Taught in: [Tools and MCP](../curriculum/07-tools-and-mcp.md)

### Hype ledger
This harness's running list of claims that circulate as fact but are unsupported: vendor
benchmarks, self-reported multipliers, urgency framing, "you must adopt X now."
*Why you care:* knowing what is oversold protects your time and your credibility more than
knowing one more trick.
Taught in: [The hype ledger](../curriculum/12-the-hype-ledger.md)

---

## I

### Inference
One run of the model: it reads the context, predicts the next chunk of text, and repeats.
Everything you experience as thinking, planning, or deciding is built out of this.
*Why you care:* it explains the pricing and the behaviour. The model re-reads the whole
context every turn, which is why long conversations get slow and expensive.
Taught in: [What the model actually is](../curriculum/01-what-the-model-actually-is.md)

### Injection (prompt injection)
When text the AI reads while working (a web page, an email, a document, a file comment)
contains instructions aimed at the AI, and the AI treats them as commands from you.
*Why you care:* anything the AI reads is data, not orders. If a document tells your assistant
to email a file somewhere, that is an attack, not a task. Say so in your rules, and expect
your tools to enforce it.
Taught in: [Safety, privacy and trust](../curriculum/10-safety-privacy-and-trust.md)

---

## L

### Loop (open and closed)
A loop is: act, observe the result, decide whether the goal is met, repeat. A **closed loop**
has a bounded goal and a clear check at each step. An **open loop** is told to go find work to
do and do it.
*Why you care:* closed loops are the default for almost everyone. Open loops discover things
you would not have thought of and burn budget wandering. Choose deliberately.
Taught in: [The loop](../curriculum/03-the-loop.md)

---

## M

### Maker-checker
A two-role shape: one AI does the work, a different one grades it. The checker never fixes;
the maker never grades its own work.
*Why you care:* it is the smallest possible structure that produces a real quality jump, and
it works for writing and analysis, not just code.
Taught in: [Verification](../curriculum/04-verification.md)

### Mastery track
The tracked list of topics this harness teaches, each one carrying what counts as knowing it, a
rung on the **understanding ladder**, and the dated evidence that justified the rung.
*Why you care:* it is the difference between a course and a folder of reading. It is also allowed
to go down as well as up, which is the only reason a mark on it is worth anything.
Taught in: [Mastery](../progress/MASTERY.md)

### MCP (Model Context Protocol)
An open standard for plugging outside tools and data sources into an AI, so any compliant AI
can talk to any compliant tool without custom wiring.
*Why you care:* it is the reason your assistant can touch your calendar or your notes at all.
It also means each server you add costs context whether or not you use it that day.
Taught in: [Tools and MCP](../curriculum/07-tools-and-mcp.md)

### Memory
Anything the AI knows across sessions rather than within one. In this harness memory means
plain files it reads and writes, not a mysterious internal store.
*Why you care:* memory in files is portable, inspectable, and correctable. You can open it,
fix a wrong fact, and hand the whole folder to a different AI tomorrow.
Taught in: [Memory and the second brain](../curriculum/06-memory-and-second-brain.md)

### Model
The trained system that produces the text: the engine. Providers ship several tiers, roughly
small and fast, mid and balanced, large and deliberate.
*Why you care:* choosing the tier is a real cost and quality decision, but it is the second
lever, not the first. Structure beats model choice more often than people expect.
Taught in: [What the model actually is](../curriculum/01-what-the-model-actually-is.md)

---

## O

### Orchestrator
The AI (or the person) that holds the plan, hands pieces of work to others, reads what comes
back, and decides what happens next. It should not be doing the detailed work itself.
*Why you care:* when one AI tries to plan, build, and check at once, all three suffer. The
separation is the point.
Taught in: [Subagents and swarms](../curriculum/08-subagents-and-swarms.md)

---

## P

### Permission mode
The standing setting for how much the AI may do without asking. Typical options: ask before
every action, auto-approve a named list of safe actions, plan only (read but never write), or
approve everything.
*Why you care:* the right setting is per task, not per person. Reading and drafting can be
loose. Sending, deleting, publishing, and paying should always stop and ask.
Taught in: [Safety, privacy and trust](../curriculum/10-safety-privacy-and-trust.md)

### Plan mode
A mode where the AI investigates and proposes an approach but is blocked from changing
anything until you approve.
*Why you care:* reading the plan is quick, and it catches the wrong-target mistakes, which are
the expensive ones. Use it whenever the job touches something you care about.
Taught in: [The loop](../curriculum/03-the-loop.md)

### Prompt
What you say to the AI. Specific beats vague by a wide margin: the goal, the constraints, the
format, and what "done" looks like.
*Why you care:* a good prompt gets you one good result. A good **skill** gets you that result
every time without retyping it.
Taught in: [Prompt patterns](PROMPT-PATTERNS.md)

### Provenance
Where a claim came from: read from a source, inferred by the model, or guessed. Tagging each
claim with its origin is a habit, not a feature.
*Why you care:* without it, inferences quietly become "facts" in your notes, and next month
you cannot tell which is which. Ask for sourced / inferred / uncertain tags on anything you
intend to keep.
Taught in: [Verification](../curriculum/04-verification.md)

---

## R

### Read-only auditor
A second agent pointed at the same folder as the first, with permission to read but not to change
anything, and asked to review what the first one did.
*Why you care:* it is the cheapest independent check that cannot quietly "fix" the thing it was
supposed to be judging — so what comes back is a finding you can act on rather than an edit you did
not see.
Taught in: [Running many models](../curriculum/17-many-models.md)

### Remote
A copy of a **repository** kept somewhere else, usually on a hosting service, that your machine can
exchange snapshots with. Sending yours up is called a push.
*Why you care:* it is the offsite copy and the place other people get your work from. Until you
push, your history exists on exactly one machine.
Taught in: [Git](../curriculum/15-git.md)

### Repository
A folder that version control is watching: the files, plus the entire history of snapshots taken of
them.
*Why you care:* "put this folder under git" and "make this a repository" are the same sentence, and
it is the sentence that makes letting an AI edit your files reversible.
Taught in: [Git](../curriculum/15-git.md)

### Router file
A short file the AI reads at the start of every session that says who you are, how you work,
and where to look for what. It routes; it does not contain everything.
*Why you care:* it is the difference between re-explaining your context every day and never
explaining it again. Keep it short, because it is paid for on every single turn.
Taught in: [Memory and the second brain](../curriculum/06-memory-and-second-brain.md)

### Rubric
An explicit scoring sheet: the criteria, what each score means, and what evidence justifies
it. Given to a checker so its judgment is comparable rather than moody.
*Why you care:* "score this out of 10" produces a number that means nothing. A rubric
produces a number you can act on and re-run next week.
Taught in: [Verification protocol](../protocols/VERIFICATION-PROTOCOL.md)

---

## S

### Second brain
A folder of plain files, organised so that both you and your AI can find things again. Notes,
decisions, references, project state.
*Why you care:* the test of a second brain is not how pretty it looks. It is whether the
answer can be found again in one hop. If not, the structure is wrong, not the AI.
Taught in: [Memory and the second brain](../curriculum/06-memory-and-second-brain.md)

### Session
One continuous conversation with its own context window. It starts empty, fills up as you
work, and ends when you close it or hand off.
*Why you care:* sessions are disposable and cheap to restart. Treating one as precious is how
you end up fighting **context rot** instead of just opening a new one.
Taught in: [Session protocol](../protocols/SESSION-PROTOCOL.md)

### Session log
The running file where one short entry is appended per session: what was attempted, what actually
got done, and what was accepted without being checked.
*Why you care:* an AI generally cannot read your other conversations. This file is how the system
remembers across them, and it is the reason a look back at last month is possible at all.
Taught in: [Session log](../progress/SESSION-LOG.md)

### Shell
The program running inside a **terminal** window that reads the line you typed and decides what to
do with it. Different systems ship different ones, and they understand different wording.
*Why you care:* it is the usual reason a command that worked for a colleague fails for you. Tell
your AI which system and shell you are on before asking for a command.
Taught in: [The terminal](../curriculum/16-the-terminal.md)

### Situation taxonomy
A named catalogue of the spots you actually find yourself in when working with AI — going in
circles, unsure whether an answer is right, doing the same thing for the fourth time — with what is
really happening in each and the next move.
*Why you care:* most stuck-ness is not a lack of ability, it is not knowing what kind of trouble you
are in. Once the situation has a name, the move is usually obvious.
Taught in: [Situations](../protocols/SITUATIONS.md)

### Skill
A saved playbook the AI loads when a matching task shows up: a description of when to use it,
step-by-step instructions, and the tools or scripts it needs.
*Why you care:* a prompt dies with the chat; a skill compounds. Every time a skill is used you
can sharpen it, so the version you have in month three is better than the one you wrote today.
Taught in: [Skills](../curriculum/05-skills.md)

### Slash command
A short typed shortcut that triggers a saved instruction or skill, usually written with a
leading slash.
*Why you care:* it turns a paragraph you keep retyping into three keystrokes, which is the
difference between a good habit you have and a good habit you actually use.
Taught in: [Skills](../curriculum/05-skills.md)

### Subagent
A separate AI worker started by your main one, with its own clean context window and its own
narrow assignment. It reports back a result rather than dumping its whole process into your
conversation.
*Why you care:* it is how big jobs stay tidy. The heavy reading happens somewhere else and
only the conclusion lands in your session.
Taught in: [Subagents and swarms](../curriculum/08-subagents-and-swarms.md)

### Swarm
Several agents working on one goal at the same time, usually with an **orchestrator** above
them and a verification step below them.
*Why you care:* impressive, occasionally correct, and frequently overkill. Most work needs the
checking half, not the parallel half. Reach for a swarm when the work genuinely splits into
independent pieces.
Taught in: [Subagents and swarms](../curriculum/08-subagents-and-swarms.md)

### System prompt
The standing instructions loaded before your conversation starts: the AI's role, rules, and
constraints. You often do not see it, but it shapes everything.
*Why you care:* your **router file** and your skills are effectively your own additions to it.
That is the layer where you get to define how the AI behaves for you specifically.
Taught in: [What the model actually is](../curriculum/01-what-the-model-actually-is.md)

---

## T

### Terminal
The window you open to type instructions to your computer directly instead of clicking. The window
is the terminal; the program inside it that understands what you typed is the **shell**.
*Why you care:* you need enough of it not to be afraid of it, not mastery — open it, know where you
are, move to a folder, run something, stop a runaway, and read an error well enough to paste it
somewhere useful. Everything else you can ask for.
Taught in: [The terminal](../curriculum/16-the-terminal.md)

### Token
The unit text is chopped into for the model: roughly a short word or a piece of one. Context
size and billing are both measured in tokens.
*Why you care:* it makes cost intuitive. A long document pasted into a chat is re-read on
every turn afterwards, so length is not a one-time charge.
Taught in: [The context window](../curriculum/02-the-context-window.md)

### Tool
Any capability the AI can invoke rather than imagine: read a file, run a search, send a
request, take a screenshot, run a script.
*Why you care:* tools are the difference between an assistant that describes your calendar
and one that reads it. When results are wrong, ask which tool produced them.
Taught in: [Tools and MCP](../curriculum/07-tools-and-mcp.md)

---

## U

### Understanding ladder
The four rungs a topic climbs on the **mastery track**: untouched, explained to you, explained back
by you, demonstrated on your own real work. Only the last one counts as known.
*Why you care:* it is evidence-before-done applied to your own education. It is why nothing gets
ticked off because you nodded, and why you should ask to see the evidence line behind any mark you
did not watch yourself earn.
Taught in: [Teaching protocol](../protocols/TEACHING-PROTOCOL.md)

---

## V

### Verification
Confirming the work is actually right, with evidence, by something other than the thing that
did the work.
*Why you care:* this is the load-bearing idea of the entire harness. Never let the worker
grade its own work; evidence comes before "done."
Taught in: [Verification](../curriculum/04-verification.md)

---

## W

### Worktree
An isolated copy of a project that one AI can work in without colliding with anyone else's
changes, merged back when the work is good.
*Why you care:* it is the practical answer to "can I run three of these at once?" Yes, if each
has its own space. In the same space, they overwrite each other.
Taught in: [Subagents and swarms](../curriculum/08-subagents-and-swarms.md)

---

## A note on words that go stale

Product names, model tier names, menu locations, and flag names change on a schedule nobody
publishes. The definitions above are written to describe mechanisms, which change slowly, and
to avoid naming specific versions, which change fast. If a term here does not match what your
tool calls it this month, the concept still applies. See
[Sources and provenance](SOURCES.md) for how to check anything time-sensitive.

## Try this now

Paste this into your AI and read what comes back before doing anything else:

```
Read reference/GLOSSARY.md in this folder.

Then quiz me. Pick the five terms you judge most load-bearing for someone
who has never used AI seriously at work. For each one:
1. Ask me to define it in my own words. Wait for my answer.
2. Tell me plainly whether I got it, and what I missed.
3. Give me one example from THIS kind of work: <describe your job in one line>.

Do not move to the next term until I have answered the current one.
At the end, tell me which of the five I understand weakest and which
curriculum file I should read first because of it.
```

## What you should now be able to do

- Read any file in this harness without stopping on unfamiliar vocabulary.
- Explain to a colleague, without notes, why a long chat gets worse and more expensive.
- Tell the difference between a claim ("done") and a receipt (the evidence), and ask for the
  second one by name.
- Spot when a term you have been given is a mechanism (durable) versus a product feature
  (likely to be renamed, and worth checking live).
