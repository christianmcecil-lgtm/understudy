# The First 90 Days

*A week-by-week plan for using AI to get good at a new job fast, without embarrassing yourself. Read time: 25 minutes. Working time: one quarter.*

Everything before this chapter was equipment. This is the field manual.

You have started a new job. You know less than everyone around you and that is temporary,
but only if you are deliberate about it. The plan below is not "use AI more." It is a
sequence, and the sequence matters: **learn, then notice, then remember, then automate.**
People who skip to automation build fast machines that do the wrong thing confidently.

Read the whole chapter once. Then come back each week and do that week.

---

## The 90-day map

| Weeks | Goal | The artifact you end up with |
|-------|------|------------------------------|
| 1 | Learn the job faster than anyone expects | A glossary of internal terms, a live list of what you do not understand, and a copy of the company's AI policy |
| 2-4 | Notice your own repetition | A friction log, and three skills built from the top of it |
| 5-8 | Build the memory layer | A job folder with a router file, notes on people, systems, decisions, and processes |
| 9-12 | Automate one thing, and start teaching | One boring reversible automation, and a reputation for accuracy |

Underneath all of it, one rule that never goes on a schedule:

> Never present unverified AI output as your own work. Not once. Ninety days of good work
> can be erased by one confident wrong number in a room full of people who trusted you.

---

## Week 1 - Learn the job faster than anyone expects

New hires are given a grace period where asking questions is free. Most people spend it
being quiet. Spend yours extracting everything.

### Day 1: find the AI policy before you use AI

Do this first. Not because it is exciting but because doing it in week one is cheap and
doing it in week six, after you have already pasted something you should not have, is not.

Ask three questions and write down the answers:

1. Is there a written policy on AI tools? Where is it?
2. Which tools are approved, and is there a company account, or are people using personal ones?
3. What categories of information may not be pasted into an AI tool - customer data,
   personal data, contracts, source code, anything under an agreement with a client?

Who to ask, in order: your manager, then whoever runs IT or security, then the person on your
team who obviously already uses AI. If nobody knows, that is itself the answer: assume the
strictest interpretation and work from public or already-published material until you get a
real one. See [Safety, privacy and trust](10-safety-privacy-and-trust.md) for how to think
about the boundary.

Exact wording that works, sent to your manager on day one or two:

> Before I start using AI tools for any of my work, I want to make sure I am inside whatever
> the company expects. Is there a written policy, an approved tool, and a list of things that
> should not go into one? Happy to just follow the strictest version if it is not written down yet.

That message does two things. It gets you the answer, and it puts on the record that you are
the sort of person who asks first.

### Days 2-4: build the internal glossary

Every company has a private language. Project codenames, three-letter systems, a word like
"ledger" or "account" that means something specific here and something else everywhere else.
Not knowing it is the single biggest thing slowing you down, and it is the thing nobody
thinks to explain, because to them it is not jargon, it is just words.

Here is the move that makes this fast. Do not ask the AI to explain your company's terms - it
does not know them, and if you ask, it will make something up that sounds plausible. Instead:
**feed it real internal documents you already have access to, and have it interview you.**

The AI is a reading machine that has no idea what matters. You are a person who knows what
matters but has not read the documents. Together you are a glossary.

Gather whatever you legitimately have: the onboarding deck, the team wiki pages you were
pointed at, a handful of recent email threads you are on, meeting notes, the last few
project updates. Nothing you have not been given. Nothing from a system you were not granted.

Then:

```
I started a new job last week. I am going to paste in internal documents I have been given
access to. I do not want a summary.

Do this instead:

1. Pull out every term, acronym, system name, project codename, role title, and piece of
   internal shorthand that appears. Include ones you can only half-infer.
2. For each one, write what you think it means BASED ONLY ON THIS DOCUMENT, and mark your
   confidence: CLEAR (the document defines it), INFERRED (I am guessing from context), or
   UNKNOWN (it appears but I cannot tell what it is).
3. Then interview me. Ask me one question at a time about the INFERRED and UNKNOWN ones.
   Ask the question a curious new colleague would ask, not a quiz question. Wait for my
   answer before asking the next.
4. As I answer, build a running glossary table: Term | What it means | Who owns it |
   Where I learned this | Confidence.

Never fill in a definition you invented. If I do not know either, write UNKNOWN - ASK
SOMEONE and leave it.

Here is the first document:
```

