# Done-Checks

*A catalog: for each kind of work, what actually counts as proof it is finished, and which checks only look like proof. Read time: 18 minutes.*

---

## What a done-check is

A done-check is the specific, stated-in-advance thing that has to be true before a piece of work
is called finished. Not a feeling. Not a review. A check.

It has exactly three properties, and if any one is missing you do not have a done-check, you have
a hope:

1. **Someone who was not there can run it.** If the only way to know the work is done is to have
   watched it being done, it is not checkable.
2. **It can fail.** If there is no realistic outcome where the check comes back negative, it is
   decoration. A check that always passes was never a check.
3. **You could state it before the work started.** A standard invented after seeing the output is
   a description of the output, not a test of it.

That is the whole idea. Everything below is that idea applied to the kinds of work you actually
do.

Why it matters more with AI than without: a person who is unsure hesitates, hedges, or asks. A
model produces its best guess in the same confident register as its best knowledge. The tell is
absent. The done-check replaces the tell. This is also what makes a loop safe to run unattended —
see [The loop](../curriculum/03-the-loop.md) — because a loop with a vague done-check does not
stop, it drifts.

The procedure for running these checks — who checks, how they are framed, what verdicts they
return — is in [Verification Protocol](VERIFICATION-PROTOCOL.md). This file is only about *what*
to check.

---

## How to read the catalog

Each entry has three columns and you should read the third one first.

- **Strong check** — do this when the work matters, is irreversible, or leaves the building.
- **Acceptable check** — real, weaker, appropriate for reversible work you will read yourself.
- **The fake check** — the thing people run instead, believe they have verified something, and
  have not. These are not strawmen. Every one of them is a thing that gets done daily by
  intelligent people, including by AIs asked to check their own work.

The fake-check column is the important part of this file. Almost nobody skips verification
outright. What they do is run a fake check and stop.

---

## 1. Research and fact-finding

**Done means:** every claim traces to a source that actually says it, and the gaps are named.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Open each cited source and confirm the claimed sentence is present in it. Check the source's own date and whether anything supersedes it. Ask a fresh checker to try to refute the top three claims. | Spot-check the claims that carry the most weight — the ones you would act on — directly at the source, and require every uncited claim to be labelled unsourced. | Asking the AI "are you sure?" and accepting yes. Or checking that the citations look plausible without opening any of them. |

**Why the fake one fools people:** a citation list is a visual proxy for rigour. It has the shape
of evidence. But a fabricated citation and a real one look identical until you open them, and
"are you sure?" reliably produces "yes, I'm confident" from a system that was equally confident
thirty seconds ago when it was wrong.

**The sharper trap:** the source exists, the page is real, and it does not say what was claimed.
This is far more common than an invented source and much harder to catch, because the link
resolves. Checking that a link works is not checking that it supports the claim.

---

## 2. A written document or an email

**Done means:** it says the true thing, to the right person, with nothing in it you would have to
walk back.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Every fact in it verified per the protocol. Then a fresh reader given the recipient's context and asked one question: "what in here could be read in a way I would not want, and what does it commit me to?" Then you read it aloud. | Read it once yourself hunting only for facts and commitments — dates, numbers, promises, names — ignoring style entirely on that pass. Then a second pass for tone. | Re-reading your own draft and finding it reads well. Or asking the AI to "polish" it and treating the polished version as checked. |

**Why the fake one fools people:** fluency is not accuracy, and polishing improves fluency while
leaving every factual error exactly where it was. Worse, a polished draft feels more finished, so
it gets less scrutiny than the rough one did.

**The commitment check.** Read the draft and list every sentence that commits you to something —
a date, a deliverable, a price, an agreement, an implied yes. That list is what you are actually
sending. If the list contains something you did not decide to commit to, the AI decided it for
you.

---

## 3. A summary of a long source

