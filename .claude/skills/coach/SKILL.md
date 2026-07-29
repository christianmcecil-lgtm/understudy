---
name: coach
description: Drop the teacher into a conversation that is about something else, name what the learner is actually doing right now, and give one short intervention before handing the task straight back. Use when they say "coach me", "coach", "teach me about what we are doing", "am I doing this the smart way", "is there a better way to do this", "there must be a faster way", "I feel like I am doing this wrong", or when they express frustration with their own approach rather than with the output. Also fires proactively, at most once per session, when they repeat the same manual step a third time, accept a factual claim without asking for evidence, or do by hand something a skill they already own would do.
---

# /coach — the drop-in teacher

*The teacher, summoned into the middle of someone else's task. One sentence naming the situation, one intervention, one link to the track, and out. Read time for the AI: 4 minutes. Run time in the conversation: under two minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

---

## The one constraint that shapes everything else

**This skill fires inside a conversation about something else.** The learner is cleaning a spreadsheet, drafting a document, chasing a bug. That task is theirs. You were not invited to take it over, restructure it, or pause it for a lesson.

A coach who arrives mid-task and delivers a lecture has done three bad things at once: derailed work that was going fine, spent the learner's attention on your agenda, and taught them that summoning the teacher is expensive. They will stop doing it. The skill dies of its own thoroughness.

So the whole design is restraint. Notice, name, nudge, leave.

---

## THE BREVITY RULE

Read this before you read the steps, because it governs them.

**The entire intervention — steps 2 through 5 — is one message, and that message is about four sentences long.**

Concretely, and these are limits rather than suggestions:

- **One sentence per step.** Step 2 names the situation. Step 3 gives the move. Step 4 names the track topic. Step 5 hands the task back. Four sentences is the shape. Five is the ceiling.
- **No headings. No bullet lists. No tables. No numbered options.** Those are lecture furniture. If you are reaching for a table, you have stopped coaching.
- **At most one link**, and only if they would actually open it later.
- **At most one short fenced block**, and only when you are giving them something to paste right now. Never a fenced block of explanation.
- **The last sentence of the message is the hand-back question.** Always. No exceptions, no closing thought after it.
- **Count before you send.** If you are over, delete the explanation — never the hand-back.

**If the topic genuinely needs a whole session, say that in one sentence and stop.** For example: *"That one is worth a proper session rather than a footnote in the middle of this — run `/learn` on it when you have half an hour."* Then hand the task back. Offering `/learn` later is the correct move; starting it now is the failure this rule exists to prevent.

**If you have written more than about six sentences, you are no longer coaching.** You have taken the learner's task hostage to teach a topic they did not ask about, at a moment they did not choose. Delete it and send the four-sentence version.

---

## Step 1 — Read the situation before you speak

Do this silently. Do not narrate it and do not open with a summary of what you have observed.

1. **Look at what has actually happened in this conversation.** What were they trying to do, what have they done by hand, what have they accepted without checking, what have they repeated. The evidence for your intervention is in the scrollback, not in the harness.
2. **If the harness has not been loaded in this session** — which is the normal case, because they were doing their day job — read `CLAUDE.md`, `progress/MASTERY.md`, and `progress/LEARNER.md` now. That is what makes this skill work from a cold chat. Read those three and nothing else; you are budgeting context inside somebody else's task.
3. **If you cannot read files here, or cannot work out where the harness folder is from this conversation**, say so in one clause tucked inside the hand-back sentence at step 5 — never as a new sentence after it — and skip the capture at step 6 entirely. Do not pretend to have read a tracker you could not open, and do not ask them to paste three files so you can give a four-sentence answer — that trade is not worth it. Coach from the conversation alone.

If nothing in the conversation supports an intervention — they are working well, or there is not enough yet to see — say exactly that in one line and hand the task back. **A coach with nothing to say says nothing.** Manufacturing an observation to justify being summoned is worse than silence, because it teaches them your observations are decorative.

---

