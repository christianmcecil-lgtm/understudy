# Review Routine

*How to make the coaching review happen again next month instead of once. The manual version,
the automated version, what keeps it safe, and the specific way recurring reviews die. About ten
minutes to read; the routine itself takes twenty minutes a week.*

This file is addressed to both of you. The learner needs the cadence argument and the calendar
wording. The AI needs the safety constraints and the wallpaper countermeasure.

All paths below are given from the root of the harness folder — the folder containing
`README.md`.

The review itself lives in
[`.claude/skills/review-my-work/SKILL.md`](../.claude/skills/review-my-work/SKILL.md). This file
is only about making it recur.

---

## Why a review needs to recur at all

You cannot see your own working patterns from inside a session. Inside one conversation
everything looks like a reasonable response to what was in front of you — and it usually was.
The thing worth seeing is not any single session. It is the shape across several: the task you
have now done by hand four times, the check you skip when the deadline is close, the topic you
learned in March and have not touched since.

That shape is invisible at close range and obvious at a distance. A recurring review is how you
get the distance, on purpose, instead of noticing in six months that you have been doing
something the hard way the whole time.

---

## The cadence argument

Two forces pull in opposite directions, and the right cadence is where they balance.

**A review needs enough material to see a pattern.** One session is an anecdote. Two is a
coincidence. A pattern needs several sessions, which is the same rule of three that governs when
to build a skill in [Skills](../curriculum/05-skills.md). Review too often and every review says
"not enough happened", which trains you to ignore reviews.

**A review needs the specifics to still be in reach.** The findings have to be checkable by you.
If a review tells you something about a session six weeks ago and you cannot remember whether it
is true, you cannot act on it and you cannot correct it when it is wrong. Review too rarely and
the material becomes an archive rather than a memory.

So:

| Situation | Cadence | Why |
|---|---|---|
| Actively learning — new topics, new skills, working habits still forming | Weekly | Habits are still forming, which means they are still cheap to change. A week is enough sessions to show a pattern and recent enough that you can still check it. |
| Stable — the practice is settled, the skills are built, you are using rather than learning | Monthly | Less changes week to week, so weekly reviews start repeating themselves, and a review that repeats itself gets skipped. |
| In between, or unsure | Start weekly, lengthen when two reviews in a row feel thin | Thinness is the observable signal. Do not guess the cadence; let it tell you. |

**Signals to change cadence, in either direction:**

- Two consecutive reviews find little because the window is nearly empty — lengthen the interval.
- You cannot remember the sessions the review is describing — shorten it.
- Three consecutive reviews name the same top item and nothing changed — the cadence is not the
  problem. See "the same item three times" below.

---

## The manual version — do this one

This is the unglamorous version, it works in every tool including ones with no automation of any
kind, and it is the one most people should actually use. An automated review you never read is
worth less than a manual one you sit down for.

**The whole routine:** a standing appointment with yourself. Twenty minutes. Same slot each week.

Put this in whatever calendar or reminder system you already use — the point is that it arrives
without you having to remember it exists:

```
Weekly - 20 min - AI practice review

1. Open a NEW session with the harness folder and type:  /review-my-work
   (If your tool has no slash commands, paste instead:
    "Read .claude/skills/review-my-work/SKILL.md in this folder and follow it.")
2. Read the first paragraph. That is the whole point of the review.
3. Pick ONE item. Do it before this reminder is closed.
4. Tell it what you did, so it goes in the record.
```

Three things about that wording, each doing real work:

- **A new session.** The review reads files; it does not need the conversation you were having,
  and a session already full of other work will produce a worse review for the reasons in
  [The context window](../curriculum/02-the-context-window.md).
- **Read the first paragraph.** The review is built to put the single most valuable change there,
  alone. If you read nothing else, read that.
- **Do one item before closing the reminder.** This is the step that makes the difference between
  a routine and a habit of generating documents.

**Pair it with the thing that makes it work.** The review is only as good as the record it reads,
and on most setups that record is `progress/SESSION-LOG.md`, appended at the end of each session
per the CAPTURE phase of [SESSION-PROTOCOL.md](./SESSION-PROTOCOL.md). If sessions are not being
logged, fix that first. A weekly review over an empty log is a weekly reminder that you have no
record.

---

## The automated version, described by shape

