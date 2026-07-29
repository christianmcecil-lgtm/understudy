# The Hype Ledger

*How to read any AI claim and work out for yourself whether it is true, plus an honest list of what is actually well supported. Read time: about 20 minutes.*

You are going to spend the next few years being told things about AI by people who benefit
from you believing them. Some of those things will be true. Most of the confident ones will
not be, and the difference is not obvious from the outside.

This file does not give you a list of what to believe. Lists go stale, and a list makes you
dependent on whoever wrote it — which is the exact problem. It gives you the reading method,
then applies that method honestly to the claims this harness itself makes, including the ones
it cannot fully support.

Two things to hold at once, because both are true and people usually only manage one:

- Most AI content you encounter is selling something, and its claims are unverifiable by
  construction.
- The underlying capability is real, and dismissing all of it because the marketing is bad
  costs you more than the marketing does.

The skill is separating those. It is a short method, and it gets easier every time you apply
it, because you start recognizing the shapes.

---

## Part 1 — The genre

AI hype content has a form. Once you can see the form, you stop evaluating each piece from
scratch, because you recognize the template before you have finished the first minute.

The template has four beats, usually in this order.

### Beat 1 — The confident demo

Something appears on screen, fast. A working app in twenty minutes. An agent that answered
email overnight. A dashboard that assembled itself. The demo is real in the narrow sense that
it happened, and it is not evidence of what it appears to be evidence of.

Three reasons a demo proves less than it looks like it proves:

- **You are watching the take that worked.** You do not see the four attempts before it, the
  prompt that was refined off-camera, or the parts quietly fixed by hand.
- **Demos select for demoable problems.** Building a clone of a well-known app is a task the
  model has seen a million examples of. Your actual job is a task it has seen zero examples
  of, with constraints living in your colleagues' heads.
- **Nobody shows the maintenance.** The interesting question about the twenty-minute app is
  what it looks like in week six, when someone needs it changed. That footage does not exist,
  because it is boring and because it is often bad.

A demo is an existence proof: this is possible under some conditions. It is not a
distribution: this is what happens when you try it.

### Beat 2 — The number with no methodology

A figure appears. Ten times faster. Ninety percent cheaper. Forty percent fewer tokens. Two to
three times better quality.

Ask one question: **how was that measured, on what, against what?** In hype content the answer
is essentially never present. The number came from one run, on the author's own machine, on a
task they chose, compared against a baseline they did not describe, with no repetition.

The tell is precision without procedure. "Roughly half the cost, in my experience, on this
kind of task" is a person reporting honestly. "40% token reduction" with no further detail is
a number doing rhetorical work rather than measurement work.

### Beat 3 — The scarcity or urgency frame

"This window is closing." "Access is being restricted." "In six months everyone will know this
and the advantage will be gone." "If you are not doing this now, you are already behind."

Urgency exists to prevent the thing that kills a sale: you closing the tab and thinking about
it for a day. Any argument that gets weaker when you take a day is an argument you should take
a day on.

There is a specific version aimed at professionals, and it is nastier because it uses your
conscientiousness: *your peers are already doing this and you are falling behind.* You cannot
verify that. Neither can they. It is unfalsifiable by design.

### Beat 4 — The funnel

At the end, a link. A community, a course, an "operating system," a Discord, a template pack,
a one-line install for the creator's own product. Sometimes a paid tier, sometimes free-now-
paid-later.

The funnel does not make the content wrong. It does mean every claim upstream of it was
selected for its ability to make you click, not for its accuracy. That is not cynicism about
the creator's character. It is how the incentive works regardless of character.

### Recognizing it in the wild

If a piece of content has all four beats, you have learned one thing from it: that this
technique exists and is worth investigating from a source that is not selling. That is a real
contribution. Take the pointer, discard the numbers, and go verify it yourself on your own
work.

---

## Part 2 — The checklist for reading any AI claim

Five questions. They take under a minute once you have internalized them, and they work on
research papers, vendor blog posts, colleagues in meetings, and this file.

