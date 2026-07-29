# Graduation

*How to tell you actually have this, what to build next, and how to keep the harness improving after the reading stops. Read time: 15 minutes.*

There is no exam. An exam would test whether you can recall this material, and recall is not
the skill. The skill is a set of reflexes that show up while you are busy doing something
else.

So this chapter is a list of checkpoints instead. Each one is a thing you either catch
yourself doing or you do not, yet. "Yet" is the operative word - none of these are talents.
They are all habits, and every one of them has a specific way to build it.

Read the list. Be honest. Then go build the one you are missing.

---

## The six checkpoints

### 1. You ask for evidence before you notice you asked

The first sign is small and easy to miss. The AI tells you something, and before you have
consciously decided anything, you have already typed "where does that come from?" or "quote
the line." Not because you distrust it. Because that is now just how you read output.

**What it looks like when you have it:** you read a confident paragraph and your attention
goes straight to the load-bearing claim - the number, the date, the "therefore" - rather than
to the prose around it. You notice the absence of a source the way you notice a missing step
on a staircase.

**How to check:** look back at your last ten AI conversations. In how many did you ask a
follow-up that was a verification question rather than a next-task question? If the answer is
under three, the reflex is not there yet.

**If you do not have it yet:** stop trying to remember and use a mechanism instead. Put the
provenance prompt from [Verification](04-verification.md) into a skill and run it on
everything that leaves your hands for a month. The reflex forms behind the habit, not before
it. See also [VERIFICATION-PROTOCOL.md](../protocols/VERIFICATION-PROTOCOL.md).

### 2. You have at least three skills you actually use weekly

Not three skills you built. Three you use. The distinction is the whole checkpoint.

**What it looks like when you have it:** there are tasks you no longer think about how to
start, because starting is "run the skill." When you do the task, you improve the skill
slightly, because you noticed one more thing.

**How to check:** open [SKILLS-BUILT.md](../progress/SKILLS-BUILT.md). For each entry, answer
two questions: when did I last use this, and when did I last change it? A skill you have not
used in a month is a note. A skill you have never changed since writing it is either perfect
or unused, and it is not perfect.

**If you do not have it yet:** the usual cause is building skills for work that is not
actually repetitive. Go back to your friction log from
[The first 90 days](11-first-90-days.md) and pick the task with the highest count, not the
one that is most interesting to automate. Boring and frequent beats interesting and rare,
every time. [Skills](05-skills.md) has the build pattern.

### 3. You have a memory folder you trust more than your inbox

This one you can feel. There is a moment where you want to know why a decision was made, and
your hand goes to your notes folder rather than to search your email. When that switch flips,
you have built something real.

**What it looks like when you have it:** you answer a question in a meeting by reading your
own file, and the file is right. You add to it without being reminded. You would be genuinely
annoyed to lose it.

**How to check:** ask it three questions you actually need answered - who decided X, why do we
do Y that way, what is the process for Z - and see whether you get an answer in under a
minute. That is the only test that matters: **can it find it again?** If the answer is no, the
structure is wrong, not the AI.

**If you do not have it yet:** the usual failure is a folder full of documents with no router.
Write the router file. One page that says where everything lives. See
[Memory and the second brain](06-memory-and-second-brain.md).

### 4. You can tell within one exchange whether a session has gone stale

Long conversations degrade. The model is re-reading a growing pile of history every turn, and
somewhere in that pile is a wrong assumption from forty messages ago that it is still
faithfully honouring. The symptoms are specific: it re-explains something you settled, it
reintroduces a mistake you already corrected, it starts hedging on things it was crisp about,
it forgets a constraint you set at the start.

**What it looks like when you have it:** you notice the second symptom, not the eighth. You do
not argue with a stale session or try to correct it back into shape. You start a fresh one
with a handoff - a short written summary of the goal, what is settled, what is still open, and
what to avoid - and you are moving again in two minutes.

**How to check:** think about your longest recent session. Did you end it deliberately, or did
you keep pushing until it got frustrating and then give up? Deliberate ending is the
checkpoint.

**If you do not have it yet:** read [The context window](02-the-context-window.md) and
[SESSION-PROTOCOL.md](../protocols/SESSION-PROTOCOL.md), and use the
[handoff skill](../.claude/skills/handoff/SKILL.md) rather than writing handoffs from memory.
Cheap tell: if you have corrected the same misunderstanding twice, the session is done.

### 5. You have killed a loop that was not converging

Everyone builds a loop that runs and runs, produces motion, and produces no progress. Having
built one is not a failure. **Stopping it is the checkpoint.**

