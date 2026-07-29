# Session Log

*One short entry per session: what was attempted, what got done, what went unchecked. This is how the system remembers across conversations that cannot see each other. The AI appends to it at the end of every session. Reading time: about 5 minutes.*

---

## Why this file exists — and it is a lesson, not bookkeeping

**An AI generally cannot read your other conversations.** Each session is a closed box. Some tools let the assistant look at prior sessions; most chat interfaces do not, and nothing in this harness can be built on the assumption that yours does. When this conversation ends, everything in it is gone — not filed somewhere, not compressed, gone.

So this file is the memory. It is written *during* the sessions it describes, by the only participant who was there and can type fast, and it is read by every later session that needs to know what already happened.

That is the whole idea of [memory living outside the conversation](../curriculum/06-memory-and-second-brain.md), applied to the thing people most wrongly assume is automatic. Name it out loud the first time you write here. A learner who understands *why* they need a log will keep it. A learner who thinks it is admin will not.

Everything backward-looking in this harness runs on this file. `/recall-session` reads it to find a past piece of work. `/review-my-work` reads it to see patterns across weeks. Both of those degrade to guessing if the entries are missing or thin.

---

## For the AI: how to append

**At the end of every session, append one entry.** Do not wait to be asked. Do not skip it because the session was short, or unfinished, or went badly — those entries are the ones that turn out to matter.

Six rules, all of them hard:

1. **Append only. Newest at the bottom.** Never rewrite, tidy, merge, or delete a past entry. An edited log is not a record. A backfilled entry — one written later for a session that was never logged, usually surfaced by `/recall-session` — still goes at the bottom rather than back into the history. It keeps the date of the work it describes and says `(backfilled <today's date> from recall — date approximate)` on its title line, so an out-of-order date reads as deliberate rather than as an error.
2. **Keep it to the six fields, one line each.** The whole entry should take under a minute to write.
3. **`NONE` is allowed in any field, but only when it is true.** `UNVERIFIED: NONE` on a session where nothing was checked is a lie that a later review will act on.
4. **Facts, not narrative.** "Cleaned the supplier list, 340 rows, deduped by email" is an entry. "Made good progress on the data" is not.
5. **Show the entry in the chat before writing it**, so the learner can correct anything you got wrong about their own experience.
6. **If you cannot write files**, say so plainly and put the entry text in the chat for them to paste. Never claim to have written something you did not write.

### The format is short on purpose

**A heavyweight format is a format that gets skipped.** That is the single most important design decision in this file, and it is why the entry is six one-line fields instead of a report.

If you find yourself writing a paragraph in a field, you are writing the wrong file. The depth goes elsewhere: teaching detail and what the learner can now do belong in [`LEARNER.md`](LEARNER.md); a real choice with alternatives belongs in [`DECISIONS.md`](DECISIONS.md); anything built belongs in [`SKILLS-BUILT.md`](SKILLS-BUILT.md). This file is the index that lets a later session find those.

That does mean this file overlaps slightly with the session log in `LEARNER.md`, and that is accepted rather than accidental. The split: **`LEARNER.md` is about the person** — what they can do now, what confused them, what to teach next. **This file is about the work** — what was attempted and when, so it can be found again and reviewed for patterns. Do not paste the same paragraph into both.

### The entry format — copy this block

```
### YYYY-MM-DD — <title in about five words>

TRIED TO: <what the learner set out to do, in their terms>
GOT DONE: <what actually exists now that did not before. Be concrete. "Partly" is a real answer>
USED: <skills, tools, connectors, files touched — comma separated, no prose>
STUCK ON: <what fought back, confused, or took three attempts. NONE only if true>
UNVERIFIED: <anything accepted without a check, especially anything that went to another person>
NEXT: <the single most useful follow-up, or NONE>
```

### The field that earns this file its keep

`UNVERIFIED` is the one that gets skipped, and it is the most valuable line in the entry. It is the only place in the harness where "I took its word for it" gets written down at the moment it happens rather than reconstructed later when it has already caused something.

Write it honestly and without softening. If a document went to a colleague on the strength of the AI's say-so, that goes in. If a number was pasted into a report without being traced to its source, that goes in. A review that finds three of those in a fortnight has found something genuinely worth changing — but only if somebody wrote them down.

