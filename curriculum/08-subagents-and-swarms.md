# Subagents and Swarms

*What it means to run more than one AI worker at a time, when that genuinely helps, and the four rules that stop it from turning into a mess. Reading time: about 20 minutes.*

---

## Read this warning before you read anything else

Most tasks do not need a fleet. They need one good loop with real verification.

Running many AI workers at once is the most photogenic thing you can do with these tools and one of the least often necessary. It looks like productivity. It feels like scale. And if the underlying single-agent process is sloppy — vague instructions, no done-check, nobody grading the work — then adding nine more workers does not fix any of that. It reproduces it nine more times, in parallel, and hands you nine sloppy outputs instead of one.

Say it plainly: **scaling a system you do not understand just scales the bugs.**

So the order of operations is fixed:

1. Get one worker producing something you would stake your name on.
2. Get a separate check that proves it (see [Verification](../curriculum/04-verification.md)).
3. Only then ask whether the work splits into parts that could run at the same time.

You will notice this chapter comes after [The loop](../curriculum/03-the-loop.md) and [Verification](../curriculum/04-verification.md). That is deliberate. If you skipped them, go back. Parallelism built on an unverified loop is a way to be wrong faster.

Also on the record: "I run swarms 24/7" is a social-media flex, not a benchmark. Nobody owes you a fleet. Match the machinery to your actual work — see [The hype ledger](../curriculum/12-the-hype-ledger.md).

---

## What a subagent actually is

A **subagent** is a fresh worker with its own clean desk.

That is the whole concept. When your main session spawns a subagent, the subagent gets:

- Its own separate context window — its own working memory, empty at the start except for the instructions you give it.
- Its own set of tools (often deliberately narrower than yours — for example, read-only).
- One job.

It does that job, and then it disappears. The only thing that survives is a written report it hands back to whoever spawned it. Everything else it read, tried, backtracked on, and discarded goes away with it.

A plain-language analogy that holds up: you are running a small office. You do not walk a new hire through every conversation you have had this month. You say, "Go find out what our contract with this supplier actually says about termination, and come back with the clause and the page number." They go and read forty pages. They come back with three sentences. You never had to read the forty pages, and your own head stays clear.

That is a subagent.

Two terms you will see used loosely and can treat as near-synonyms: **subagent**, **agent**, sometimes **worker**. A **swarm** or **fleet** just means several of them running at once. **Orchestrator** means the one on top that hands out the jobs and assembles the answers. Full definitions live in [the glossary](../reference/GLOSSARY.md).

### Check whether your setup can do this at all

Spawning a real subagent is a feature of the tool you are using, not of the model. Some setups can do it; a plain chat window generally cannot. This changes often enough that you should not trust anything written here about which product has it today — ask directly:

```
Can you spawn subagents in this environment - separate workers with their
own context that report back to you? Answer yes or no. If no, say so
plainly and do not simulate it.
```

If the answer is no, this chapter is still worth reading, and everything in it still works. You run the same shapes yourself, one at a time: one fresh chat per question, each with a single question and a reporting template, and you play the synthesizer. Slower, identical discipline. What you must not accept is an assistant that cheerfully role-plays five scouts inside one conversation and hands you a merged summary. That is one context doing all the work while telling you it is five, which is the opposite of the point.

---

## The real reason to use them: context hygiene, not speed

Everyone assumes the point is speed. Speed is the smaller half.

The bigger half is that the main session stays clean.

Recall from [The context window](../curriculum/02-the-context-window.md): the model re-reads the entire conversation on every turn, and as the conversation fills up, quality quietly degrades. Old details get muddled. Instructions from the top get less weight. Nothing announces this — the answers just get worse.

Now picture the alternative to subagents. You want to compare five vendors. You do it yourself, in one chat. You paste in vendor one's pricing page. Then vendor two's. Then a support forum thread. Then a PDF. By the time you reach the comparison — the part you actually care about — your session is stuffed with raw source material, most of which you will never reference again. The model is now doing its most important thinking in its most cluttered state.

With subagents, the same job looks like this: five workers each read one vendor's material in their own private context, and each hands you back a half-page of structured findings. Your session receives five half-pages. It never sees the raw pages at all. You reach the comparison with a clean desk and exactly the material you need on it.

That is the trade that matters. Read a lot, keep a little. The parallelism is a bonus; the compression is the point.

