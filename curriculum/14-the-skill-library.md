# The Skill Library

*A guided tour of every skill and every worker that ships inside this folder — what each one is for, when it fires, what it actually does, and how they chain together. Read time: about 25 minutes.*

---

## What you already own

[05 Skills](05-skills.md) taught you what a skill is: a file describing a job, which your AI
reads when the job comes up. This chapter is about the ones that came in the box.

This folder ships **eleven skills and five workers**. You did not build any of them, and the map in
[00 Orientation](00-orientation.md) gives each one a single line — enough to know it exists, not
enough to reach for it. They cover the moments this harness expects you to hit — not knowing
what to ask for, being stuck, having done the same thing three times, not trusting an output, a
session that has gone bad, wanting to know whether you are actually improving.

The point of a tour is not that you memorise the list. It is that when one of those moments
arrives, something in the back of your head says *there is a thing for this*. That is the whole
goal of this chapter.

Two kinds of thing live in here, and they behave differently:

| | **Skills** | **Workers** (also called subagents or agents) |
|---|---|---|
| Where they live | `.claude/skills/<name>/SKILL.md` | `.claude/agents/<name>.md` |
| Who starts them | You, by typing or by phrasing a request | Your AI, on your behalf, usually inside a skill |
| What they are | A procedure your AI follows | A separate worker with an empty memory, given one job |
| Do you call them by name | Yes — `/verify-this` | Rarely. You ask for the outcome and the dispatch happens |

If your setup does not support slash commands, none of this is lost. You say the procedure by
name instead — "follow `.claude/skills/verify-this/SKILL.md` on the draft above" — or you open the
file and paste it. [INSTALL.md](../INSTALL.md) covers the difference per environment.

---

## The index

Skim this once. The detail is below.

| Skill | Reach for it when | It ends with |
|---|---|---|
| `/whats-possible` | You do not know what to ask for | One real finished thing, plus a receipt |
| `/grill-me` | You know AI should help but not where | Exactly three candidates, ranked |
| `/im-stuck` | You cannot even name the problem | The situation named, and the first move made |
| `/skillify` | You have now done this three times | A tested skill file, logged |
| `/verify-this` | You are about to act on something | A per-claim verdict and one recommendation |
| `/learn` | You want to be taught, not to read | One tracked topic, done on your real work |
| `/quiz` | You are not sure what has stuck | An honest tracker, up or down |
| `/coach` | Mid-task, something feels clumsy | One intervention, then the task back |
| `/review-my-work` | You want to know if you are improving | One change to make today |
| `/recall-session` | You need something from a past session | What was decided, built, and left open |
| `/handoff` | This conversation has gone stale | A short document and the text to paste |

| Worker | Dispatched to | Never does |
|---|---|---|
| `verifier` | Check claims against primary sources | Fix anything |
| `adversary` | Try to break a conclusion | Give you a balanced view |
| `scout` | Answer one narrow factual question | Recommend, compare, or synthesise |
| `teacher` | Explain one concept using your own material | Do your work for you |
| `reviewer` | Run one lens over a window of past sessions | Write the review itself |

---

## Group one — finding the work

### `/whats-possible`

**For:** the door-opening problem. You cannot want something you have never seen, and no amount
of willingness fixes not knowing what to ask for.

**Fires on:** "I don't know what's possible", "what should I be using this for", "show me
something ambitious", "I feel like I'm barely scratching the surface" — and on a first session
with someone who has no stated goal.

**What it actually does:** asks exactly three questions, one at a time, about your actual job —
what you do day to day, what part of the week you dread, what you wish you had more time for.
Then it offers five doors named for motivations rather than technologies (make the boring thing
disappear; know things you could not know before; never lose anything again; do work that used to
need a team; catch your own mistakes before anyone else does), with the examples built out of
your own words. Then it names one adjacent thing you did not know to ask for. Then — the part
that matters — it **finishes one real piece of work inside the conversation**, shows the evidence,
and says plainly what it could not confirm.

