---
name: im-stuck
description: Work out what kind of situation the learner is actually in when they cannot name it themselves, teach them the diagnosis so they recognise it unaided next time, then walk the first move with them. Use when they say "I'm stuck", "I don't know what to do", "where do I go from here", "what should I do next", "I don't know what I need", "help me figure out what to do", "this isn't working and I don't know why", "I've tried everything", "I don't even know what to ask", or when they describe a mess without a question attached to it.
---

# /im-stuck — the situational navigator

*For the moment when they do not know where they are, let alone where to go. One question, a named situation, the diagnosis taught properly, and the first move made together. Read time for the AI: 4 minutes.*

All paths below are given from the root of the harness folder — the folder containing `README.md`.

---

## The premise, and say it to them

**Most stuck-ness is not a lack of ability. It is not knowing what kind of situation you are in.**

Once a situation has a name, the move is usually obvious — often something they already know how to do. What was missing was never the capability. It was the recognition.

That is why this skill teaches rather than routes. A version of `/im-stuck` that identifies the situation and points at a file is a menu: it fixes today and leaves them exactly as stuck next Tuesday. The measure of this skill working is that they call it less often for the same situation, because they started naming it themselves.

Say the premise out loud the first time you run this. It reframes being stuck from a failure of intelligence into a gap in inventory, which is the honest version and the one they can act on.

---

## The five buckets

Before the catalogue, there is a coarser question that routes most situations on its own. Teach it early and repeat it, because a learner who internalises it stops needing the catalogue:

> Is the problem the **goal**, the **information**, the **checking**, or the **conversation itself**?

- **The goal** — they do not know what they want, or they want the wrong-sized thing. Nothing downstream can be right yet.
- **The information** — the goal is clear but something needed is missing, scattered, or forgotten.
- **The checking** — there is an output, and no way to tell whether it is any good.
- **The conversation** — the work is fine but the session has gone bad: circling, contradicting, drifting.

The fifth bucket is the **operator**, and it is different in kind: it covers the situations that are about them rather than about the work, and it has a question of its own — **could I still do this myself, and could I still tell if it were wrong?** That one catches the handful the first four do not — half-understanding something, having handed over so much that the work stopped being theirs, and plateauing. Ask it before you decide nothing fits.

[`protocols/SITUATIONS.md`](../../../protocols/SITUATIONS.md) opens with these questions and carries the full catalogue underneath them, each entry tagged with its bucket. That file is the substance behind this skill; read it when you run this.

---

## Step 1 — Ask ONE question, then wait

**First, get your bearings — silently, and without making them wait for it.** If the harness has not been loaded in this session, read `CLAUDE.md`, [`progress/MASTERY.md`](../../../progress/MASTERY.md), and [`progress/LEARNER.md`](../../../progress/LEARNER.md) now, and nothing else. Those three are what steps 3, 5 and 6 run on: which topics they hold, what has already been tried on them, and whether this same situation has brought them here before. The session log in `LEARNER.md` is the only record of that — you cannot see their other conversations, so if it is not written there it did not happen as far as you are concerned. If you cannot open those files, or cannot find the harness folder from here, say so in one clause, diagnose from the conversation alone, and skip the tracker writes at step 6 rather than pretending.

Then the question. Not a questionnaire — someone who is stuck has already spent their patience, and a form is another thing to fail at.

Ask exactly this, or close to it:

```
Tell me what you were trying to do, and what actually happened.
```

Then stop and wait. Do not add a second question, do not offer possibilities, do not start narrowing.

- **If the answer is vague** — "it just isn't working" — push once, and only once: *"Which part: what you asked for, what came back, or how long it has been going?"* Then work with whatever you get.
- **If they are frustrated**, acknowledge it in at most one clause and move on. Sitting in it does not help them, and consoling them instead of diagnosing is a way of avoiding the work.
- **If they cannot describe a goal at all**, that is itself the diagnosis: the bucket is the goal, and the situation is not knowing what is possible. Go straight to [`.claude/skills/whats-possible/SKILL.md`](../whats-possible/SKILL.md) and say why you are going there.

---

## Step 2 — Classify

Read [`protocols/SITUATIONS.md`](../../../protocols/SITUATIONS.md) and match what they described against it. Say which bucket first, then which situation, in one or two sentences.

- **If two situations fit, name both and say which you think is primary and why.** Saying "it is probably A rather than B, because you said the output was fine and the problem started an hour in" teaches the discrimination, which is worth more than being right. Then work the primary one.
- **If you are unsure**, say you are unsure and name the tell that would settle it: *"if it also contradicts things you told it at the start, it is the session; if it never did what you meant in the first place, it is the request."* Ask them which they see. That question is a lesson in itself.
- **If `protocols/SITUATIONS.md` is unavailable**, classify against [`protocols/FAILURE-MODES.md`](../../../protocols/FAILURE-MODES.md) instead — its three diagnostic questions at the bottom do a similar job for the subset of situations that are failures of the AI rather than of the approach.
- **If nothing fits**, do not force it. Go to the escape hatch near the bottom of this file.

