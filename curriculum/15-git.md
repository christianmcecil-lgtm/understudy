# Git

*The undo history for a whole folder — and the single thing that makes it safe to let an AI change your files. Read time: about 20 minutes.*

---

## Start here: the only reason you need to care

You are going to ask an AI to change things. Not one file — a folder. "Reorganize these
notes." "Update every template to use the new wording." "Fix the numbers across all three
documents." It will do it in seconds, across more files than you can read.

And then one of two things is true.

Either you can put it all back exactly the way it was, in one sentence, with total
confidence — or you cannot.

That is the whole subject. Git is the thing that makes the first one true.

Everything else in this file — the vocabulary, the commands, the diagrams — exists to serve
that one sentence. If you take nothing else away: **before an AI touches a lot of files, you
take a snapshot. That snapshot is a floor you can always fall back to.** Without a floor, you
are doing trapeze work without a net and calling it velocity.

There is a second-order effect that matters just as much. When you know you can undo
anything, you stop supervising nervously. You let the AI take a bigger swing. You try the
version you were not sure about. The net is not just protection — it is what lets you work
at the speed the tool is actually capable of. People without a net become cautious, and
cautious is slow, and slow is the thing they were trying to escape.

This connects directly to the trust ladder in
[Safety, privacy, and trust](10-safety-privacy-and-trust.md). The reversibility test asks
"could I undo this myself in under a minute?" Git is how you make the answer yes for an
entire category of work that would otherwise be a no.

---

## Part 1 — What problem git actually solves

Three problems, in order of how much you will care.

**1. Undo, for a whole folder, across time.**
Your word processor has undo for one document, in one session, until you close it. Your
cloud drive has version history, sometimes, for a limited window, one file at a time. Git
gives you an undo history for *every file in a folder at once*, kept indefinitely, where each
point in that history is a coherent moment — the state of everything, together, as it was.

That "together" is the part that matters. If a change spanned six files, half-undoing it is
worse than not undoing it at all. Git's unit of undo is the whole folder at one moment, so
you never end up with three files from Tuesday and three from Thursday.

**2. A record of what changed, when, and why.**
Every snapshot carries a message you wrote. Six weeks later, "why is this paragraph phrased
so oddly" has an answer: you can see exactly when it changed, what it looked like before, and
the note you left about the reason. This is memory for a folder, in the same spirit as
[Memory and the second brain](06-memory-and-second-brain.md) — durable notes outside anyone's
head.

**3. Several people — or several AI agents — working without destroying each other.**
Two people editing the same shared file live is a mess of overwrites. Git lets each work on
their own copy and then combines the results, showing you the places where the two genuinely
conflict rather than silently picking one. That is also how multiple agents working on the
same project stay out of each other's way — the pattern you will meet in
[Subagents and swarms](08-subagents-and-swarms.md).

Note what is *not* on that list. Git is not a backup system — a copy that lives only on your
machine dies with your machine. Git is not cloud storage. Git is not a syncing tool. It gets
paired with those things constantly, which is why people conflate them, but its actual job is
history.

---

## Part 2 — The mental model: snapshots, not diffs

This is the load-bearing idea in the whole file. Get it and the rest of git stops being
confusing. Miss it and every explanation you read afterwards will feel like it has a hole in
it, because it will.

### The wrong model almost everyone starts with

Most people assume git works like tracked changes in a document: it stores a list of
*edits*. Change 4 was "added a paragraph." Change 5 was "fixed a typo." The history is a pile
of edits stacked on each other, and going back means peeling edits off the top.

That model is wrong, and it is wrong in a way that makes everything downstream confusing. If
history is a stack of edits, then going back in time sounds destructive — you would have to
*remove* the edits above you. Branching sounds expensive. Being in two places at once sounds
impossible.

### The right model

**A commit is a snapshot of the entire folder at one moment, with a message attached.**

Not "what changed." The whole thing. Every file, as it stood, at that instant.

The history is a chain of those snapshots, each one pointing back at the one it came from:

```
    snapshot A  <---  snapshot B  <---  snapshot C  <---  snapshot D
    "first        "added the       "fixed the        "rewrote the
     draft"        intro"           numbers"          summary"

                                                          ^
                                                          |
                                                     you are here
```

**You are always standing on exactly one snapshot.** Your folder, right now, as you see it in
your file browser, is that snapshot plus whatever you have edited since. Git knows the
difference between the two, which is why it can always tell you "here is what you have
changed since the last snapshot."

