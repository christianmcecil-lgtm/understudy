# Situations

*The catalogue of the spots you actually find yourself in when working with AI, what is really going on in each one, and the next move. Twenty minutes to read straight through; thirty seconds to use when you are in one.*

---

## This file and its twin

There are two catalogues in this harness and they are organised on different axes. Open the right one.

| File | Organised by | Open it when |
|---|---|---|
| [`FAILURE-MODES.md`](./FAILURE-MODES.md) | What went wrong **mechanically** | You know something is wrong with the output and want to name the mechanism |
| This file | What you are **experiencing** | You do not know what is wrong, or whether anything is wrong at all |

Put plainly: failure modes are diagnoses of an output. Situations are diagnoses of a moment. You can be in a situation with nothing wrong at all — "I do not know what to ask for" is not a malfunction, it is a normal place to stand. Several situations here end by pointing at a failure mode, because that is where the trail leads. Follow the link when it does.

The entries below are written for the person, not the machine. If you are the AI reading this in service of [`.claude/skills/im-stuck/SKILL.md`](../.claude/skills/im-stuck/SKILL.md), your job is to name the situation out loud in one sentence, teach the diagnosis, and then walk the first move with them — not to read the block aloud.

---

## The meta-skill: four questions that route almost everything

Most stuck-ness is not a lack of ability. It is not knowing what kind of trouble you are in. Once the trouble has a name, the move is usually obvious — which is why the fastest thing you can learn from this file is not the twenty entries, it is the four questions that route them.

Ask them in this order and stop at the first one that gets an uncomfortable answer.

**1. Is the problem the GOAL?**
Do you actually know what you want, and have you said it out loud? Could a stranger tell whether you got it? Situations in this bucket feel like vagueness, drift, or "this is technically what I asked for and it is useless." The fix is almost always upstream of the AI: get specific, or set a boundary, or change the shape of the work.

**2. Is the problem the INFORMATION?**
Does the AI have what it needs, and can you find what you already have? This bucket feels like repetition, re-explaining, lost notes, and "it does not know about the thing I told it last week." The fix lives in files, not in better prompting.

**3. Is the problem the CHECKING?**
Is there anything in this process that would have caught an error? This bucket feels like unease with output you cannot fault. If the honest answer is "nothing would have caught it," you have found the problem, and it was never the answer quality.

**4. Is the problem the CONVERSATION ITSELF?**
Has this particular session become the obstacle — long, contradictory, circling, carrying rejected ideas it will not put down? This bucket feels like arguing with someone who was listening an hour ago. The fix is a fresh session with a written handoff, and it is almost never worth delaying.

Those four cover most of what follows. Three situations sit outside them, and it is worth being honest about which: **the last group is about you, not about the work.** "I think I understand this but I am not sure", "I have stopped understanding my own work", and "I have plateaued" are operator problems, tagged below as such. They have a fifth question of their own: **could I still do this, and could I still tell if it were wrong?** That question is uncomfortable by design, which is why it needs to be on a list rather than left to occur to you.

**A learner who internalises those five questions needs this catalogue less every month.** That is the intended direction. The entries exist to teach the pattern behind each situation, so that eventually you name your own situation before you finish typing the sentence about it. If you find yourself scrolling this file for a match, ask the four questions first — you will usually land in the right neighbourhood without help.

---

## The index

