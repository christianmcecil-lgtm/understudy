# Reviews

*The append-only log of coaching reviews: what was working, what to change next, and whether it ever got changed. The AI appends one entry each time a review runs. Reading time: about 5 minutes.*

---

## For the AI: how to append

One entry per review, appended at the bottom, written by [`/review-my-work`](../.claude/skills/review-my-work/SKILL.md) at the end of its run.

Six rules, all of them hard:

1. **Append only. Newest at the bottom.** A review is a snapshot of what was true and visible on one date. Rewriting an old one to match what you now think destroys the only thing the file is for, which is showing whether the same advice keeps getting given.
2. **The one permitted edit to a past entry is filling in its `ACTED ON` line.** Date it. Nothing else in a past entry is ever touched.
3. **State the tier.** Every review is built from whatever access to past work actually existed — the four tiers are in [`../.claude/skills/recall-session/SKILL.md`](../.claude/skills/recall-session/SKILL.md). A review built from one-line summaries is a different document from one built from full transcripts. The learner must be able to see which they are reading, months later, without asking.
4. **Findings cite instances.** Every point names the specific session, date, or artifact behind it. "You should verify more" is not a finding. "Three entries in the last fortnight have something in `UNVERIFIED`, and two of those went to another person" is.
5. **No generic praise.** `WENT WELL` is held to exactly the same evidence standard as the criticism. If you cannot cite it, do not write it.
6. **A review with nothing to improve is a failed review.** If you got there, you did not dig hard enough — go back to the lenses. The inverse also holds: a review that is only criticism is both demoralising and inaccurate, because nobody working steadily for two weeks improved at nothing.

Before writing, read [`SESSION-LOG.md`](SESSION-LOG.md), [`LEARNER.md`](LEARNER.md), [`MASTERY.md`](MASTERY.md), [`SKILLS-BUILT.md`](SKILLS-BUILT.md) and [`DECISIONS.md`](DECISIONS.md). Before writing the top item, read the last three entries in **this** file — see the note below on recurring items, which changes what the top item should be.

---

## The entry format — copy this block

```
### YYYY-MM-DD — Review of <the window in a few words>

TIER: <1 native session access / 2 exported transcripts / 3 SESSION-LOG summaries /
  4 pasted by the learner> — <one clause on what that means for how much to trust this>
WINDOW: <dates covered, and how much material: how many logged sessions, how many gaps>

WENT WELL: <two or three lines, each citing the specific session or artifact. Real progress
  named specifically, never encouragement>

TOP ITEM: <the single most valuable change to make next, phrased as an action that could be
  done this week. A sentence or two: the change, and the evidence that makes it the top one>

THEN:
  2. <second item — ranked by payoff over effort, not by how bad it sounds>
  3. <third item>

COULD NOT ASSESS: <what this review could not see, and why. On tier 3 or 4 this is usually
  long. Say so plainly rather than reviewing confidently on thin material>

ACTED ON: <blank until it happens, then: date and what actually changed>
```

`TOP ITEM` is item one of the three; it is pulled out because a review that opens with a list gets skimmed and a review that opens with one thing gets done. Do not repeat it inside `THEN`.

`ACTED ON` is the field that keeps this file honest. A review nobody acted on is not a neutral event — it is evidence that the review was too long, too vague, or aimed at the wrong thing.

---

## How to use this file

**Do not read one review in isolation.** A single review tells you what one fortnight looked like. The file tells you something better: whether you are actually changing.

Three passes, in order of value:

**1. Read the `TOP ITEM` line of the last three reviews. Only those three lines.**

If it is the same item, or three phrasings of the same item, you have found the most useful signal this file produces: **a recurring top item means it is being avoided.** Not forgotten — avoided. Something about it is harder, duller, or more uncomfortable than it looks on the page.

The response is not to write it a fourth time. It is to ask why. Usually one of three things: it is bigger than one line made it sound and needs breaking down; it depends on something not yet learned; or it is genuinely not important and the review keeps surfacing it because it is easy to spot. All three are worth naming out loud. The AI should raise this unprompted the moment it sees the pattern.

And it changes what the next `TOP ITEM` is, which is why this check happens before the top item is written. If the item is too big, the top item becomes its smallest concrete first step, not the item again. If it depends on something not yet learned, the top item becomes that prerequisite, named as the prerequisite. If it is not actually important, say so plainly, drop it, and promote the next item — a review that keeps recommending something nobody will ever do is training the learner to skim.

**2. Read the `ACTED ON` lines.** Two consecutive blanks means the reviews are not landing. Change the cadence, change the format, or stop — an unread recurring report is worse than no report, because it costs time and creates the feeling that something is being handled.

**3. Read the `WENT WELL` lines across all reviews.** This is the honest version of progress. It is specific, it is dated, and it is the thing to reach for on the day this all feels like it is not working.

The cadence, the automated version, and what makes a recurring review safe are in [`../protocols/REVIEW-ROUTINE.md`](../protocols/REVIEW-ROUTINE.md).

---

## Worked example

*This entry is an illustration of the format. The learner, the dates and the work are invented. Delete it once there are two or three real reviews below, or keep it as a reference. Do not treat anything in it as a fact about the actual learner.*

```
### 2026-04-19 — Review of the fortnight to 19 April

TIER: 3 — built from the one-line summaries in SESSION-LOG.md, not from the conversations
  themselves. I can see what was done and what was flagged; I cannot see how it was done.
WINDOW: 6 April to 19 April. Nine logged sessions. Two working days have no entry at all,
  so this review is missing whatever happened on the 11th and 16th.

WENT WELL: Ran /verify-this on the numbers in the client update on the 9th without being
  prompted — that is the first unprompted verification in the log. Caught the false company
  merge in the supplier dedupe on the 7th, and caught it from an unexpected row count rather
  than from the AI saying so, which is the right instinct. Ended the failing session on the
  14th with a handoff rather than pushing on for a fourth hour.

TOP ITEM: Turn the supplier list cleanup into a skill this week. It appears in the log three
  times in a fortnight (7th, 12th, 18th), takes most of an hour each time, and every run has
  had to rediscover that deduping on company name is wrong and email is right. That
  rediscovery is exactly what a skill exists to stop.

THEN:
  2. The client update on the 9th went out with two timeline sentences marked UNVERIFIED in
     the log, sourced from memory of a meeting rather than from notes. They went to a client
     as fact. Low effort to fix, and it is the second entry this fortnight where something
     unverified reached another person.
  3. The saved structure for the monthly update still does not exist anywhere findable — the
     9th records twenty minutes spent hunting for last month's version. Ten minutes to fix,
     recurs monthly.

COULD NOT ASSESS: Anything about how questions are actually being phrased, because I am
  reading summaries and not conversations. The two undated gaps. Whether the verification on
  the 9th was thorough or nominal — the log says it ran, not what it found.

ACTED ON: 2026-04-21 — supplier cleanup written up as a skill, recorded in SKILLS-BUILT.md.
  Items 2 and 3 not done.
```

---

*Real reviews start below this line. Newest at the bottom.*