That last instruction is load-bearing. Without it you will get a beautiful glossary that is
partly fiction, and you will quote it in a meeting. With it, the unknowns stay visibly
unknown, which is exactly what you want in week one, because unknowns are your question list.

Save the result as a plain file. Call it `glossary.md`. You will move it into your job folder
in week five.

The "Where I learned this" column is not bureaucracy. In three weeks you will read a
definition and wonder whether a person told you that or the machine guessed it. That column
is the answer. This is provenance, and it is the same discipline described in
[Verification](04-verification.md): every claim carries where it came from.

### Days 2-5, in parallel: the "I do not understand" list

Open a second plain file. Call it `questions.md`. Every single time something goes past you
that you do not follow - a term, a decision, a reference to something that happened before
you arrived, a process nobody explained - write one line in it. Do not stop to research. Do
not feel bad. Just write the line.

Format:

```
2026-01-14 | Someone said the "Q3 migration" is why we cannot change the export. What migration?
2026-01-14 | What is the difference between the ops dashboard and the reporting dashboard?
2026-01-15 | Who actually approves a discount? Manager said "it depends" and moved on.
```

Then, once a week, turn that file into a research loop instead of forty separate questions.
This is the loop shape from [The loop](03-the-loop.md), applied to your own ignorance:

```
Here is my list of things I do not understand about my new job. For each item, sort it into
exactly one of three buckets and tell me which:

A. ANSWERABLE FROM DOCUMENTS I HAVE - you can answer it from material I paste in.
B. ANSWERABLE FROM GENERAL KNOWLEDGE - it is a standard industry or software concept, not
   specific to this company, and you can explain it without guessing about my company.
C. MUST ASK A HUMAN - it depends on internal history, politics, or a decision nobody wrote
   down.

For bucket B, answer them now, briefly, and mark clearly where the general explanation might
NOT match how my company does it.

For bucket A, do not answer yet. Tell me, for each one, exactly which document or page I
should paste in, and then wait. Once I paste it, answer only from what is in it.

For bucket C, draft the actual question I should ask, and tell me who is most likely to know
based on what I have told you about the team. Keep each question to one sentence and make it
sound like a colleague, not an interrogation.

Do not answer anything in bucket A or C from general knowledge. Leave them.

My list:
```

Bucket B is the win. Half of what confuses you in a new job is not company-specific at all -
it is a standard concept everyone assumes you know. The AI clears those in minutes, for free,
without you having to admit to a human that you did not know what a purchase order is.

Bucket C is the other win. You walk into your one-on-one with five sharp, specific questions
instead of a vague "still getting up to speed." That is what looking fast looks like.

### End of week 1, the honest checkpoint

You should have three files: `glossary.md`, `questions.md`, and either a copy of the AI policy
or a written note saying who you asked and what they said. That is it. Nobody has automated
anything. That is correct.

---

## Weeks 2-4 - Notice the repetition

By week two you are doing actual work, and you are doing some of it for the second and third
time. This is the phase where most people's AI use plateaus, because they use it
conversationally - ask, get answer, close tab, forget - and rebuild the same prompt from
scratch every Tuesday.

The fix is embarrassingly low-tech: **write down the thing you did twice.**

### The friction log

One plain file. Call it `friction.md`. Keep it open. Every time you catch yourself doing
something for the second time, or being annoyed by something, add a line. Thirty seconds
maximum, or you will stop doing it.