**A branch is just a movable label pointing at one snapshot.** That is genuinely all it is.
Not a copy of the folder, not a separate directory — a sticky note with a name on it, stuck
to one snapshot in the chain. When you make a new snapshot, the label you are standing on
slides forward to the new one. Making a second branch costs almost nothing, because it is
just a second sticky note.

### The analogy — and exactly where it stops being true

The closest everyday thing is **a save file in a video game.**

When you save, the game does not write down "player pressed forward twice, then jumped." It
writes down the entire state of the world at that moment. Later, you load that save and the
whole world comes back exactly as it was. You can keep many saves. You can jump to any of
them.

That analogy carries a lot of weight correctly, and it is the right thing to hold in your
head while you build the habit. But it will start lying to you, and here is exactly where, so
you can drop it before it does damage:

- **Game saves usually overwrite each other or age out. Git snapshots do not.** Every commit
  stays in the history. Making a new one never destroys an old one. This is the most
  important difference and the one that should make you relax: *committing is not risky.* The
  worst case of an unnecessary commit is a slightly cluttered history.
- **Loading a game save throws away the future. Standing on an old commit does not.** In a
  game, loading Tuesday's save means Wednesday never happened. In git, moving to an older
  snapshot leaves every newer snapshot exactly where it was. You are visiting, not rewinding.
  You can walk back to the newest one whenever you like.
- **A game saves the whole world automatically at checkpoints. Git snapshots only what you
  tell it to, when you tell it to.** Nothing is captured until you deliberately commit. Work
  you have not committed is not protected by anything. This is the usual way
  people lose work with git — not by using it wrong, but by not using it yet. The reasoning
  is simple: git can only give back what it was told to keep.
- **Under the hood, git is not literally writing a fresh copy of every file each time.** It is
  clever about storing files that did not change. But — and this is why the snapshot model is
  still the correct one to think with — it *behaves* exactly as if it did. You never have to
  reason about "which earlier version does this depend on." Each commit stands alone as a
  complete picture. The storage trick is an implementation detail you are allowed to never
  think about again.

Now drop the analogy. From here on, think in snapshots.

### What the snapshot model immediately explains

Once you hold this, a pile of git behaviour stops being mysterious:

| The thing that confused you | What the snapshot model says |
|---|---|
| "How do I see what changed between Monday and today?" | Git compares two snapshots and computes the difference on demand. The difference is calculated, never stored. That is why you can compare *any* two points, not just adjacent ones. |
| "Isn't making a branch expensive?" | No. It writes one small label. Nothing is copied. |
| "If I go back, do I lose my recent work?" | No. Those snapshots still exist. You moved where you are standing, not what exists. |
| "Why does it keep asking me what to include?" | Because a snapshot is a deliberate act. Git makes you say which changes belong in this moment of the story. |
| "Why do people say committing is safe?" | Because a commit only ever *adds* a snapshot. It cannot remove one. |

That last row is the one to internalize. Commits are additive. Almost everything genuinely
dangerous in git involves work that was **never committed**.

---

## Part 3 — The words you will hear

You do not need to use these. You need to recognize them when a colleague or an AI says them,
so you are not quietly lost.

| Word | What it actually means |
|---|---|
| **Repository** (repo) | A folder that git is watching. It has a hidden `.git` subfolder holding the entire history. Delete that subfolder and you have deleted the history, not the files. |
| **Commit** | One snapshot, with a message. Used as both noun and verb. |
| **Message** | The note attached to a snapshot. "Rewrote the intro after the client call" is a good one. "update" is not. |
| **Staging** | The waiting room. You pick which changes go into the next snapshot before you take it. This is why some changes are "staged" and others are just "modified." |
| **Branch** | A movable label pointing at one snapshot. The default one is usually called `main`. |
| **Clone** | Making your own complete copy of a repository, history and all, usually from somewhere online. |
| **Remote** | A copy of the repository that lives somewhere else — usually on a hosting service, so it is shared and off your machine. Your local repo knows its address and can exchange snapshots with it. |
| **Push** | Send your snapshots up to the remote. Nothing leaves your machine until you do this. |
| **Pull** | Fetch the remote's snapshots and combine them into yours. |
| **Pull request** | Not a git feature — a feature of the hosting services built around git. It is a formal proposal: "here are my snapshots, please review them and fold them into the main line." It exists so a human reads the change before it becomes official, and it is where review comments and approvals happen. Some services call it a merge request; same idea. |
| **Conflict** | What happens when two people changed the same lines and git will not guess which one wins. It stops and asks a human. |
| **Diff** | The computed difference between two snapshots, shown as lines added and removed. |

