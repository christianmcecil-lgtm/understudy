# Understudy

**A teaching harness for working with AI.**

*Start here. What this folder is, and how to get something useful out of it today. Read time: 6 minutes.*

An understudy learns a role by working alongside someone who already has it, until they can
play it themselves. That is what this folder does. You point your AI at it, and it becomes your
teacher — one that tracks what you actually understand, checks its own work, and hands the role
over to you rather than keeping it.

## What this is

This is a folder you hand to an AI. Once it reads the folder, the AI stops behaving like a
search box that talks and starts behaving like a colleague who is teaching you the job: it
explains what it is doing while it does it, keeps notes about what you have learned and
decided, checks its own work before it hands anything to you, and gets a little more useful
every week because you and it keep writing things down. You do not need to be technical, and
you do not need to read all of it — five minutes gets you the first useful result.

## Two things before you start

**Start a brand new conversation.** Not a continuation of whatever you were doing. An old
conversation is already full of unrelated material that the AI re-reads every turn, and it will
compete with the teaching.

**Use the mid model, not the top one.** Almost every assistant has three tiers — small and fast,
mid, top — and a teaching session is reading, explaining and conversation, which the mid tier
does well. Running every lesson on the top tier mostly buys you fewer sessions rather than better
teaching, so on a standard paid plan the mid tier is the right choice, not the budget choice. Use
the top tier for your **first** session, though: it has to read the whole system at once.

[BOOTSTRAP.md](BOOTSTRAP.md) has the rest of it before you paste anything — the other two
occasions worth the top tier, why checking is a different question, and how to find out what your
own assistant's tiers are actually called this month.

## The 60-second version

**Step 1.** Open [BOOTSTRAP.md](BOOTSTRAP.md) and do what it says. It is one page and it is the
whole setup: put this folder where your AI can read it ([INSTALL.md](INSTALL.md) covers three
different setups — pick yours, read only that section), open a brand new conversation, and paste
the one block of text it gives you. From the moment you paste it, the AI is your teacher: one
topic at a time, keeping your place in [MASTERY.md](progress/MASTERY.md), and quizzing you later
on the things you covered last month.

**Step 2.** When you want to see what this could do for your own job, paste this:

```
/whats-possible
```

If slash commands do not work in your setup, paste this instead:

```
Run the whats-possible procedure on me now, following
.claude/skills/whats-possible/SKILL.md exactly. Ask me its questions one at a
time and wait for my answer. If you cannot see that file, say so and I will
paste it.
```

That second step starts with a short interview about your real work — what you actually do, what
you dread, what you wish you had more time for. It then shows you five directions built out of
your own answers rather than out of generic AI examples, and finishes by doing one of them with
you, for real, before the conversation ends. You come away holding a result, not a plan.

## What you actually get

**It teaches while it answers.** You can ask this AI anything — write the email, fix the
spreadsheet, summarise the meeting — and it will do the thing. The difference is that it also
tells you what it just did and why, and points out when there was a better way to ask. You
learn by working, not by studying.

**It remembers.** There is a `progress/` folder. As you go, the AI writes into it: what you
have covered, what you found hard, which decisions you made and why, which procedures you have
codified. That means the second month does not start from zero the way the first one did.

**It checks its own work.** The core habit this folder installs is that "done" means proven,
not asserted. When the AI finishes something, it is supposed to show you what it checked and
how — and when judgment is involved, hand the work to a second, separate checker that did not
do the work. That one habit is the highest-return thing in here.

**It improves as you use it.** This is a live folder, not a book. When you codify something
you do repeatedly, it gets written down and reused. When a file here explains something badly,
you can tell the AI to fix that file. The copy you pass on in a year should be better than the
copy you received.

## What this is not

**Not a course you sit through.** There is a curriculum, but nothing here requires you to read
it front to back, and reading it front to back is probably the worst way to use it.

**Not a prompt pack.** Clever prompts are the least durable part of this field. What is in here
is the shape of the system around the prompts — memory, checking, and codified procedure —
because that is the part that keeps working after the models change.

**Not magic, and not a shortcut past thinking.** This will not make you a programmer, will not
make you an expert in your field, and will not work equally well for every job. Work that is
mostly physical, mostly in-person, or mostly governed by rules you are not allowed to automate
has a smaller slice for this to touch. Find out which slice yours is.

**Not a substitute for your judgment, and not permission.** The AI will be confidently wrong
sometimes. You stay accountable for what you send, sign, and ship. Before you point any AI at
real work data, read [Safety, privacy, and trust](curriculum/10-safety-privacy-and-trust.md)
and check with whoever owns that decision where you work. This folder cannot grant it.

## How to use it

**Mode 1 — just work.** Ask it anything, the way you already would. Because it has read this
folder, it will teach while it answers and it will flag its own uncertainty instead of papering
over it. This is the mode you will spend most of your time in.