```
# Friction log

Format: date | what I did | how long | did I do this before? | could a machine do the boring part?

2026-01-20 | Rewrote the weekly status update from my notes | 40 min | yes, 2nd time | probably - the shape is identical every week
2026-01-21 | Chased 4 people for numbers before the report | 25 min | yes, 3rd time | no, that is a people problem, not an AI problem
2026-01-21 | Reformatted a client's spreadsheet into our template | 30 min | yes, 2nd time | yes, this is pure mechanics
2026-01-22 | Read a 60-page vendor doc to find one clause | 50 min | 1st time | maybe, if it happens again
2026-01-23 | Wrote the same "here is what we need from you" email to a new supplier | 10 min | yes, 4th time | yes, obviously
```

Two columns matter more than the others. "Did I do this before" is the trigger. "Could a
machine do the boring part" is the honest filter - and notice that the answer is allowed to be
no. Chasing four people for numbers is not an AI problem. Writing that down and choosing not to
automate it is a correct outcome, and it is a skill in itself.

### The rule of three

Once is an event. Twice is a coincidence. **Three times is a process, and a process should be
written down.** That is the whole heuristic. You do not need a scoring rubric.

At the end of week three, run this:

```
Here is my friction log from the last two weeks. I want to turn the top of it into repeatable
procedures.

1. Cluster the entries. Things that look different but are the same underlying task should be
   grouped - say so when you group them and why.
2. Rank the clusters by (how often it recurs) x (how much of it is mechanical rather than
   judgement). Show me your reasoning in one line each, not a score out of 10.
3. Recommend exactly three to codify first. For anything you do NOT recommend, say why -
   "too rare", "needs judgement I cannot verify", "this is a people problem", or "a rule or a
   template would fix this without AI at all".
4. Be honest about number 4: if one of them should just be a saved template or a spreadsheet
   formula, tell me that instead of proposing an AI solution.

My friction log:
```

Point 4 is the one people delete, and it is the most valuable. The discipline is
**deterministic before probabilistic**: if a template, a rule, a saved search, or a formula
does the job, use that. It is faster, it is free, and it does the same thing every time. Save
the model for things that genuinely need judgement. A large share of what you first want to
automate turns out to be a template.

### Turn the top three into skills

A skill is a written-down procedure the AI reads and follows: a description of when to use it,
the steps, and any tools or reference material it needs. Full treatment is in
[Skills](05-skills.md); here is the ninety-day version.

Take the number-one cluster. Do it once, well, with the AI. Get the output right. Then:

```
Look back at the work we just did together on [the weekly status update].

Turn it into a reusable skill:

- A one-line description of exactly WHEN this should be used, specific enough that you would
  recognise the situation without me naming the skill.
- The step-by-step procedure we actually followed, including the corrections I made to you
  along the way - those corrections are the most important part, do not drop them.
- The inputs I have to provide every time, listed explicitly.
- A done-check: how do we know the output is right BEFORE I send it? Make it something you
  can actually check, not "looks good".
- What must never happen (the mistakes we hit today).

Write it as a single markdown file I can save and hand back to you next week. Keep it under
one page. Do not pad it.
```

Save it. Next week, before you do that task, paste the skill file back in and say "use this."
Then improve it. Every time you correct the AI on that task, ask whether the correction is a
one-time thing or a rule that should live in the skill forever. If it is a rule, update the
file. That single habit is the difference between an assistant that is the same on day ninety
as on day one and one that is meaningfully better.

Record each one in [SKILLS-BUILT.md](../progress/SKILLS-BUILT.md) so you can see the pile grow.
By day ninety, three real skills that you use weekly beats thirty clever prompts you have
forgotten.

---

## Weeks 5-8 - Build the memory layer

You now have a glossary, a question list, a friction log, and three skills, and they are
probably scattered across a desktop, a notes app, and a chat window. Week five is where they
become a system that the AI can read.

This is the layer that carries most of the value. The full argument is in
[Memory and the second brain](06-memory-and-second-brain.md). The ninety-day version is: the
AI forgets everything when the conversation ends, so your memory has to live in files outside
the conversation, and those files have to be organised so that they can be found again.

