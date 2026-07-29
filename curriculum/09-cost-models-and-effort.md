# Cost, Models and Effort

*Cost has two levers, not one. Almost everyone uses the first and ignores the second. This file teaches both, plus how to write a routing policy instead of guessing every time. Read time: about 20 minutes.*

---

## Start here, because it changes how you read the rest

**Specific model names, version numbers, and prices go stale in weeks.** Any number written down
in a file like this one is wrong by the time you read it, and a confident wrong number is worse
than no number.

So this file teaches the **shape** of the decision — which is stable — and deliberately prints no
prices and no model version numbers. When you need current specifics, ask your assistant
directly. There is a prompt for exactly that at the end.

If you take one thing: the shape has been the same through several generations of models, and it
will probably outlive the next several. Learn the shape.

---

## Why cost exists at all, mechanically

You do not need billing knowledge, but you do need the mechanism, because it explains behavior
you will otherwise find baffling.

Text is broken into **tokens** — roughly word-sized pieces. You are charged, or your usage is
counted, on tokens in and tokens out. Two consequences:

**Long conversations get expensive on their own.** Every turn, the model re-reads the entire
conversation so far in order to produce the next reply. Turn 40 re-reads everything from turns
1 through 39. Nothing accumulates for free. This is why a sprawling all-day chat costs more per
useful answer than five focused ones, and it is a second reason — beyond quality — to hand off
to a fresh session. See [The context window](02-the-context-window.md).

**Reading is not free.** Pointing your assistant at a 300-page document costs whether or not the
answer needed page 3 only. That is the same insight as "deterministic before probabilistic" from
[Tools and MCP](07-tools-and-mcp.md), arriving from the money side: search first, read second.

Whether you pay per token or through a subscription with usage limits, the mechanism is
identical. On a subscription you feel it as running out of room sooner rather than as a bill.
Everything in this file applies either way.

---

## Lever one: which model

Assistants offer a choice of engine. The naming changes constantly, but the tiers do not. There
are essentially three, and every vendor ships something in each band:

| Tier | What it is for | The honest trade |
|------|----------------|------------------|
| **Strong** | Hard reasoning: difficult code, subtle architecture, long-form prose that has to actually be good, ambiguous problems where the hard part is deciding what the problem is | Slowest and most expensive. Wasted on anything easy. |
| **Mid** | Most knowledge work: analysis, summarizing, drafting, decks, research synthesis, ordinary code, everyday judgment | The default. Good enough for the large majority of real work. |
| **Small and fast** | Grunt work: reformatting, extracting a known field, classifying into buckets, renaming, tidying, first-pass triage, mechanical transformation | Cheapest and quickest. Will disappoint you on anything requiring taste. |

Three things people get wrong about this:

**Wrong 1: always using the strongest one.** It is the safe-feeling choice and it is expensive
without being better at reformatting a list. The tiers pull apart on problems that are genuinely
hard and converge on ones that are not — a list is either reformatted correctly or it is not, and
there is no extra credit available. That convergence on easy work is the whole reason routing
saves anything.

**Wrong 2: always using the cheapest one.** The failure is not that it produces obviously bad
output. It produces *plausible* output with quiet errors, and you spend more time finding them
than you saved. Cheap models are excellent at mechanical work and unreliable at judgment.

**Wrong 3: treating it as a permanent setting.** The choice belongs to the *task*, not to you.
Changing tier mid-session is normal and takes one command in most tools.

A useful framing borrowed from people who do this all day: the harness is the car, the model is
the engine. You can swap engines for the drive you are actually making. A delivery van and a
sports car are not ranked; they are chosen.

---

## Lever two: how much effort, on a single task

This is the one almost nobody uses.

Most modern assistants let you control how much reasoning the model spends *before* it answers —
sometimes called effort, thinking budget, or reasoning level, usually with a few settings from
low to maximum. It is a separate dial from which model you picked. You can run a strong model at
low effort or a mid model at high effort.