**What it refuses to do:** end in a plan. That rule overrides everything else in the file. If the
conversation produces a roadmap and no output, it failed, however good the discussion was.

**One real moment:** your first week in a new job, before you know what the tools are. Run it, and
walk out with one finished artifact and the name of the pattern that produced it.

It also has a "go wilder" mode for repeat runs, where everything ambitious comes paired with an
honest cost and an honest failure mode. And it reads
[`progress/LEARNER.md`](../progress/LEARNER.md) first, so a second run starts from where the last
one stopped rather than re-offering the same five doors.

### `/grill-me`

**For:** the opposite problem. You are willing, you have a week full of work, and you cannot see
which part of it is the automatable part — because you stopped noticing it years ago.

**Fires on:** "what should I automate", "audit my workflow", "I don't know what to build",
"interview me about my job".

**What it actually does:** interviews you, one question at a time, in plain text, with **no
suggestions until the interview is over** — because the moment it starts proposing, you start
agreeing instead of telling it things. The sequence walks through last Monday hour by hour, what
recurs, what you dread, what you redo, what you wait on, what breaks, and what would fall over if
you were away for two weeks. Then it plays back what it heard and asks what it got wrong. Then it
builds a table of candidates in your words, and recommends **exactly three**, ranked by how often
the task recurs against how much work the fix is.

**What it refuses to do:** recommend more than three, rank by how impressive something would be,
or stay quiet about a task that should not be automated at all.

**One real moment:** two weeks into a job, when someone asks what you are going to use AI for and
you do not want to answer with a guess.

It also teaches the friction log — one line written in the moment something annoys you, never
after. Bring that to the next run and it becomes the agenda.

### `/im-stuck`

**For:** the state where you cannot even ask a good question, because you do not know what kind of
trouble you are in.

**Fires on:** "I'm stuck", "I don't know what to do", "where do I go from here", "this isn't
working and I don't know why" — or on you describing a mess with no question attached.

**What it actually does:** asks **one** question — what were you trying to do, and what actually
happened — and then classifies your answer against
[`protocols/SITUATIONS.md`](../protocols/SITUATIONS.md), a catalogue of twenty named situations.
Then it does the thing that makes it a teacher rather than a menu: it tells you what the situation
*is*, what causes it mechanically, and **how you will recognise it next time without asking**.
Then one route, with the literal wording to use, and it walks the first step with you here rather
than sending you away with an assignment.

**The premise, and it is worth carrying around:** most stuck-ness is not a lack of ability. It is
not knowing what kind of situation you are in. Once it has a name, the move is usually something
you already knew how to do.

Underneath the catalogue is a coarser question that routes most cases on its own: is the problem
the **goal**, the **information**, the **checking**, or the **conversation itself**? Learn those
four and you need the catalogue less.

**What it refuses to do:** force a match. If nothing in the catalogue fits, it says so, reasons it
out with you from first principles, and then adds the new situation to the file — the taxonomy is
supposed to grow.

---

## Group two — building and checking

### `/skillify`

**For:** the moment a piece of work stops being a one-off. This is the skill that turns effort into
an asset, and it is the one with the most compounding attached to it.

**Fires on:** "make this a skill", "save what we just did", "I do this every week", "I don't want
to explain this again".

**What it actually does:** reads [`progress/SKILLS-BUILT.md`](../progress/SKILLS-BUILT.md) first,
because two things there decide whether it should build at all — whether an existing skill already
covers this (sharpen that one instead), and the **rule of three**: a task earns a skill on its
third real occurrence, and earlier ones go in the Candidates table with a note on what varied.
Then it takes one real run of the work, splits it out loud into the repeatable core and the
one-off specifics, names it, and drafts all three layers — description, instructions, and the
tools layer of templates, checklists and scripts that most people skip. Then it **tests the new
skill on a different real example**, ideally with a reader who was not in the conversation that
wrote it. Then it logs a row with a usage count of zero.

**What it refuses to do:** count a usage it did not watch happen, or ship a skill with no
objective done-check.

