# 06 - Memory and the Second Brain

*How to give the AI a memory that survives the end of the chat - and why the hard part is not the AI. Read time: about 20 minutes. Doing time: about 30.*

---

## Start with the uncomfortable diagnosis

You are about to be told, by a lot of people, that your AI needs a better memory system. Vector databases. Knowledge graphs. Always-on sync. Before any of that, sit with this:

**The bottleneck is almost never retrieval. It is that the knowledge never left your head in the first place.**

You know your manager prefers decisions delivered as a recommendation plus two rejected options. You know the quarterly numbers get pulled from the finance export, not the dashboard, because the dashboard lags by a day. You know the client hates the word "solution." None of that is written down anywhere. It lives in your head, and your head does not have an API.

So when the AI produces something that misses all three of those things, the instinct is: the AI does not remember me. The accurate statement is: the AI was never told.

Run this check before you build anything:

> Before I blame the AI for not knowing something, can I point to the file where I wrote it down?

If you cannot point to the file, the problem is capture, not memory. And capture is a habit, not a technology. No amount of infrastructure fixes it. In my experience this is the most common way people waste effort here - building elaborate retrieval over an empty store.

The good news: capture is cheap. It is one step at the end of a session, which this file will give you word for word.

---

## What a second brain actually is

A second brain is a folder of plain text files that the AI reads and writes, sitting outside any single conversation.

That is the whole definition. Not a product. Not an app you subscribe to. A folder.

It exists because of a fact you already met in [The context window](02-the-context-window.md): the conversation is short-term memory and it is erased. Every new chat starts from zero. Anything that must survive has to live somewhere the AI can open on demand.

There is exactly one test of whether your second brain works:

> **Can it find it again?**

Not "is it tidy." Not "does it look impressive in a diagram." Can the AI, in a fresh session, with no memory of you, find the thing? If the answer is no, your structure is wrong. Not the AI.

And one design rule that follows from the test:

> **Work backwards from the question.**

Decide how you will ask for it later, then store it in the shape that answers that question. If you will later ask "what did we decide about vendor pricing," then a file called `decisions.md` with a line per decision beats a folder of meeting transcripts, every time. If you will later ask "what happened in the March 5 meeting," then the whole March 5 transcript as one file beats a database of scattered fragments.

Store for the question. Not for the storing.

---

## The five levels of retrieval

There are five ways to get information back out of a store. They escalate in power and in cost. The rule that matters more than anything else in this file:

> **Use the lowest level that kills your actual pain.**

Higher is not better. Higher is more expensive, more brittle, and more work to keep alive. You climb only when a specific, repeated, named pain forces you to - and you should be able to state that pain in one sentence before you climb.

| Level | The question it answers | What it is | What it costs you |
|---|---|---|---|
| **1. Files and keyword** | "Find the thing with this exact word in it" | Well-named plain files in folders. Search by keyword. | Nothing. Zero setup. |
| **2. Linked notes with a router** | "Pull together everything on this topic" | The same files, plus an index file at the top of each area that says what is where. | One sitting to set up. One line added to the index each time you add a file. |
| **3. Semantic search** | "I searched using different words than I wrote" | A search that matches meaning rather than exact words. | Setup, a running service, ongoing indexing. |
| **4. Knowledge graph** | "Trace the chain: who connects to what, through what" | Named things plus named relationships between them. | Real engineering. Real upkeep. |
| **5. Always-on agents** | "Keep the store current without me asking" | Scheduled jobs that read and write the store on their own. | Engineering plus trust plus watching it. |

### Level 1 - plain files, named well

You write things down as text files in folders. You find them by searching for a word you know is in them.

This sounds too simple to count as a system. It is the foundation of every level above it, and for a surprising amount of work it is sufficient on its own. The AI can list a folder, open a file, and search for a word. That is three capabilities and they cover a lot of ground.

Level 1 works when your store is small enough that you roughly remember what is in it, and your file names are honest. It stops working when you have enough files that the AI does not know which folder to look in - and, importantly, an AI will not reliably search your whole store on its own initiative. Reading everything is slow and expensive, so by default it does not try. Which is exactly what Level 2 fixes.

### Level 2 - linked notes with a router

Same files. You add one thing: an **index file** at the top of each area that says what lives where, and links between notes that belong together.