The test for whether your memory system is any good is exactly one question: **can it find it
again?** If the answer is no, the folder structure is wrong. It is not the AI's fault.

### The folder

Make one folder for the job. Anywhere you like, as long as it is somewhere you can point an AI
tool at, and somewhere that complies with whatever the policy said in week one.

```
my-job/
  README.md            <- the router: read this first, it says where everything is
  glossary.md          <- from week 1
  questions.md         <- from week 1, still live
  friction.md          <- from weeks 2-4, still live
  people.md            <- who does what, who decides what, how they like to be talked to
  systems.md           <- what tools exist, what each is for, who owns it, my access level
  decisions.md         <- append-only log of decisions made and why
  processes/
    weekly-status.md   <- one file per recurring process
    new-supplier.md
  skills/
    weekly-status/
    supplier-intro/
```

Do not build more structure than that on day one. Folders are cheap but empty folders are a
lie about how organised you are.

### The router file

`README.md` is the most important file in the folder and the shortest. It exists so that an
AI, reading it cold, knows where to go next without reading everything. Reading everything is
slow and expensive, and it crowds out the actual work - see
[The context window](02-the-context-window.md).

Write it roughly like this:

```markdown
# My job - start here

I am a [role] at a [what the company does] company. I started [month].
My team is [n] people; my manager is [name/role].

## What I am responsible for
- [thing 1]
- [thing 2]

## Where things live - read ONLY what the current task needs
- Internal terms and acronyms -> glossary.md
- Who does what, who decides -> people.md
- What tools exist and who owns them -> systems.md
- Why something is the way it is -> decisions.md
- How to run a recurring task -> processes/<task>.md
- Things I still do not understand -> questions.md

## Rules for you when you work with me
- Read this file plus the ONE file the task needs. Never read the whole folder.
- Anything you tell me that is not in these files, mark as your own inference, not fact.
- If a fact belongs in this folder and is not there yet, say so and offer the exact line
  to add and the file to add it to.
- Never write anything into these files that identifies a customer or client by name.
```

That last rule is deliberate. Your memory folder will end up as the thing you paste into AI
tools most often, so it must be clean.

### What actually goes in the files

**`people.md`** - the file that most improves your first year, and the one people are most
squeamish about writing. Keep it professional. It is a working file, not a diary.

```markdown
## [Name] - [role]
- Owns: [what they decide, what they can unblock]
- Works with me on: [what]
- Prefers: short written asks, decisions in writing, no surprises in meetings
- Learned this from: three meetings + my manager mentioned it
```

If a line in that file would embarrass you to have read aloud by the person it describes, do
not write it. That is the whole rule, and it is enough.

**`systems.md`** - what the tool is, what it is for, who owns it, whether you have access,
and any trap you hit. Future-you will look up "why can I not export from that" nine times.

**`decisions.md`** - append-only. Never edit a past entry; add a new one that supersedes it.

```markdown
2026-02-03 | We are keeping the manual approval step for discounts over 10%.
  Why: two mispriced deals last year. Decided by: [role]. Source: team meeting.
  Reconsider if: volume doubles.
```

This file will make you look like you have been there for years, because it holds the one
thing nobody writes down and everybody forgets: **why**.

**`processes/<task>.md`** - the steps, the inputs, the done-check, the traps. If it feels
familiar, it should: this is the same shape as a skill. Some of these will graduate into
skills and that is the natural progression.

### The weekly capture habit

Fifteen minutes, same slot every week, protected. Friday afternoon works because the week is
still in your head. Without a fixed slot this dies in three weeks, and then in month six you
will be re-learning things you already learned.