Here is the part that matters: **on routine work, low effort usually produces the same answer for
less.** Reformatting a table does not benefit from extended deliberation. Neither
does extracting dates, classifying emails, or restructuring text you already wrote. The extra
thinking is spent and then discarded.

And the reverse: on a genuinely hard problem — a design with real trade-offs, a bug whose cause
is not where the symptom is, a document whose structure is the actual difficulty — raising effort
on the *same* model is often a bigger improvement than moving up a tier.

| Situation | Effort |
|-----------|--------|
| Mechanical transformation, known format in, known format out | Low |
| Ordinary drafting, summarizing, routine analysis | Low to medium |
| Anything where you would want a smart colleague to think before speaking | Medium to high |
| Architecture, ambiguous specs, subtle debugging, high-stakes prose | High or maximum |
| Second opinion on work you suspect is wrong | High, and a different model than produced it |

Two honest caveats. First, effort controls are named differently in every tool and some tools do
not expose them at all — ask your assistant what it has rather than assuming. Second, this is a
principle drawn from how these systems work and from practitioner reports, not a measured result
with a number attached to it. Test it on your own routine tasks: run the same low-stakes job at
low and at high effort, and see whether you can tell the outputs apart. If you cannot, you have
found your default.

---

## Routing as a written policy, not a vibe

Here is what actually happens without a policy: you use whatever the tool defaulted to, forever,
and you either overpay on everything or under-serve your hardest work. Deciding fresh each time
is a decision you will not reliably make, because it arrives at the moment you are focused on
something else.

So write it down once. A routing policy is four or five lines of plain English that live where
your assistant reads them every session — your project instructions file, or your standing
context. See [Memory and the second brain](06-memory-and-second-brain.md) for where that lives.

### A starter policy you can adapt today

```
ROUTING POLICY

Default: mid tier, low-to-medium effort. Most of my work lands here.

Escalate to the strongest model when:
  - the output is going to a client, an executive, or the public
  - it is code that other people will depend on
  - the problem is ambiguous and the hard part is deciding what the
    problem actually is
  - I have already gotten a wrong or shallow answer once

Drop to the small fast model when:
  - the task is mechanical: reformat, extract a known field, classify
    into buckets I have already defined, rename, tidy, convert
  - I am doing a first-pass triage over a large pile and a human
    (me) will review the shortlist anyway

Raise effort rather than changing model when:
  - the task is hard but small
  - the failure I got was shallow reasoning, not missing knowledge

Always tell me which tier and effort you used, in one line at the end,
so I can learn where my guesses were wrong.
```

That last line is the part people skip and it is the most valuable one. It turns every task into
a data point about your own routing. After two weeks you will know which of your rules were
wrong.

### A starter routing table by task type

Adapt the rows to your actual job. The point is not this exact table; it is having *a* table.

| Task | Tier | Effort | Why |
|------|------|--------|-----|
| Reformat a messy list into a clean table | Small | Low | Mechanical, verifiable at a glance |
| Extract dates, names, amounts from many similar documents | Small | Low | Known fields, and you will sample-check |
| Classify a backlog into categories you defined | Small | Low | Rules are already set; the model is applying, not deciding |
| Summarize one meeting transcript | Mid | Low | Common, well-practiced, low ambiguity |
| Draft a routine internal update | Mid | Low | Judgment, but familiar judgment |
| Analyze a spreadsheet and tell you what is notable | Mid | Medium | Requires noticing, not just reporting |
| Research a question across several sources and synthesize | Mid | Medium | Volume plus judgment; escalate if conclusions conflict |
| Write a plan or spec for a substantial piece of work | Strong | High | Downstream cost of a bad plan is enormous |
| Write or restructure prose that has to be genuinely good | Strong | High | This is the tier gap at its widest |
| Design or debug something with real trade-offs | Strong | High | Ambiguity is the whole task |
| Adversarially check work you already have | Strong | High | Use a different model than produced it — see below |
| Decide whether "done" is really done | Strong or Mid | Medium | See [Verification](04-verification.md) |