### 1. Who measured it?

Not who said it — who *measured* it. There is a large difference between:

- A vendor measuring its own product
- A creator measuring a tool they are affiliated with
- An independent party with no stake, publishing method
- Someone reporting their own subjective experience and saying so

Only the last two are informative, and the fourth is informative in a limited way: it tells
you the thing is possible for one person on one workload. That is genuinely worth knowing. It
is not a general result, and honest people say which one they are giving you.

### 2. Against what baseline?

"Three times faster" than what? Than doing it by hand? Than the previous version? Than the
competitor's default settings, chosen by the person being compared against?

Most impressive AI numbers come from an unstated or badly chosen baseline. The classic is
comparing a carefully optimized new approach against a deliberately naive old one. Both
numbers are real; the ratio between them is fiction.

If you cannot name the baseline in one sentence, the comparison carries no information.

### 3. Could I reproduce it?

Concretely: could you, tomorrow, on your own work, run the same thing and see the same result?

If the claim is "this pattern makes my summaries better," yes — you can run twenty summaries
both ways and read them. If the claim is "this configuration is 46 times cheaper per query,"
you probably cannot, because you do not have their corpus, their queries, or their previous
setup.

Claims you can test are worth more than bigger claims you cannot. Prefer the small verifiable
one every time. The reproducible claim also has a second value: running it teaches you
something about your own work regardless of the result.

### 4. What would it look like if this were false?

This is the most useful question on the list and almost nobody asks it.

Take the claim and imagine the world where it is wrong. What would you observe? If the answer
is "exactly what I am observing now," the claim is unfalsifiable and you have learned nothing
by hearing it.

Worked examples:

| Claim | If it were false, you would see... | Verdict |
|---|---|---|
| "This prompt structure gets better answers" | Blind comparison of both versions shows no preference | Testable — go test it |
| "You are falling behind if you are not using agents" | Nothing. No observation distinguishes it | Unfalsifiable — ignore |
| "Cheaper models handle summarization fine" | Side-by-side summaries where the cheap one is visibly worse | Testable — go test it |
| "This tool is the best memory system available" | Depends entirely on undefined "best" | Unfalsifiable as stated |
| "Verification catches errors before they ship" | Verified runs shipping the same errors as unverified ones | Testable, and mechanically likely |

### 5. What is this person selling?

Not an accusation. A category. Everyone is selling something: a product, a subscription, a
consultancy, an identity as the person who knows things, an argument they already committed to
publicly. Including this harness, which is selling you a method and therefore has every reason
to overstate how well the method works.

Name it, then discount accordingly. A vendor's own benchmark is not worthless — it is a lower
bound on what they could achieve under favorable conditions, which is real information, just
not the information the headline claims.

### Running the checklist on a real-shaped claim

Here is a claim in the shape you will meet constantly. It is a composite, not a quotation from
anyone: the wording is assembled to carry the pattern, and the numbers are deliberately round
so that nobody mistakes them for a measurement.

> "This tool beats every other way of handling what the AI remembers — my setup takes 10,000
> tokens of context down to 1,000. One-line install, link in the description."

- **Who measured?** The person who built it and is distributing it.
- **Baseline?** Unstated. 10,000 tokens of what, doing what, against which configuration?
- **Reproducible?** No. You do not have their notes, their queries, or their prior setup.
- **If false?** You would see exactly this video. The number was asserted, never demonstrated
  on screen.
- **Selling?** The tool, plus a community.

Conclusion: one useful pointer (memory systems have a storage, injection, and recall problem,
and those are separable — that framing is genuinely useful), zero usable numbers. Take the
framing. Bin the ratio. Test on your own material if you care.

---

## Part 3 — Claim shapes that are reliably overstated

These are patterns, not accusations about specific products. When you see the *shape*, raise
your threshold for evidence before you act.

### Self-reported benchmarks from the vendor being benchmarked