The index file is often called a **router**, because its job is to route: it sends the AI to the right file rather than containing all the content itself. The AI reads the router (cheap, short) and then opens only the one or two files it actually needs (also cheap). It never has to read everything.

**This is where most people should stop.** Level 2 covers the overwhelming majority of real needs: your preferences, your projects, your decisions, your recurring documents, your notes on people and processes. Practitioners who teach this material say plainly that routed plain text is enough for nearly all personal memory. Treat that as their considered judgment from experience, not as a measured result - nobody has run a controlled study on your filing habits. But the judgment is consistent across the practitioners who actually run these systems, and it matches what you will find yourself: the failures at this level are almost always missing content, not missing retrieval power.

### Level 3 - semantic search

Semantic search matches by meaning instead of by exact word. You search "how do we handle unhappy customers" and it surfaces a note titled "escalation policy" that never uses the word "unhappy."

The pain that justifies it: **your vocabulary and your notes' vocabulary have drifted apart.** You have enough material, written over enough time, by enough different people, that you genuinely cannot guess the words that are in the file. That is a real pain and semantic search is the real fix for it.

Two honest warnings before you get excited:

1. **It is bad at whole-document questions.** Semantic search works by cutting documents into pieces and finding the pieces that seem related. Ask it to summarize a specific meeting and it hands back a few fragments that resemble your question - not the whole meeting. Ask it for the highest number in a long report and it may return one chunk containing a number, having never seen the larger ones. When you need completeness, read the whole file. Semantic search is a way to find the file, not a substitute for reading it.
2. **It is not magic and it is not free.** Something has to index your notes, keep the index current, and run when you search. That is a service to install, feed, and fix.

### Level 4 - a knowledge graph

A graph stores things *and the named relationships between them*: this person works at that company; this company was recommended by that person; this document supersedes that one.

The pain that justifies it: **the relationships matter more than the things.** You are constantly asking questions of the form "how does X connect to Y, and through whom." If you find yourself manually tracing chains through notes, over and over, a graph is the right shape.

If you cannot name that pain out loud, you do not have it. Building a graph because it produces a beautiful diagram is the single most seductive waste of time in this whole space.

### Level 5 - always-on agents

Scheduled jobs that read and write your store without being asked: a nightly pass that files new notes, a morning pass that assembles a brief, a watcher that updates a status file when something changes.

The pain that justifies it: **the capture step is failing because you are not doing it**, and the work is boring, repeatable, and low-stakes enough that a machine can do it unattended.

The gate here is not technical. It is trust. Something that writes to your memory without you watching can also corrupt it without you watching. Start it on the most boring, most reversible thing you have. There is more on earning that trust in [Safety, privacy, and trust](10-safety-privacy-and-trust.md).

### The blunt summary

Levels 3, 4 and 5 are usually premature. They are the most common form of wasted effort in this area, and they are attractive for exactly the wrong reason: they feel like building a system, whereas writing down what your manager wants feels like admin.

Anything you see marketed as a memory product that "beats" another memory product is a marketing claim from the company selling it, not a measurement. See [The hype ledger](12-the-hype-ledger.md).

---

## The four rules that make a plain file store work

Level 2 is where you are going to live. These four rules are the difference between a store that gets better every month and one that rots.

### Rule 1 - one fact in one place, and link instead of copy

Every fact gets exactly one home. When another file needs it, that file points at the home rather than repeating it.

The moment a fact exists in two files, it is on a countdown. One copy gets updated, the other does not, and now your store contains two answers and no way to tell which is current. An AI reading both will pick one, probably the wrong one, and will not tell you there was a conflict.

The habit: when you find yourself pasting something you already wrote, stop. Write `see projects/acme/pricing.md` instead.

### Rule 2 - a router file at the top of every area

Each folder gets one file whose only job is to say what is in the folder and when to open each thing. It is a table of contents, not a container.

Two properties matter. It must be **short** - a router that grows into an essay stops being cheap to read and starts competing with the content. And it must be **honest** - a router that lists files that no longer exist is worse than no router, because it sends the AI confidently to nothing.

### Rule 3 - archive, do not delete

When something stops being true, move it to an `archive/` folder rather than deleting it. Mark the top of the file with the date it stopped being current and what replaced it.