There is a second-order benefit worth naming. Because a subagent starts empty, it cannot be confused by earlier turns of your conversation. It has no memory of the wrong direction you tried an hour ago, no leftover assumption from the tangent you abandoned. A fresh reader with one clear question often outperforms an experienced reader carrying baggage.

---

## What "one agent reports back" actually returns

This is the part people get wrong, so be precise.

A subagent does not hand back its transcript. It does not hand back the files it read. It hands back **one message of text** — whatever it decided to write at the end. That message is the entire interface between its work and yours.

Which leads to a rule with a lot of consequences: **if you do not specify the shape of that report, you get whatever shape it chooses.** Usually that is a chatty summary with the useful parts buried in prose, no sources, and no honest statement of what it could not find.

So specify the shape. Always. Every time.

Bad:

```
Look into vendor A's pricing and tell me what you find.
```

Good:

```
Research vendor A's pricing only. Do not compare it to anything else.

Report back in exactly this format and nothing else:

VENDOR: <name>
ENTRY PRICE: <number and unit, or NOT FOUND>
PRICE AT 50 SEATS: <number, or NOT FOUND>
CONTRACT LENGTH REQUIRED: <answer, or NOT FOUND>
WHAT COUNTS AS A SEAT: <one sentence>
HIDDEN COSTS I FOUND: <bullets, or NONE FOUND>
SOURCES: <url or document name for each number above>
CONFIDENCE: <high / medium / low, plus one sentence on why>
COULD NOT DETERMINE: <bullets, or NONE>
```

Four things that format buys you, none of which you get by accident:

| The field | What it prevents |
|---|---|
| `NOT FOUND` as an allowed answer | The worker inventing a plausible number rather than returning an empty box |
| `SOURCES` per number | A confident figure you cannot trace, defend, or re-check next quarter |
| `CONFIDENCE` with a reason | Treating a firm number and a guess as though they were the same kind of thing |
| `COULD NOT DETERMINE` | Silent gaps — the most dangerous output of all, because they look like completeness |

The last one deserves emphasis. An agent that returns "here is everything" is telling you less than one that returns "here is what I found, and here are the two things I could not confirm." Build the honest gap into the template and you will get honest gaps back. Leave it out and you will get smooth prose covering a hole.

There is one more field worth adding when the work feeds into a decision:

```
DISAGREEMENT WITH THE OBVIOUS ANSWER: <if your findings contradict what a
casual reader would assume, say so here. If not, write NONE.>
```

That single line has a way of surfacing the thing you would otherwise have missed.

---

## The three topologies worth knowing

There are exactly three shapes you need. Everything fancier is a combination of these.

### Topology 1: Parallel scouts into one synthesizer

```
                 you
                  |
     +------+-----+-----+------+
     |      |     |     |      |
  scout1 scout2 scout3 scout4 scout5     <- read-only, one question each
     |      |     |     |      |
     +------+-----+-----+------+
                  |
            synthesizer                   <- reads the five reports, writes one answer
                  |
                 you
```

Several read-only workers run at the same time. Each owns exactly one question. None of them writes anything, changes anything, or talks to the others. Their reports come back to one place, and one worker (or you) turns those reports into a single answer.

This is the topology you will use most often, and it is the safest one, because nothing can collide. Reading the same document from five directions at once is harmless.

Use it for: research, comparisons, "what does our documentation actually say about X," reviewing a long report from five different angles, gathering the facts before a decision.

The synthesizer is not optional. Five reports sitting in a folder are not an answer. Somebody has to reconcile them — including reconciling the places where they disagree, which is often where the real finding is hiding.

### Topology 2: Maker and checker

```
   maker  ---->  the work  ---->  checker  ---->  verdict
     ^                                              |
     |                                              |
     +------------ one revision round --------------+
```

One worker produces. A different worker, which did not produce it, grades it against stated criteria and returns a pass or a list of specific problems. If there are problems, the maker gets one round to fix them. Then it goes back to the checker.

This is not really parallelism at all — it runs in sequence — but it is the pattern this harness relies on more than any other, and it belongs in this chapter because the whole discipline rests on it. It is the same idea as [Verification](../curriculum/04-verification.md), given a second body so the check is structurally independent rather than politely requested.

Note the cap: **one revision round**, not unlimited. Without a cap, maker and checker can pass work back and forth indefinitely, each round costing money and neither converging. If one revision round does not clear the checker's objections, that is information — the task is underspecified, and it comes back to you.

### Topology 3: Orchestrator with specialists