| Code | It feels like | Bucket |
|---|---|---|
| [S-01](#s-01--i-do-not-know-what-to-ask-for) | I do not know what to ask for | Goal |
| [S-02](#s-02--i-have-been-going-in-circles-for-an-hour) | I have been going in circles for an hour | Conversation |
| [S-03](#s-03--i-cannot-tell-whether-this-is-right) | I cannot tell whether this is right | Checking |
| [S-04](#s-04--i-have-done-this-exact-thing-several-times) | I have done this exact thing several times | Goal |
| [S-05](#s-05--i-cannot-find-something-i-know-i-wrote-down) | I cannot find something I know I wrote down | Information |
| [S-06](#s-06--it-keeps-forgetting-what-i-told-it) | It keeps forgetting what I told it | Conversation |
| [S-07](#s-07--it-changed-things-i-did-not-ask-it-to-change) | It changed things I did not ask it to change | Goal |
| [S-08](#s-08--it-was-confidently-wrong-and-i-caught-it-by-luck) | It was confidently wrong and I caught it by luck | Checking |
| [S-09](#s-09--this-is-taking-longer-and-costing-more-than-it-should) | This is taking longer and costing more than it should | Goal |
| [S-10](#s-10--i-do-not-know-whether-i-am-allowed-to-put-this-in) | I do not know whether I am allowed to put this in | Information |
| [S-11](#s-11--someone-told-me-i-have-to-use-a-new-tool) | Someone told me I have to use a new tool | Goal |
| [S-12](#s-12--i-want-this-to-run-while-i-am-not-here) | I want this to run while I am not here | Goal |
| [S-13](#s-13--i-have-to-touch-files-and-i-am-afraid-of-breaking-something) | I have to touch files and I am afraid of breaking something | Goal |
| [S-14](#s-14--i-want-a-second-opinion-and-i-only-have-one-ai) | I want a second opinion and I only have one AI | Checking |
| [S-15](#s-15--i-am-drowning-in-repetitive-work-and-cannot-see-what-to-fix-first) | I am drowning in repetitive work and cannot see what to fix first | Goal |
| [S-16](#s-16--i-think-i-understand-this-but-i-am-not-sure) | I think I understand this but I am not sure | Operator |
| [S-17](#s-17--it-is-doing-so-much-that-i-have-stopped-understanding-my-own-work) | It is doing so much that I have stopped understanding my own work | Operator |
| [S-18](#s-18--the-answer-sounds-right-and-i-cannot-tell-if-it-is-hollow) | The answer sounds right and I cannot tell if it is hollow | Checking |
| [S-19](#s-19--i-need-to-look-back-at-something-i-did-before) | I need to look back at something I did before | Information |
| [S-20](#s-20--i-have-plateaued-and-do-not-know-what-to-get-better-at) | I have plateaued and do not know what to get better at | Operator |

One entry carries a variant rather than a code of its own: [S-02a](#s-02a--the-variant-where-the-loop-is-with-the-ai-in-front-of-you), for when the loop you are going in circles in is with the AI you are talking to right now. It lives inside S-02 because it is the same situation seen from the inside, and it is probably the commonest one in the file.

Exact wording to paste for many of the moves below lives in [`PROMPT-PATTERNS.md`](../reference/PROMPT-PATTERNS.md). The entries here give you the shape of the sentence; that file gives you the whole thing.

---

## Where this file meets the failure catalogue

Six of the twenty situations are the lived experience of a specific mechanical failure. When you are in one of those, read both: this file tells you what to do next, and the linked entry in [`FAILURE-MODES.md`](./FAILURE-MODES.md) tells you the mechanism and gives you the recovery prompt to paste.

| The situation you are in | The failure it usually is |
|---|---|
| [S-02](#s-02--i-have-been-going-in-circles-for-an-hour) circling for an hour | [F-04, the stale session](./FAILURE-MODES.md#f-04--the-stale-session) |
| [S-07](#s-07--it-changed-things-i-did-not-ask-it-to-change) it changed more than I asked | [F-06, the scope creep](./FAILURE-MODES.md#f-06--the-scope-creep) |
| [S-08](#s-08--it-was-confidently-wrong-and-i-caught-it-by-luck) confidently wrong, caught by luck | [F-01, the confident fabrication](./FAILURE-MODES.md#f-01--the-confident-fabrication) |
| [S-12](#s-12--i-want-this-to-run-while-i-am-not-here) I want it to run unattended | [F-12, the automation that outran trust](./FAILURE-MODES.md#f-12--the-automation-that-outran-trust) |
| [S-17](#s-17--it-is-doing-so-much-that-i-have-stopped-understanding-my-own-work) I have stopped understanding my work | [F-13, the dependency trap](./FAILURE-MODES.md#f-13--the-dependency-trap) |
| [S-18](#s-18--the-answer-sounds-right-and-i-cannot-tell-if-it-is-hollow) it sounds right and may be hollow | [F-07, the plausible-but-wrong structure](./FAILURE-MODES.md#f-07--the-plausible-but-wrong-structure) |

The other fourteen have no mechanical twin, which is the point of having two files. Not knowing what to ask for, not being able to find your own notes, not knowing whether you are allowed to paste something — nothing malfunctioned in any of those. They are still the situations that cost people the most time.

---

## S-01 — I do not know what to ask for

**What it feels like.** "Everyone says this stuff is transformative and I am using it to reword emails. I open a session and stare at it. I do not know what to ask for, and I suspect I am not even asking for the right kind of thing."

**What is actually happening.** You are not missing skill; you are missing a map of the possible. Every request you make is drawn from your mental catalogue of what this tool does, and that catalogue was built from the two or three things you happened to try first. Nothing in normal use ever expands it: the tool answers what you ask, competently, and so confirms that what you asked for is the kind of thing it is for. The gap is invisible from the inside because a thing you never imagined asking for does not feel like an absence. This is the reason the harness treats curiosity as the actual subject rather than a nice extra — execution is the cheap part now, and knowing what to request is the bottleneck.

**The move.** Stop trying to think of a question. Describe your week instead — the meetings, the documents, the parts you dread — and ask for the questions rather than the answers: "Given what I have just described, what could I be asking you for that I probably do not know is possible? Rank by how much time it would save me." Then pick one and do it today.

**The tool.** [`.claude/skills/whats-possible/SKILL.md`](../.claude/skills/whats-possible/SKILL.md), which interviews you and works backwards to what is now in reach.

**Learn it properly.** [`curriculum/13-graduation.md`](../curriculum/13-graduation.md) on generating your own questions, and [`curriculum/00-orientation.md`](../curriculum/00-orientation.md) for the map of what the layers make possible.

**How to spot it next time.** Your requests over a whole week fit into two or three shapes — summarise, reword, explain — and none of them involve the AI touching a file, running a check, or remembering anything between sessions. That narrowness is the signature. It is not about how often you use it; someone can use AI daily for a year inside one shape.

---

## S-02 — I have been going in circles for an hour

**What it feels like.** "We keep arriving back at the same place. I say no to something, and twenty minutes later it comes back slightly reworded. I have re-explained the goal three times. I am starting to argue with it."

**What is actually happening.** Nothing carries over between turns except the text of the conversation itself, which the model re-reads whole every time it replies. So an hour in, the pile it is reading contains your goal, every rejected idea, every correction, and every apology, all with equal standing and none of it marked as superseded. Your "no" from earlier is in there as one line among hundreds. The rejected option is in there too, described in detail, which makes it *more* available rather than less. You are not being ignored; you are being outvoted by your own transcript.

**The move.** Stop the work. Do not send another correction — corrections make the pile heavier. Ask for a handoff document instead: goal, done-check, what is finished, what is not, every option already rejected, and the files a fresh session should load. Then open a new session and paste it. Expect the new session to be sharper immediately; that is the tell that this was the problem.

**The tool.** [`.claude/skills/handoff/SKILL.md`](../.claude/skills/handoff/SKILL.md), and the staleness checklist in [`SESSION-PROTOCOL.md`](./SESSION-PROTOCOL.md).

**Learn it properly.** [`curriculum/02-the-context-window.md`](../curriculum/02-the-context-window.md). The mechanical version of this is [F-04, the stale session](./FAILURE-MODES.md#f-04--the-stale-session).

**How to spot it next time.** The signature is a **repeated rejection**: you have now said no to the same suggestion twice. Once is normal. Twice means the conversation is no longer steering, and every further minute in it costs more and works less. A second signature: your last three messages were about the conversation rather than about the work.

### S-02a — the variant where the loop is with the AI in front of you

Everything above describes a session as though you could step outside it to talk about it. Usually you cannot: the session going in circles is the one you are in, and the assistant you would be describing it to is the one you are circling with. That does not change the diagnosis much, but it changes what you should do next, and it adds one advantage you do not have in any other version of this.

*What it feels like.* "I asked you for this an hour ago and we are still going back and forth. Every version has something wrong with it. I do not even know what I am asking for any more." The give-away is in your own sentence: it is full of **you** and **we**, because the failed work is in this chat rather than in a previous one.

*What is actually happening.* The pile-up described above may be part of it, but it is rarely the whole story, and treating it as the whole story sends you to a fresh session that fails the same way. The usual cause is **an under-specified goal that neither of you has ever stated** — so every attempt is fixing a different guess at what you wanted, and every correction narrows a different dimension of it. That is why each version has something wrong and no two are wrong in the same way. You are not converging on one target; you are orbiting several, because no one has written down which is the target. An hour of this feels like a failure to communicate. It is a missing sentence.

*What to do about it.* Stop asking for another version — another version is another guess. Write the goal and the done-check instead: what this is for, who reads it, and the three to five conditions that would make it right ([`DONE-CHECKS.md`](./DONE-CHECKS.md)). Then use the one advantage of being stuck with the AI rather than about it: **it can see the whole failed exchange, so make it do the diagnosis.** Ask what it now thinks you were actually asking for, what each attempt guessed instead, and which of them came closest — then correct that. Its answer will be wrong in a useful way, and correcting a wrong sentence is far easier than producing a right one when you are past caring. Hand off to a fresh session afterwards if the conversation is genuinely heavy, but not before the goal is written down, or the new session inherits the same missing sentence.

*How to spot it next time.* The signature is **two attempts that fix different things**. Not two attempts that are both wrong — two that are wrong in unrelated ways, where the second broke something the first had right. That is the mark of a goal nobody has stated, and it is visible on the second draft, long before the hour is gone. A second signature: you are giving feedback in the form of "not quite" rather than naming a condition it failed.

*The other side of it.* The AI's instructions for this case are the step 1b branch in [`.claude/skills/im-stuck/SKILL.md`](../.claude/skills/im-stuck/SKILL.md): read the exchange back rather than diagnose from the complaint, own its share in one sentence, and offer its own reading rather than ask you to adjudicate. If you are working with an assistant that does not do those things, the three questions in *what to do about it* are the manual version.

---

## S-03 — I cannot tell whether this is right

**What it feels like.** "It gave me something. It looks fine. I have no way of knowing whether it is any good, and I am about to send it to someone whose opinion of me matters."

**What is actually happening.** You are missing a standard, not a check. Checking is comparing a thing against a statement of what it had to be, and you never made that statement — so there is nothing to compare against, and "does it look right" is all that is left. Looking right is exactly what the output is optimised for, so that instinct is the one signal you cannot use here. The unease is accurate and it is information: it is telling you that this artifact arrived with no criteria attached and therefore cannot be evaluated by anyone, including a careful human.

**The move.** Write the done-check now, after the fact if necessary — three to five conditions a colleague who was not in the room could test. Then get the artifact and those conditions checked by something that did not write it: a fresh session, ideally a different assistant, given the artifact and the criteria and nothing about how it was made. Ask for a met / not met / cannot tell table with a quoted line for each verdict, not an opinion.

**The tool.** [`.claude/skills/verify-this/SKILL.md`](../.claude/skills/verify-this/SKILL.md), backed by [`DONE-CHECKS.md`](./DONE-CHECKS.md) and [`VERIFICATION-PROTOCOL.md`](./VERIFICATION-PROTOCOL.md).

**Learn it properly.** [`curriculum/04-verification.md`](../curriculum/04-verification.md).

**How to spot it next time.** Ask one question before you ask for the work: **"what would I check this against?"** If you cannot answer in a sentence, you are already in this situation and the work has not started yet. The recognisable signature after the fact is hesitation at the send button with no specific objection — objectionless hesitation is a missing standard, every time.

---

## S-04 — I have done this exact thing several times

**What it feels like.** "I am typing something I have typed before. I think I have a version of this instruction in an old chat somewhere. I am rebuilding my own prompt from memory again, and probably worse than last time."

**What is actually happening.** The work is repeating but the improvement is not compounding, because the thing you are repeating lives in your head and in dead conversations. Each run re-derives the instructions from memory, so the fixes you discovered last time are lost unless you happen to recall them. This is the difference between a prompt and a skill: a prompt is a single performance, a skill is a written procedure that gets sharper every time you correct it. The reason it does not feel urgent is that each individual retype is cheap. The cost is the improvement you never keep.

**The move.** Do not write the prompt again. Write it down instead: what the task is, what stays the same every time, what changes per run, what "done" looks like, and the one workaround you had to apply by hand last time. That is a skill. Save it, then run the task from it rather than from memory.

**The tool.** [`.claude/skills/skillify/SKILL.md`](../.claude/skills/skillify/SKILL.md). Log the result in [`progress/SKILLS-BUILT.md`](../progress/SKILLS-BUILT.md) so the next session knows it exists.

**Learn it properly.** [`curriculum/05-skills.md`](../curriculum/05-skills.md), then [`curriculum/14-the-skill-library.md`](../curriculum/14-the-skill-library.md) for how skills compose.

**How to spot it next time.** The signature is **searching your own history**. The moment you scroll back through old chats to find how you phrased something, that task has earned a skill. Do not wait for a third occurrence to feel significant; the search is the trigger.

---

## S-05 — I cannot find something I know I wrote down

**What it feels like.** "I definitely captured this. It is in a note, or a doc, or a chat, or that folder. I have spent ten minutes looking and I am now considering just writing it again."

**What is actually happening.** You have storage but no routing. Things were captured wherever you were standing at the time, which means the location of a fact is a function of your mood on a Tuesday rather than of what the fact is about. Search does not rescue you because you cannot remember the words you used. And the deeper cost is not your ten minutes — it is that an AI cannot use any of it either, because there is no entry point it could be pointed at. Notes that only a human can navigate are notes an AI cannot read.

**The move.** Stop looking. Rewrite the fact once, in the place it should have been, and start the router: one small file that says what kinds of things live where. From now on, one fact in one place, and when you capture something ask where it belongs before you write it. Where the fact concerns a decision, it goes in [`progress/DECISIONS.md`](../progress/DECISIONS.md); where it concerns you and your capability, [`progress/LEARNER.md`](../progress/LEARNER.md).

**The tool.** The capture phase of [`SESSION-PROTOCOL.md`](./SESSION-PROTOCOL.md), which routes what you learn to a fixed place at the end of every session instead of wherever you happen to be. The `progress/` files are a working router you already own; copy the shape before inventing one.

**Learn it properly.** [`curriculum/06-memory-and-second-brain.md`](../curriculum/06-memory-and-second-brain.md).

**How to spot it next time.** The signature is the sentence **"I know I wrote this down somewhere."** The word "somewhere" is the diagnosis. A second signature: you have the same fact in two places and cannot say which is current — that is worse than losing it, because now you will act on the stale copy.

---

## S-06 — It keeps forgetting what I told it

**What it feels like.** "I told it my job title, my client, and how I like things formatted. Next session, nothing. I am re-onboarding this thing every single morning."

**What is actually happening.** Two different mechanisms get blamed on one word. Within a session, nothing is forgotten — everything you said is still there, it is just competing for attention with everything else, which is [S-02](#s-02--i-have-been-going-in-circles-for-an-hour). Between sessions, there is genuinely nothing: a new session starts with no knowledge that you exist unless something on disk tells it. Most people try to fix the second problem with better prompting, which cannot work, because the problem is not phrasing. It is that the only durable memory is a file somebody wrote.

**The move.** Write the onboarding once, to a file, and have every session read it. Start with the things you have now said twice: who you are, what you are working on, the formatting you always ask for, and what you never want. Then the next session opens with that file instead of an interrogation. If your tool cannot read files, keep the same text as a note you paste at the top of a new session — it is the same idea with a manual step.

**The tool.** [`progress/LEARNER.md`](../progress/LEARNER.md) already holds this, and [`SESSION-PROTOCOL.md`](./SESSION-PROTOCOL.md) makes reading and updating it a habit rather than a good intention.

**Learn it properly.** [`curriculum/06-memory-and-second-brain.md`](../curriculum/06-memory-and-second-brain.md), then [`curriculum/02-the-context-window.md`](../curriculum/02-the-context-window.md) for the within-session half.

**How to spot it next time.** The signature is **you typing your own context from scratch** at the start of a session. If your opening message would be identical to last Tuesday's opening message, that message should have been a file weeks ago.

---

## S-07 — It changed things I did not ask it to change

**What it feels like.** "I asked for one fix. It reorganised the whole thing. Some of it is genuinely better, which somehow makes it worse, because now I have to read everything to find out what happened."

**What is actually happening.** You gave a positive instruction and no negative one. Helpfulness generalises: a request to improve one part reads as licence to improve nearby parts, because in most of what the model has seen, that is what the person wanted. There is no internal sense of a boundary you did not draw. Anything you did not fence off is, from the inside, in scope. The improvements are not evidence that the boundary is unnecessary — they are the reason people stop drawing one, and then it happens on the paragraph they deliberately left alone.

**The move.** Ask for the change list before you accept anything: every change made, one line each, marked as asked-for or not. Revert the unrequested ones even where they were improvements. Then re-issue the request with the negative half attached: "change only this paragraph, do not touch formatting, structure, or any other section, and if you see something else worth changing, tell me instead of doing it."

**The tool.** The scope fence pattern in [`PROMPT-PATTERNS.md`](../reference/PROMPT-PATTERNS.md), and [`curriculum/15-git.md`](../curriculum/15-git.md) for making the change list mechanical rather than self-reported.

**Learn it properly.** [`curriculum/01-what-the-model-actually-is.md`](../curriculum/01-what-the-model-actually-is.md) on why trained-in helpfulness generalises past the thing you actually asked for, then [F-06, the scope creep](./FAILURE-MODES.md#f-06--the-scope-creep), which has the recovery prompt in full.

**How to spot it next time.** The signature is the phrase **"I also went ahead and"** in the reply — or, before you even send the request, noticing that your instruction contains no sentence starting with "do not". Anything you care about and did not name is where this lands.

---

## S-08 — It was confidently wrong and I caught it by luck

**What it feels like.** "A number was off, and I only noticed because I happened to know that one. Everything else was delivered in exactly the same tone. What else has been wrong?"

**What is actually happening.** Two things at once, and the second is the important one. First, the fluent, confident tone is produced by the same machinery whether the content is right or invented, so tone carries no information about correctness — you have spent your whole life reading confidence as a competence signal in humans, and here that signal is simply disconnected. Second, and this is the part worth sitting with: **you caught it because you happened to be the domain expert on that one line.** Everything you are not expert in went past unexamined. Luck was your entire quality process, and luck does not scale to the parts of the work that made you delegate in the first place.

**The move.** Do not re-read the same output looking harder — that is the process that already failed. Instead pick two or three specific claims and check them yourself in under a minute each, then treat the rest of the answer as roughly as reliable as your sample. And fix the process, not the artifact: for anything that goes to another person, a check by something that did not write it becomes standing procedure from today, not a thing you remember when nervous.

**The tool.** [`.claude/skills/verify-this/SKILL.md`](../.claude/skills/verify-this/SKILL.md); for anything with stakes, add [`.claude/agents/adversary.md`](../.claude/agents/adversary.md) after the check.

**Learn it properly.** [`curriculum/04-verification.md`](../curriculum/04-verification.md), and [F-01, the confident fabrication](./FAILURE-MODES.md#f-01--the-confident-fabrication).

**How to spot it next time.** The signature is asymmetric: **the errors you catch are always in your own specialty.** If every mistake you have ever found was in the one area you happen to know well, your detection rate is a measure of your expertise, not of the output quality. Assume the same error rate in the parts you cannot see.

---

## S-09 — This is taking longer and costing more than it should

**What it feels like.** "The bill is bigger than I expected, or the wait is. This should be a quick thing and it has eaten an afternoon."

**What is actually happening.** Usually one of three, and it is worth telling them apart rather than economising in general. **Weight:** long sessions are re-read in full on every turn, so a heavy conversation costs more per exchange than a fresh one doing the same task, and it does not announce this. **Tier mismatch:** the strongest model at the highest effort is being used for work with no judgment in it — extraction, formatting, reformatting — which is paying for reasoning you do not need. **No stop condition:** something is running toward a target that was never defined, so it does not converge and there is nothing to point at as finished, which is [F-05, the runaway loop](./FAILURE-MODES.md#f-05--the-runaway-loop).

**The move.** Diagnose before economising. If the session is long, hand off to a fresh one — that alone often fixes it. If the task has no judgment in it, drop the tier or the effort and compare the two outputs yourself rather than assuming the expensive one is better. If something is running open-endedly, stop it and write the done-check before restarting.

**The tool.** [`.claude/skills/handoff/SKILL.md`](../.claude/skills/handoff/SKILL.md) for weight, [`DONE-CHECKS.md`](./DONE-CHECKS.md) for the stop condition.

**Learn it properly.** [`curriculum/09-cost-models-and-effort.md`](../curriculum/09-cost-models-and-effort.md) for the two levers — which model, and how much effort — and [`curriculum/03-the-loop.md`](../curriculum/03-the-loop.md) for bounded work.

**How to spot it next time.** The signature is **cost that does not track with difficulty**: a routine task that costs the same as a hard one. When the boring job and the demanding job cost you the same, you are paying for something other than thinking.

---

## S-10 — I do not know whether I am allowed to put this in

**What it feels like.** "This document has a client name in it. Or salary numbers. Or something from a system I signed something about. I do not want to be the person who finds out the hard way, so I am hovering."

**What is actually happening.** You are trying to answer a policy question with a technical instinct, and the two do not meet. What a tool *can* do with your data, what your employer's agreement *permits*, and what a reasonable person would consider appropriate are three separate questions, and only the first is about AI at all. Hesitation here is not timidity — it is the correct response to an unanswered question. What makes it a bad place to stay is that hovering has a cost too: people who cannot resolve this either paste something they should not, or quietly stop using the tool for the work where it would help most.

**The move.** Split the question. Ask your employer — or find the written policy — for the general rule about which tools may see which categories of information; that is a human question with a human answer and it takes one message to the right person. Meanwhile, do the work with the sensitive parts removed: replace names with roles, real figures with representative ones, and put the specifics back yourself at the end. Never paste credentials, keys, card numbers, or government identifiers into any assistant, and treat that as a rule rather than a judgment call.

**The tool.** Write your own do-not-paste list, in your own words, into the line that already exists for it in [`progress/LEARNER.md`](../progress/LEARNER.md) — *What they are not allowed to put into an AI tool*, in the Who this learner is section. Edit that line in place; do not start a new section of your own for it. Future sessions read it and hold the line with you. If the answer came out of a real choice with alternatives, the choice itself also belongs in [`progress/DECISIONS.md`](../progress/DECISIONS.md), in that file's entry template.

**Learn it properly.** [`curriculum/10-safety-privacy-and-trust.md`](../curriculum/10-safety-privacy-and-trust.md).

**How to spot it next time.** The signature is **a pause with your finger over paste**. That pause is a reliable instrument; it fires on exactly the material worth checking. Treat it as a prompt to answer the policy question once and write the answer down, rather than as a feeling to push through.

---

## S-11 — Someone told me I have to use a new tool

**What it feels like.** "A colleague says everyone is switching to this. There is a post claiming I am already behind. It might be right and I do not have the background to tell."

**What is actually happening.** You are being handed an urgency claim without the problem it solves. Nearly every "you must switch" message is missing the same thing: what specifically was hard before, and what specifically got easier. Urgency is doing the work that evidence should be doing, and urgency is cheap to manufacture. There is a real version of this too — genuinely useful things do appear, and dismissing everything is its own failure — so the answer is not scepticism as a posture, it is converting the claim into a testable statement.

**The move.** Restate the claim as a problem: "this tool would help if my current problem is X." Then check whether X is a problem you actually have this month. If it is, run a bounded trial on one real task with a stated done-check, and compare against how you do it now. If it is not, record it in [`progress/DECISIONS.md`](../progress/DECISIONS.md) using that file's entry template rather than a note of your own shape — the claim restated as the decision you took, your actual reasoning, and the tool under `RULED OUT` with the specific reason it lost — so that when it comes round again you are not re-litigating from nothing.

**The tool.** [`progress/DECISIONS.md`](../progress/DECISIONS.md), and [`.claude/skills/verify-this/SKILL.md`](../.claude/skills/verify-this/SKILL.md) when the claim has checkable specifics in it.

**Learn it properly.** [`curriculum/12-the-hype-ledger.md`](../curriculum/12-the-hype-ledger.md), and [`reference/SOURCES.md`](../reference/SOURCES.md) for how the harness separates what is supported from what is one person's report.

**How to spot it next time.** The signature is **a recommendation with no named problem**. If someone cannot tell you what was hard before and is easy now, in one sentence, they are relaying enthusiasm. A second signature: the pitch leans on how fast things are moving rather than on what the thing does.

---

## S-12 — I want this to run while I am not here

**What it feels like.** "This happens every Monday and I always do it by hand. It should just be done when I sit down. How do I make it run on its own?"

**What is actually happening.** You have spotted a real pattern, and the instinct is right, but the question is out of order. Automation does not make a process reliable — it makes an already reliable process cheaper, and an unreliable one faster at being wrong. Watching a task succeed a handful of times has shown you its normal path and none of its edge cases: the empty input, the odd format, the week the source was late. When you are in the room, you absorb all of those without noticing you are the error handler. Remove yourself and every failure mode runs unopposed, at three in the morning, repeatedly.

**The move.** Automate it in propose-only mode first. It produces a draft, a list, or a report and does nothing else; you approve. Stay there through several real runs including at least one strange week. Bound the blast radius to one folder or one label, cap how many items a run may touch, and keep a log detailed enough to reverse anything. Never automate the sending step early — drafting is reversible, sending is not.

**The tool.** [`curriculum/03-the-loop.md`](../curriculum/03-the-loop.md) for the loop shape, [`DONE-CHECKS.md`](./DONE-CHECKS.md) for the stop condition, and [`REVIEW-ROUTINE.md`](./REVIEW-ROUTINE.md) for a worked example of a good first automation — read-only, bounded, produces a document and changes nothing else.

**Learn it properly.** [`curriculum/10-safety-privacy-and-trust.md`](../curriculum/10-safety-privacy-and-trust.md) for the trust ladder, and [F-12, the automation that outran trust](./FAILURE-MODES.md#f-12--the-automation-that-outran-trust).

**How to spot it next time.** The signature is **enthusiasm about a task you have not yet found boring**. If the work is still interesting, you have not seen its edge cases. Trust is earned in an empty parking lot: the right first automation is dull, reversible, and low-stakes, and if that sounds unambitious, that is the point.

---

## S-13 — I have to touch files and I am afraid of breaking something

**What it feels like.** "It wants to edit my documents, or a folder, or something with the word repository in it. I am not technical. If it wrecks something I will not know how to put it back."

**What is actually happening.** The fear is proportionate to a real gap, and the gap is not technical knowledge — it is the absence of an undo. Everything you do in a document editor has a safety net you have never had to think about. Files on disk, edited by an agent across a whole folder, do not have that net by default, and your instinct has correctly noticed its absence. That is why the answer is not "be careful" or "learn more first". It is to install the net, once, and then stop being afraid, because with a floor to fall back to, the worst case becomes a minute of work.

**The move.** Put the folder under version control and take a snapshot before letting anything change it. You do not need to memorise commands; you need to be able to say what you want — "commit everything as it is now with a message saying pre-cleanup", "show me what changed since that snapshot", "put this folder back the way it was this morning". Ask for the change list afterwards, and read it. On top of that: work on a copy for anything genuinely irreplaceable, and require the AI to state exactly what it will change before it changes anything.

**The tool.** The pause-before-anything-irreversible step in [`SESSION-PROTOCOL.md`](./SESSION-PROTOCOL.md), which makes the AI state what it is about to change and wait — and version control underneath it, so that the pause has a floor behind it rather than just a warning.

**Learn it properly.** [`curriculum/15-git.md`](../curriculum/15-git.md), then [`curriculum/16-the-terminal.md`](../curriculum/16-the-terminal.md) for the honest treatment of the terminal — enough not to be afraid of it, not mastery.

**How to spot it next time.** The signature is **being asked to approve a change whose undo you cannot describe**. Not the number of files, not how technical it sounds — just that one question: if this goes wrong, what is the exact sentence that puts it back? No answer means take the snapshot first.

---

## S-14 — I want a second opinion and I only have one AI

**What it feels like.** "I know I should not let it mark its own homework. But I only have the one assistant, and I do not have a colleague who can review this."

**What is actually happening.** Independence is not binary, and treating it as binary is what makes this feel hopeless. A model's errors are patterned rather than random — they follow from its training and its habits of expression — so when the same model reviews its own work inside the same conversation, it re-runs the patterns that produced the answer, with the answer sitting comfortably in the middle of what it finds plausible. But you can buy back independence in increments, and the first increment is free: a fresh session of the same model has dropped the conversation and the prior commitment, which removes a large part of the pull toward approval.

**The move.** Climb the ladder as far as the stakes justify: same session self-check, then a fresh session of the same model, then a different model, then a different model instructed to refute rather than review, then a check that involves no model at all — a calculation, a search, a source you open yourself. Give the checker the artifact and the criteria, and nothing about how it was made or who made it. The reasoning is the thing you are trying to escape.

**The tool.** [`.claude/skills/verify-this/SKILL.md`](../.claude/skills/verify-this/SKILL.md) and the tier ladder in [`VERIFICATION-PROTOCOL.md`](./VERIFICATION-PROTOCOL.md).

**Learn it properly.** [`curriculum/17-many-models.md`](../curriculum/17-many-models.md), including the caveat that matters: models trained on overlapping material can be wrong in the same direction, so agreement raises confidence and does not prove correctness. A deterministic check still beats any number of agreeing models.

**How to spot it next time.** The signature is **the checker knowing the story**. If whatever is reviewing the work has seen how it was produced, you have a proofread, not a check. The fix is usually one new browser tab and a paste.

---

## S-15 — I am drowning in repetitive work and cannot see what to fix first

**What it feels like.** "There are twenty things I do over and over. I can see they should all be automated. I have no idea which one to start with, so I have started none of them."

**What is actually happening.** You are trying to prioritise from memory, and memory ranks by annoyance rather than by cost. The task that irritates you most is rarely the one eating the most time, and the one eating the most time is often invisible precisely because it is habitual. Meanwhile a second sorting is missing entirely: some of those twenty are genuinely repetitive — same shape every time, judgment only at the edges — and some just feel repetitive while actually requiring a fresh decision each run. Only the first kind pays back the effort of codifying it.

**The move.** Get interviewed rather than introspecting. Walk through a real week out loud — what you touched, how long each thing took, how often it recurs, and how much of it was a decision versus a procedure — and let the ranking fall out of that. Then take exactly one: the highest frequency multiplied by the least judgment. Build it, use it twice on real work, and only then look at the list again.

**The tool.** [`.claude/skills/grill-me/SKILL.md`](../.claude/skills/grill-me/SKILL.md) to find the candidates, then [`.claude/skills/skillify/SKILL.md`](../.claude/skills/skillify/SKILL.md) to build the one you picked.

**Learn it properly.** [`curriculum/05-skills.md`](../curriculum/05-skills.md), and [`curriculum/11-first-90-days.md`](../curriculum/11-first-90-days.md) for sequencing this over weeks rather than in one heroic afternoon.

**How to spot it next time.** The signature is **a list with no order**. Any time you can name more than three things to fix and cannot say which is first, you are in this situation, and the missing input is always the same: real frequency and real duration, from an actual week rather than from your impression of one.

---

## S-16 — I think I understand this but I am not sure

**What it feels like.** "I read the chapter. It made sense while I was reading it. If someone asked me to explain it in a meeting I think I would manage, but I would not bet on it."

**What is actually happening.** You are experiencing the gap between recognition and recall, and the gap is real. Reading something coherent produces a genuine feeling of understanding — the material is well organised, each sentence follows the last, nothing is confusing — and that feeling is generated by the text doing its job, not by you having acquired anything. The test is not whether it made sense. It is whether you can produce it without the source, in your own words, using your own examples. That last part is the discriminator: an explanation built from the chapter's examples is a memory of the chapter, and an explanation built from your Tuesday meeting is knowledge.

**The move.** Close the file and explain it to someone who is not there — out loud, in your own words, using an example from your own work. Where you go vague, you have found the exact broken link, and it is usually much narrower than "I do not understand this topic". Then repair that one link rather than rereading the chapter.

**The tool.** [`.claude/skills/quiz/SKILL.md`](../.claude/skills/quiz/SKILL.md) for application questions rather than definitions, and [`.claude/skills/grill-me/SKILL.md`](../.claude/skills/grill-me/SKILL.md) when you want it harder.

**Learn it properly.** The four-rung ladder in [`TEACHING-PROTOCOL.md`](./TEACHING-PROTOCOL.md) and the tracker at [`progress/MASTERY.md`](../progress/MASTERY.md), which is deliberately built so that reading something never counts as knowing it.

**How to spot it next time.** The signature is **reaching for the harness's words instead of your own**. If your explanation reuses the phrasing you read — the same metaphor, the same example — you have memorised a sentence. A real explanation is in your vocabulary, about your work, and slightly clumsier than the original.

---

## S-17 — It is doing so much that I have stopped understanding my own work

**What it feels like.** "The output is good and there is a lot of it. But I could not defend most of it if challenged, and I am not sure I could produce any of it on my own now. Nothing is going wrong, which is somehow the worrying part."

**What is actually happening.** Skill comes from doing the difficult part, and the difficult part is what gets delegated first. For a while after you stop doing something you retain the ability to recognise good work in it, and that residual judgment is exactly what makes early delegation feel free. It fades quietly. The dangerous version is specific and worth stating plainly: it is not that you cannot produce the work, it is that your ability to **judge** it degrades — and every other failure in this system is caught by a human who can tell good from bad. If that goes, nothing downstream catches anything, and you will not notice it going, because from the inside a plausible answer and a correct answer feel identical.

**The move.** Draw the line between execution and judgment, and defend the judgment side. Before asking for anything that matters, spend two minutes forming your own view and write it down; then compare, and where you disagree, find out why. Keep one task in each important area that you do unaided, periodically, as a calibration check on yourself rather than for productivity. And apply the hard rule with a clear test: if you cannot explain to someone why the output is right, you do not own it and it should not go out under your name.

**The tool.** [`.claude/skills/grill-me/SKILL.md`](../.claude/skills/grill-me/SKILL.md), pointed at your own recent output rather than at a topic — have it test you instead of tell you.

**Learn it properly.** [F-13, the dependency trap](./FAILURE-MODES.md#f-13--the-dependency-trap), and [`curriculum/13-graduation.md`](../curriculum/13-graduation.md) for what retained competence actually looks like.

**How to spot it next time.** The signature is **the drought of caught errors**. If it has been a long time since you caught the AI being wrong, that is not evidence it stopped being wrong. Combine it with a second signature — volume of output going up while your questions about it go down — and this is what it looks like from the inside.

---

## S-18 — The answer sounds right and I cannot tell if it is hollow

**What it feels like.** "It has the right shape. Headings, a framework, named parts, a confident recommendation. It reads like something an expert would produce, and I asked precisely because I am not the expert."

**What is actually happening.** Fluency, structure and confidence are the surface form of expert work, and that surface is abundant in training data and cheap to reproduce. Correctness is not a separate component that gets attached; it comes along when the topic is well represented and quietly does not when it is not. So the failure concentrates exactly where you cannot personally check — unfamiliar domains, niche subfields, anything you asked about because you did not already know. Worse, the signals you would normally use to judge competence are the same signals the output is best at producing. Related but distinct from [S-03](#s-03--i-cannot-tell-whether-this-is-right): there you had no standard; here you have a suspicion that the structure is load-bearing in appearance only.

**The move.** Probe the structure rather than reading it again. Ask three things: what is the single load-bearing assumption and what collapses if it is false; which parts are standard established material and which are being reconstructed, with the boundary named; and what a practitioner in this field would most likely push back on. Real reasoning can name a falsifier. A plausible shell tends to answer with more shell. Then check two or three specifics yourself, and if the domain matters, get ten minutes from one human who works in it — that is the cheapest check available and there is no substitute for it.

**The tool.** [`.claude/skills/verify-this/SKILL.md`](../.claude/skills/verify-this/SKILL.md), escalating to [`.claude/agents/adversary.md`](../.claude/agents/adversary.md), ideally run on a different model per [`curriculum/17-many-models.md`](../curriculum/17-many-models.md).

**Learn it properly.** [F-07, the plausible-but-wrong structure](./FAILURE-MODES.md#f-07--the-plausible-but-wrong-structure), then [`curriculum/04-verification.md`](../curriculum/04-verification.md).

**How to spot it next time.** The signature is **a framework you cannot trace to a source**. Named categories, tidy tiers, a three-part model — ask where the framework comes from. If it has a source you can open, it is probably real; if it was assembled on the spot to answer you, it may be sound and it may be decoration, and you cannot tell which by reading it more carefully.

---

## S-19 — I need to look back at something I did before

**What it feels like.** "We worked something out a couple of weeks ago and I need it. I do not remember which chat, or what I called it, only roughly what it was about."

**What is actually happening.** You are assuming a shared history that mostly does not exist. An AI generally cannot read your other conversations — each session is its own thing, and while some tools do expose prior sessions to the assistant, most chat interfaces do not. So the honest question is not "can it remember" but "what was written down at the time, and where". This is the same lesson as [S-05](#s-05--i-cannot-find-something-i-know-i-wrote-down) arriving from the other direction: memory that lives in a conversation dies with it, and the only history that survives is history something wrote to a file.

**The move.** Ask for the lookup with what you actually remember — the topic, the rough week, what you were trying to do — and expect to be told which source is being used, because it matters. Native session access, an exported transcript, the harness's own [`progress/SESSION-LOG.md`](../progress/SESSION-LOG.md), or you pasting the conversation back in are four different qualities of answer, and a review built from one-line summaries is not the same thing as one built from a full transcript. Then close the loop: whatever durable thing surfaces, write it to the right progress file so the next lookup is cheap.

**The tool.** [`.claude/skills/recall-session/SKILL.md`](../.claude/skills/recall-session/SKILL.md), which establishes the source tier and says which one it used.

**Learn it properly.** [`curriculum/06-memory-and-second-brain.md`](../curriculum/06-memory-and-second-brain.md), and the capture step in [`SESSION-PROTOCOL.md`](./SESSION-PROTOCOL.md) that makes the log exist in the first place.

**How to spot it next time.** The signature is **needing a decision rather than a conversation**. What you almost always want back is what was decided, what was built, and what was left open — three lines. If those three lines were written down at the end of the session, this situation lasts ten seconds. If they were not, no search technique recovers them.

---

## S-20 — I have plateaued and do not know what to get better at

**What it feels like.** "I am comfortable. The obvious wins are done. I am clearly not as good as I could be, but I cannot see the next thing, and nothing is going badly enough to point at."

**What is actually happening.** Comfort is the plateau. Everything you currently do well was once a thing you did not know to try, and the mechanism that surfaced it — friction, error, being stuck — is exactly what competence removes. So a person plateauing has no error signal to follow, and introspection will not produce one, because you are looking with the same eyes that built the ceiling. The way off is not more effort at what you already do; it is evidence about how you have actually been working, gathered by something that was not you, over a window long enough to show a pattern.

**The move.** Run a structured review of your own practice across specific lenses rather than asking yourself an open question. What did you do more than twice that never became a skill; where did you act on output without checking it, especially anything that went to another person; where did you do by hand something a tool you already own would have done; what did you never try that is well within reach; and which things you once knew have not been used lately and are slipping. Then take one item, do it that day, and mark it. A review that produces a backlog rather than an action has failed.

**The tool.** [`.claude/skills/review-my-work/SKILL.md`](../.claude/skills/review-my-work/SKILL.md), with the cadence argument in [`REVIEW-ROUTINE.md`](./REVIEW-ROUTINE.md) and the history in [`progress/REVIEWS.md`](../progress/REVIEWS.md).

**Learn it properly.** [`curriculum/13-graduation.md`](../curriculum/13-graduation.md) for the checkpoints, and [`progress/MASTERY.md`](../progress/MASTERY.md) for which topics are sitting below the top rung right now.

**How to spot it next time.** The signature is **nothing new in your progress files for weeks**. No skill built, no decision logged, no rung moved, while the work continued as usual. Steady output with a static record is what a plateau looks like from outside. A second signature: the top item of your last three reviews is the same item, which means it is not hard, it is being avoided.

---

## When nothing here fits

Say so rather than forcing a match. A wrong label is worse than no label, because it sends you confidently at the wrong move and you will trust the outcome.

If you are the AI and the learner's situation does not map cleanly:

1. **Say plainly that the catalogue does not cover this**, and do not stretch an entry to reach.
2. **Reason from the five questions instead** — goal, information, checking, conversation, operator. Even when no entry fits, one of those five is usually the source, and naming the bucket is most of the value.
3. **Work it out with them from first principles**: what were they trying to do, what actually happened, what would have had to be true for it to go right, and what is the smallest next action.
4. **Add the new situation to this file** in the same six-part block, numbered from the next free code, once the resolution is known. Write the mechanism you actually found, not a guess. Then add its row to [the index](#the-index) with one of the five buckets, because an entry the index does not list is an entry nobody routes to and the next session will not find it; and if it turns out to be the lived experience of an entry in [`FAILURE-MODES.md`](./FAILURE-MODES.md), add the crosswalk row too. A taxonomy that never grows is a taxonomy that is quietly failing to describe the world.

The block template, for consistency:

```
## S-nn — <the situation in the learner's own words>

**What it feels like.** <first person, their likely phrasing, one short paragraph>

**What is actually happening.** <the mechanism, not a restatement of the symptom>

**The move.** <concrete and immediate, doable in the next few minutes>

**The tool.** <a skill or protocol in this harness, linked by exact filename>

**Learn it properly.** <the chapter, linked by exact filename>

**How to spot it next time.** <the recognisable signature, not the feeling>
```

The "how to spot it next time" line is the one that decides whether an entry is worth having. If it just describes the feeling again, the entry teaches nothing — the learner already had the feeling, that is why they came. It has to name something observable: a phrase that appears, a thing you find yourself doing, a pattern in what you catch and what you miss.

---

## The point of this file

The catalogue is scaffolding. What it is trying to install is the habit of asking, before anything else, **what kind of trouble is this** — goal, information, checking, conversation, or me. Every entry above is a worked example of that question being answered well.

You will know it has worked when you stop opening this file and start naming your own situation mid-sentence: "hold on, this is a done-check problem, not a wording problem." That sentence is the whole skill. Everything here is a rehearsal for it.

---

## Try this now

Do not pick a situation from the index. Start from a real one — the last time this week that working with an AI felt worse than it should have. Then paste this into a session:

```
I want to practise naming the situation I am in rather than reaching for a fix.

Here is what happened: <what you were trying to do, and what actually happened —
two or three sentences, no tidying up>

Ask me the four routing questions one at a time, in order, and wait for my answer
to each: is the problem the goal, the information, the checking, or the conversation
itself. If none of them lands, ask the fifth one — could I still do this myself, and
could I still tell if it were wrong.

Then tell me which bucket you think it is and why, before you tell me any move.
If you think two buckets fit, say both and say which is primary.
```

Answer the questions yourself before you look anything up. Then, and only then, open the index and find the entry. The point is not to be right first time — it is to notice how much of the diagnosis you can do without the catalogue, because that number is what should grow.

## What you should now be able to do

- Name which of the five buckets you are in — goal, information, checking, conversation, or yourself — before you start typing a fix, and say why that bucket rather than a neighbouring one.
- Tell a situation from a failure: whether you need this file, [`FAILURE-MODES.md`](./FAILURE-MODES.md), or both, without guessing.
- Recognise at least three of the signatures from memory — the repeated rejection, "I know I wrote this down somewhere", errors you only ever catch in your own specialty — and act on them before the situation has cost you an afternoon.
- Say plainly when nothing in the catalogue fits, reason it out from the five questions instead, and write the new situation into this file so the next person is not starting from nothing.