**One real moment:** the third Wednesday you retype the same instructions from memory.

It also carries the **sharpening rule**, which applies after every later run of any skill: was
that correction a one-time fix, or something the skill should handle forever? If forever, the file
gets updated while the correction is still fresh. A skill that never changes after the day it was
written is not compounding.

### `/verify-this`

**For:** anything you are about to act on, send, or repeat to another person. This is the
invocable form of [the verification protocol](../protocols/VERIFICATION-PROTOCOL.md), and
[04 Verification](04-verification.md) is the chapter behind it.

**Fires on:** "check this", "is this right", "before I send this", "are you sure", "did you make
this up".

**What it actually does, in order:** lists every load-bearing claim explicitly — a claim is
load-bearing if you would do something different were it false — and shows you that list, which is
often the moment you realise how many assertions were sitting in two paragraphs. Then it tags each
claim as sourced, inferred, or uncertain. Then it picks the strongest check actually available per
claim: a deterministic one where possible (re-read the source, recount it, open the link,
recompute by a second route), independent judgment where the question needs judgment, structured
self-review only for low-stakes reversible claims. Then it runs the checks — dispatching the
[verifier](../.claude/agents/verifier.md) and the [adversary](../.claude/agents/adversary.md) if
it can, and saying plainly that it is in degraded mode if it cannot. Then a verdict table with
evidence on every row, an explicit statement of what could not be checked, corrections shown next
to the originals, and exactly one recommendation: **safe to send**, **needs the marked fixes**, or
**do not send**.

**What it refuses to do:** improve the work. While this skill is running, your AI is the checker
and not the author. It also refuses to fold if you push back on a finding without new evidence,
and it stops after two failed attempts at the same claim rather than trying a third time — a third
attempt finds new wording, not new evidence.

**One real moment:** a summary with six numbers in it, going to someone senior, on a Friday.

If the stakes justify it, push the check further than a fresh session of the same model:
[17 Many Models](17-many-models.md) explains why a different model catches things a fresh session
of the same one structurally cannot, and gives you the paste-into-another-tab version.

---

## Group three — being taught

### `/learn`

**For:** working through this harness as a taught course instead of reading it alone.

**Fires on:** "teach me", "where should I start", "next lesson", "continue where we left off".

**What it actually does:** finds out where you are before it starts — it does not open at topic
one by default — then teaches **exactly one topic from the mastery track per session**, using your
real work as the input to that topic's exercise, and refuses a second topic in the same sitting
because that is how the first one gets forgotten. It ends by checking that you can *use* the idea
rather than recognise it: a new situation you have to apply it to cold, never "does that make
sense?" Then it writes down where you got to.

**The anti-lecture rule is the load-bearing part:** if it has produced more than about three
paragraphs without you doing or saying something, it is doing it wrong. A session where it talked
and you nodded is a failed session no matter how good the explanation was.

The order of topics lives in [`progress/MASTERY.md`](../progress/MASTERY.md), and the teaching
method — the ladder, the transitions, what evidence moves a rung — lives in
[`protocols/TEACHING-PROTOCOL.md`](../protocols/TEACHING-PROTOCOL.md).

### `/quiz`

**For:** finding out what actually stuck, which you cannot tell from the inside. The gap between
understanding something and having recently heard it explained well is invisible to the person in
it.

**Fires on:** "quiz me", "do I actually know this", "have I forgotten this" — and at the start of
any returning session, before new teaching begins.

**What it actually does:** reads the tracker, picks two or three topics — one or two whose last
recall is oldest, at most one current — and asks three to five **application** questions against
your own work. Not definitions. It rotates three forms: where in the last month would this have
changed what you did; here is a deliberately broken example from your domain, what is wrong with
it; here is a setup, predict what happens. Then it writes what it found back into
[`progress/MASTERY.md`](../progress/MASTERY.md), including downwards.

**What it refuses to do:** grade you, use multiple choice, quiz a topic you have never been
taught, or mark a topic as demonstrated on the strength of a good answer. A quiz is talk, and
talking about work is not doing work — the most it can promote is a genuine explain-back.