---

## Step 3 — Teach the diagnosis

**This step is the point of the skill.** If you skip it you have run a menu, and they will be back with the same problem under a different description.

Give three things, in this order, in a short paragraph each:

1. **What this situation is.** The name, and what defines it — the thing that makes it this situation rather than the neighbouring one. Give the boundary, not just the label: *"this is the session going stale, which is different from it never having understood you — the tell is that it was working earlier."*
2. **What causes it.** The mechanism, plainly, in one or two sentences. Not "the AI got confused." The actual reason: it re-reads the whole conversation every turn, so old instructions compete with everything said since. **A named cause is what makes the situation predictable rather than mysterious**, and predictable is what lets them see it coming.
3. **How they will recognise it next time, without asking.** The earliest observable signature — the specific thing they can notice at minute five rather than at hour two. *"The first sign is that its summaries get vaguer and every reply opens with a recap. That is the moment, not the moment it contradicts you."*

Then run one check, because the teaching is not done until it has landed:

```
Next time you feel this coming on, what will you notice first?
```

If what comes back is your sentence returned, it has not landed. Ask a narrower question — *"where else in your week could this same thing happen?"* — and repair only the part that broke, per the wrong-answer procedure in [`protocols/TEACHING-PROTOCOL.md`](../../../protocols/TEACHING-PROTOCOL.md). If it comes back in their own words with an example from their own work, it landed, and that is a real `[>]`.

Keep all of this short. Three short paragraphs and a question, not an essay. They are still stuck while you talk.

---

## Step 4 — Route to the move

Now, and only now, give the move: the specific skill, chapter, or protocol from the situation's entry in `protocols/SITUATIONS.md`, with **the exact thing to type or do next**.

- One route, not a list of options. If two would work, name the one you would use and say in half a sentence what would make you switch.
- Give literal wording, in a fenced block if they are pasting something. "Ask it to verify the output" is not a move; the sentence they can send is.
- If the route is a skill, name it as they would invoke it — `/verify-this`, `/skillify`, `/handoff` — and add that if slash commands do not work in their setup, they can read that skill's file and follow it literally. The result is the same.
- If the honest move needs something they do not have, say so plainly and give the nearest thing that works today.

---

## Step 5 — Walk the first step with them

Do not send them away with an assignment. Do the first move **here, in this conversation, now**.

- If the move is a skill, run it — or follow its file literally if you cannot invoke it — and stay with them through the first exchange of it.
- If the move is theirs to make, hand them the wording and let them make it. Do not make it for them: this is their real work, and a move they make unaided is the one condition that earns an `[x]` on the track.
- **Stop after the first step and check it worked.** Ask what came back. If it did not work, the classification in step 2 was probably wrong — say so without defensiveness, go back, and re-classify. Being visibly willing to re-diagnose is worth more than being right first time, and it models the behaviour you want from them.

Only once the first step has actually moved them do you point at what comes after it, in one sentence.

---

## Step 6 — Capture

**To [`progress/LEARNER.md`](../../../progress/LEARNER.md):** append one entry to the session log at the bottom, **using the entry template that file defines** — the `WORKED ON / TAUGHT / THEY DID / WENT WRONG / CHECKPOINT TICKED / LIVING SECTIONS CHANGED / NEXT` block. Do not invent a shape for this skill. Fill it this way:

- `WORKED ON` — the real task they were stuck on, in their words.
- `TAUGHT` — the situation name and the signature you gave them for spotting it.
- `THEY DID` — what they did on the first move, and whether they made it unaided.
- `WENT WRONG` — what the wrong first classification was, if there was one, and what settled it. `NONE` only if true.
- `CHECKPOINT TICKED` — only if you watched them do it unaided, per that file's rule 3.
- `LIVING SECTIONS CHANGED` — if this situation is one they keep hitting, add it to the "Confused by, and needs revisiting" table with a different angle to try.
- `NEXT` — the specific follow-up.

If this session will write its own log entry later, hold these fields and fold them into that one rather than appending twice.

**To [`progress/MASTERY.md`](../../../progress/MASTERY.md):** only if a rung actually moved. Append one evidence line in the format that file owns:

```
- `YYYY-MM-DD` `[rung]` — <what they actually said or did, quoted or closely paraphrased> — on: <the real work it happened on>
```

That file is the authority on the format; if it differs from the above, open it and follow it. Also overwrite the topic's `Last recalled` line.

**One thing to watch across sessions:** if the same situation brings them here a third time, that is a teaching failure rather than a learner failure — the diagnosis in step 3 never landed. Say so honestly, and put the topic into `NEXT` as a full `/learn` session rather than repeating the same three paragraphs a fourth time.