Two reasons. First, "we used to do it this way and changed" is genuinely useful context, and you cannot reconstruct it later. Second, deletion is the one operation with no undo, and you are handing file access to a system that occasionally misreads instructions. Archiving makes every mistake recoverable.

The corollary: the router should not point at the archive. Archived material is available when asked for, not loaded by default.

### Rule 4 - capture at the end of the session, as an explicit step

**There is no automatic memory.** Some tools have a feature with "memory" in the name that saves a bit of what it judges worth saving. Treat that as a bonus, never as the mechanism. Anything it did not think to record is gone, and you will not find out until you need it.

So capture is a step you take, deliberately, at the end of a working session. Not during - during, you are working, and stopping to file things kills the work. At the end, when the useful conclusions actually exist.

This is a habit, and habits need a trigger. The trigger is: **the session is ending.** The action is the prompt in the next section, pasted verbatim.

---

## The folder shape to start with

Start here. Adapt it after a month of real use, not before - you cannot design a filing system for work you have not done yet.

```
brain/
  ROUTER.md              <- the top-level map; read first, every session
  about-me.md            <- how you work, what you prefer, how to talk to you
  people.md              <- who is who, what they care about, how they like things
  decisions.md           <- append-only log: date, decision, why, what we rejected
  projects/
    ROUTER.md            <- what projects exist and their state
    <project-name>/
      brief.md           <- what this is, who it is for, what done looks like
      notes.md           <- running log, newest at the top
  reference/
    ROUTER.md            <- what reference material exists
    <topic>.md           <- one file per stable topic
  archive/
    ...                  <- anything no longer true, dated, never in a router
```

Six notes on this shape:

- **`ROUTER.md` at the top is the only file that is always read.** Everything else is opened on demand. That is the whole point.
- **`decisions.md` is append-only.** You add to the bottom, never rewrite the middle. A decision that later changed gets a new entry saying so. The history is the value.
- **One file per topic, not one folder per topic.** Folders multiply faster than content. Split a file into a folder when the file gets genuinely unwieldy, not in anticipation.
- **File names are search terms.** `q3-pricing-decision.md` is findable. `notes2.md` is not. Name the file the way you will later ask for it.
- **Newest at the top** inside running logs, so the current state is visible without scrolling.
- **Plain text, always.** Markdown files open in anything, live for decades, and can be read by any AI you switch to later. Do not put your memory somewhere only one product can read.

### What to put in it, and what to leave out

There is a useful split between two kinds of information:

| Kind | Examples | What to do |
|---|---|---|
| **Stable** | Decisions, preferences, how a process works, who cares about what, project briefs | Write it into the store |
| **Volatile** | Today's inbox, a live chat thread, current ticket status, this week's numbers | Do **not** write it into the store. Make sure the AI can go get it when needed |

Volatile information rots. If you copy today's inbox into your store, then next month your store confidently tells you something that stopped being true four weeks ago - and it looks exactly as authoritative as the parts that are still correct. A stale file is worse than a missing one.

The way to handle volatile information is a live connection, covered in [Tools and MCP](07-tools-and-mcp.md). Store the stable; fetch the volatile.

### Mark what the AI wrote

One more habit, small and worth it: when a file was written or summarized by the AI rather than by you or a source document, say so at the top of the file.

```
Source: AI summary of the 2026-03-05 vendor call transcript. Not verified against the recording.
```

Why: the summary might have dropped or distorted something, and six months from now you will have no way to tell a distillation from an original. Worse, the AI will read its own summaries as ground truth and summarize those, and each round drifts further from what actually happened. Keeping originals distinguishable from distillations stops that drift. This connects directly to the provenance discipline in [Verification](04-verification.md): tag what you know versus what you inferred.

---

## What a router file actually looks like

People hear "index file" and write four vague lines. Here is a complete one. Read it as a template - the shape is what matters, not the specific projects.