```
It is my weekly capture. I am going to brain-dump what happened this week - meetings,
decisions, things that confused me, people I worked with, things that went wrong.

Your job is to sort it into my job folder, not to summarise it.

For each thing I mention:
- Say which file it belongs in (glossary.md, people.md, systems.md, decisions.md,
  processes/, questions.md, friction.md) and give me the EXACT line or block to paste in.
- Match the format already used in that file.
- If something contradicts what is already in a file, flag the contradiction explicitly and
  ask me which is right. Do not silently overwrite.
- If something belongs in no file, say "no home - discard" and move on. Do not invent a
  new file unless the same kind of thing has come up three times.
- Anything involving a named client or customer: replace the name with a role or a label.

Then, at the end, ask me the three questions a colleague would ask about my week that I did
not answer.

Here is my week:
```

Dictate it if that is easier. Rambling is fine; sorting is the machine's job.

That final instruction - ask me the three questions I did not answer - is what turns a filing
exercise into learning. It regularly surfaces the thing you have been avoiding.

---

## Weeks 9-12 - Automate one boring thing, and start showing others

### The one automation

One. Not a system. One boring, reversible, low-stakes task, run by you, checked by you, on
something where being wrong costs you fifteen minutes and no credibility.

Trust is earned in an empty parking lot, not on the highway.

Pick a candidate against these criteria. All of them, not most:

| Criterion | Why |
|-----------|-----|
| Reversible | If it is wrong, you undo it. No sent emails, no filed records, no external systems |
| Internal only | Nothing a client, customer, or vendor sees |
| Boring | The output is mechanical and you can tell instantly if it is wrong |
| Yours | It is your own work product, not a shared or team-owned process |
| Repeated | You have done it at least five times, so you know what right looks like |
| Checkable | There is an objective done-check, not a vibe |

Good candidates in most jobs: turning your rough notes into the standard weekly update
format; reformatting incoming data into your template; drafting the first version of a
recurring internal document; pulling the same five figures out of the same report into the
same summary; producing a first-pass agenda from last meeting's notes.

Bad candidates, no matter how tempting: anything that sends, posts, files, submits, or
replies to a human outside your team.

Then wrap it in a done-check, because an automation without a done-check is just a faster way
to be wrong. See [Done checks](../protocols/DONE-CHECKS.md).

```
I want to automate [the task]. Before we build anything, design the done-check.

1. Write down what a CORRECT output looks like, as a list of specific checkable properties -
   not "well written", but things like "every figure in the summary appears in the source
   document", "the date range matches the requested range", "there are exactly five sections
   in this order".
2. For each property, say HOW it gets checked and WHO checks it - you, me, or a separate
   pass that re-reads the source with fresh eyes.
3. Tell me the three most likely ways this quietly goes wrong without looking wrong.
4. Give me a hard stop: if the check fails twice on the same input, stop and hand it back
   to me rather than trying again.

Only after that, write the procedure itself.
```

Run it manually for two weeks with you checking every output before it goes anywhere. If it
is right every time for two weeks, you have earned the right to trust it a little. If it is
wrong once, you learned something more valuable than the time you were trying to save - write
it into the failure list in [Failure modes](../protocols/FAILURE-MODES.md).

Log the decision in [DECISIONS.md](../progress/DECISIONS.md): what you automated, why, and
what would make you turn it off.

### Start being the person who shows others

Around week nine, people will have noticed that you turn things around quickly and that your
work holds up. Some of them will ask how. What you do next determines whether the next
ninety days are pleasant.

The useful thing to share is **the method, not the fact that you used a tool.**

"I used AI" tells a colleague nothing, invites a debate about AI, and in some rooms reads as
"my work is machine-generated." "I keep a file of every decision we make and why, so I do not
have to ask twice" tells them something they can copy tomorrow, and it is also the true
answer.

Concretely, when someone asks how you turned that around so fast:

> I keep a running file of the recurring stuff - the steps, the format, the mistakes we made
> last time. So the second time is mostly assembly. I run the draft past a checklist before I
> send it. Happy to show you the file if it is useful.

That is honest, it is specific, and it is repeatable by them. If they then ask what tools you
use, tell them plainly. The order matters: method first, tools second.