```
                orchestrator            <- plans, delegates, assembles, decides
                /    |     \               (writes no work product itself)
          recon   builder   verifier
        (read)    (writes)   (read)
```

One coordinator holds the plan. It does not do the work. It hands out jobs, reads what comes back, decides what happens next, and keeps the record. Specialists do the actual work — and crucially, the one who builds is never the one who checks.

This is the heaviest pattern and the one to reach for last. It earns its complexity on multi-stage work where the stages are genuinely different kinds of thinking: gather facts, then design, then execute, then check.

A discipline that makes this pattern work, taken from a practitioner's own written playbook: the orchestrator writes no work product. The moment your coordinator starts doing the task itself, it stops coordinating, its context fills with detail, and the plan degrades. Keep the coordinator empty-handed and clear-headed.

---

## The four hard rules

These are learned expensively. Each one is here because ignoring it produces the specific failure written underneath it, and that failure is usually silent.

### Rule 1: Only one writer touching the same thing at a time. Ever.

Two workers editing the same file, the same document, the same spreadsheet, or the same record will produce a mess that is harder to untangle than doing the work yourself would have been. Not sometimes. Reliably.

The failure is not dramatic. Nothing crashes. Worker A reads the file, worker B reads the file, both make sensible edits based on what they read, and the second one to save silently erases half of the first one's work. Now you have a document that looks finished and is quietly missing things, and neither worker knows, because from inside each one's view everything went fine.

So: one writer per thing being written. If you genuinely need two workers writing at once, they must write to two different places, and something must merge those places afterwards — deliberately, by a third party who can see both.

### Rule 2: Read-only work can overlap freely

The corollary, and the reason this whole chapter is worth reading. Reading collides with nothing. You can run as many readers at once as you can afford. Five workers reading the same contract from five angles is perfectly safe.

This gives you a practical scheduling habit: **while one writer works, run the reading for the next stage in parallel.** Scouts gathering material for step three cannot possibly interfere with the writer finishing step two. That is free overlap, and it is the only kind you should take without thinking hard first.

What you must never overlap: a writer and anything that changes the state that writer depends on. If one worker is editing a document while another restarts the system that document configures, you will spend the evening diagnosing a problem that does not exist.

### Rule 3: Give each worker a single question, not a vague area

Compare:

| Vague area (do not) | Single question (do) |
|---|---|
| "Look into our onboarding process" | "List every step a new hire must complete in their first week, in order, with the owner of each step. Sources only, no recommendations." |
| "Research the competitor" | "What does this competitor charge, at what tiers, and what is included in each tier?" |
| "Review the report" | "Find every numeric claim in this report and state, for each, whether a source is cited." |

A worker given an area will choose its own question, and it will usually choose an easier one than you had in mind. It will then answer that easier question competently and report success. You will not notice for a while, because the report will look thorough.

A worker given one exact question either answers it or tells you it could not. Both outcomes are useful. "Competent answer to a question I did not ask" is not.

Two sharpeners to add to any scout's instructions:

```
Facts and sources only. No suggestions, no recommendations, no summary of
what you think I should do.

If you cannot answer the question from the material available, say
"CANNOT ANSWER" and state exactly what was missing. Do not substitute a
different question.
```

The first line stops scouts from spending their effort on opinions you did not ask for and will not use. The second stops the quiet substitution.

### Rule 4: Never let a worker verify its own output

The oldest rule in the harness, and the one people quietly break when they are in a hurry.

A worker that has just produced something has, by definition, already concluded that it is correct — that conclusion is why it stopped. Asking it to check its own work asks it to reach the opposite conclusion using the same reasoning that produced the original. It will usually confirm itself, in confident language, and you will be worse off than before because now you have a passing grade attached to unchecked work.

The check must come from a worker that did not do the work, was not told the answer was good, and is graded on finding problems. Give the checker the actual output, the actual criteria, and permission to fail it. Full mechanics in [the verification protocol](../protocols/VERIFICATION-PROTOCOL.md).

A related trap, less obvious: do not let the checker also fix. If your checker repairs the problems it finds, it has become the maker, and now nobody is checking the repairs. Checkers report. Makers fix. Then the checker looks again.

---

## The decision rule: when fan-out actually pays

Before spawning anything, all three of these must be true. Not two.

**1. The work splits cleanly into independent parts.**
Can you write down the parts as a numbered list right now, without hedging? If part two needs part one's answer before it can start, they are not parallel — they are sequential, and running them at the same time just means part two guesses.

