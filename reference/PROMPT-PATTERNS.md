# Prompt Patterns

*A copy-paste arsenal, organised by what you are trying to do. Skim in 15 minutes; steal from it forever.*

Every pattern below is a literal block you can paste. Anything in `<ANGLE BRACKETS>` is a
placeholder you replace. Nothing here needs a special tool, a plugin, or a terminal. They work
in a chat window, in a coding assistant, and inside a [skill](../curriculum/05-skills.md).

Read the "why it works" line on each. The wording is doing specific work, and if you paraphrase
it into something softer you usually lose the effect. The most common failure is politeness:
"could you maybe check this over" gets you a compliment, while "find three things wrong with
this" gets you three things wrong with it.

**How to use this file with your AI:** point it here directly. "Read
reference/PROMPT-PATTERNS.md and apply the refutation request to what you just gave me" works.

---

## Contents

| Intent | Patterns |
|---|---|
| Starting something vague | Structured interview opener, Three options with tradeoffs, Plan before you act |
| Keeping it on the rails | Scope fence, Assumption surfacing, Pre-mortem |
| Checking the work | Evidence demand, Refutation request, Rubric score, Provenance tagging |
| Making it compound | Skillify, Handoff doc, Friction log review |
| Checking yourself | Teach-me-back |
| Session hygiene | Stale-session check |

---

# 1. Starting something vague

## The structured interview opener

**When to use it.** You know you want something but cannot specify it. This is the single
highest-value pattern in the file, because one of the most expensive mistakes in AI work is a
fast, confident answer to the wrong question.

```
I want <ROUGH GOAL, ONE SENTENCE>. I have not thought it through and I am
not sure what is possible.

Do not start yet. Interview me first.

Ask me questions ONE AT A TIME, waiting for each answer before the next.
Aim for about <8> questions total. Prioritise questions where my answer
would most change what you build. Include at least two questions about
things I probably have not considered, and say why you are asking them.

When you have enough, stop and write back:
- What I actually asked for, in your words
- The three decisions I made during the interview, and what they rule out
- What you still do not know, and what you will assume in place of it
- What you propose to do, in order

Then wait for my go-ahead.
```

**Why it works.** One question at a time forces you to think instead of skimming a wall of
bullets. "Where my answer would most change what you build" makes it prioritise; without that
line you get eight questions about your favourite colour. The read-back at the end is where
you catch the misunderstanding, while it is still free.

---

## Three options with tradeoffs

**When to use it.** Any decision where you suspect the AI is going to hand you its first idea
dressed up as the only idea.

```
Give me three genuinely different ways to do <THING>. Not three versions
of the same approach.

For each one:
- Name it in three words
- One paragraph on how it works
- What it costs me: time, money, ongoing maintenance, and what I have to
  learn
- What it is bad at, stated plainly
- Who it is wrong for

Then pick one and defend the pick in two sentences. If two are close,
say so instead of manufacturing a winner.

Rank them for someone whose actual constraint is <YOUR REAL CONSTRAINT,
e.g. "I have four hours a week and no budget">.
```

**Why it works.** "Not three versions of the same approach" blocks the usual output of
small/medium/large of one idea. Naming the real constraint changes the ranking more than any
other line. Asking it to admit a tie prevents the fake-confidence ending.

---

## Plan before you act

**When to use it.** Before anything that changes files, sends things, or takes more than a few
minutes. Especially when you are new to a tool and do not yet know what it is willing to do.

```
Before you change anything, write the plan.

1. What you understand the goal to be, in your words.
2. Exactly what you will touch: files, systems, messages. List them.
3. What you will NOT touch.
4. The order of steps, and what could go wrong at each one.
5. How I will know at the end whether it worked, stated as something
   checkable rather than "it should be fine".

Then stop and wait. Do not begin until I reply with "go".
```

**Why it works.** The list of what it will touch is the part that saves you. Reading it takes
thirty seconds and catches the wrong-target mistake, which is the expensive one. "Wait for go"
must be explicit or an eager agent starts anyway.

---

# 2. Keeping it on the rails

## The scope fence

**When to use it.** Whenever the AI has access to more than the thing you want changed. Agents
tidy. Tidying is how unrelated things break.