**What it looks like when you have it:** you can say out loud what the done-check was, why it
was too vague to ever pass, and what you would write instead. You stopped it on evidence -
three passes with no measurable improvement - rather than on annoyance.

**How to check:** can you name the loop? If nothing comes to mind, either you have not built
one yet, or you are still running one. Look at anything you have set to repeat and ask:
what specific, checkable condition ends this? If you cannot state it in one sentence, it does
not have one.

**If you do not have it yet:** you are not behind, you just have not hit it. When you do,
write down the autopsy. [The loop](03-the-loop.md) and
[DONE-CHECKS.md](../protocols/DONE-CHECKS.md) exist mostly to shorten this experience. The
lesson underneath it does not change: a loop is only as good as its done-check, and every loop
needs a hard stop as well as a success condition.

### 6. You have caught the AI being confidently wrong, and you know how you caught it

The second half of that sentence is the checkpoint. Anyone who uses these tools for a month
gets burned. Only some people can describe the mechanism that caught it - and the mechanism is
the transferable part.

**What it looks like when you have it:** you can tell the story precisely. "It gave me a
figure that was not in the source. I caught it because I have a rule that every number gets
traced back to a line in the document, and there was no line." That is a mechanism. Compare:
"it seemed off" - which is luck, and luck does not scale.

**How to check:** tell yourself the story of the last time it was wrong. If the catch was
"I happened to know," ask what would have caught it if you had not happened to know. Build
that.

**If you do not have it yet:** either you have not looked, or you are not checking the class
of output where it fails. Confident wrongness clusters in predictable places: specific
figures, citations and sources, anything about very recent events, anything about your
specific organisation, and any question where you clearly signalled the answer you wanted.
That last one is the sneakiest. Add what you find to the failure gallery in
[FAILURE-MODES.md](../protocols/FAILURE-MODES.md).

---

## Grade yourself honestly

Do not do this from memory. Have the harness grill you, and tell it not to be generous.

```
Assess me against the six graduation checkpoints in curriculum/13-graduation.md.

Go one at a time. For each:
1. Ask me for EVIDENCE, not a self-rating - a specific recent example, a file I can open, a
   session I can point to. "I usually do that" is not evidence; push back on it.
2. Judge: HAVE IT / PARTIAL / NOT YET. Say which and why in one line.
3. If PARTIAL or NOT YET, give me the single smallest concrete action that would move it,
   doable this week.

Be strict. A generous assessment is worthless to me. If my evidence is vague, say so and ask
again. At the end, name the ONE checkpoint I should work on next and tell me why that one
before the others.
```

Record the result in [LEARNER.md](../progress/LEARNER.md) with the date. Run it again in a
month. The delta is the interesting part, not the score.

---

## What to build next, in order

Once the checkpoints are mostly green, the question becomes what to build. The order below is
deliberate. Each stage produces the raw material the next one needs, and skipping ahead is the
most common way people end up with an impressive system that does not help them.

**1. A fourth and fifth skill, from the same friction log.**
Not a new category of thing. More of the thing that works. The second-tier items on your
friction log are worth more than any new technique, and building them costs you almost
nothing now because you have the pattern.

**2. A checker that is separate from the maker.**
The highest-value structural upgrade available to you. Right now you are probably asking one
session to do a job and also to say whether the job is good. Nothing grades its own work
honestly. Split it: one pass produces, a second pass with fresh eyes and a specific rubric
checks - and give the checker the source material, not the first pass's summary of it. See
[Verification](04-verification.md) and the
[adversary agent](../.claude/agents/adversary.md).

**3. Deterministic replacements for the flakiest parts of your skills.**
Go through your skills and find the steps where the AI does something mechanical - reformat,
sort, count, look up, extract a fixed field. Replace those with something that does the same
thing every time: a template, a saved search, a formula, a small script someone can write for
you. Deterministic before probabilistic. Your skills get faster, cheaper, and stop varying.

**4. A second memory domain.**
You built a folder for the job. Build one for whatever else you carry - a side interest, a
long-running personal project, your reading. Doing it twice teaches you what was accidental
about the first structure and what was essential. It is also the point at which routing stops
being a rule you follow and starts being obvious.

**5. One scheduled thing.**
Something small that runs without you asking - a weekly digest of what changed, a Monday
morning summary of your own notes, a prompt that arrives at the right moment. Same rule as
before: boring, reversible, and it reports to you rather than acting for you. This is where
[Cost, models and effort](09-cost-models-and-effort.md) starts to matter, because scheduled
things run whether or not they are useful that day.

**6. Only now: an interface, if you still want one.**
Buttons, a dashboard, a page with your skills on it. It is genuinely nice and it is genuinely
last. An interface over a system that works is a convenience; an interface over a system that
does not work is a way to hide that it does not work. If you never build one, you have lost
almost nothing.