One rule that overrides the table: **do not have the same model at the same effort grade its own
output.** A checker should be different from the worker, and for anything consequential the
checker should not be the cheap tier. This is the core idea in
[Verification](04-verification.md) and it is worth spending on.

---

## The two-tier plan/execute pattern

This is the highest-value pattern in this file, and it needs no special feature — it is a way of
splitting a request, so it works in any tool.

Most large tasks have two very different phases. Phase one is figuring out what to do: reading
the material, understanding constraints, deciding on an approach, writing it down. Phase two is
doing it: many steps, mostly mechanical once the approach is settled, but long.

Those phases want different engines.

**The pattern:**

1. **The strong tier, at high effort, researches and writes the plan.** Give it the material, have
   it ask you questions, have it produce a written plan with explicit success criteria. Spend
   here without flinching: this phase is short — it is thinking, not producing — so the expensive
   tier costs little in absolute terms, and a wrong decision made here gets paid for at every
   step afterwards.
2. **You read the plan.** This is the whole point. A plan is short enough to actually review,
   unlike the output it will produce. Correct it here, where correcting is free.
3. **A model executes against the approved plan.** It is not re-deriving the approach; it is
   carrying out a decided approach, with a written standard to be checked against. Because the
   hard decisions are already made, this phase can often drop a tier — which is where the saving
   comes from, since this is the long phase.

Why this saves money and improves quality at the same time: an unplanned run spends its most
expensive reasoning re-deciding the approach at every step, and drifts as a result. A planned run
spends its reasoning on execution against a fixed target. And when it goes wrong, you can see
*where*, because there is a plan to compare against.

Variations you will see recommended, all the same idea: research with a cheaper model and hand
the notes up; plan with the strong model and execute with the mid one; plan once and execute
many times. Which direction you split depends on where the difficulty lives — if deciding is
hard, spend up top; if doing is hard, spend at the bottom.

### Exact wording to start it

```
Before you do any of this work, produce a PLAN only. No implementation,
no drafting the deliverable, no files changed.

The plan must contain:
1. What you understand the goal to be, in your own words.
2. The steps, in order, with what each one produces.
3. The success criteria: how we will both know this is done and correct.
   Make these checkable, not adjectives.
4. Every assumption you are making, and every question you need me to
   answer before starting.
5. What could go wrong, and what you will do about it.

Keep it under one page. Then stop and wait for me to approve it.
```

Then, after you have edited it:

```
Execute the approved plan exactly. If you hit something the plan did not
anticipate, stop and tell me rather than improvising. At the end, walk
through the success criteria one at a time and show me the evidence for
each.
```

That last sentence connects this file to [Verification](04-verification.md), which is where the
"show me the evidence" habit is taught properly.

---

## Turn expensive output into a cheap, reusable artifact

Here is the compounding move, and it is the difference between saving money once and saving it
permanently.

When a strong model at high effort produces something genuinely good — a plan, a spec, a
checklist, a template, a set of rules, a worked example — **that output is an asset.** Capture it
as a file. Then a cheaper model executes against it, repeatedly, for as long as the work recurs.

You paid the hard price once, for the thinking. You never pay it again for the doing.

Concretely:

| Expensive thing you produced once | Cheap thing it enables forever |
|-----------------------------------|-------------------------------|
| A carefully reasoned plan for a recurring project type | Every future project of that type starts from the template |
| A specification of what "good" looks like for your reports | A mid or small model drafts, and checks itself against the spec |
| A worked example of the exact output format you want | Every future run matches the format without negotiation |
| A written checklist of the failure modes in your domain | A cheap model runs the checklist mechanically |
| A well-designed prompt that took an hour to get right | A [skill](05-skills.md) anyone on your team invokes by name |

The last row is the general case, and it is why [Skills](05-skills.md) is the highest-leverage
file in this harness. A skill is expensive thinking, frozen into a reusable form, executed
cheaply from then on. The routing question and the skills question are the same question viewed
from two sides.

A caution so this does not become dogma: an artifact captured from one good run can also freeze
in a mistake, and a cheap model executing a flawed spec will execute it flawlessly, forever.
Review your artifacts when the work changes. Note the review date in
[DECISIONS.md](../progress/DECISIONS.md).