```markdown
# ROUTER - read this first, every session

This folder is my working memory. You are reading the router. Its job is to tell
you which file to open. Do not read every file - open only what the task needs.

## How to use this file

1. Read this router.
2. Open the ONE file the current task points to.
3. If that file points to another, follow it. Stop when you have what you need.
4. If nothing here covers the task, say so and ask. Do not guess and do not
   read the whole folder.

## Always read at the start of a session

- `about-me.md` - how I work, what I prefer, how to write for me.

## Routing rules

| If the task involves... | Open |
|---|---|
| How I like things written, tone, formatting | `about-me.md` |
| A person, their preferences, their role | `people.md` |
| Why something was decided, or what we already rejected | `decisions.md` |
| Any named project | `projects/ROUTER.md`, then that project's folder |
| Background on a topic, a process, a system | `reference/ROUTER.md` |
| Something that used to be true and no longer is | `archive/` - only if I ask |

## Live data - not stored here

These change daily and are deliberately NOT in this folder. Fetch them at the
time of asking; never quote a stored copy:

- Current ticket and project status
- Anything in email or chat
- This week's numbers

## Rules for writing to this folder

- One fact in one place. If it is already written somewhere, link to that file
  rather than repeating it.
- New decisions go at the BOTTOM of `decisions.md`, with the date, the decision,
  the reason, and what was rejected. Never edit an existing entry - add a new one
  that supersedes it.
- Never delete. Move it to `archive/`, add a line at the top saying the date it
  stopped being true and what replaced it, and remove it from the routing table.
- If you write or summarize a file yourself, put a line at the top saying so.
- When you add a file, add its row to the routing table above in the same turn.
  A file that is not in the table does not exist as far as future sessions know.

## Known gaps

Things I know are missing. If a task touches one of these, tell me it is missing
rather than inventing an answer:

- Nothing recorded yet about the annual planning cycle.
- Nothing recorded yet about how the reporting pipeline actually works.
```

Notice what that router does that a vague index does not:

- It tells the AI **how to read it** (open one file, not all of them).
- It gives explicit **routing rules** as a table, so matching is mechanical.
- It names what is **deliberately absent** and must be fetched live.
- It states the **write rules**, so the AI maintains the store correctly instead of pasting duplicates everywhere.
- It lists **known gaps**, which converts a silent hole into an honest "I do not have that."

That last section is the one people skip and the one that pays. An AI that knows what it does not know will tell you, instead of filling the hole with something plausible.

---

## The end-of-session capture prompt

This is the habit. Paste this at the end of any session that produced something worth keeping. Word for word.

```
We are wrapping up. Do the memory capture step.

1. List everything from this session that is worth keeping. For each item say
   which category it is:
   - a decision (what we chose, why, what we rejected)
   - a preference of mine you learned
   - a fact about a person, process, or system
   - a correction (something you got wrong and how I corrected it)
   Leave out anything volatile - status, numbers, or anything true only today.

2. For each item, tell me which existing file it belongs in, and whether it
   would duplicate something already there. If it duplicates, say what should be
   updated instead of adding a copy.

3. Show me the exact text you propose to add to each file, as a diff or a
   quoted block. Do not write anything yet.

4. Wait for me to approve. Then write it, and update the routing table in the
   relevant ROUTER.md in the same turn.

If nothing from this session is worth keeping, say that plainly. Do not invent
entries to look thorough.
```

Why each part is there:

- **Categories** stop you from getting a shapeless blob. Decisions, preferences, facts, and corrections are what compound; narration of what happened does not.
- **"Which file, and does it duplicate"** enforces Rule 1 at the moment the violation would happen.
- **"Show me before you write"** is a verification gate. It is the same principle as everywhere else in this harness: the worker does not get to grade its own work. See [Verification](04-verification.md).
- **"Update the routing table in the same turn"** prevents the most common decay: files that exist but nothing points to, which is functionally the same as not having written them.
- **"Say plainly if nothing is worth keeping"** removes the pressure to produce output, which is what generates filler.

Run this often enough and it becomes automatic. When it does, turn it into a skill so it is one word instead of a paste - that is exactly what [Skills](05-skills.md) is for, and the session-end sequence is written up in [SESSION-PROTOCOL.md](../protocols/SESSION-PROTOCOL.md).

---

## How a store like this rots, and how to notice

Four failure modes. Each has a tell you can check for in under a minute.

