# Sources and Provenance

*Where this harness came from, what kind of claim you will find in it, and what you should not trust it for. Five minutes.*

You are about to take working advice from a folder. Before you do, you deserve to know how it
was made, so you can weigh it correctly. That is the same standard the harness asks you to
apply to everything your AI tells you, so it would be strange to exempt itself.

---

## What this is

This is one operator's working synthesis, written down and handed to another person.

The material behind it comes from a large body of practitioner sources: recorded talks and
video walkthroughs, vendor and tool documentation, open-source project readmes, written
postmortems from people running these systems, and a lot of hands-on operating experience with
the tools themselves over an extended period. Those inputs were read, distilled into notes,
cross-checked against each other where they overlapped, and then rewritten into the curriculum
you have.

That is the honest description. Now the honest caveat.

**This is not research.** There is no peer review behind it, no controlled comparison, no
sample size. The practitioner sources are overwhelmingly self-reported: somebody tried a thing,
it worked for them, they made a video about it. Some of those people are excellent. Some are
selling something. The distillation tried hard to tell the difference, and will have got it
wrong somewhere.

**Nobody is named on purpose.** Not the individuals whose talks fed it, not the channels, not
the companies, not the person who assembled it. Naming sources here would imply endorsement in
both directions, and it would also date the file badly, since the loudest voices in this field
rotate every few months. The ideas were worth keeping; the personalities are not part of the
package.

---

## What kind of claim you will find here

Almost everything in this harness is one of two things:

**A mechanism.** How something actually works: the model re-reads the whole conversation each
turn, so long chats get slower and more expensive. A checker that also did the work is a soft
checker. A skill that saves the actual script is cheaper than one that describes the script.
Mechanisms are the durable part. They are the reason the advice still applies after the
products get renamed.

**A practice that holds up in daily use.** Demand evidence before accepting "done." Give a loop
an objective stopping condition and a hard cap. Keep memory in plain files. These are reported
as things that hold up under repeated use, by someone who uses them, not as things that have
been measured.

What you will **not** find, deliberately:

- **Numbers.** No percentages, no multipliers, no "this makes you X times faster," no dollar
  figures, no benchmark scores. Where the source material had numbers, most of them were
  self-reported by someone with an incentive, and the rest were vendor benchmarks of the
  vendor's own product. So the harness describes the mechanism instead and lets you observe the
  magnitude in your own work. The only figures you should see are reading-time estimates. If you
  find a measurement of results in here presented as fact, that is a defect. Treat it as one.
- **Urgency.** No claim that you must adopt something now or fall behind. Scarcity framing is a
  sales technique, not an engineering argument, and it appears constantly in the source
  material. See [The hype ledger](../curriculum/12-the-hype-ledger.md) for the specific claims
  that were examined and set aside.
- **Product rankings.** No assertion that one tool beats another, because most of the readily
  available evidence for those claims is marketing published by the winner.

---

## What goes stale, and how fast

Some parts of this field change on a timescale of weeks. The harness was written to keep those
parts out of the durable files, but they leak in anywhere a concrete example is needed.

**Check these live, always. Do not trust this folder for them:**

| Thing | Why it moves |
|---|---|
| Model names and tier names | Providers rename and re-tier constantly, and the naming rarely maps cleanly to the previous generation |
| Prices, per-token or per-seat | Change without much notice, including promotional pricing that later ends |
| Context window sizes | Advertised sizes climb, and the advertised number is not the same as the size at which quality stays good |
| Which menu, which flag, which button | Product surfaces get redesigned; the concept survives, the click path does not |
| What a specific tool can do today | Capabilities ship weekly; a limitation described here may already be gone |
| Which integrations exist | The list grows and occasionally shrinks |

**These change slowly and are safe to lean on:** the shape of a loop, why verification has to
be separate from the work, why context is a budget, why skills compound and prompts do not, why
deterministic steps beat probabilistic ones when both would work, and why trust with an
automated system should be built on small reversible tasks first.