---

## Five habits that cut cost without costing quality

1. **Start fresh sessions.** A new session for a new task is cheaper than continuing a long one,
   because the long one re-reads its whole history every turn. Use a
   [handoff](../protocols/SESSION-PROTOCOL.md) when you need to carry context across.
2. **Search before reading.** Find the six relevant documents rather than reading four hundred.
   The tool discipline in [Tools and MCP](07-tools-and-mcp.md) is also a cost discipline.
3. **Ask for the shape first.** An outline, a table of contents, or a one-paragraph approach
   before the full draft. Correcting a wrong direction after one paragraph costs nothing;
   correcting it after ten pages costs ten pages twice.
4. **Disconnect connectors you are not using.** Their descriptions occupy the context window on
   every single turn, whether used or not.
5. **Set a stop condition on anything that runs unattended.** An agent looping without a hard
   stop is the easiest way there is to spend real money on nothing. This is covered in
   [The loop](03-the-loop.md) and [DONE-CHECKS.md](../protocols/DONE-CHECKS.md).

---

## What not to believe

- **"Model X beats model Y"** based on the vendor's own announcement. Vendors benchmark
  themselves favorably. The only benchmark that matters is your own work, and it takes one sitting
  to run: same task, both models, compare the outputs yourself.
- **Precise multipliers.** "3x faster," "40% cheaper," "twice the quality" — these are marketing
  artifacts unless someone shows you the method. Quality especially does not have a unit.
- **Urgency.** Any pitch where the reason to adopt something is that you will fall behind is
  selling, not advising. See [The hype ledger](12-the-hype-ledger.md).
- **Any price or model name written in a document,** including this harness. Check it live.

---

## Try this now

Two prompts. The first gets you current facts, which this file deliberately does not contain.
The second turns them into a policy you will actually use.

```
I need current, specific information about model choice and cost, because
the guidance I am reading deliberately avoided printing names and prices
that go stale.

Tell me, for the assistant I am using right now:

1. Which models are available to me, listed from cheapest and fastest to
   strongest and most expensive. Give me the exact names and how I switch
   between them in this tool.

2. Whether I have any control over reasoning effort or thinking budget on
   a single task, what the settings are called, and exactly how I set them.
   If I do not have this control, say so plainly.

3. How I am actually billed or limited — per token, by subscription
   allowance, or both — and where I can see my current usage.

4. For each of these, tell me which tier and effort you would use and why:
   reformatting a messy list; summarizing a long meeting transcript;
   writing a project plan I will send to my manager; extracting dates and
   amounts from fifty similar invoices; debugging something that is failing
   for a reason I cannot see.

Mark clearly anything you are unsure about or that may have changed since
your training. Do not guess at prices.
```

Then:

```
Using the answers you just gave me, write a routing policy for me in plain
English, under fifteen lines. It should cover: my default tier and effort,
the conditions that make me escalate, the conditions that make me drop to
the cheap tier, and a rule for when to raise effort instead of changing
model. End it with an instruction that you tell me which tier and effort
you used at the end of every task, so I can correct the policy over time.

Then tell me exactly where to save this file so you read it automatically
at the start of every session in this tool.
```

Save the policy. Revisit it in two weeks against what actually happened.

---

## What you should now be able to do

- Explain why cost has two levers — which model, and how much effort on a single task — and use
  the second one, which most people never touch.
- Route a task to a tier on purpose, using a written policy rather than a guess, and improve that
  policy from evidence because you asked the assistant to report what it used.
- Run the two-tier plan/execute pattern: get a short reviewable plan with checkable success
  criteria first, correct it while correcting is cheap, then execute against it.
- Recognize expensive output as an asset — capture it as a plan, spec, or skill that a cheaper
  model then executes repeatedly — and know that any model name or price you read, here included,
  needs checking live.

---

Next: [Safety, privacy and trust](10-safety-privacy-and-trust.md) — the rules for what you let an
assistant touch, and how trust gets earned in small, reversible steps.