**Done means:** someone who reads only the summary reaches the same conclusions as someone who
read the whole thing.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Reverse the direction: from the summary alone, write down the three questions a reader would now ask, then check the source for whether it answers them differently than the summary implies. Separately, have a fresh reader list what the source contains that the summary omits. | Pick three passages from the source at random — beginning, middle, end — and check each is either represented in the summary or genuinely minor. Require the summary to name what it left out. | Reading the summary and finding it coherent. Or asking the AI whether the summary is complete. |

**Why the fake one fools people:** a summary is always coherent. Coherence is what summarising
produces. The failure mode of a summary is never incoherence — it is silent omission, and there
is nothing in the summary to indicate the omission, because the omitted thing is not there. You
cannot detect an absence by reading. You detect it by going back to the source.

**The killer question:** "what was in the source that changes the conclusion, and is it in here?"
Ask that of a checker, not of the summariser.

---

## 4. A spreadsheet or a calculation

**Done means:** the numbers are right, and they will still be right when the inputs change.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Recompute the headline figure by a completely different route and compare. Test the edge cases deliberately: zero, empty, negative, a date at a month or year boundary, a missing row, a text value where a number belongs. Check the ranges actually cover all the data. | Verify a few rows by hand against the source data. Confirm the totals reconcile to a number you already know from somewhere else. | Confirming the formula "looks correct." Or that the spreadsheet opens without an error. Or that the total is a plausible-looking number. |

**Why the fake one fools people:** a spreadsheet's most expensive errors do not produce errors.
A range that stops one row short of the data, a percentage applied to the wrong base, a lookup
silently matching approximately — all of these return confident, plausible, wrong numbers, and
the file opens perfectly. There is no red text. Plausibility is what a wrong spreadsheet
specialises in.

**Say the range out loud.** Most spreadsheet failures are range failures. Have the AI state, in
words, which rows and columns each formula covers, and compare that to how much data there
actually is.

---

## 5. A list extracted from messy input

Names from a thread, action items from a transcript, invoices from a folder, contacts from
notes — anything where the answer is "all the X in Y."

**Done means:** everything that should be in the list is in it, nothing else is, and none of the
entries were smoothed into something that was never said.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Count independently. Count the items in the source by a mechanical route — a search, a filter, a count of occurrences — and compare to the length of the list. Then check both directions: every list entry appears in the source, and every source occurrence appears in the list. | Verify the count against the source, then spot-check five entries back to where they came from, chosen from different parts of the input. | Reading the list and finding it reasonable. Or asking "did you get all of them?" |

**Why the fake one fools people:** this is the single most dangerous check in the catalog because
the failure is invisible by construction. A list of nine items where there should be eleven looks
exactly like a complete list. There is no gap to see. And "did you get all of them?" asks the
system that already thinks it did.

**The two-directional rule.** Checking that every item on the list is real catches invention. It
does nothing about omission, and omission is the failure you cannot see. You must also check from
the source back to the list. Only the second direction finds what is missing.

---

## 6. Code or a script

Including things you would not call code: a spreadsheet macro, an email rule, an automation step,
a formula someone wrote for you.

**Done means:** it does the intended thing on real input, and does something sensible on input it
did not expect.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Run it, on real data, and look at the actual output — not the description of the output. Run it on an input where you already know the correct answer. Run it on a deliberately broken input and confirm it fails loudly rather than quietly producing nothing. Have a fresh reader read the code hunting for what happens when an assumption does not hold. | Run it once on real input and inspect the result yourself against what you expected. | The code runs without an error message. Or the AI says it tested it. Or it "should work." |

**Why the fake one fools people:** "no error" and "correct" are unrelated conditions. A script
that processes zero files finishes instantly and successfully. A script that overwrites the wrong
file does so cleanly. The absence of a complaint is not evidence of a result — go look at the
result.

**Never accept a claim of testing without the output.** If it was tested, there is output. Ask
for what the run actually printed, and read that instead of the summary of it.

---

## 7. A decision recommendation

"Which vendor should we use", "should we do this", "which of these three".