```
Scope fence for this task.

IN SCOPE: <EXACTLY WHAT MAY CHANGE - files, sections, documents>

OUT OF SCOPE: everything else. Do not edit, reformat, rename, "improve",
or reorganise anything outside the in-scope list, even if you are
confident it is wrong.

If you find something outside the fence that genuinely needs attention,
do not fix it. Add it to a list called OUT OF SCOPE FINDINGS at the end
of your reply and keep going.

Before you finish, state which files or documents you changed. If that
list is longer than the in-scope list, say so explicitly.
```

**Why it works.** "Even if you are confident it is wrong" pre-answers the excuse. The findings
list gives the AI somewhere legitimate to put the urge, so it does not act on it. The final
self-report makes drift visible without you auditing everything.

---

## Assumption surfacing

**When to use it.** After any answer you are about to rely on. It takes one paste, and it is a
reliable way to find the flaw before it becomes yours.

```
List every assumption you made producing that.

Split them into:
A. Things I told you
B. Things you inferred from what I told you
C. Things you filled in from general knowledge because I never said

For each item in B and C: one line on what happens to your answer if the
assumption is wrong.

Then tell me which single assumption, if wrong, would do the most damage,
and what question I should answer to settle it.
```

**Why it works.** Category C is where the bad ones hide, and separating it from A forces the
model to notice its own invention. "What happens if it is wrong" turns a list into a risk
ranking you can actually act on.

---

## The pre-mortem

**When to use it.** Before you commit to a plan, hire on a plan, or automate a plan. Imagining
the failure has already happened produces far better answers than "any risks?"

```
Assume it is <THREE MONTHS> from now and <THE PLAN> failed badly.
It did not half-work. It failed.

Write the post-mortem from that future. Cover:
- The single most likely cause of the failure
- Four other plausible causes, ranked by likelihood
- The earliest visible warning sign for each one, and roughly when it
  would have appeared
- Which of these I could cheaply detect NOW, before committing

Be specific to my situation, not generic risk-register language. If the
most likely failure is that I lose interest or run out of time, say that
rather than inventing a technical cause.
```

**Why it works.** Stating the failure as fact removes the hedging that ruins ordinary risk
questions. Asking for warning signs converts a worry list into a monitoring list. The last
line blocks the polished, useless corporate answer.

---

# 3. Checking the work

## The evidence demand

**When to use it.** Every single time an AI says it did something. Asking for proof costs you
one line and changes what the AI is willing to claim.

```
Do not tell me it is done. Show me.

For each thing you claim you did, give me the evidence:
- The exact file path or location you changed
- The relevant lines, pasted, not summarised
- The command or check you ran and its actual output
- If you could not verify something, say "UNVERIFIED" next to it and
  explain what would be needed to verify it

If any part of this is you assuming rather than checking, mark it. I would
rather have three verified items and two honest gaps than five confident
claims.
```

**Why it works.** It moves the burden from your trust to its proof. The explicit permission to
report gaps is essential: without it, a model under pressure to look complete will paper over
the one thing you needed to know about.

---

## The refutation request

**When to use it.** On anything you are about to send, publish, or act on. Also on the AI's own
work, in a fresh conversation, which is where it is hardest on itself.

```
Find three things wrong with this. Not three suggestions, three problems.

<PASTE THE WORK, OR NAME THE FILE>

Rules:
- Your job is to attack it, not to be encouraging. Skip anything positive.
- Rank them: the one that would embarrass me most goes first.
- For each: what is wrong, why it matters, and the smallest change that
  fixes it.
- If you genuinely cannot find three real problems, say so and give me
  the strongest objection a hostile expert reader would raise instead.

Do not rewrite it. Just find the problems.
```

**Why it works.** A fixed number forces the search to continue past the first easy nitpick.
"Skip anything positive" removes the compliment sandwich that hides the real issue.
"Do not rewrite" keeps the finder and the fixer separate, which is the whole
[maker-checker](../curriculum/04-verification.md) idea in one line.

---

## The rubric score

**When to use it.** When you need judgment that is comparable across time or across items:
candidates, drafts, options, submissions. A bare "score this out of 10" produces a number that
means nothing.

```
Score this against a rubric.

<PASTE THE WORK>

Criteria, each scored 1 to 5:
1. <CRITERION> - 5 means <WHAT EXCELLENT LOOKS LIKE>, 1 means <WHAT BAD
   LOOKS LIKE>
2. <CRITERION> - 5 means <...>, 1 means <...>
3. <CRITERION> - 5 means <...>, 1 means <...>

For each criterion give: the score, the single line of evidence from the
work that justifies it, and the one change that would raise it by a point.

Do not give a 3 because you are unsure. If you are unsure, give the lower
score and say what evidence is missing.

Finish with the total, and one sentence on whether the total is
misleading.
```