Then do one thing that is worth more than any of it: **give one skill away.** Take your best
process file, strip anything specific to you, and hand it to the next new person. It costs
you nothing. It changes how you are seen from "fast" to "makes the team faster," and those are
very different reputations.

```
Take my process file for [task] and rewrite it so a colleague who has never used an AI tool
could follow it.

- Remove anything specific to me, my folder structure, or my access.
- Assume they know the job but not the tool.
- Keep the exact prompts, in copyable blocks - those are the useful part.
- Add a short "what can go wrong" section at the end with the mistakes I actually hit.
- Do not add enthusiasm or a sales pitch. Plain and useful.
```

---

## Throughout: the professional and political dimension

This section is the one that protects everything else, and it gets skipped because it is not
fun. Read it twice.

### Never present unverified output as your own work

Not a moral point - a survival one. Every AI system produces confident, fluent, wrong output
sometimes. Fluency is not accuracy. If you pass it along unchecked and it is wrong, the
failure is attributed to you, correctly, because you are the one who sent it.

The rule that keeps you safe is small: **anything with a number, a name, a date, a
quotation, a policy, or a commitment in it gets checked against the source before it leaves
you.** Not skimmed. Checked. Prose can be edited; facts have to be verified.

```
Go back through this draft and mark every claim that a reader would take as fact - numbers,
dates, names, policies, quotes, causal claims, commitments.

For each one, tag it:
[SOURCED] - it came from a document I gave you, and quote the exact supporting line
[INFERRED] - you worked it out, and say from what
[UNCERTAIN] - general knowledge rather than the documents, or you are not confident, or
              the sources disagree, or you filled a gap with a default. Say which one

List every UNCERTAIN and INFERRED item at the top as a checklist for me. Do not soften
this - if you cannot point at the source line, it is UNCERTAIN, even if you are confident.
```

Run that on anything that leaves your hands. It takes under a minute and it is the single
highest-value habit in this chapter.

### Be known for accuracy, not for volume

There is a strong temptation, in a new job with a fast tool, to become the person who produces
a great deal of output. Resist it for a quarter.

Volume is easy now and everyone can see that it is easy. Being the person whose numbers are
always right, who says "I do not know yet, I will confirm by Thursday," and who then confirms
by Thursday is not easy, and it compounds. A handful of careful documents beats a pile of fast
ones. The pile creates work for other people, and they will notice who created it.

Practical version: when you have finished something quickly, do not immediately send it. Spend
some of the time you saved on checking it. You are still faster than everyone. You are also
right.

### When someone asks whether you used AI

Answer plainly. Do not be defensive, do not be evangelical.

> Yes, for the first draft and the formatting. The figures I pulled from the source report
> myself and checked, and the recommendation is mine.

That sentence is complete. It says what the tool did, what you did, and where the judgement
came from. Nobody who hears it is worried.

What not to say: "AI wrote it" - which gives away your judgement, or a vague deflection -
which sounds like concealment. And never claim you did not use it when you did. That one is
unrecoverable.

### Do not become the AI person

If your identity at work becomes "the AI person", two bad things happen. You get handed every
half-formed automation idea in the building, and your actual work becomes invisible. Be a
person who is good at the job. The method is how, not what.

---

## Things not to do in the first 90 days

A short list. Each one has ended someone's good start.

**Do not automate anything client-facing.** No auto-replies, no auto-sent messages, no
generated content that reaches a customer, vendor, or partner without a human reading every
word. The upside is a few minutes. The downside is a wrong commitment in writing, under your
name, to someone outside the company.

**Do not connect the AI to systems you do not own.** Do not wire it into the shared CRM, the
team's email, the billing system, or a production database because you found a way to. Access
you were given for your own reading is not authorisation to hand to a tool. If you want a
connection, ask the person who owns the system, in writing, and let them say yes. See
[Tools and MCP](07-tools-and-mcp.md) for what these connections actually are, and
[Safety, privacy and trust](10-safety-privacy-and-trust.md) for the boundary.