Every vendor publishes numbers showing their thing is fastest, cheapest, or smartest. Those
numbers are usually not fabricated. They are selected: the benchmark chosen, the configuration
tuned, the comparison run in conditions favorable to the result. A vendor benchmarking itself
is measuring its best day.

Useful reading: treat as an upper bound on the vendor's performance, not an expected value for
yours.

### Precise multipliers on quality

"Verification makes output two to three times better." "This prompt pattern gives 10x results."

Quality is not a scalar. There is no unit. A precise multiplier on an unmeasurable quantity is
a rhetorical device wearing the costume of a measurement. The underlying claim — that checking
work improves work — is sound and mechanically obvious. The number is invented, and the number
is what people repeat.

When you catch yourself about to say "verification roughly doubles quality," say instead:
"having something check the work catches errors that the thing doing the work does not catch,
because it has no stake in the answer being right." That sentence is defensible and it is
actually more persuasive.

### "X beats Y," where the source is X's own marketing

Includes video titles, launch blog posts, comparison tables published by one of the two
parties, and community posts by people affiliated with one side. The comparison is real work
by real people, and it was constructed to produce a conclusion that was chosen first.

The strongest version of this trap is when the claim is *plausible*. A cheaper model probably
does handle a lot of everyday knowledge work well. That does not mean a specific figure like
"ninety-five percent as good at half the price" is a measured fact — that shape of claim
typically traces to a single editorial side-by-side on a handful of tasks. Believe the
direction. Do not repeat the ratio.

### Urgency and scarcity framing

"Access is being restricted." "Do this now or lose the advantage." "Everyone will know this in
six months."

Set aside whether it is true. Ask what it is *for*. Urgency is included to compress your
decision time, and compressed decision time favors the seller in every transaction that has
ever existed. A genuinely good tooling decision survives a week of thinking. Any that does not
was not a decision, it was a purchase.

Practical rule: never adopt a tool, subscribe to a service, or restructure a workflow on the
same day you first heard urgency framing about it. Wait a week. Almost everything looks
different, and the small number of things that still look good are the real ones.

### Anything that requires running agents around the clock

"Swarms working while you sleep." "Twenty-four seven agent fleets." "Overnight builds shipping
features."

Two problems, one obvious and one not.

The obvious one: cost and supervision. Unattended agents consume money continuously and
produce work nobody has checked. If the done-check is vague, they can run for many hours and
produce something unusable — a failure mode reported by the same practitioners who advocate
the technique, which is the version of a warning worth listening to.

The non-obvious one: **scaling a system you do not understand just scales its bugs.** A single
loop with a good verification step will outperform a fleet with a bad one, every time, for
much less money. Adding agents does not add judgment. It multiplies whatever judgment is
already encoded, including the wrong bits.

There are real uses for parallel agents — see [Subagents and swarms](08-subagents-and-swarms.md)
— and they look like "four reviewers reading the same document from four angles," not "an
army building a product overnight."

### The twenty-minute clone

A live build of something that already exists, in an unreasonably short time. Genuinely
impressive, and specifically unrepresentative: the model has seen enormous numbers of examples
of well-known application types, and none of your company's actual problem.

The honest version of the lesson is: **AI is fastest on well-trodden ground and slowest on
anything specific to you.** That is still extremely useful. It is just a different claim than
the one the demo implies.

### "One-line install"

Frictionless adoption is a sales feature, not a quality signal. And a one-line install of
someone's skill, plugin, or connector is you running their instructions and often their code —
see the installation warning in [Safety, privacy, and trust](10-safety-privacy-and-trust.md).
Ease of installation tells you about their packaging, not about their software.

---

## Part 4 — What is actually well supported, and boring

Now the fair part. If the whole field were noise, nobody serious would be spending time on it.
Here is what holds up, why it holds up mechanically, and how confident you should be.

The pattern to notice: **none of these are exciting.** That is the signal. The claims with real
support are structural, boring, and describe mechanisms rather than magnitudes.

### Verification improves output

*Confidence: high. The mechanism is plain and you can reproduce it today.*