Two of those deserve a sentence more.

**A remote** is what turns your personal history into a shared one and, incidentally, into an
off-machine copy. Until you have pushed, your entire history exists in exactly one place. If
that place is a laptop, your history has the same survival odds as the laptop.

**A pull request** is where most workplace friction about code actually lives. If you join a
team that uses one, the thing to understand is that it is a review gate with a conversation
attached — the same idea as never letting the worker grade its own work, from
[Verification](04-verification.md), enforced by process instead of by good intentions.

---

## Part 4 — What to actually say to your AI

You are not going to memorize commands. You are going to describe outcomes, and the AI will
pick the commands. That works well, and it works *because* you have the snapshot model — you
can describe what you want in terms of snapshots and be understood.

These are literal sentences. Say them as they are.

**Setting up, once per folder:**

```
Set this folder up with git. Before you commit anything, create a .gitignore
appropriate for what is in this folder, show me the list, and tell me what you
chose to exclude and why - I want to check that nothing sensitive is about to be
recorded. Then make a first commit that captures everything else as it stands
right now, and tell me in one line what you did.
```

The order there is deliberate, not fussiness. A `.gitignore` is a plain list of things you are
telling git to pretend it cannot see — a file of passwords, a folder of downloads, anything
private or enormous. It has to exist *before* the first commit, because once something has
been captured in a snapshot, getting it back out is a separate and much more annoying job.
Set the fence before you let anything into the field.

**Before you let it loose — the floor:**

```
Before you change anything: commit everything as it stands now with the message
"before <what you are about to do>". Confirm the commit succeeded and tell me
there are no uncommitted changes left. Then do the work.
```

That is the single most valuable sentence in this file. Say it every time you are about to
ask for a large or sweeping change. Make it a reflex.

**Finding out where you stand:**

```
What has changed in this folder since the last commit? Summarize it in plain
English by file - do not show me raw diff output unless I ask.
```

```
Show me the history of this folder for the last two weeks, one line per commit,
in plain English.
```

```
Show me what changed in this file between now and yesterday morning, and explain
the change in words rather than showing me symbols.
```

**Saving a moment:**

```
Commit everything with a message describing what we just did. Write the message
yourself, be specific about the what and the why, and show it to me before you
commit.
```

**Undoing — the ones that will save you:**

```
Put this folder back exactly the way it was at the last commit. I want to throw
away everything uncommitted. Tell me exactly what you are about to discard
before you do it.
```

```
Something has gone wrong. Show me the last ten commits with their messages, then
help me pick the one I want to go back to. Do not change anything until I choose.
```

```
I think I have lost some work. Search the repository history, including commits
that are no longer on any branch, for anything matching <description>. Report
what you find before restoring anything.
```

**The standing instruction worth installing** — put this wherever your assistant reads its
persistent setup, so you stop having to remember it:

```
GIT RULES.

Before making changes across more than a couple of files, check whether this
folder is a git repository. If it is and there are uncommitted changes, commit
them first with a descriptive message and tell me you did. If it is not a
repository, tell me that before you start, so I can decide.

Never discard uncommitted work, force-push, or rewrite history without telling
me exactly what will be lost and getting a yes from me in this conversation.

After any change, tell me the commit message you used, so I know the name of the
floor I can fall back to.
```

---

## Part 5 — The handful of commands worth recognizing

Not to memorize. To recognize when they scroll past, so you know whether something safe or
something destructive just happened.

| Command | What it does | Is it destructive? |
|---|---|---|
| `git status` | Tells you where you are standing and what you have changed since the last snapshot. | No. Reads only. Run it constantly. |
| `git diff` | Shows the actual changed lines. | No. Reads only. |
| `git add` | Puts changes in the waiting room for the next snapshot. | No. |
| `git commit` | Takes the snapshot. | No — it only ever adds. |
| `git log` | Lists the snapshots, newest first, with messages. | No. |
| `git reflog` | **The recovery one.** Lists every position you have stood in recently, including ones no branch points at any more. This is how "lost" commits get found. | No. Reads only. |