The practical rule: if a sentence in this harness names a product, a version, or a figure, go
check it. If it describes why something behaves the way it does, it is more likely to still
hold.

---

## How this harness was verified during its own construction

The harness was not written by one pass of one AI and shipped.

Each file was drafted against a fixed specification that stated the rules in advance: no
invented statistics, no marketing claims, no personal details, a concrete exercise at the end
of every teaching file, exact cross-file link names. Then independent adversarial readers went
through every file with instructions to break it. They were not asked whether the file was
good. They were asked to find:

- Numbers, percentages, benchmarks, or study results that had been invented or smuggled in
  without support.
- Claims from the hype ledger asserted as fact.
- Cross-references pointing at files that do not exist under that name.
- Missing exercises, or exercises that were not actually copy-pasteable.
- Personal details about the author that should have been scrubbed for a folder meant to be
  handed to a stranger.
- Condescension, filler, and padding written to hit a length rather than to teach.
- Any instruction that sounds fine but would not survive an AI following it literally. That
  last one catches the defects the other checks miss.

Findings came back, and the files were corrected. Some claims were removed rather than fixed,
because they could not be supported once someone pushed on them.

**That process is not incidental. It is the method the harness teaches, applied to the harness
itself.** A worker produced the draft; a separate adversarial reader graded it against explicit
criteria; the reader did not fix anything, and the writer did not grade anything. If you want a
worked example of [maker-checker](../curriculum/04-verification.md), you are holding one. If
the harness had been written without that pass, it would contain confident errors, because
everything written this way does.

It also means the harness is not error-free. An adversarial pass reduces defects; it does not
eliminate them. Some remain.

---

## What to do when this file is wrong

It will be wrong somewhere, and it will be out of date within months of you reading it. That is
expected and it is not a reason to distrust the whole thing. It is a reason to treat it as a
starting position rather than a reference work.

When you find something that no longer matches reality:

1. **Check the live source first.** Vendor documentation for product behaviour, the tool itself
   for what it can do now.
2. **Fix the file.** This folder is yours. Editing it is the intended use, not a violation of
   it. A harness you have corrected three times is more valuable than the one you were given.
3. **Record the correction** in [Decisions](../progress/DECISIONS.md) with the date and what
   changed, so future-you knows which parts you have already checked and when.
4. **Keep the mechanism even if the specifics moved.** If a model tier got renamed, the routing
   logic still applies. Do not throw away a working principle because its example expired.

---

## A closing note on trust

The most valuable thing in this folder is not any individual technique. It is the habit of
asking, about any claim including this one: where did that come from, is it a mechanism or a
measurement, and what would it look like if it were wrong.

Apply that to your AI. Apply it to the confident people making videos about your AI. Apply it
here. If a file in this harness makes you suspicious, you are using it correctly.

## Try this now

Point your AI at this harness and have it audit the claims rather than teach them:

```
Read the folder I have given you, especially reference/SOURCES.md and
curriculum/12-the-hype-ledger.md.

Now audit it against its own standard. Go through the curriculum files and
find me:
1. Any claim stated as fact that is really one practitioner's experience
2. Any statement that would go out of date within six months, and what
   makes it perishable
3. Anything that contradicts something else in the folder
4. The three claims that are most load-bearing, meaning the most other
   advice collapses if they are wrong

For each finding, quote the exact sentence and name the file.

Do not fix anything. Just report. Rank by how much damage the claim would
do if it turned out to be wrong.
```

Read what comes back with your own judgment engaged. Some of its findings will be wrong too.

## What you should now be able to do

- State plainly what kind of authority this harness has: distilled practitioner experience, not
  research, and weigh its advice accordingly.
- Tell the difference between a claim about a mechanism, which ages slowly, and a claim about a
  product, which ages in weeks, and know which of the two to go verify.
- Recognise the absence of numbers here as a deliberate honesty choice rather than a gap, and
  get suspicious when other AI advice is full of precise figures with no source.
- Correct and date this folder yourself when reality moves, instead of treating it as fixed.