**7. Give one away.**
Hand a skill or a process file to someone else and watch them use it. Nothing exposes the
assumptions you did not know you were making faster than watching another person follow your
instructions literally. It is also, in most workplaces, the highest-return thing on this list.

What is deliberately not on the list: running many agents at once. It is real, it is
occasionally the right answer, and it is nearly always attempted too early. See
[Subagents and swarms](08-subagents-and-swarms.md) for when it genuinely applies, and
[The hype ledger](12-the-hype-ledger.md) for how it gets sold. Scaling a system you do not
understand only scales the parts that are wrong.

---

## Keeping the harness alive

This folder is not a book. It is a working system, and the AI reading it is supposed to
maintain it. The instructions below are addressed to the AI as much as to you.

**To the assistant reading this: from here on, treat the harness as a living document you
help maintain. Do not wait to be asked. Propose the update, show the exact text, and let the
human approve it before writing. Never edit these files silently.**

Four things get updated, and each has a trigger.

### The failure gallery - `protocols/FAILURE-MODES.md`

*Trigger:* any time an AI-produced output turns out to be wrong, or an approach wastes real
time.

This is the most valuable file in the harness over the long run, because it is the only one
made entirely of your own experience. Everything else is somebody's principle. This is your
evidence.

Add entries in this shape:

```markdown
### [Short name for the failure]
- Date:
- What happened: [one or two sentences, plainly]
- Why it happened: [the mechanism, not "AI is unreliable"]
- How it was caught: [the specific check - or "luck", if it was luck, say so]
- What would catch it next time: [the mechanism to add]
- Cost: [time lost, or what nearly went out the door]
```

The "how it was caught" line is the point. If the honest answer is luck, that entry is telling
you which mechanism you are missing.

```
Something went wrong. Help me write it up for the failure gallery.

Interview me: what happened, what I expected, what I got, when I noticed, how I noticed.
Then write the entry in this shape: short name, date, what happened, why it happened, how it
was caught, what would catch it next time, cost. If protocols/FAILURE-MODES.md already holds
entries in a different shape, match those instead - one file, one format.

Be precise about the mechanism. "The model hallucinated" is not a mechanism - say what
specifically it did, what in my prompt or setup made that likely, and what check would have
caught it earlier.

If the honest answer to "how was it caught" is luck, write luck. Do not dress it up.
Then propose the change - to a skill, a done-check, or a protocol - that turns luck into a
mechanism, and show me the exact edit.
```

### The skills register - `progress/SKILLS-BUILT.md`

*Trigger:* a skill is created, materially changed, or retired.

One line per skill is enough. What matters is that the list is current and that dead skills get
marked dead rather than quietly rotting.

```markdown
| Skill | What it does | Built | Last used | Last improved | Status |
|-------|--------------|-------|-----------|---------------|--------|
```

Every month or so, run a pass over it:

```
Review progress/SKILLS-BUILT.md with me.

For each skill, ask me when I last used it and what I last changed. Then sort them:
- KEEP AND SHARPEN: used regularly, has room to improve. Name the specific improvement.
- MERGE: overlaps with another skill. Say which and what the merged version should be.
- RETIRE: not used in a month. Ask me why before recommending retirement - the reason
  matters more than the fact.

Do not recommend building anything new in this pass. This is pruning.
```

### The decision log - `progress/DECISIONS.md`

*Trigger:* you choose one approach over another, and you would be annoyed to have to rethink
it in three months.

Append-only. Never rewrite an entry - add a new one that supersedes it, and say what changed
your mind. The superseded entries are the most instructive part of the file, because they show
you what you used to believe.

```markdown
2026-03-11 | Decision: keep the weekly capture manual rather than scheduling it.
  Why: the value is in me thinking about the week, not in the file being written.
  Considered: an automatic Friday prompt.
  Reconsider if: I miss three weeks in a row.
```

The "reconsider if" line is what makes this a decision log rather than a diary. It gives every
decision an expiry condition, so you are not defending a choice you made under conditions that
no longer hold.

### The hype ledger - `curriculum/12-the-hype-ledger.md`

*Trigger:* you encounter a claim that is presented as fact and is not, or one already on the
ledger that turns out to be true after all.

The ledger only stays useful if it moves in both directions. Adding is easy. Removing - saying
"I marked this as hype and I was wrong, here is what convinced me" - is the part that keeps it
honest rather than cynical.