**Why it works.** Defining what 5 and 1 mean is what makes the number portable; without
anchors, scores drift session to session. Banning the safe middle score forces a real judgment.
The "is the total misleading" line catches the case where one fatal flaw is hidden by four good
scores.

---

## Provenance tagging

**When to use it.** On any research, summary, or analysis you intend to keep, share, or repeat.
This is the habit that stops inferences quietly becoming facts in your notes.

```
Tag every claim in your answer with one of:

[SOURCED] - you read this in a specific place. Name the place.
[INFERRED] - you worked it out from something sourced. Say from what.
[UNCERTAIN] - you are working from general knowledge rather than anything in front of you,
             you are not confident, the sources disagree, or you filled a gap with a
             reasonable default. Say which, and if it was a default, say what default.

Rules:
- Every factual sentence gets a tag. No untagged claims.
- Do not upgrade an [INFERRED] to a [SOURCED] because it feels obvious.
- If most of the answer ends up [UNCERTAIN], tell me that plainly at the
  top rather than burying it.
- Numbers get extra scrutiny: any figure you cannot source is
  [UNCERTAIN], not [INFERRED].
```

**Why it works.** The tags make the shape of the answer visible at a glance. The rule about
numbers matters most, because a made-up figure travels further and does more damage than a
made-up sentence.

---

# 4. Making it compound

## The skillify request

**When to use it.** The moment you finish a task you know you will do again. This is how a good
session becomes a permanent capability instead of a nice memory.

```
We just did <TASK>. I will do this again.

Turn what we just did into a reusable skill. Write it as a file I can
keep, containing:

1. A description of exactly when this skill should be used, and when it
   should NOT be used. Be specific enough that it fires on the right
   request and stays quiet on the wrong one.
2. The step-by-step instructions, written for a competent stranger who
   was not in this conversation.
3. The inputs it needs from me each time, as a short list of questions.
4. Any script, template, checklist, or fixed wording we used, saved
   inside the skill rather than described.
5. The done-check: how it knows the work is finished and correct.

Include the mistakes we made this session as explicit "do not do this"
notes, so the skill does not repeat them.

Then tell me the one part of this skill most likely to need fixing after
the next real use.
```

**Why it works.** Point 4 is where most people stop short: saving the actual template or
script, not a description of one, is what makes the skill cheap and repeatable rather than a
prompt in a costume. Encoding this session's mistakes is what makes the version in month three
better than today's.

---

## The handoff doc request

**When to use it.** When a session has gone long, or when the next phase of work deserves a
clean start. Better than letting a bloated conversation limp on.

```
This session is getting heavy. Write me a handoff document so a fresh
session can pick this up cold.

The next session's purpose is: <ONE SENTENCE, SPECIFIC>

Include, in this order:
- The purpose above, first line
- Current state: what is done, what is half-done, what is untouched
- Decisions we made and the reasoning, so they are not relitigated
- Things we tried that did NOT work, and why
- Pointers to the relevant files or sources by name - do not paste their
  contents
- The exact next action, specific enough to start on without asking me
  anything

Rules: no secrets, no personal data, no credentials. Leave out anything
irrelevant to the stated purpose, even if we spent a long time on it.
```

**Why it works.** Requiring a stated purpose is what keeps the doc short; without it you get a
transcript summary, which is the thing you were escaping. "Things that did not work" prevents
the fresh session from cheerfully repeating your dead ends. Pointers instead of pasted content
keeps the new context clean.

---

## The friction log review

**When to use it.** Every week or two, once you have been keeping notes on what annoyed you.
This is diagnosis before building, which is the right order.

```
Here is my friction log: every moment in the last <TWO WEEKS> where
working with you was slow, wrong, or annoying.

<PASTE THE LOG, ROUGH NOTES ARE FINE>

Do this:
1. Cluster the entries into recurring themes. Ignore one-offs.
2. For each cluster, estimate how often it happens and roughly how much
   time it costs me each time.
3. For each cluster, propose exactly ONE fix, and say which kind it is:
   - a standing rule I should add to my instructions file
   - a skill I should build
   - a deterministic check or script that needs no AI at all
   - nothing, because the fix costs more than the friction
4. Rank the fixes by (how often it bites) divided by (how hard the fix
   is).

Recommend the ONE I should do this week. Argue for it in three sentences.
Be honest about the "nothing" option; not every annoyance is worth
automating.
```