Some environments can start a session on a schedule, run a fixed instruction with nobody present,
and leave a file behind. If yours can, this review is an unusually good candidate for it. If
yours cannot, you have lost nothing — go back to the manual version, which is the one that always
works.

**What to ask for, rather than what to type.** Scheduling works differently in every tool, the
tools change, and a specific command written here would be wrong somewhere and would probably
become wrong here too. So do not trust an instruction from this file. Ask your own AI, in your
own setup:

```
What in my current setup can run a fixed instruction on a schedule, without me present?

Tell me:
- what mechanism exists, if any, and where it runs from
- what it can and cannot do while I am not there (can it read files? write one file?
  send anything?)
- whether it costs anything per run
- exactly how I would turn it off

If nothing in my setup can do this, say so plainly rather than suggesting something I would
have to install.
```

The last line matters. The honest answer for many setups is "nothing here does that", and a
routine you had to install three things to get is no longer a low-stakes automation.

**Why this particular task is a good first automation.** It fits the profile the trust ladder in
[Safety, privacy, and trust](../curriculum/10-safety-privacy-and-trust.md) asks for in an opening
move: it is read-only over your own files, it is low-stakes, it is completely reversible, and its
entire output is one document that changes nothing else. Nothing is sent. Nobody sees it but you.
If it runs badly, you delete a file.

That is what "automate the boring, reversible, low-stakes thing first" looks like in practice,
and it is worth noticing that the first thing you automate is a thing that inspects your own
work rather than does it.

---

## What the routine needs to be safe

Whether it runs on a schedule or you run it by hand, these constraints hold. If the automated
version cannot honour all of them, run it manually instead.

| Constraint | What it means | Why |
|---|---|---|
| Read-only scope | It reads `progress/`, the harness files, and whatever transcripts it has access to. It reads nothing else on the machine. | A routine with a broader reach than its job is a routine whose blast radius nobody has thought about. |
| A bounded window | Explicit start and end dates, stated in the output. | An unbounded window quietly grows until every review is a review of everything, which is a review of nothing. |
| One output file | It appends to [`progress/REVIEWS.md`](../progress/REVIEWS.md) and writes nowhere else. | One known place to look, and one known place to undo. |
| No tracker writes while unattended | It may *propose* rung changes in `progress/MASTERY.md`; it may not make them. | A rung change is meant to be shown to the learner before it is written — see [TEACHING-PROTOCOL.md](./TEACHING-PROTOCOL.md). Nobody is present at 6am to disagree with it. |
| Nothing sent, nothing external | No messages, no emails, no posts, no calls out to anything. | Drafting is reversible; sending is not. This is the line in the PAUSE phase of [SESSION-PROTOCOL.md](./SESSION-PROTOCOL.md), and an unattended run cannot pause. |
| A human read before action | The review recommends. It never acts on its own recommendation. | The whole point is that a person decides what to change about how they work. |
| An off switch you have tested | You know how to stop it before you start it. | Untested off switches are a category of trouble on their own. |