If the thing that produced the work also judges the work, it judges it against the same
assumptions that produced it. Its errors are invisible to it in exactly the way your typos are
invisible to you in your own writing. A separate pass — a different session, a different model,
a checklist, or a person — does not share those assumptions and therefore sees things the
first pass could not.

What you should *not* say: any specific multiplier. What you *can* say: a check by something
with no stake in the answer catches a category of error that self-review structurally cannot.

Stronger still: prefer checks that are objective over checks that are opinions. "The file
exists and contains these four fields" beats "does this look good?" See
[Verification](04-verification.md) and `../protocols/DONE-CHECKS.md`.

### Structured memory beats re-explaining yourself

*Confidence: high, for the mechanism. Specific tooling claims are much weaker.*

The model has no memory between conversations beyond what is put in front of it. So every
session either starts from your re-explanation or starts from a file. A file is more complete,
more consistent, and free to reuse.

What is well supported: writing down your context once, in plain files the AI reads, produces
better and more consistent output than re-describing it each time, and the gap widens as the
context gets more specific to you.

What is *not* well supported: that any particular memory framework, vector database, or
knowledge-graph product is required to get this. Plain markdown files with clear names get
most of the benefit for almost all individuals. Use the simplest thing that stops your actual
pain, and add machinery only when you can name the pain it removes. See
[Memory and the second brain](06-memory-and-second-brain.md).

### Codified repeat work compounds

*Confidence: high for the mechanism. Magnitude varies enormously by person.*

A prompt dies with the chat. A written-down procedure — a skill — survives, gets used again,
and gets a little better each time it is used. That is arithmetic: work you do once and reuse
n times costs 1/n per use, and work you improve on each use gets better monotonically.

The honest caveat: this only pays off on work that genuinely repeats. Codifying a one-off is
pure overhead, and enthusiastic new practitioners codify everything. The discipline is
noticing the third time you do something, not the first. See [Skills](05-skills.md).

### Cheaper models handle more than people expect

*Confidence: moderate-high for the direction. Any specific ratio is unsupported.*

Model tiers exist because tasks differ in difficulty, and most tasks are not difficult. Summarizing,
extracting, classifying, reformatting, triaging, and drafting first passes are handled well by
smaller and cheaper models. Frontier models earn their price on genuinely hard reasoning, long
horizons, and prose that has to be good rather than adequate.

What you can trust: routing easy work down a tier usually costs less than you expect in
quality and saves more than you expect in money, and the only way to know for your workload is
to try it on your workload.

What you cannot trust: any published percentage of how close one tier is to another. Those come
from small editorial comparisons and change with every release. See
[Cost, models, and effort](09-cost-models-and-effort.md).

### Deterministic beats probabilistic where both work

*Confidence: high. This is close to definitional.*

If a rule, a search, a filter, or a piece of ordinary code can do the job, it does the job the
same way every time, for free, and you can read it to see what it does. A model doing that same
job costs money, varies between runs, and cannot be inspected.

So: sort with a sort. Filter with a filter. Route with a keyword check. Save the model for the
judgment that actually requires judgment. This is unglamorous and it is one of the largest
practical wins available.

### Context is a budget

*Confidence: high for the mechanism. The specific thresholds are folklore.*

Everything the model considers has to fit in the context window, and the whole conversation is
reprocessed every turn. So long sessions cost more per turn and degrade: with more material in
front of it, attention spreads thinner and earlier detail gets less weight.

That is why loading only what you need beats loading everything, and why starting a fresh
session with a purpose-built summary beats grinding on in a bloated one.

What you should treat as folklore: any specific token number at which quality "falls off." You
will see confident thresholds quoted. They vary by model and by task, they change with every
release, and they are mostly people's impressions. The mechanism is real; the line is not
where anyone says it is. See [The context window](02-the-context-window.md).

### The summary table