| Failure | What it looks like | The tell | The fix |
|---|---|---|---|
| **Empty store** | The AI keeps asking things you thought it knew | You cannot point at the file | Capture. Nothing else. |
| **Duplicate facts** | Two answers to the same question, one stale | Search a key phrase, find it twice | Delete one, replace with a link |
| **Orphan files** | Real content nobody ever finds | A file not listed in any router | Add it to the router or archive it |
| **Bloated router** | Sessions feel slow and unfocused from the start | The router is longer than a screen | Move content into files, leave pointers |

Bloated router deserves a note. The router is read every session, so its length is a permanent tax on every conversation you will ever have. When it starts accumulating actual content instead of pointers, sessions get more expensive and, worse, the important routing rules get buried among detail. Keep it to a screen. Push everything else down into files. This is the same context budget discipline as [The context window](02-the-context-window.md), applied to memory.

More failure patterns are collected in [FAILURE-MODES.md](../protocols/FAILURE-MODES.md).

---

## The harness's own memory: your learner file

You do not have to imagine this. The harness you are reading has a working second brain, and you are in it.

[`progress/LEARNER.md`](../progress/LEARNER.md) is your file. The AI reads it at the start of a session to know where you are, and updates it as you go. It is not decoration and it is not a certificate - it is a live memory file that changes the AI's behavior. When it says you have already covered verification, the AI stops re-explaining verification. When it records that you found subagents confusing, the AI slows down there next time.

Two sibling files complete the picture:

- [`progress/SKILLS-BUILT.md`](../progress/SKILLS-BUILT.md) - what you have codified, so nothing gets built twice.
- [`progress/DECISIONS.md`](../progress/DECISIONS.md) - what you chose and why, so a future session does not quietly reverse a decision you already made.

Between them, those three files are a complete Level 2 second brain: a small set of well-named files, an index that routes to them, one fact in one place, and an explicit capture step at the end of every session. Same rules, smaller scale. If you want to see what the pattern feels like from the inside, work through a few sessions and then open `LEARNER.md` and read what accumulated. That accumulation is the entire point of this file.

When you finish the harness, the natural next move is to build the same shape for your actual job - starting with the folder above, and nothing more.

---

## Try this now

Open your AI and paste this. If your AI can write files, point it at a folder you can write to. If it cannot, it will hand you the file contents as text and you save them yourself - the exercise works either way.

```
I want to build the smallest useful second brain: plain files plus one router.
No database, no semantic search, no graph. If you are ever tempted to suggest
one of those, do not - tell me instead which pain would justify it.

Step 1 - interview me. Ask me one question at a time, up to six questions total,
to pull out things I currently keep only in my head about my work. Aim for:
how I like written output, who the recurring people are and what they care
about, what decisions have already been made that a newcomer would get wrong,
and which tasks I repeat. Do not ask more than one question per turn, and do
not summarize until the interview is finished.

Step 2 - when the interview is done, propose a folder structure. Use only:
ROUTER.md, about-me.md, people.md, decisions.md, and a projects/ folder.
Show me the proposed contents of each file before writing anything.

Step 3 - after I approve, write the files out. If you can save files, save them.
If you cannot, print each file in its own block so I can save it myself. Write
ROUTER.md as a routing table that says which file to open for which kind of
task, plus a "known gaps" section listing what I clearly have not told you yet.
```

Then do the part that is actually the test. Open a **brand new chat** - one that has never met you - give it only the text of `ROUTER.md`, and paste this:

```
This is the only thing you know about me. For the task "draft an update for my
manager," which file would you open first, and why? Name exactly one file. If
this router does not make the answer obvious, tell me what is missing from it.
```

That second chat is the exercise. Building the folder proves nothing. Making a cold read of the router land on the right file is the test - and the test is "can it find it again." It has to be a new chat, because a chat that just interviewed you already knows the answer and cannot tell you whether the router does.

---

## What you should now be able to do

- Diagnose whether a memory problem is a **capture** problem or a **retrieval** problem, and stop reaching for infrastructure when the store is simply empty.
- Name the five retrieval levels, state the specific pain that would justify climbing to each one, and defend staying at level 2 - which is where nearly all real work sits.
- Set up a plain file store that survives contact with reality: one fact in one place, a short honest router at the top of each area, archive instead of delete, and a deliberate capture step at the end of every session.
- Write a router file that a cold session can follow to the right file on the first try, including a "known gaps" section so the AI says "I do not have that" instead of inventing it.