The failure this table is guarding against is
[F-12, the automation that outran trust](./FAILURE-MODES.md#f-12--the-automation-that-outran-trust).
A review routine is about as safe as an unattended task gets — which makes it a good place to
practise the constraints, while they are cheap.

---

## The way recurring reviews die: they become wallpaper

This is the actual failure mode, and it is close to universal. Nobody reads the weekly report by
week five.

**The mechanism**, because knowing it is what lets you counter it: a recurring document arrives
in a constant format, on a constant schedule, with nothing on its surface to signal whether this
one is different from the last one. The cost of reading it stays the same every week. The
perceived payoff drops every week, because the last four contained things you already knew. So it
gets skimmed, then filed, then ignored — and the routine keeps running, producing documents,
looking like a working system while doing nothing at all. That last part is what makes it worse
than not having the routine: it occupies the slot where a real review would go.

**Three countermeasures. All three, not one.**

**1. Lead with the single most valuable change, and nothing else, in the first paragraph.**
Whatever is at the top is the only part reliably read, so the top must be the finding, not a
preamble, not a summary of the window, not a recap of what the review is. This is why the output
shape in [`review-my-work`](../.claude/skills/review-my-work/SKILL.md) puts the one thing above
even the genuine praise.

**2. The unread check.** Every entry in [`progress/REVIEWS.md`](../progress/REVIEWS.md) carries an
`ACTED ON` line, and each new review fills in the previous entry's. Be precise about what this can
actually detect: a routine cannot know whether you read something. It can know whether anything
visibly changed — a new skill in `progress/SKILLS-BUILT.md`, a rung change in
`progress/MASTERY.md`, an item marked as done. So the check is "no evidence of action", not
"unread", and it should be written that way.

**If two consecutive reviews show no evidence of action, the next review opens with that fact and
asks a direct question**, before any findings:

```
The last two reviews both led with the same kind of item and I can see no change in the
record after either one. That usually means one of three things: the cadence is wrong, the
items are too big to act on, or this routine is not earning its slot.

Which is it? I can move to monthly, shrink the items so item 1 always fits in ten minutes,
or stop running this and you can call for it when you want it.
```

Then wait. A routine that asks whether it should still exist is doing something an unread
document cannot do.

**3. Keep everything else identical.** Same sections, same order, same length, every time. It is
tempting to vary the format to keep it interesting; do not. If the format is constant then the
only thing that changes is the content, which means the top line is genuinely informative rather
than being one of several things competing for a first read.

---

## What to do with a review once it exists

**Pick one item. Do it that day. Mark it.**

That is the whole instruction, and it is not a simplification for the sake of brevity. A review
that generates a backlog has failed, because a backlog of self-improvement items is a list you
will feel bad about and never open. Three items were produced so that you could choose, not so
that you could do three.

- **Pick one**, usually item 1, but pick a different one if you know something the review does
  not. You are allowed to overrule it. Say why, so the next review does not re-raise it.
- **Do it that day**, ideally in the session that produced the review, which is why the skill ends
  by offering exactly that.
- **Mark it** in the record, so the next review can see whether anything changed. One line.
- **Let the other two go.** Do not carry them forward as a list. If they still matter, they will
  appear in the next review, with fresh evidence, which is a better signal than a stale to-do.

### When the same item appears three times

This is the most informative thing this routine produces, and it is the reason
[`progress/REVIEWS.md`](../progress/REVIEWS.md) is worth keeping as an arc rather than as
separate documents. If the top item of the last three reviews is the same item, you are avoiding
it. That is a fact about the item, not a character flaw, and there are exactly two honest moves:

1. **Shrink it until it is doable.** An item that survives three reviews is usually too big or
   too vague to start. "Turn the weekly note into a skill" is a session. "Open last week's note
   and paste it to me" is two minutes, and it is the first move of that session. Replace the item
   with its first move.
2. **Decide out loud that you are not going to do it**, and write that in
   [`progress/DECISIONS.md`](../progress/DECISIONS.md) with the reason. A rejected item with a
   reason recorded is finished. An item you keep not doing is a small recurring cost forever.

Both are fine. Continuing to list it is not.

---

## Try this now

You do not need a review to have happened yet. Set the routine up first — it takes about two
minutes.

Put a weekly recurring reminder in whatever you already use, with this as the body:

```
Weekly - 20 min - AI practice review

1. New session with the harness folder. Type: /review-my-work
   (No slash commands? Paste: "Read .claude/skills/review-my-work/SKILL.md in this folder
    and follow it.")
2. Read the first paragraph.
3. Do ONE item before closing this reminder.
4. Tell it what you did.
```

Then, in your next session, paste this:

```
Two questions about making the review recur, and I want honest answers, not options.

1. Given how I have actually been working, is weekly or monthly right for me, and what in
   the record makes you say that?
2. Can anything in my current setup run a fixed instruction on a schedule without me
   present? If nothing can, say so plainly rather than telling me what to install.

Then tell me which of the safety constraints in protocols/REVIEW-ROUTINE.md my setup could
not honour if it ran unattended.
```

## What you should now be able to do

- Choose a review cadence from a reason rather than a habit, and recognise the two observable
  signals that say it should get longer or shorter.
- Run the review without any automation at all, on any tool, from a calendar reminder you can
  write in one minute.
- Say why a read-only, single-output, nothing-sent routine is the right shape for a first
  unattended automation, and name what would have to change for it to stop being safe.
- Spot a recurring report turning into wallpaper before it does, and apply the three
  countermeasures — the finding at the top, the no-evidence-of-action check, and a format that
  never varies.
- Treat a review as one action, not a backlog, and recognise a top item appearing three times as
  avoidance rather than as a persistent problem.