| Claim | Support | Say it like this |
|---|---|---|
| Verification improves output | Strong mechanism, reproducible | "A separate check catches what self-review structurally cannot" |
| Structured memory beats re-explaining | Strong mechanism | "Write context down once; sessions start from the file, not from you" |
| Codified repeat work compounds | Strong for genuinely repeated work | "Reuse divides the cost; iteration raises the floor" |
| Cheaper models go further than expected | Direction supported, ratios not | "Route easy work down and measure on your own tasks" |
| Deterministic before probabilistic | Near-definitional | "If a rule can do it, a rule should do it" |
| Context is a budget | Strong mechanism, no reliable threshold | "Load the router plus the one thing you need" |
| Specific quality multipliers | None | Do not say it |
| Vendor benchmarks | Upper bound only | "Their best day, not your expected day" |
| 24/7 agent swarms as a default | Weak, and expensive to be wrong about | "One loop with a good done-check first" |

---

## Part 5 — Where this harness is uncertain about itself

An honest ledger audits its own side. Things this harness teaches that you should hold loosely:

- **The five-layer model** (engine, skills and loops, memory and state, interface, distribution)
  is a useful way to organize thinking. It is a framing, not a finding. Nobody measured that
  memory and skills are "ninety percent of the value" — that is a practitioner's summary of where
  effort paid off for them, and it is repeated here because the reasoning is sound, not because
  it was tested.
- **The trust ladder** in [Safety, privacy, and trust](10-safety-privacy-and-trust.md) is a
  risk-management convention borrowed from how organizations delegate to people. It is
  sensible. It is not empirical.
- **"Boring for a while" before promoting** has no defined duration, because the right duration
  depends on how often the task runs and how bad the failure would be. Anyone giving you a
  specific number of weeks is guessing.
- **Everything about specific models, prices, and product features** goes stale in weeks. Any
  file here that names a model tier or a price is a snapshot. The routing habit outlives the
  price tag; check the price tag yourself.

If a section of this harness ever states something with more confidence than that, treat the
confidence as an editing error rather than as evidence.

---

## Part 6 — Keeping your own ledger

The point of this file is not the current contents. It is the habit. Some of what is oversold
today will be ordinary next year, and some of what is well supported today will be superseded.
A ledger you maintain stays useful; a list you inherited decays.

### The format

One file. A table. Five columns. Nothing more, because anything heavier will not survive
contact with a busy month.

> **This is a filled-in example, not anybody's real ledger.** The rows, the testing, the
> judgements, and the dates below are invented to show the format. Nothing in it is a finding,
> and none of it is evidence for or against any of the claims it names — your own rows are the
> only ones that mean anything.

```markdown
# My hype ledger

| Claim | Where I heard it | Status | What would change my mind | Last checked |
|---|---|---|---|---|
| Cheap model is fine for meeting summaries | A video, and my own testing | HOLDS - tested on a dozen of my own summaries, could not tell them apart | A summary that misses something a colleague catches | 2026-03 |
| Agent swarms overnight are worth it for me | Two videos, no personal test | UNTESTED - and expensive to test | A bounded overnight run that produced something I actually used | not yet |
| Verification catches things I miss | Own experience, repeatedly | HOLDS - mechanism is obvious | A month of separate-check passes finding nothing | 2026-03 |
| "40% fewer tokens" from a tool I saw | One video, no method shown | UNSUPPORTED - number asserted, never demonstrated | Someone showing before/after context measurements | 2026-03 |
```

Four statuses is enough:

- **HOLDS** — you tested it on your own work, or the mechanism is plain and you have used it.
- **UNTESTED** — plausible, unverified, and you have not paid the cost of finding out.
- **UNSUPPORTED** — asserted with no method, no baseline, or by someone selling it.
- **STALE** — was true, product or model has changed since, needs rechecking.

### The column that does the work

"What would change my mind" is the one people skip and the one that makes this a ledger instead
of a list of opinions. Filling it in forces you to state the claim in a form that could fail,
and a claim that cannot fail is not a claim you can act on.