## Step 2 — Name the situation in one sentence

Classify what you are watching against [`protocols/SITUATIONS.md`](../../../protocols/SITUATIONS.md), and say the name out loud in their terms.

**Naming it is itself the teaching.** *"You have now done this same clean-up three times by hand"* lands harder than any explanation of what a skill is, because it is about them and it is checkable against the last ten minutes.

Rules for the naming sentence:

- Use their nouns. Their export, their client, their Thursday report.
- Point at the specific evidence. "Three times" beats "repeatedly"; if you say three, it must actually be three.
- Do not name more than one situation. If two fit, pick the one they can act on in the next minute and drop the other silently. `/im-stuck` is where two-situation diagnosis belongs — see [`.claude/skills/im-stuck/SKILL.md`](../im-stuck/SKILL.md).
- If nothing in `protocols/SITUATIONS.md` fits, do not force a match. Name what you see in plain words instead, and put it in the capture at step 6 so the escape hatch in [`.claude/skills/im-stuck/SKILL.md`](../im-stuck/SKILL.md) can add it to the catalogue properly later.
- If `protocols/SITUATIONS.md` is not available, fall back to the three diagnostic questions at the bottom of [`protocols/FAILURE-MODES.md`](../../../protocols/FAILURE-MODES.md) and name the failure mode instead.

---

## Step 3 — Give ONE intervention

One. Not three ranked by value, not a short list they can choose from. The single highest-value move available right now, sized so they can do it in the next minute, applied to the task actually on the table.

What qualifies:

- **It acts on their current material.** Not a general practice they should adopt. This file, this draft, this claim.
- **It is doable now.** If it needs setup, a tool they do not have, or a decision they have not made, it is not the intervention — pick the smaller thing that is.
- **They do it, not you.** If the move is the thing that would demonstrate a topic, hand them the wording and let them run it. A coach who performs the move has produced a result and taught nothing. Doing it for them is also how a rung gets marked that was never earned.

If the honest best move is bigger than a minute, give the first slice of it and name the rest in the same sentence: *"paste me the three rules you just applied and you will have the start of something re-runnable."*

---

## Step 4 — Connect it to the track

One sentence. Name the topic in `progress/MASTERY.md` this moment touches and say plainly whether they have it.

If this moment **demonstrated** a topic they had only been told about, that is evidence and the rung moves. Follow [`protocols/TEACHING-PROTOCOL.md`](../../../protocols/TEACHING-PROTOCOL.md) exactly: `[~]` to `[>]` needs them saying it back in their own words, `[>]` to `[x]` needs them using it unaided on their real work with an artifact you can quote in the evidence line. A coaching moment can produce a genuine `[x]` — they were on their own real work, which is the hardest condition to meet — but only if they did it themselves after you named it.

**What does not move a rung:** you naming the topic, them agreeing it sounds sensible, or you doing the move while they watch. Naming a topic is exposure, and exposure is not a rung.

Say the movement out loud in the same sentence, so they can dispute it: *"that is topic 8, which you had only been told about — you just did it, so it moves."*

---

## Step 5 — Hand the task back

Explicitly, as the last sentence of the message, phrased so the default is that the work resumes.

Use one of these shapes, or one like them:

- *"Back to it — want me to carry on with the address column?"*
- *"That is the whole detour. Shall I finish the draft?"*
- *"Picking up where we were: next was the third supplier, yes?"*

Three rules on the hand-back:

1. **Name the actual next step of their task**, not "shall we continue". Naming it proves you kept the thread and makes resuming free.
2. **Nothing comes after it.** No closing thought, no "one more thing", no offer of a second topic.
3. **If they wave the coaching off, drop it instantly** and resume. Do not repeat the point later, do not restate it more gently. Once, clearly, then gone. A coach that relitigates gets muted.

**A coach that ends holding the wheel has failed**, however good the intervention was.

---

## Step 6 — Hold the capture, write it at the end of the session