**2. Each part is genuinely separable.**
Can one worker complete its part without knowing what any other worker found? If workers need to compare notes mid-flight, you do not have five tasks; you have one task that you have awkwardly cut into pieces. Sequence it instead.

**3. The results need synthesizing, not sequencing.**
At the end, are you combining findings into one picture, or building a chain where each link sits on the last? Combining is what fan-out is for. Chaining is what a single well-run loop is for.

If any one of the three fails, use one agent and one good verification pass. That is not a lesser option; it is the correct option, and it is the right answer far more often than the internet suggests.

Two more practical gates on top:

- **Is the cost proportionate?** Every worker reads its instructions and writes its report — you pay for all of it. Five scouts is five sets of that overhead. For a comparison you will act on, that is cheap. For idle curiosity, run one. See [Cost, models and effort](../curriculum/09-cost-models-and-effort.md).
- **Can you actually check the result?** If you cannot tell whether the synthesized answer is right, parallelism has only produced a more impressive-looking thing you cannot trust.

---

## Worked example: five vendors, in parallel, then one comparison

You have been asked to recommend a project-management tool for a forty-person team. There are five candidates. This is the exact shape parallel scouts were made for: five separable questions, no dependencies between them, one synthesis at the end.

Here is the whole thing, start to finish.

### Step 1: the prompt you actually type

```
I need to compare five project management tools for a 40-person team.
The five are: [A], [B], [C], [D], [E].

Run five subagents in parallel, one per tool. Each is READ-ONLY and
researches ONLY its assigned tool. No agent compares tools. No agent
makes a recommendation.

Give every agent these exact instructions:

  Research ONLY [tool name]. Do not mention or compare any other product.

  Answer in exactly this template. Use NOT FOUND where you cannot confirm
  something. Never estimate a number without labelling it an estimate.

  TOOL:
  PRICE PER USER PER MONTH, BILLED ANNUALLY:
  PRICE AT 40 USERS PER MONTH:
  MINIMUM CONTRACT LENGTH:
  WHAT THE CHEAPEST TIER EXCLUDES THAT THE NEXT TIER INCLUDES:
  DATA EXPORT: (can we get our data out, in what format, how)
  ACCESS CONTROL: (can we restrict who sees what, at which tier)
  INTEGRATIONS WE CARE ABOUT: (email, calendar, file storage — which are
    native, which need a paid add-on, which do not exist)
  MOBILE: (real app or web wrapper)
  KNOWN LIMITS AT ~40 USERS: (anything documented about scale or quotas)
  SOURCES: (one link or document per fact above)
  CONFIDENCE: high / medium / low, and why
  COULD NOT DETERMINE:

When all five report back, do NOT just paste them. Produce:
1. One comparison table, tools as columns, my criteria as rows.
2. A "conflicts and gaps" section: anything where two scouts disagree,
   plus every NOT FOUND, listed by tool.
3. A shortlist of two, with the single reason each made it.
4. The one question I should ask each shortlisted vendor on a call,
   chosen because the answer would change my recommendation.

Cite the scout report behind every cell. Do not add facts at the
synthesis step that no scout reported.
```

### Step 2: what comes back, and what to do with it

Each scout returns roughly half a page. Your session receives five half-pages instead of five vendor websites, three pricing PDFs, and a support forum. That is the context hygiene benefit made concrete.

The synthesis step is where the value appears, and it is not the table. It is section 2. The gaps and conflicts are the finding. If three scouts found a documented user limit and two wrote `NOT FOUND` for the same field, that tells you something real: either two vendors do not publish it, or two scouts did not dig. Both are worth a follow-up, and neither would be visible in a smooth merged summary.

### Step 3: the check

You are not done. Nobody has graded this yet. Add one more worker:

```
You are a checker. You did not do this research.

Here is a comparison of five tools and the five source reports behind it.

Find every claim in the comparison that is not supported by the source
report it cites. Find every place the comparison states something more
confidently than its source did. Find every NOT FOUND in a source that
became a definite statement in the comparison.

List what you find with the exact quote from both. Then state a verdict:
SUPPORTED or NOT SUPPORTED. Do not fix anything.
```

That prompt is short, and it is the difference between a comparison you can present and one you merely have. Note that the checker did not do the research and is not allowed to fix — Rule 4 and its corollary, applied.

### What this example is not