**Do not paste what you have not cleared.** Customer data, personal data, anything under a
contract or NDA, unreleased financials, source code, security details, anything marked
confidential. If you are unsure, the answer is no until someone with authority says yes.
"I did not know" is not a defence anyone accepts.

**Do not build a big system in month one.** You do not yet know what the job actually is. The
elaborate thing you build in week two will encode your week-two misunderstanding and you will
defend it for a year because you built it.

**Do not let the AI represent you in a room.** Do not read out an answer you do not
understand. If you cannot explain it in your own words, you cannot present it. Every
experienced person in that room can tell, and they will ask the follow-up question.

**Do not fix a process on your first look at it.** Things that appear stupid usually have a
reason that predates you - a regulator, an incident, one furious customer. Put it in
`questions.md`, ask why, and then decide. Suggesting an improvement is good. Announcing that
everything here is broken in week three is not.

**Do not quietly change a shared document with generated content.** If you improve a team
document, say what you changed and why. Silent edits are how trust ends.

**Do not use it as a therapist about your colleagues.** It is a work tool, on work systems,
and it agrees with you far too readily. Whatever it says about the difficult person in your
team is not evidence, and you do not want that conversation existing anywhere.

**Do not skip the boring documentation of what you learned.** The week you stop writing things
down is the week your advantage starts decaying, silently, and you will not notice for months.

---

## If you fall behind the schedule

You will. Weeks are not sacred; the order is. Each stage makes the raw material for the next -
the glossary and questions feed the memory folder, the friction log feeds the skills, the
skills feed the automation - so if week five arrives and the folder does not exist, build the
folder. Do not jump to automation because the calendar says week nine.

The one thing you cannot skip is week one's policy question. If you have gone six weeks
without asking, ask this week.

---

## Try this now

Copy this whole block into your AI tool. It builds your week-one starting kit in one pass.

```
I have just started a new job and I am going to use you as a learning system for the first
90 days. Set me up right now.

Ask me these, one at a time, and wait for each answer:
1. What is the job, and what am I actually responsible for?
2. What documents or materials have I already been given access to?
3. What has confused me most in the first few days?

Then produce four things:

A. A short list of the questions I should ask my manager this week about AI use at this
   company - policy, approved tools, and what must never be pasted into one. Written so I
   can send them as-is.

B. A starter glossary file with the terms I have already mentioned, each marked CLEAR,
   INFERRED, or UNKNOWN. Do not invent definitions. UNKNOWN is a good answer.

C. A "questions.md" starter file with everything I said confused me, one per line, dated.

D. A "friction.md" file with the header and format ready, plus one example row, so I can
   start logging repeated work from tomorrow.

Rules for you throughout: never state something about my specific company as fact unless I
told you or it is in a document I pasted. Mark inferences as inferences. If you do not know,
write UNKNOWN and tell me who to ask.
```

Then, at the end of your first week, come back and run the research-loop prompt from the
week-one section on your `questions.md`.

---

## What you should now be able to do

- Run a structured first week that produces three real artifacts - a glossary built from your
  own documents, a live list of what you do not understand, and a clear answer on your
  company's AI policy - instead of a vague feeling of catching up.
- Catch your own repeated work with a friction log, apply the rule of three, and tell the
  difference between work that deserves a skill and work that just needs a template or a
  conversation with a human.
- Stand up a job memory folder with a router file that an AI can navigate cheaply, and keep it
  alive with a fifteen-minute weekly capture habit.
- Choose a first automation that is boring, reversible, and internal, give it a real
  done-check, and explain your method to colleagues without making the tool the story.
- Recite the things not to do without looking them up, because those are the ones that end
  good starts.

---

Next: [The hype ledger](12-the-hype-ledger.md) - what to disbelieve, including some of what
you will hear at your new job. Then [Graduation](13-graduation.md).