**One real moment:** the first five minutes of a session two weeks after the last one.

**Honest un-checking** is part of the design. If something has decayed it moves back down, said out
loud and kindly, with the reason. A tracker that only ever goes up is a tracker that lies.

### `/coach`

**For:** the middle of a task that is about something else entirely. You are cleaning a
spreadsheet, and something about how you are doing it feels wrong.

**Fires on:** "coach me", "is there a better way to do this", "there must be a faster way", and on
you expressing frustration with your own approach rather than with the output.

**What it actually does:** reads what has actually been happening in the conversation, names the
situation in one sentence using your nouns and countable evidence ("that is the third export you
have cleaned by hand"), gives **one** intervention sized to the next minute and applied to the
material on the table, names which tracked topic it touches, and hands the task straight back.

**The brevity rule has teeth:** the whole intervention is about four sentences, no headings, no
bullet lists, no ranked options, and the last sentence is always the hand-back. If the topic
genuinely needs a session, it says so in one sentence and offers `/learn` later rather than
starting it now.

It will also **offer** coaching unprompted — at most once per session, as a one-line question you
can wave off, when it notices you doing the same manual thing a third time, accepting a claim
without evidence, or doing by hand something a skill you already own would do. Wave it off and it
drops the point permanently. Restraint is part of the skill: a coach who comments on everything
gets muted, and a muted coach teaches nothing.

**What it refuses to do:** end holding the wheel.

---

## Group four — looking back

### `/review-my-work`

**For:** the pattern you cannot see from inside any single session — what you repeat, what you
avoid, what you accept without checking, what you are quietly forgetting.

**Fires on:** "review my work", "how am I doing", "what should I get better at", "am I improving".

**What it actually does:** first, it establishes **which source it can actually read** and states
that in a banner at the top of the review, because an AI generally cannot read your other
conversations. Four tiers, strongest first: native access to session history if this environment
has it; exported transcripts on disk; the harness's own
[`progress/SESSION-LOG.md`](../progress/SESSION-LOG.md), which is the tier the whole design is
built around because it works everywhere; or you pasting the material in. Then it runs five fixed
lenses over the window — repetition, unverified acceptance, the hard way, unopened doors, decay —
dispatching the [reviewer](../.claude/agents/reviewer.md) once per lens if it can. Then it
produces a fixed shape: the one thing to change, what genuinely went well with evidence, the three
ranked by payoff over effort, and what it could not assess.

**What it refuses to do:** produce a clean bill of health, or produce a review that only
criticises. Both are failures, and both fail the same way — writing a sentence it cannot point at.
It also refuses to say "you did not check this" when what it actually knows is "no check was
recorded". Those are different claims and only one of them is true.

**One real moment:** a standing fortnightly appointment with yourself. The cadence argument and the
scheduled version are in [`protocols/REVIEW-ROUTINE.md`](../protocols/REVIEW-ROUTINE.md).

### `/recall-session`

**For:** "what did we decide about that", three weeks later.

**Fires on:** "what did we do last time", "find that chat where", "what did I decide about",
"did we already try this".

**What it actually does:** the same four tiers, stated out loud before it answers anything. Then it
searches on **what you actually remember** — the task words, the rough week, who it was for, what
was annoying — because nobody remembers what a chat was called. Then it reports in a fixed shape
rather than as a retelling: what was decided, what got built and where it is, what is still open,
and **what this source does not tell you**. That last field is what makes it trustworthy.

**What it refuses to do:** reconstruct a session it did not read. A confident, plausible account of
a conversation that never happened is the specific failure this skill is designed around, and you
would have no way to catch it.

It also offers to capture anything durable that surfaced and was never written down, appended in
the target file's own format and marked as backfilled so the out-of-order date reads as deliberate.

### `/handoff`

**For:** a session that has gone heavy, circular, or stale. The mechanism is in
[02 The context window](02-the-context-window.md); this is the procedure.

**Fires on:** "this session is getting long", "start fresh", "write me a handoff" — and your AI
should offer it unprompted when it notices the staleness signals: re-reading a file it already
read, contradicting itself, repeating advice, or a debugging attempt that has cycled three times
with no new information.

**What it actually does:** demands a **purpose** for the next session first, and refuses to write
the document without one — with no purpose there is no basis for leaving anything out, so you get a
bloated summary and the next session starts exactly as clogged as this one. Then a short document:
purpose, goal, current state, decisions with their reasons, what was explicitly ruled out, pointers
to files rather than their contents, open questions, and one immediate next action. Then it redacts
anything that should not be written down, saves the document **outside this folder**, and gives you
the literal block to paste into the new chat.

**What it refuses to do:** keep working after writing the handoff. That is how a handoff goes stale
before it is used.

**One real moment:** hour three of a debugging session, when you notice you have explained the same
constraint twice.

---

## The five workers

You will rarely type these names. They matter because knowing they exist changes what you ask for:
"check this and dispatch an adversary at it" is a different request from "check this".
[08 Subagents and swarms](08-subagents-and-swarms.md) is the chapter behind all of them.

**[`verifier`](../.claude/agents/verifier.md)** — the read-only checker. It grades claims against
**primary sources**, not summaries of them, and returns exactly one of four verdicts per claim:
confirmed, corrected, demoted-to-uncertain, or could-not-check. Every verdict carries the specific
thing it opened — the file and the section, the URL and the sentence — so you can repeat the check
and land in the same place. It never fixes anything, never pads with praise, and always lists what
it did not check. Not being able to check something is a legitimate result; fabricating a check is
the one unforgivable failure in the role.

**[`adversary`](../.claude/agents/adversary.md)** — the refuter. Deliberately one-sided, and that
is the point: everything else in the process is biased toward the claim being right. It assumes the
claim is wrong and goes hunting for how, attacking the load-bearing assumption rather than the
wording, and writing out the list of everything that would have to be true before checking each
item. When it is unsure it defaults to *refuted-unsupported* rather than to a pass, because an
adversary that finds nothing obvious and rubber-stamps is worse than no adversary. It reports the
strongest counter-case it found even when the claim survives, and it ends with the observable thing
that would show up first if the claim turns out to be wrong. It is at its strongest when it is not
running on the same machinery that produced the work — see [17 Many Models](17-many-models.md).

**[`scout`](../.claude/agents/scout.md)** — one narrow question, answered with facts and exact
locations, in under a page. It exists so the session that dispatched it never has to read the raw
material: it reads forty pages and returns half of one. Suggestions are absolutely forbidden — no
"you should", no "this looks like a problem", no "overall the picture is" — because five scouts
each adding an opinion formed on one fifth of the picture will anchor the main session before it
has seen any facts. Facts from the workers, judgment at the top. Fan several out at once when you
need the same kind of fact about five different things.

**[`teacher`](../.claude/agents/teacher.md)** — explains **one** concept, pitched at where you
actually are, using your own material as the example rather than a generic one. Hard cap of about
300 words before you have to do something, and a maximum of three explain-then-do cycles in one
dispatch. It shows what the failure looks like, not just the success, and it names the tell. It
never praises completion and never does your work for you. It is the only worker permitted to write
to the `progress/` folder, and it may tick a capability checkpoint only if it watched you do the
thing unaided.

**[`reviewer`](../.claude/agents/reviewer.md)** — one lens, one window of past sessions, findings
tied to dated instances. Its whole standard is **instances, not impressions**: "they do not verify
enough" cannot be acted on, checked, or disputed; "on the 16th the board summary went to three
people and the record names no check on its figures" can be all three. It ranks by payoff over
effort, holds praise to exactly the same evidence standard as criticism, and reports what it could
not see from the material it was handed.

---

## How they compose

None of these are meant to be used alone. The chain that shows up most often in real weeks:

```
   YOU ARE STUCK                         YOU DO NOT KNOW WHAT IS POSSIBLE
        |                                              |
   /im-stuck  ------ names the situation ------>  /whats-possible
        |                                              |
        |                                   finishes one real thing
        |                                              |
        +------------------> /grill-me <---------------+
                                 |
                   finds the work worth codifying
                                 |
                            /skillify  ---- builds and tests the skill,
                                 |          then logs it in progress/SKILLS-BUILT.md
                                 |
                          you run the skill on real work
                                 |
                    +------------+-------------+
                    |                          |
               /verify-this                 /coach
             (dispatches the             (in flight, once,
           verifier and adversary)         then hands back)
                    |                          |
                    +------------+-------------+
                                 |
                              /quiz  ---- proves it stuck, updates progress/MASTERY.md
                                 |
                        /review-my-work  ---- five lenses, five reviewers,
                                 |             one thing to change
                                 |
                            /handoff  ---- when the session is spent
                                 |
                        a fresh session, and round again

   ACROSS ALL OF IT:  /recall-session pulls back anything from before,
                      reading progress/SESSION-LOG.md when it cannot read the chats.
```

Read the chain as sentences, because that is how you will actually remember it:
`/im-stuck` names where you are, `/whats-possible` opens a door you did not know was there,
`/grill-me` finds the work worth building, `/skillify` builds it, `/verify-this` checks it,
`/coach` corrects you in flight, `/quiz` proves it stuck, `/review-my-work` finds the next thing
to fix, and `/handoff` moves the session when it is spent.

Three things worth noticing about that shape:

1. **The skills hand off to each other explicitly.** `/grill-me` ends by offering to build item one
   and passing straight to `/skillify`. `/review-my-work` routes a repetition finding to
   `/skillify`, an unverified-acceptance finding to `/verify-this`, and a decay finding to `/quiz`.
   You are not supposed to remember the routing; the files do it.
2. **Everything durable lands in `progress/`.** Skills write there and read from there — the
   tracker, the learner file, the skills table, the decisions, the session log, the reviews. That
   folder is why any of this survives a closed chat, and it is
   [06 Memory and the second brain](06-memory-and-second-brain.md) made concrete.
3. **The checking layer is separate from the doing layer on purpose.** The skills that build never
   grade their own output; the workers that grade never fix. That separation is the whole idea in
   [04 Verification](04-verification.md), built into the plumbing rather than left to your
   discipline.

---

## How a skill actually fires

This is the mechanism, and understanding it saves you a lot of confusion.

Your AI does not hold all eleven skill files in mind at once — that would fill its working memory
with things it does not need. It holds a short list: each skill's **name and description**. On
every request it scans that list and asks whether anything matches what you just said. If yes, it
opens the full file and follows it.

So the description is the only part read every time, and **the phrasing you use is what gets
matched against it.** That is why the descriptions in this folder are full of slightly awkward,
literal sentences — "I feel like I am barely scratching the surface", "there must be a faster way",
"did we already try this". They are trying to contain the words a real person actually types.

Two consequences:

- You do not have to remember command names. Describing your situation in plain language is
  usually enough, and it is the intended way to use this.
- When you build your own, the description is the highest-leverage sentence in the file. A
  brilliant procedure behind a vague description never runs.

### When one does not fire

In rough order of likelihood:

| What you see | What is actually wrong | The fix |
|---|---|---|
| Nothing happens when you type `/name` | Your environment does not do slash commands | Say the procedure by name: "follow `.claude/skills/verify-this/SKILL.md` on the draft above" |
| It says it cannot find the file | It is not seeing this folder at all | Check you are pointed at the folder containing `README.md`; worst case, open the file and paste it |
| It answers in general terms instead of following the steps | It found the topic but not the file | "Open the file and follow it literally, step by step, including the parts that look obvious" |
| The right skill exists and it used the wrong one | Two descriptions overlap | Name the one you want, then add a "do not use for X" line to the loser's description |
| It never fires on how you naturally ask | The description lacks your phrasing | Add your literal words to the description, including the lazy version |

The general escape hatch, which works in every environment including the ones with no file access
at all: open the `SKILL.md`, paste its contents into the chat, and say "follow this now."
[INSTALL.md](../INSTALL.md) has the per-environment detail.

---

## Adding your own

You do not hand-write skill files. You run [`/skillify`](../.claude/skills/skillify/SKILL.md) after
doing the work once, and it writes the file, the frontmatter, and the tool files with you.

What is worth knowing anyway:

- **Where it goes.** `.claude/skills/<your-name>/SKILL.md`, alongside the eleven that shipped. Your
  skills and the harness's skills are the same kind of object and sit in the same place.
- **Yours should be about your job, not about AI.** The eleven here are about the *practice* of
  working with AI, because that is what a teaching harness is for. The valuable ones you build will
  be about your actual work — your weekly note, your reconciliation, your onboarding pack.
- **Keep them small and let them call each other.** Fixing one small skill improves everything that
  uses it. [05 Skills](05-skills.md) covers the reasoning; the mechanics are in `/skillify`.
- **Read anyone else's before you install it.** A skill is instructions your AI will follow, which
  makes installing one closer to installing software than to reading an article. The review prompt
  for that is in [05 Skills](05-skills.md), under the supply chain section.

---

## The honest note: an unused skill is clutter

Eleven skills is already more than most people will use.

Every skill in the list is one more description your AI scans on every request, one more thing
competing to fire, and one more file you feel vaguely guilty about. A library of five you actually
run beats thirty you built in an enthusiastic weekend.

So: **the fix for a skill you do not use is deleting it.** Not renaming it, not sharpening it, not
promising yourself you will get to it. Delete the folder. If you were wrong, it is a file — you can
write it again, better, on the day you actually need it.

This applies to the ones that shipped here too. If you have been working this way for three months
and have never once run `/recall-session` because your tool has real session history and you just
ask it directly, that folder is dead weight. Remove it. The
[`progress/SKILLS-BUILT.md`](../progress/SKILLS-BUILT.md) usage count is there precisely so this
decision is made on evidence rather than on feeling: a skill that has been sitting at zero across a
whole review window is either badly described or genuinely unwanted, and both of those are findings.

The one thing not to delete on those grounds is a skill you avoid because it tells you things you
do not want to hear. `/verify-this` and `/review-my-work` are the two most likely candidates. That
is a different problem: deleting the only independent check leaves the work graded by the person who
did it, which is the human-side version of
[F-10, the self-graded pass](../protocols/FAILURE-MODES.md#f-10--the-self-graded-pass). The fix is
there, not in this chapter.

---

## Try this now

Do not sit down and read all sixteen files. Have the system explain itself against your own week,
which is the only version you will remember.

```
You have access to this harness folder. Read only the frontmatter description of
every SKILL.md under .claude/skills/ and of every file in .claude/agents/ - the
description lines, not the whole files.

Then ask me one question: what did I actually do at work in the last three days?
Wait for my answer.

Then map it. For each of the moments in what I tell you, name which single skill
or worker would have applied, quote the phrase in its description that would have
made it fire, and say in one line what it would have changed. Where nothing here
applies, say so plainly instead of stretching one to fit.

Finish with exactly two things: the one skill I should run today and why that one,
and the one that I probably will not need at all in my job, with your honest reason.
```

The last sentence is the one to pay attention to. A tour that recommends all eleven has told you
nothing.

---

## What you should now be able to do

- Name the moment each of the eleven skills is for, without scrolling a list — and reach for the
  right one at the point of need rather than after the fact.
- Say what the five workers do and how they differ, and ask for one deliberately: an adversary when
  you want something attacked, a scout when you want a fact without reading the source, a verifier
  when you want a claim graded.
- Explain why a skill fires or does not fire, and fix a description that does not match the way you
  actually phrase things.
- Chain them without being told to: name the situation, open the door, find the repeated work,
  build it, check it, prove it stuck, review it, hand off.
- Delete a skill you do not use, and tell that case apart from a skill you are avoiding.

Next: [15 Git](15-git.md), which is what makes it safe to let any of this change your files.