It also does something quietly valuable: it tells future-you what evidence to watch for. Six
months later you will notice the disconfirming thing precisely because you wrote down what it
would look like.

### Cadence

- **When you hear a new claim:** add a row. Ten seconds. Status UNTESTED, with what would
  change your mind.
- **When you test something:** update the status and the date. This is the only entry that
  requires real effort and it is the only one that produces real knowledge.
- **Every few months:** scan for STALE. Anything naming a model, a price, a product feature, or
  a limit is a candidate — those move fastest.
- **When something you marked UNSUPPORTED turns out to be true:** change it, and note what
  changed. This is the entry that keeps you honest, because it proves the ledger is measuring
  the world rather than defending your priors.

### Promotion, demotion, and the parallel to trust

The ledger mirrors the trust ladder. Claims get promoted by evidence, one step at a time, and
demoted the moment something surprises you. UNTESTED becomes HOLDS only after you tested it on
*your* work — not after you saw someone else's demo, and not after you read a convincing
argument.

Test the cheap ones. A claim you can check in twenty minutes on your own material should be
checked, not debated. A claim that would cost a week to check stays UNTESTED, and there is no
shame in that column — it is an accurate description of what you know.

### When someone at work cites hype at you

You will be in a meeting where a colleague or a manager repeats a number from a video as
though it were established. Attacking the number makes you the difficult one. Try this shape
instead:

> That is interesting — do you know how they measured it? I ask because I have been trying to
> work out which of these claims hold up on our kind of work, and the ones I can test on our
> own material have been much more useful to me than the published numbers. Would it be worth
> running a small version on something real of ours and seeing?

You have not called anyone gullible. You have moved the conversation from citation to
evidence, and you have volunteered to do the work. That is close to the highest-status move
available in a room full of people repeating things they read.

---

## Try this now

Pick one AI claim you have heard recently — from a video, a colleague, a newsletter, or
anywhere in this harness — and run it through the method properly.

```
I want to evaluate an AI claim rigorously. Here is the claim:

[paste the claim, and say where you heard it and what that person or company sells]

Do these five things, in order, with a heading for each:

1. Restate the claim in its strongest, most precise form - the version most likely to
   be true. Steelman it before you criticize it.
2. Run the checklist: who measured it, against what baseline, could I reproduce it,
   what would it look like if it were false, and what is the source selling? Answer
   each explicitly, and say "unknown" where it is unknown rather than guessing.
3. Separate the mechanism from the magnitude. Is there an underlying reason this
   would be true, independent of the number attached to it? State that reason plainly,
   or say there isn't one.
4. Design the cheapest possible test I could run on my own work this week to find out.
   It must take under an hour, use material I already have, and produce a result I
   could not talk myself out of.
5. Give me one ledger row: claim, source, status (HOLDS / UNTESTED / UNSUPPORTED /
   STALE), what would change my mind, today's date.

Do not be diplomatic about the claim. If the honest answer is "there is no way to know
from what you have given me," say that.
```

Save the row. That is your ledger started. Add to it whenever you hear something confident.

---

## What you should now be able to do

- Recognize the four-beat structure of AI hype content — confident demo, number without
  methodology, urgency frame, funnel — and extract the useful pointer from it without adopting
  its claims.
- Run five questions on any claim: who measured it, against what baseline, could you reproduce
  it, what would falsehood look like, and what is the source selling.
- Name the claim shapes that are reliably overstated, and separate a sound mechanism from an
  invented magnitude when you repeat something to a colleague.
- State what is genuinely well supported — verification, written memory, codified repeat work,
  cheaper models, deterministic-first, context as a budget — in mechanism terms rather than in
  numbers you cannot defend.
- Keep a five-column ledger of your own, with a "what would change my mind" column, and update
  it as the field moves rather than trusting a snapshot someone else wrote.

---

Next: [Graduation](13-graduation.md) — what it looks like when you no longer need this harness.
Related: [Verification](04-verification.md) is the discipline this file is an application of.
Sources and how they were treated: `../reference/SOURCES.md`.