**Done means:** the reasoning is stated, the assumptions are visible, and the case against the
recommendation was actually made.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Have a fresh reader argue the opposite recommendation as forcefully as possible using the same facts. Then compare. If the opposite case is strong and was not addressed in the original, the recommendation is not done. Separately, list every assumption and mark which ones, if false, flip the answer. | Require the recommendation to state, in the document, what would change its mind — the specific fact that would flip it. If nothing would, that is a finding. | Asking the AI for the pros and cons of the option it just recommended. Or asking whether it considered alternatives. |

**Why the fake one fools people:** an AI asked for the downsides of its own recommendation will
produce downsides — mild, manageable ones, framed to be survivable, because it is still arguing
for the recommendation while appearing to argue against it. The cons list becomes part of the
sales pitch. The only version of this that works is a separate reader told to win the other side.

**The flip test.** "What is the one fact that, if I learned it tomorrow, would make this the
wrong call?" If that question has no answer, the recommendation is not a recommendation, it is a
preference with paragraphs.

---

## 8. A scheduled or automated routine

Anything that will run again without you watching. A daily digest, a weekly report, a monitor,
a triage rule.

**Done means:** it works on today's input, it will not run forever, and you will find out when it
breaks.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Run it manually, end to end, and inspect the real output. Then run it against an empty or unusual input and confirm it does something sensible rather than producing a confident empty result. Confirm three things exist: a hard stop (a cap on time, passes, or cost), a log you can read afterwards, and a visible failure — you get told when it does not run. | Run it manually once and inspect the output. Confirm the hard stop exists. | Confirming that it is scheduled. Or that it ran. Or that it produced a file. |

**Why the fake one fools people:** "it ran" is a statement about the schedule, not about the
work. The characteristic failure of an automated routine is not that it stops — it is that it
keeps running while its input has quietly gone empty, and mails you a beautifully formatted
report about nothing, every morning, for two months. It looks alive. It is producing zero.

**The silent-failure question, asked before you schedule anything:** "if this breaks on a Tuesday,
how do I find out?" If the answer is "I would notice eventually", add a check that fails loudly
instead.

---

## 9. Anything client-facing

External, on the record, attributable to you. The threshold is not importance — it is that you
cannot quietly fix it afterwards.

**Done means:** every fact verified, every commitment intentional, and nothing in it you cannot
support if asked where it came from.

| Strong check | Acceptable check | The fake check |
| --- | --- | --- |
| Two independent passes with different jobs: one on facts (each verified per the protocol, with sources attached), one on consequences ("what does this commit us to, what could be read the wrong way, what happens if the recipient forwards it"). Plus a named human — you — who has read every line and can say where each number came from. | One fact pass and one consequence pass, both done by you, on separate readings. Never in the same pass. | Confidence that it reads professionally. Or that it followed the template. Or that the AI said it was ready to send. |

**Why the fake one fools people:** polish and correctness are produced by different mechanisms,
and AI is much better at the first. A flawless-looking document with one wrong number does more
damage than a rough one, because the polish buys the wrong number credibility and nobody
double-checks a document that looks that good.

**The hard rule:** nothing goes out with a fact in it that you could not, if challenged, say
where it came from. If you cannot source it, cut it or hedge it. "I do not have that figure
confirmed" costs you nothing. A confidently wrong figure costs you the room.

---

## The fake checks, gathered

The same handful of patterns produce almost every fake check in the catalog. Learn the patterns
and you will spot the ones this file did not list.