It is not a claim that five scouts produce a better comparison than you sitting down for two hours with five browser tabs. It might, it might not, and it depends heavily on how good your prompts are. What it reliably does is: keep the raw material out of your thinking space, force one exact question per source, and make the gaps visible instead of smoothed over. Those are process guarantees, not quality guarantees. Treat them as such.

---

## What goes wrong, and what it looks like

| Symptom | What actually happened | Fix |
|---|---|---|
| Five reports that all say roughly the same generic things | Each scout was given an area, not a question | Rule 3. One exact question per worker, written out |
| A synthesis containing facts no scout reported | The synthesizer filled gaps from its own general knowledge | Add "do not add facts at synthesis" and run the checker prompt above |
| A document that looks finished but is missing sections you know were written | Two writers on one file | Rule 1. One writer per thing, always |
| Everything passes, nothing improves | The worker graded itself | Rule 4. Separate checker, permission to fail it |
| Enormous cost, thin result | Fan-out on work that was really sequential | The decision rule. All three conditions, or one agent |
| Workers waiting on each other, output arrives late and confused | The parts were not independent | Sequence it. This was never a parallel problem |

More patterns and their tells live in [Failure modes](../protocols/FAILURE-MODES.md).

---

## The harness's own workers

This harness ships with four worker definitions, in [`.claude/agents/`](../.claude/agents/). They exist so you do not have to write these prompts from memory every time:

| Worker | What it is for |
|---|---|
| [`scout.md`](../.claude/agents/scout.md) | A read-only researcher. One question, sources required, no recommendations. The unit you fan out. |
| [`verifier.md`](../.claude/agents/verifier.md) | Checks work against stated criteria and returns evidence. Never fixes. |
| [`adversary.md`](../.claude/agents/adversary.md) | Tries to break a conclusion, including the verifier's. Reports what was taken on faith. |
| [`teacher.md`](../.claude/agents/teacher.md) | Explains what happened and why, at your level, without softening the parts that went badly. |

Open one and read it. They are plain markdown — a description, a set of instructions, and the tools that worker is allowed to use. That is all an agent definition is, and once you have seen one you can write your own for the specific work you repeat. The same logic that makes a skill worth writing makes a worker definition worth writing: see [Skills](../curriculum/05-skills.md).

A note on how they are meant to be used together: `scout` fans out, `verifier` grades what came back, and `adversary` gets pointed at the verifier when the stakes are high enough that a rubber-stamped pass would hurt. You will not need all three often. Knowing which one you need is most of the skill.

---

## Try this now

Pick something you genuinely have to decide this month — a tool to buy, a supplier to pick, a process to choose between. Then paste this, filling in the brackets:

```
I need to decide: [the decision, in one sentence].
The options are: [option 1], [option 2], [option 3].

Before you research anything, do this in order:

1. Tell me honestly whether this job actually needs parallel subagents.
   Check all three conditions and say yes or no to each:
   - Does the work split cleanly into independent parts?
   - Can each part be done without knowing what the others found?
   - Do the results need synthesizing rather than sequencing?
   If any answer is no, say so and tell me to use one agent instead.
   Do not flatter the idea.

2. If all three are yes, write me the EXACT instruction you would give
   one scout — including the reporting template, with NOT FOUND and
   COULD NOT DETERMINE as allowed answers. Show me the template before
   you run anything.

3. Then run one scout on the FIRST option only, and show me its report.
   If you cannot spawn a real subagent in this environment, say so
   plainly instead - do not pretend. Give me the scout instruction to
   paste into a fresh chat myself.

4. Then ask me whether the report was good enough to be worth running
   on the other options. Do not assume it was.
```

The point of stopping at one scout is that you get to see the quality of a single report before paying for five. If report one is thin, the fix is the prompt, not more workers. That habit — prove the unit before multiplying it — is worth more than anything else in this chapter.

---

## What you should now be able to do

- Explain what a subagent is in one sentence, say why context hygiene is a better reason to use one than speed, and check whether your setup can spawn one at all.
- Apply the three-part decision rule out loud before spawning anything, and reach the answer "one agent, verified" without feeling like you settled.
- Write a scout instruction that contains one exact question and a reporting template with `NOT FOUND`, `SOURCES`, `CONFIDENCE`, and `COULD NOT DETERMINE` fields.
- Name the four hard rules and the failure each prevents, and run the five-vendor shape end to end: fan out, synthesize, then check with a worker that did not do the research.