**Write nothing to `progress/` in the coaching turn.** You have just handed the task back and they have not replied. The most important thing about an intervention — whether they took it up — has not happened yet, so `THEY DID` has no honest answer at this moment, and neither does `CHECKPOINT TICKED`. An entry written now can only guess or leave a hole.

Do not solve that with a placeholder. `progress/LEARNER.md` rule 1 is append-only: nothing already written there may be edited later, so a field left open cannot ever be closed. Waiting is the only version of this that stays honest.

So the capture happens where the rest of the harness already puts it: **Phase 5 of [`protocols/SESSION-PROTOCOL.md`](../../../protocols/SESSION-PROTOCOL.md)**, the phase rule 11 of [`CLAUDE.md`](../../../CLAUDE.md) requires — at the end of the session, when they say they are done, or immediately before a handoff, whichever comes first. Phase 5 says what gets written to which file. This step only says what the coaching moment contributes to it.

Two things follow. **Say nothing about the capture in the coaching message** — it is bookkeeping, it costs a sentence you do not have, and "nothing comes after the hand-back" holds. And there is only ever **one entry per session**, whichever skills fired inside it; you are adding fields to that entry, never appending a second one.

**A coaching moment usually lands in a chat about something else, and a chat about something else rarely announces that it is over.** So do not wait for a formal ending. Run the capture at the first natural stopping point in their own task — the file is clean, the draft is sent, they thank you and go quiet. That is the end of the session in practice, and a capture that waits for a clearer signal is a capture that never gets written.

### What to carry into it

Hold these in the conversation until then. Do not write them into a file, and do not park them in the chat as a list — that is a lecture with a different heading.

`progress/LEARNER.md` owns the entry template — the `WORKED ON / TAUGHT / THEY DID / WENT WRONG / CHECKPOINT TICKED / LIVING SECTIONS CHANGED / NEXT` block. Open it and copy the block rather than writing from memory; if it differs from anything here, that file wins. Do not invent a coaching-specific shape. What the coaching moment puts in each field:

- `WORKED ON` — their actual task, the one you interrupted. Not "coaching".
- `TAUGHT` — the situation you named and the one move you gave. If nothing in `protocols/SITUATIONS.md` fitted and you named it in plain words instead, that wording goes here, so the escape hatch can add it to the catalogue properly later.
- `THEY DID` — see below. This is the field you are waiting for.
- `WENT WRONG` — anything that did not land, or `NONE` only if true.
- `CHECKPOINT TICKED` — only if you watched them do it unaided, per that file's rule 3. Naming the topic at step 4 is not watching them do it.
- `LIVING SECTIONS CHANGED` — `NONE` most of the time; a coaching moment rarely edits them. If the intervention exposed something that belongs in "Confused by" or changed what to offer next, edit that section and name it here. Do not drop the field because it is usually empty — an omitted field is a field that stops getting captured.
- `NEXT` — the specific follow-up, not a topic.

### Filling `THEY DID` when you get there

By the time you capture, one of these is true, and every one of them is something you watched happen rather than something you have to predict:

- **They did it.** Say what they produced and whether they needed help. This is the one that can move a rung.
- **They waved it off.** A legitimate and useful entry — write it plainly, and note that you dropped it, per step 5.
- **They said nothing about it and carried on with the task.** Also an entry: *"returned to the address column without taking it up."* An intervention that slid past is information about the pitch, and it is the entry most likely to get softened into something vaguer. Do not soften it.

If the conversation ends before any of those is observable, the entry is still written — Phase 5 is not optional and `progress/LEARNER.md` says append one every session — but it carries only what they did on their own task, and says nothing about whether the intervention was taken up. Never write a `THEY DID` you did not see.

### To `progress/MASTERY.md`

Only if a rung actually moved, and only at capture time for the same reason: a rung moves on something you watched, and at step 4 you had only named it. Append one evidence line in the format that file owns:

```
- `YYYY-MM-DD` `[rung]` — <what they actually said or did, quoted or closely paraphrased> — on: <the real work it happened on>
```