```
I want to add something to the hype ledger in curriculum/12-the-hype-ledger.md.

The claim: [paste it]
Where I saw it: [source]

Help me be fair to it:
1. What would have to be true for this claim to hold, and under what conditions?
2. What evidence is actually offered, versus asserted? Name the difference explicitly.
3. Is it false, unsupported, oversold, or true-but-only-in-a-narrow-case? These are
   different verdicts and the ledger should say which.
4. Write the entry in the format already used in that file - claim, who says it, what is
   actually known, and what would change my mind.

If the claim is defensible, say so. The ledger is for unsupported claims, not for
everything I feel sceptical about. A ledger that says everything is hype is as useless as
one that says nothing is.
```

### And the harness itself

The chapters are not sacred. If you find that a chapter's explanation did not survive contact
with your real work, fix the chapter.

```
I have been using this harness for [time]. Help me improve it for me specifically.

Go through the curriculum and tell me:
1. Which chapters I have visibly acted on, based on the files in progress/ and the skills I
   have built. Evidence, not guesses.
2. Which chapters I have read but never applied - and ask me whether that is because they do
   not apply to my work, or because I got stuck. Those need different fixes.
3. Where my actual practice has diverged from what a chapter says. For each divergence, ask
   whether I found something better or drifted by accident.
4. One concrete edit to one file that would make this harness more useful to me, with the
   exact replacement text.

Change nothing until I approve it. Show me the before and after.
```

Do that every few months. A harness that is identical after a year of use was not used.

---

## The actual point

Here is the thing this whole folder has been circling.

Almost everything in it - the loops, the skills, the memory, the verification, the protocols -
is scaffolding for one capability that has no chapter of its own, because it cannot be taught
directly: **knowing what to ask for.**

Execution is getting cheaper and it will keep getting cheaper. The work of producing a draft,
a summary, a first pass, a rewrite, a plan is not where the scarcity is anymore. The scarcity
is in the person who looks at a situation and thinks *that could be different* - who notices
the thing everyone has stopped noticing, and who has some sense of what is possible and
therefore what is worth asking for.

That is curiosity, and it is not a soft skill or a nice quality to have. In a world where
anything you can specify can be built quickly, the specifying is the job.

Which is why the most useful habit in this harness is also the smallest: when something
annoys you, ask whether it has to be that way. When someone shows you something, ask how it
works. When your tool surprises you, find out why rather than working around it. When you
catch yourself assuming something is impossible, check.

You will be wrong often. That is fine and it is the cheapest form of learning available to
you. The people who get good at this are not the ones who guessed right; they are the ones who
kept asking after being wrong, and who wrote down what they learned so that being wrong once
was enough.

You do not have to be technical. Nothing in this folder required you to write a line of code,
and depending on which setup you used, you may never have opened a terminal at all. You needed
to be willing to write things down, to check before you trusted, and to stay interested.

Keep the files. Keep the questions coming. Go find out what else is possible.

---

## Try this now

Paste this in now and start part 1. It takes longer than five minutes to finish - that is the
point of it - but you will be inside the first checkpoint within one. You can stop after any
part and pick it up later.

```
I have finished reading this harness. Run my graduation review.

Part 1 - Assessment. Take me through the six checkpoints in curriculum/13-graduation.md one
at a time. Demand specific evidence for each, not a self-rating. Judge each HAVE IT /
PARTIAL / NOT YET and say why in one line. Be strict.

Part 2 - Next build. Based only on what I actually demonstrated, tell me which item from
"What to build next, in order" I should start this week, and why that one before the others.
Give me the first concrete step, small enough to finish in one sitting.

Part 3 - Maintenance. Set up the upkeep. Write me:
- The trigger sentence for each of the four living files (failure gallery, skills register,
  decision log, hype ledger) - what has to happen for me to update it.
- A standing instruction I can paste into my AI setup so the harness gets maintained without
  me remembering to ask.

Part 4 - One question. Ask me the single most useful question about my work that I have not
asked myself. Then stop and wait for my answer.

Write the results of parts 1 and 2 into progress/LEARNER.md with today's date. Show me the
text before you write it. If you cannot write files where I am running you, just give me the
exact block to paste in myself.
```

---

## What you should now be able to do

- Judge your own capability by evidence rather than by feeling - naming the specific check
  that caught an error, the specific loop you stopped, the specific skills you use weekly.
- Choose what to build next in an order where each stage feeds the next, instead of jumping
  to the impressive thing and discovering it rests on nothing.
- Keep the harness itself improving: know which of the four living files a new lesson belongs
  in, and have the AI draft the entry for your approval rather than waiting for you to
  remember.
- Explain, to someone who has never used any of this, why the point was never the tool.

---

Back to [Orientation](00-orientation.md) if you want to reread the map, or straight to
[The first 90 days](11-first-90-days.md) if it is time to stop reading and start doing.