`git reflog` is the one worth knowing by name, because it is the answer to the sentence "I
think I destroyed my work." As long as the work was ever committed, it is very probably still
there and reflog is how you find it. It is not permanent — old entries do get cleaned up
eventually — so this is a recovery tool for today's disaster, not an archive. When something
goes wrong, say the word "reflog" to your AI and it will know what you mean.

Four more you should recognize as **potentially destructive**, so that seeing them makes you
slow down and ask: `git reset --hard`, `git checkout --` (or `git restore` used to discard),
`git clean`, and `git push --force`. The first three throw away uncommitted work. The fourth
rewrites shared history. None of them are wrong to use — but if an AI is about to run one,
you want it to tell you first, which is exactly what the standing instruction above forces.

---

## Part 6 — What is genuinely hard to undo, and what only looks scary

Beginners are usually frightened of the wrong things. Here is the honest split.

### Genuinely hard or impossible to undo

- **Work you never committed, then discarded.** This is the big one and it is almost the only
  one. Git cannot restore a state it never captured. Most git horror stories, once you get to
  the bottom of them, turn out to be this one wearing a costume.
- **Deleting the hidden `.git` folder.** That folder *is* the history. Removing it leaves your
  current files intact and every previous snapshot gone.
- **A secret you committed and pushed.** You can remove it from the current files easily and
  from the history with effort, but if it reached a shared remote, assume other people and
  other systems have already copied it. The correct response is to treat the secret as
  compromised and rotate it, not to try to erase the past. See
  [Safety, privacy, and trust](10-safety-privacy-and-trust.md) — and this is exactly why the
  `.gitignore` file in Part 4 matters. Ask your AI to set one up on day one, before there is
  anything sensitive to leak.
- **Force-pushing over shared history that other people were building on.** Recoverable in
  principle, genuinely painful in practice, and the reason that command has a reputation.

### Looks alarming, is fine