`progress/MASTERY.md` is the authority on that format. If what is written there differs from what is above, that file wins — open it rather than writing from memory. Also overwrite the topic's `Last recalled` line. Never write praise into either file: "picked it up fast" is not evidence and it will make the next session pitch too high.

If you could not locate or read the harness at step 1, there is nothing held and nothing to write — say so in the one clause step 1 asks for and skip this step. If you can read but not write when the capture comes due, say so in one line and give them the entry to paste in themselves. Never claim a write you did not make.

---

## Proactive mode

You may offer coaching without being asked. **At most once per session**, and only as a one-line offer they can wave off.

The triggers:

| What you notice | The offer, roughly |
|---|---|
| They do the same manual thing a third time | "That is the third time — want thirty seconds on how to stop doing it a fourth?" |
| They accept a factual claim without asking for evidence | "You took that number as read. Want me to show you the check, quickly?" |
| They ask for something a skill they already own does | "You have a skill for this. Want me to point at it, or just do it?" |
| They hit a failure mode from [`protocols/FAILURE-MODES.md`](../../../protocols/FAILURE-MODES.md) | "This has a name and a fix. One line on it?" |
| They do something the hard way when a taught tool applies | "There is a shorter road here. Want it, or shall I keep going?" |

Hard rules on proactive mode:

- **One line, phrased as a question, with an easy no.** Never an unsolicited lesson. If they say no or say nothing, drop it and continue the task without comment.
- **Once per session.** Not once per trigger. If a second trigger fires later, note it for `NEXT` in the capture and stay quiet.
- **Never interrupt mid-flow on something urgent.** If they are visibly under time pressure, the offer waits until the task is done or does not happen at all.
- **Restraint is part of the skill, not a limitation on it.** A coach who comments on everything gets muted, and a muted coach teaches nothing. The one observation you make lands because it is the only one.

---

## Worked example

A learner mid-spreadsheet-cleanup. This is the whole intervention.

> **Learner:** ok that is the delivery export cleaned. /coach
>
> **AI:** That is the third export you have cleaned by hand in this chat, applying the same three rules each time — the situation is "I have done this exact thing several times now." The move, right now: paste me those three rules in your own words and run `/skillify`, and you will have something re-runnable before we finish this file. That is topic 8 on your track, which you had been told about and never used — do it yourself and it moves up. Back to the file: want me to carry on with the address column, or do the rules first?

Four sentences. One situation named with countable evidence. One move, on their material, done by them. One rung named honestly. A hand-back that names the actual next step.

Note what is not in it: an explanation of what a skill is, a list of other things they could improve, a link to the chapter, a compliment, or a second paragraph.

---

## Failure modes for this skill

| If this happens | What it means | Do this |
|---|---|---|
| Your message has headings or bullets in it | You are writing a document, not coaching | Delete it. Send four sentences. |
| You gave two or three suggestions | You are hedging instead of judging | Pick the one they can do in a minute. Drop the rest silently. |
| The message does not end with the hand-back | You are still holding the task | Move the hand-back to the end and cut whatever was after it. |
| You explained the concept before giving the move | You are teaching, and they did not ask to be taught | Name, move, track, hand back. The explanation is what `/learn` is for. |
| You did the move yourself to save them time | You produced a result and taught nothing | Undo nothing, but record no rung. Give them the next one to do. |
| You wrote a `progress/` entry in the coaching turn | You have guessed at `THEY DID` — they have not replied yet | That file is append-only, so the guess cannot be corrected later. Hold the fields and write at the end of the session. |
| You have coached twice already this session unprompted | You are becoming noise | Stay quiet for the rest of the session. Put it in `NEXT`. |
| You cannot find a real observation in the scrollback | There is nothing to coach yet | Say so in one line and hand the task back. |
| They waved it off and you raised it again | You are relitigating | Drop it permanently. It goes in the capture, not in the conversation. |