**Why it works.** Clustering first stops you from building a bespoke fix for a one-off. The
explicit "nothing" option is what keeps this honest, since an AI asked for fixes will always
find fixes. Recommending exactly one is what makes it get done.

---

# 5. Checking yourself

## The teach-me-back request

**When to use it.** When you want to find the holes in your own understanding of your own job.
Uncomfortable and unusually useful, especially in a new role.

```
I work in <YOUR FIELD / ROLE>. I am going to have you explain my own
domain back to me so I can find my gaps.

Explain <SPECIFIC AREA OF YOUR WORK> to me as if I were a sharp new hire.
Cover how it actually works, not the tidy version.

Then:
- Mark anything you are unsure about with [UNCERTAIN], because I need to
  know which parts to check rather than absorb
- List the five questions a new person in this role usually gets wrong
- List three things that are commonly believed in this field that you
  think are shaky, and say why

Then ask me three questions about this area that you would expect
somebody genuinely competent to answer easily. I will answer, and you
tell me where I am thin.
```

**Why it works.** Reading a competent explanation of your own field surfaces gaps far faster
than trying to list what you do not know, because you cannot list what you have not noticed.
The final three questions turn it from reading into testing. The [UNCERTAIN] marks matter here
more than anywhere, since you are using this on a subject where you cannot yet grade the
answer.

---

# 6. Session hygiene

## The stale-session check

**When to use it.** When answers start feeling worse, when it forgets something you said, or
just every hour or two of serious work. Before you conclude the model got dumber, check
whether the conversation got heavy.

```
Pause the task. Session check.

1. Summarise, in five bullets, what you currently believe we are doing
   and what has been decided.
2. Tell me anything from earlier in this conversation you are no longer
   confident you have straight.
3. Say whether this conversation has become long or cluttered enough
   that a fresh session would give better answers.
4. If yes, write me the handoff doc for a new session, with the purpose
   stated as: <ONE SENTENCE>.

Be honest about 3. I would rather restart than get slowly worse answers.
```

**Why it works.** Point 1 is a live test rather than a question: if the summary is off, you
have your answer without needing to ask. Explicitly permitting "yes, restart" is what makes it
usable, since an assistant will otherwise keep going by default.

---

## Combining patterns

The patterns stack. The most useful sequences are short:

| Situation | Sequence |
|---|---|
| A vague new project | Structured interview opener, then Three options, then Plan before you act |
| Anything that touches real files or systems | Plan before you act, then Scope fence, then Evidence demand |
| A document or deck going to someone who matters | Refutation request in a fresh chat, then Rubric score, then fix |
| Research you intend to keep | Provenance tagging, then Refutation request on the tagged version |
| A task you have now done twice | Skillify, then use the skill and Skillify again to sharpen it |
| A long working session | Stale-session check, then Handoff doc |

Two rules about stacking. First, run the refutation request in a **fresh conversation** where
possible; an AI reviewing its own recent work in the same context is a softer critic than one
meeting the work cold. Second, do not stack more than three; past that you are managing prompts
instead of doing the work, which is the failure mode this whole file exists to prevent.

## Try this now

Take the last substantial thing your AI produced for you: a draft, a summary, an analysis. If
you do not have one yet, ask it for a one-page briefing on something in your job, and use that.
Open a brand new conversation, paste the work in, and paste this:

```
Find three things wrong with this. Not three suggestions, three problems.

<PASTE THE WORK HERE>

Rules:
- Your job is to attack it, not to be encouraging. Skip anything positive.
- Rank them: the one that would embarrass me most goes first.
- For each: what is wrong, why it matters, and the smallest change that
  fixes it.
- If you genuinely cannot find three real problems, say so and give me
  the strongest objection a hostile expert reader would raise instead.

Do not rewrite it. Just find the problems.
```

Then decide for yourself whether the first-ranked problem was real. That judgment, made by you,
is the skill this harness is actually teaching. See
[Verification](../curriculum/04-verification.md) for what to do with the answer.

## What you should now be able to do

- Open a vague piece of work with an interview instead of a guess, and get a specification out
  of it before anything is built.
- Demand evidence rather than accepting "done", and recognise the difference on sight.
- Run an adversarial pass on your own work in a fresh conversation, and stack it with a rubric
  when the judgment needs to be comparable.
- Turn a task you have now done twice into a reusable skill, mistakes included, instead of
  retyping the prompt next month.