- **"Your branch is ahead of 'origin/main' by 3 commits."** Purely informational. You have
  three snapshots you have not pushed. (`origin` is just the default name for your remote,
  and `main` the default name for the branch — the sentence is saying "your copy has three
  snapshots the shared copy does not.")
- **"detached HEAD state."** Terrifying name, harmless meaning: you are standing on a snapshot
  directly rather than on a branch label. Nothing is broken and nothing is lost.
- **A merge conflict.** Git found two changes to the same lines and refused to guess. It is
  asking a question, not reporting damage. Nothing has been destroyed.
- **A commit with a bad message, or one you regret.** Fixable. History can be adjusted, and
  even when it cannot be, a new commit that reverses the old one is a completely normal thing
  to do.
- **Too many commits.** Not a problem. A cluttered history costs you nothing; a missing one
  costs you the work.

### Which is why "commit early, commit often" is the actual beginner advice

It is not a style preference. It follows directly from the split above. Committing is on the
safe list and can only add. Not committing is what puts you on the dangerous list. Every
minute of work you have not snapshotted is work with no floor under it.

Small, frequent commits also give you a *precise* undo. If your last snapshot was three days
and forty changes ago, going back to it costs you three days. If it was twenty minutes ago,
going back costs you twenty minutes. The frequency of your commits sets the resolution of
your undo.

### The rule, stated once

> **If an AI is about to change a lot of files, you commit first.**

Not "you should probably." Every time. It costs one sentence and about two seconds, and it
converts an irreversible action into a reversible one, which is the exact move the
reversibility test in [Safety, privacy, and trust](10-safety-privacy-and-trust.md) asks you
to make.

---

## Part 7 — What this file deliberately does not teach

Three things get named here and then dropped on purpose. You will hear all three. You should
know they exist and know you are choosing not to learn them yet.

**Branching strategy** — the team conventions about which branches exist, who may write to
which, and how work flows between them. Skipped because it is entirely a social agreement,
not a git feature. Every organization's is different, and yours will be explained to you by
the people who made it up. Learning someone else's convention in advance teaches you nothing
transferable.

**Rebasing** — rewriting a sequence of snapshots into a tidier sequence. Skipped because it
is the one common operation that genuinely changes history rather than adding to it, which
makes it the one place where a confident beginner can do real damage. It is also almost
always optional. When a team requires it, ask your AI to walk you through that specific case
at that specific moment.

**Merge conflict resolution** — deciding, line by line, which version wins when two changes
collide. Skipped because it is a mechanical skill that is much easier to learn with a real
conflict in front of you than in the abstract, and because it is one of the things an AI is
genuinely good at helping with in the moment. The right sentence when it happens is: *"I have
a merge conflict. Explain what the two versions are trying to do in plain English, tell me
which one I probably want and why, and wait for me to choose."*

The reason for cutting all three is the same, and it is worth stating plainly: **your goal is
a mental model good enough to direct an AI, not a command repertoire.** Adding these three
would triple the volume of this file and would not improve a single decision you actually
make. When you need them, you will need one of them, once, with a real situation in front of
you — and that is the cheapest possible moment to learn it. Everything in Parts 2 and 6, by
contrast, changes how you behave starting today.

If you later find yourself doing git work daily, learn them properly then. The model you have
from Part 2 will make all three straightforward, which is precisely why the model came first.

---

## Part 8 — Where this fits

Git is a floor, not a verification system. It tells you what changed and lets you undo it. It
does not tell you whether the change was any good — that is
[Verification](04-verification.md), and the two are complements. A clean history of unverified
changes is a well-documented mess.

Git lives at the command line, which means it sits next to
[The terminal](16-the-terminal.md). But it is one of the clearer cases where you genuinely do
not need the terminal: graphical git clients exist, many editors have git built in, and asking
your AI in plain English works fine. Do not let anyone tell you that typing the commands
yourself is the real version.

And when you start running more than one AI tool against the same folder — the pattern in
[Running many models side by side](17-many-models.md) — git stops being merely useful and
becomes the thing holding it together. It is how you can tell which agent changed what, and
how you undo one of them without undoing the others.

---

## Try this now

This works whether or not you have git installed, and whether or not you have ever opened a
terminal. It is deliberately written so that "it is not installed" is a successful outcome,
not a dead end.

Copy this whole block into your AI.

```
I am learning git. I may or may not have it installed - find out rather than
assuming, and do not give me install instructions for an operating system I have
not confirmed.

Step 1. Check whether git is installed on this machine and tell me plainly: yes,
with the version, or no. If you cannot check directly, tell me the one thing to
type to find out and what each possible answer means.

Step 2. If it is NOT installed: ask me which operating system I am on, wait for my
answer, and only then give me the install steps for that one. Tell me roughly how
long it takes and whether it needs admin rights. Do not guess my operating system.

Step 3. Whether or not it is installed, explain to me what setting up git on a
folder would actually do: what gets created, what gets recorded, whether anything
leaves my machine, and what I would be able to do afterwards that I cannot do now.
Be specific about the "nothing leaves your machine until you deliberately send it"
part, because I want to understand the privacy position.

Step 4. Ask me to name one folder of my own real work that would benefit from
having a history - something I edit repeatedly, where an older version has ever
been useful. Push back if my answer is vague.

Step 5. Then test my understanding, one question at a time, waiting for each
answer:
  a. In your own words, what is a commit - and name one moment in your own work
     in the last month where having one would have changed what you did?
  b. If I go back to a snapshot from last Tuesday, what happens to the work I did
     on Wednesday?
  c. I am about to ask you to rewrite forty files. What should I say to you first,
     and why?
For each answer, if I am fuzzy, do not re-explain the whole thing - ask me one
narrower question to find the exact part I have wrong, fix only that, then ask me
again.

Finally, tell me the one thing about git I am most likely to get wrong in my first
month, given what my answers revealed.
```

If it comes back saying git is already installed, go one step further and say: *"Good. Set up
git on that folder I named, write the `.gitignore` first and show it to me, then make the
first commit, and show me what `git status` says before and after so I can see the
difference."*

---

## What you should now be able to do

- Explain why git is the thing that makes it safe to let an AI change many files at once, and
  say the one sentence that puts a floor under any large change before it starts.
- Describe a commit as a snapshot of the whole folder rather than a list of edits, and use
  that model to predict git's behaviour — why branches are cheap, why going back does not
  destroy the future, and why committing can never lose work.
- Recognize the vocabulary you will hear at work — repository, commit, branch, remote, push,
  pull request, conflict — and ask for what you want in plain English without knowing a single
  command.
- Tell the difference between the four things in git that are genuinely hard to undo and the
  five that only sound alarming, and stop being frightened of the wrong ones.
- Know exactly which parts of git you have not learned, why that was the right call, and the
  sentence to say when one of them finally shows up.

---

Next: [The terminal](16-the-terminal.md) — what it is, why it matters here, and the honest
case against it.
Then: [Running many models side by side](17-many-models.md) — where a version history stops
being optional.