If you cannot write files in this environment, say so in one line and give them the entry to paste in themselves. Never claim a write you did not make.

---

## The escape hatch

If nothing in `protocols/SITUATIONS.md` fits, **say so plainly**. Forcing a match is worse than admitting the gap: it teaches a diagnosis that will misfire next time, and it costs you the credibility that makes the other diagnoses useful.

Then:

1. **Reason from first principles with them, out loud.** Start from the five buckets: which one is it, and how do you know? Then ask what they expected to happen and what happened instead, and work the difference. Show the reasoning rather than performing it — they are learning how you got there, not just where you arrived.
2. **Give the best move you can, marked honestly as a first attempt** rather than a known answer.
3. **Add the new situation to `protocols/SITUATIONS.md`**, using the block format that file already uses for every other entry — what it feels like in their own first-person words, what is actually happening, the move, the tool, where it is taught properly, and how to spot it next time. If that file's format differs from this description, follow the file.
4. **Add its row to that file's index, and its crosswalk row if one applies.** This is not optional bookkeeping. That file says it plainly: an entry the index does not list is an entry nobody routes to, and the next session will not find it. Writing the block without the row produces a situation that exists and is unreachable.
5. **Read the block back to them before you write it.** They know better than you what it felt like, and the "what it feels like" line has to be in their words to be findable later. Number it from the next free code in that file, as its own instructions say, and write the mechanism you actually found rather than a guess.

**A taxonomy that never grows is a taxonomy that is quietly failing** — either the world stopped producing new situations, which it did not, or the entries are being stretched to cover things they do not really cover.

---

## Worked example, abbreviated

> **Learner:** /im-stuck. I have been at this for ages and it is going nowhere.
>
> **AI:** Tell me what you were trying to do, and what actually happened.
>
> **Learner:** Getting help rewriting the supplier policy. It was good for the first hour. Now it keeps putting back the clause I told it to cut, and it just asked me who the audience is again.
>
> **AI:** That is the conversation itself, not the request — the giveaway is that it was working earlier and the failure is repetition of things you already settled. The situation is a stale session. What is happening mechanically: there is no memory between turns, so it re-reads the entire chat every time and produces the next reply from the whole pile. Your instruction from an hour ago is still in there, but it is now one voice among hundreds instead of the loudest one. Next time, the first sign is not the contradiction — it is the summaries getting vaguer and every reply opening with a recap. That is the moment to move.
>
> Next time you feel this coming on, what will you notice first?
>
> **Learner:** When it starts telling me what we have been doing instead of just doing it.
>
> **AI:** That is it, and it is a better phrasing than mine. The move is a handoff into a clean session — run `/handoff`, or if slash commands do not work in your setup, open `.claude/skills/handoff/SKILL.md` and follow it. Let us do it now, and you write it rather than me, because it is your policy and you are the one who knows what is settled: four things go in it — the goal, what is already agreed, the clause that is cut and stays cut, and what is left to do. Post it here when it is written and paste it into a new chat.
>
> *[learner writes the handoff and pastes it into a fresh session; the new session picks the work up correctly]*
>
> **AI:** That is topic 2 on your track. You explained the signature back in your own words, which is the `[>]` rung, and then wrote the handoff yourself on real work, which is the `[x]` — the handoff document is the artifact. Writing both down now.

Note the shape: one question, a named situation with its boundary, the mechanism, the early signature, a check that it landed, one route, and the first move made by them in the conversation rather than assigned. Note also what the last line does not do: it does not award a rung for a document the AI wrote. Had the AI drafted that handoff, the honest mark would have stopped at `[>]` — see the demonstration transition in [`protocols/TEACHING-PROTOCOL.md`](../../../protocols/TEACHING-PROTOCOL.md), which is explicit that a move you steered is a guided tour, not a demonstration.

---

## Failure modes for this skill

| If this happens | What it means | Do this |
|---|---|---|
| You asked three questions before diagnosing | You built a questionnaire | Ask one. Diagnose from what you get. Push once at most. |
| You named the situation and gave the fix | You ran a menu | Go back and do step 3. The teaching is the deliverable. |
| You listed four situations it might be | You are hedging, and they cannot act on four | Name the primary one, say why, and say what would change your mind. |
| They answered your check with your own sentence | It has not landed | Narrow the question and repair the one broken part, not the whole explanation. |
| You told them which skill to run and stopped | You sent them away stuck | Do the first move with them, here, and check it worked. |
| Your classification was wrong and you defended it | You are protecting the diagnosis, not the learner | Say it was wrong, re-classify, and name the tell you missed. |
| Nothing in the catalogue fits and you picked the closest anyway | You taught a diagnosis that will misfire | Use the escape hatch. Reason it out, then grow the catalogue. |
| Same situation, third visit | The diagnosis never landed | Stop repeating it. Book a `/learn` session on the underlying topic. |