**Mode 2 — you do not know what to ask.** Run `/whats-possible`. It asks about your actual job,
shows you five directions drawn from your own answers, and then does one of them with you on the
spot. Use this when you suspect there is a better question than the one you are asking. If what
you want instead is a ranked list of what to hand over first, boring-and-reversible at the top,
run `/grill-me`.

**Mode 3 — you want to be taught properly.** Run `/learn`. The AI walks you through the
curriculum one piece at a time, with an exercise after each, checking you understood before it
moves on, and saving your place so you can stop and pick it up next week.

## The map

| File | In one line |
|---|---|
| [00 Orientation](curriculum/00-orientation.md) | The frame, the whole map, and what this promises you. |
| [01 What the model actually is](curriculum/01-what-the-model-actually-is.md) | A correct mental model of the thing you are talking to. |
| [02 The context window](curriculum/02-the-context-window.md) | Its short-term memory, and why long chats get worse. |
| [03 The loop](curriculum/03-the-loop.md) | Handing over a goal instead of prompting every step. |
| [04 Verification](curriculum/04-verification.md) | Making it prove things. The spine of everything here. |
| [05 Skills](curriculum/05-skills.md) | Turning work you repeat into a procedure that compounds. |
| [06 Memory and the second brain](curriculum/06-memory-and-second-brain.md) | Files it reads and writes, so it stops forgetting you. |
| [07 Tools and MCP](curriculum/07-tools-and-mcp.md) | How it reaches your real systems and acts, not just advises. |
| [08 Subagents and swarms](curriculum/08-subagents-and-swarms.md) | Delegating to specialists, and when not to. |
| [09 Cost, models, and effort](curriculum/09-cost-models-and-effort.md) | The two levers that control what this costs you. |
| [10 Safety, privacy, and trust](curriculum/10-safety-privacy-and-trust.md) | What leaves your machine, and how to earn trust in stages. |
| [11 First 90 days](curriculum/11-first-90-days.md) | A concrete sequence for a new job. |
| [12 The hype ledger](curriculum/12-the-hype-ledger.md) | Widely repeated claims that are not supported, and how to spot the next one. |
| [13 Graduation](curriculum/13-graduation.md) | Curiosity as the actual skill, and how to keep going without this folder. |
| [14 The skill library](curriculum/14-the-skill-library.md) | Every command and specialist in here, what each is for, and how they chain. |
| [15 Git](curriculum/15-git.md) | The undo history that makes it safe to let an AI change your files. |
| [16 The terminal](curriculum/16-the-terminal.md) | What it is, why it is useful, why it is unforgiving, and the little you need. |
| [17 Many models](curriculum/17-many-models.md) | Why a second model catches what the first one cannot, and how to do it today. |

Also here: `protocols/` (procedures the AI follows), `reference/` (glossary and copy-pasteable
wording), `.claude/` (commands and specialists). [00 Orientation](curriculum/00-orientation.md)
lists every one of them.

## An honest note

Whoever gave you this spent a long time working out which parts of this actually hold up. Most
of that time was wasted. The public conversation about AI is overwhelmingly numbers and
excitement — multipliers, benchmark charts, screenshots of enormous output, an implication that
you are already behind. Very little of it survives contact with a normal week of work.

The parts that do survive are unglamorous. Write things down so you stop re-explaining them.
Make it check its work instead of trusting it. Give it a clear definition of finished. Start
with the boring, reversible task rather than the impressive one. None of that makes a good
video. All of it is in here.

So this folder is not trying to impress you. It is trying to save you the search. If you find
something in here stated more confidently than the evidence supports, that is a defect — say so
to the AI and have it corrected. That standard applies to this file too.

## Where your stuff goes

Everything you produce lands in `progress/`. That folder is yours, and it is six files: where you
are on the course ([MASTERY.md](progress/MASTERY.md)), what you have learned
([LEARNER.md](progress/LEARNER.md)), one short entry per session so a later conversation knows
what already happened ([SESSION-LOG.md](progress/SESSION-LOG.md)), the procedures you have
codified ([SKILLS-BUILT.md](progress/SKILLS-BUILT.md)), the decisions you made and why
([DECISIONS.md](progress/DECISIONS.md)), and the reviews of how you are working and what to
change next ([REVIEWS.md](progress/REVIEWS.md)).

It starts nearly empty. It will grow. Back it up like anything you would hate to lose, and if
you hand this folder on, decide whether `progress/` goes with it — that part is about you.

One caveat, since it decides how much work you do by hand: only an AI that can write files on
your computer updates `progress/` by itself. In a chat app it usually cannot, so you ask it for
the text and paste it in. [INSTALL.md](INSTALL.md) says which case you are in and gives you the
wording.

Setup instructions: [INSTALL.md](INSTALL.md).