`USED` is the second most useful, for a duller reason: it is what makes repetition visible. Four entries with the same tool and the same shape of task is the signal that something should become a skill, and nobody notices that from memory.

---

## Worked examples

*These three entries are illustrations of the format. The learner, the dates and the work are invented. Keep them as a reference, or delete them once there are four or five real entries below. Do not treat anything in them as a fact about the actual learner.*

```
### 2026-04-07 — Supplier list dedupe and tidy

TRIED TO: Merge three supplier exports into one clean list before the procurement meeting.
GOT DONE: Single list, 340 rows down from 512. Deduped on email, not company name, after
  company name produced obvious false merges. Saved next to the original exports.
USED: Spreadsheet upload, no skill. Asked for a row-count check before and after.
STUCK ON: First pass merged two genuinely different companies with similar names. Caught it
  because the count dropped further than expected, not because I checked properly.
UNVERIFIED: The 12 rows with no email at all got dropped rather than flagged. Nobody has
  looked at them.
NEXT: Look at those 12 rows. Then decide whether this becomes a skill — third time doing it.
```

```
### 2026-04-09 — Client update draft, sent same day

TRIED TO: Write the monthly client update from the project notes and the numbers export.
GOT DONE: Draft written, edited twice, sent. Reused the structure from last month.
USED: /verify-this on the numbers only.
STUCK ON: Nothing in the writing. Spent twenty minutes hunting for last month's version
  because it was never saved anywhere findable.
UNVERIFIED: The two sentences about the timeline slipping. They came from my own summary of
  a meeting, not from anything written down, and they went to the client as fact.
NEXT: Put the update structure somewhere permanent so next month starts from it. Check the
  timeline claim against the actual project notes before the next update repeats it.
```

```
### 2026-04-14 — Went in circles on the report

TRIED TO: Get a working version of the quarterly summary. Three hours, one session.
GOT DONE: Very little. Four drafts, each fixing the previous one's problem and reintroducing
  an earlier one. Ended by starting fresh with a handoff and getting a usable draft in
  twenty minutes.
USED: /handoff, eventually. Should have been an hour earlier.
STUCK ON: The session itself. It kept dropping the constraint about not naming individual
  team members and I kept re-explaining it instead of noticing the pattern.
UNVERIFIED: NONE — nothing was finished long enough to accept.
NEXT: Learn the staleness signals properly. Re-explaining the same constraint twice is
  apparently the tell, and I missed it four times.
```

Notice what the third example does: it records a session that mostly failed, and it is the most useful of the three. A log that only contains good days cannot show a pattern, and patterns are the entire reason this file is read.

---

## For the learner: how to read this file

You will almost never read it front to back. Three ways it earns its place:

- **Finding something.** Scan the titles and dates. Ask for `/recall-session` and let the AI search it for you.
- **Seeing what you repeat.** Read the `USED` and `TRIED TO` lines of the last ten entries in one pass. Anything that shows up three times is a candidate to codify.
- **Seeing what you trust without checking.** Read only the `UNVERIFIED` lines. This is uncomfortable and it is the highest-value five minutes available in the whole harness.

If a week has no entries, that is information too. Either you did not work with the AI that week, or the capture step is being skipped — and the second one is worth fixing immediately, because it silently disables everything that reads this file.

---

## Related

- [`../protocols/SESSION-PROTOCOL.md`](../protocols/SESSION-PROTOCOL.md) — the capture phase that writes here
- [`../curriculum/06-memory-and-second-brain.md`](../curriculum/06-memory-and-second-brain.md) — why memory has to live outside the conversation
- [`LEARNER.md`](LEARNER.md) — the person; this file is the work
- [`REVIEWS.md`](REVIEWS.md) — what the coaching review makes of these entries
- [`../.claude/skills/recall-session/SKILL.md`](../.claude/skills/recall-session/SKILL.md) — finding a past session
- [`../.claude/skills/review-my-work/SKILL.md`](../.claude/skills/review-my-work/SKILL.md) — reviewing a stretch of them

---

*Real entries start below this line. Newest at the bottom.*