| Pattern | What it sounds like | Why it is empty |
| --- | --- | --- |
| **Asking the author** | "Are you sure?" "Did you check?" "Is this right?" | You are asking the system that already believes it. It will restate the belief with more confidence. |
| **Checking the shape** | "It has citations." "It followed the template." "It has the right sections." | Structure is trivial to produce and independent of truth. A fabrication fills a template perfectly. |
| **Checking for errors instead of for correctness** | "It ran clean." "No warnings." "The file opened." | Silence means nothing happened loudly. It does not mean the right thing happened. |
| **Checking readability** | "It reads well." "It sounds professional." | Fluency is the thing these systems are best at. It is the least informative signal available. |
| **Checking one direction** | "Every item on the list is real." | Catches invention, blind to omission — and omission leaves nothing behind to notice. |
| **Accepting a report of a check** | "I verified this." "I tested it." "I confirmed the source." | A claim about a check is not a check. Ask for the output, the line, the number it came back with. |
| **Post-hoc standards** | "Yes, that is what I wanted." | A standard invented after seeing the output cannot fail. State it first or it is not a test. |
| **Plausibility** | "That number looks about right." | Plausible is exactly what a wrong AI answer is optimised to be. It is the wrong instinct, applied confidently. |

If a check you are about to run matches one of these rows, you have not verified anything yet.
Go back to the catalog and take the acceptable check at minimum.

---

## Writing a done-check for something new

The catalog will not cover everything. When you hit work it does not cover, write your own. Three
tests, all mandatory.

**Test 1 — could someone who was not there run it?**

Hand your check to a person who did not watch the work happen and has no context. If they can
carry it out and reach a verdict, it is a check. If they would have to ask you what good looks
like, it is not — it is your taste, and taste does not transfer to a subagent, a checklist, or
next month's version of you.

Fails: "make sure it is good quality." "Confirm it captures the key points."
Passes: "confirm the total in cell B40 equals the sum of the invoice PDFs in that folder."

**Test 2 — can it fail?**

Describe, concretely, what a failing result looks like. If you cannot describe one, the check
cannot fail, and a check that cannot fail is not measuring anything. This is the test most
home-made done-checks fail.

Fails: "verify the summary is accurate" — what would inaccurate look like, specifically?
Passes: "the summary must state the deadline, and it must match the deadline in the contract;
if it does not, this fails."

**Test 3 — can you state it before the work starts?**

Write the check down before the work begins. This is not a nicety. A standard written after
seeing the output tends to become a description of the output: once you are looking at a finished
thing, it is much easier to ratify it than to imagine the version you actually wanted. Writing the
check first is what makes it a test rather than a summary.

If you genuinely cannot state the check before starting, that is real information: it means you
do not yet know what you are asking for, and the first task is not the work, it is figuring out
what done looks like. Do that with the AI, out loud, before anything gets produced.

**The template.** Fill this in for any new kind of work and you have a usable done-check:

```
THE WORK:            [what is being produced]
DONE MEANS:          [one sentence, in terms of the world, not the document]
THE CHECK:           [the specific action someone else could take]
A FAILING RESULT:    [what the check returns when the work is not done]
WHO RUNS IT:         [a fresh checker / a deterministic script / me, on a second pass]
STATED BEFORE WORK:  [yes / no - if no, do not use it]
```

---

## Try this now

Pick one thing you do repeatedly at work that you currently hand to AI without checking. Paste
this:

```
I want to write a real done-check for a task I repeat. The task is:
[describe it in two sentences]

Do this:
1. Ask me the three or four questions you need in order to know what "done"
   means for it in terms of the world, not in terms of the document.
2. Then write a done-check that satisfies all three of these tests, and show
   your reasoning for each:
   - someone who was not there could run it
   - it has a concrete failing result you can describe
   - it could have been stated before the work started
3. Then tell me the FAKE check I am most likely to run instead, and why it
   would fool me.

Do not skip step 3. Be specific to my task, not general.
```

Keep the answer. That is the first entry in your own version of this catalog.

---

## What you should now be able to do

- State what "done" means for a piece of work before it starts, in a form that could actually
  come back negative.
- Recognise the eight fake-check patterns on sight, in your own work and in what an AI reports
  back to you.
- Pick the right strength of check for the stakes, instead of applying the same shallow one to
  everything.
- Write a new done-check for work this catalog does not cover, and know when you cannot yet
  write one — which is itself the useful finding.
