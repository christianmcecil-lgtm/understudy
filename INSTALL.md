# Install

*How to get this folder into your AI, for three different setups. Find your setup, read only that section. Read time: 5 minutes.*

## Two things first

Both of these apply to every setup below.

**1. Open a brand new, empty conversation.** Not the one you already have going. Whatever is
already in that conversation gets re-read by the AI on every single turn, and it will compete
with the teaching for room and attention. Start clean.

**2. Use the mid tier for lessons, and the top tier for your first session.** Nearly every
assistant offers three engines — a small fast one, a mid one, and a top one. The names change
constantly; the three tiers do not. [`BOOTSTRAP.md`](BOOTSTRAP.md) covers this properly in the
section headed *Before you paste: which model*, including when the top tier is worth it and why
a second opinion needs a different vendor rather than a stronger model. Read it there — this page
is about getting the folder installed.

**Find out what your tiers are actually called**, because the names move and the sections below
refer to switching between them. Paste this in:

```
What models can you run as? List them cheapest to most capable, tell me
which one is your mid tier, and tell me how to switch between them.
```

---

## Which one are you?

| If this sounds like you | Read |
|---|---|
| You have an AI that runs on your computer and can read a folder of files (a command-line or desktop coding agent). | [Setup A](#setup-a--an-ai-that-reads-a-folder-on-your-computer) |
| You use an AI in a browser or app that has "Projects" (or similar), custom instructions, and file upload. | [Setup B](#setup-b--a-chat-app-with-projects-and-file-upload) |
| Something else, or you are not sure what you have. | [Setup C](#setup-c--any-other-assistant) |

Then everyone does [Did it work?](#did-it-work) at the end.

---

## Setup A — an AI that reads a folder on your computer

This is the setup the harness was built for. Everything in it works.

**1. Put the folder somewhere sensible.** Wherever you keep work files is fine. Two things to
avoid: a temporary or downloads folder that you will clear out, and a path you cannot easily
type. Keep the folder name simple, with no spaces if you can help it.

**Keep it separate from anything you already have.** Do not merge these files into a project
that already has a `CLAUDE.md`, a `.claude/` folder, or its own skills and agents. The names in
here are deliberately ordinary — `/learn`, `/quiz`, `/coach`, `/handoff`, a teacher, a scout, a
reviewer, a verifier, an adversary — so if you already have something by one of those names,
merging the two means one version shadows or replaces the other, and nothing tells you which
one won. Kept separate, there is no collision and nothing of yours is touched.

**2. Open your AI so that this folder is the folder it is working in.** Most command-line
agents adopt whatever folder you launched them from, so the usual move is: open a terminal,
move into this folder, then start the AI. Desktop agents usually ask you to pick a project
folder when you open them — pick this one. If you are not sure whether it worked, the check at
the end of this file will tell you.

Most folder-reading agents switch model with a command or a setting rather than a menu — this is
one of the three occasions above, since the AI is about to read the whole folder, so run it on
the top tier and drop back to the mid tier afterwards.

**3. Say this, exactly:**

```
Read CLAUDE.md in this folder, then curriculum/00-orientation.md.
Follow them from now on. Then tell me, in five lines, what changed about
how you will work with me.
```

**4. Then say this:**

```
/whats-possible
```

If instead of answering it tells you to stop and open a brand new conversation, that is not a
fault — it means it read more of the folder than the two files you asked for, and a session
carrying the whole folder is supposed to hand off. Do what it says, using
[BOOTSTRAP.md](BOOTSTRAP.md), which is where this section ends up anyway, and run
`/whats-possible` once the new conversation is going.

**What is happening underneath.** This folder contains a `.claude/` folder with two things
inside it: `skills/` and `agents/`. An AI running in this folder picks both up on its own — you
do not install anything, and you do not point it at them.

- `.claude/skills/` holds named procedures. You run one by typing a slash and its name:
  `/whats-possible`, `/learn`, `/verify-this`, `/skillify`, `/grill-me`, `/handoff`, `/quiz`,
  `/coach`, `/im-stuck`, `/review-my-work`, `/recall-session`. The name is the folder name under
  `.claude/skills/`, so if you ever add one of your own, that is how you name it.
- `.claude/agents/` holds specialists the AI calls on its own — a verifier, an adversary, a
  scout, a teacher, a reviewer. You will rarely name these yourself.

`CLAUDE.md` in the top of this folder is the file the AI reads first and treats as standing
instructions. If you want to change how it behaves with you permanently, that is the file to
change — ask the AI to change it and say why.

Now go to [Did it work?](#did-it-work). Once that check passes, open
[BOOTSTRAP.md](BOOTSTRAP.md) and paste its ignition prompt into a brand new conversation. That
is where the teaching actually starts, and the new conversation is deliberate — BOOTSTRAP.md
explains why, in the section headed "Why a brand new session".

---

## Setup B — a chat app with Projects and file upload

**1. Make a project.** Look for something like "Projects", "Spaces", or "Custom GPTs" in your
app — a container that holds instructions and files across many conversations. Make one and
call it something you will recognise, like "Harness". Make a *new* one rather than reusing a
project you already work in: this folder brings its own standing instructions and its own set
of named procedures, and it should not be sitting on top of a setup you have already tuned. If
a name in here matches one you already use, one of the two quietly wins and nothing tells you
which.

**2. Give the project its instructions.** Look for a box called something like "custom
instructions", "project instructions", or "system prompt". **Before you paste anything into
that box, copy out whatever is already in it** and keep it somewhere — a note, a text file,
anywhere. Pasting replaces what was there, and there is usually no undo. Then open `CLAUDE.md`
from this folder in any text editor, copy all of it, and paste it in. That file is what turns a
normal assistant into this one, so if you only do one thing, do this.

**3. Upload the files.** Look for something like "Add files", "project knowledge", or a
paperclip. Upload as much of the folder as it will accept. If there is a limit, upload in this
order and stop when you run out of room:

1. `curriculum/00-orientation.md`
2. `protocols/VERIFICATION-PROTOCOL.md` and `protocols/DONE-CHECKS.md`
3. `reference/GLOSSARY.md` and `reference/PROMPT-PATTERNS.md`
4. The rest of `curriculum/`, lowest numbers first
5. The `.claude/skills/` files, if it will take folders

Some apps will not accept a folder, only individual files. If yours is like that, drag the
files in a batch at a time. Some apps also cannot see files inside folders that begin with a
dot, like `.claude/` — if that is the case, do not fight it, see step 5.

**4. Start a conversation in that project and say this, exactly:**

```
Read the project instructions and 00-orientation.md, then follow them from
now on. Then tell me, in five lines, what changed about how you will work
with me.
```

The model picker in a chat app is usually near the message box or at the top of the conversation,
and is usually set per conversation, so switching tier between lessons costs you nothing.

**5. Ask for skills by name instead of typing slashes.** Be aware of this one honestly: in most
chat apps, typing `/whats-possible` will not run anything. The slash is a feature of AIs that
read a folder, not of chat apps. It may do nothing, or it may open the app's own menu.

Instead, ask for the procedure in words. This wording works:

```
Run the whats-possible procedure on me now, following the instructions in
.claude/skills/whats-possible/SKILL.md. If you cannot see that file, tell me
and I will paste it.
```

Swap in `learn`, `verify-this`, `skillify`, `grill-me`, `handoff`, `quiz`, `coach`, `im-stuck`,
`review-my-work`, or `recall-session` for any of the others. If it says it cannot see the file,
open `.claude/skills/whats-possible/SKILL.md` in a text editor, paste the contents into the chat,
and say "follow this now." That always works.

**6. Know where your progress lives.** A chat app usually cannot write files back to your
computer. So when the AI produces something that belongs in `progress/` — what you learned, a
skill you built, a decision you made — it will show it to you and you paste it into the file
yourself. Ask for it in this form:

```
Give me the exact text to add to progress/LEARNER.md, formatted so I can
paste it straight in.
```

Now go to [Did it work?](#did-it-work). Once that check passes, open
[BOOTSTRAP.md](BOOTSTRAP.md), start a brand new conversation inside your project, and paste its
ignition prompt — where it asks for the folder location, write "the files uploaded to this
project" instead of a path. That is where the teaching starts. If the project cannot see the
harness files at all, use the version in BOOTSTRAP.md headed "If your AI cannot read files"
instead.

---

## Setup C — any other assistant

Use this if you have an assistant that is not a folder-reading agent and does not have
projects. It still works. It is just more manual.

You may not have a model picker at all here, so this is where the tier question in
[Two things first](#two-things-first) earns its keep: ask it, see which of the three tiers it
says it is running as and whether you can change it, and if the answer is that you cannot, carry
on with what you have — one topic per session matters more when you cannot pick the engine.

**1. Paste `CLAUDE.md` as the standing instruction.** Open `CLAUDE.md` from this folder in a
text editor and copy all of it. If your assistant has a settings field called something like
"custom instructions", "system prompt", or "personality", paste it there — but **copy out
whatever is already in that field first** and save it somewhere. Whatever you had in there is
replaced, not added to, and most apps will not give it back. The same goes for any procedure or
persona you have already set up under a name this folder also uses: yours may end up shadowed,
so keep a copy of it before you start. If your assistant has no such field, paste `CLAUDE.md`
as the first message of every new conversation, above whatever you were going to ask — which
changes nothing you already have.

**2. Paste files as you need them, not all at once.** Start with
`curriculum/00-orientation.md`. After that, paste only the one file that matches what you are
doing — `curriculum/04-verification.md` when you want it to check something,
`protocols/DONE-CHECKS.md` when you are defining what finished means, and so on. Pasting the
whole curriculum at once will crowd out your actual work; there is a whole file about why
(`curriculum/02-the-context-window.md`).

**3. Say this, exactly:**

```
Everything above is your standing instruction. Follow it from now on. Then
tell me, in five lines, what changed about how you will work with me.
```

**Be honest with yourself about what you lose.** Features vary a lot between assistants, and
some of this harness assumes capabilities yours may not have:

| May not work | What to do instead |
|---|---|
| Writing files (so `progress/` cannot update itself) | Ask for the exact text to paste, and keep the files yourself in any notes app. |
| Separate specialist agents (the verifier, the adversary) | Open a second, fresh conversation, paste only the output plus `protocols/VERIFICATION-PROTOCOL.md`, and ask it to find what is wrong. A fresh conversation that did not do the work is a genuine second checker. |
| Slash commands | Paste the contents of the matching `SKILL.md` file and say "follow this now." |
| Reading your real systems | Paste the data in by hand, and be deliberate about what you are pasting. |

**What still works without any of that**, and it is most of the value: the mental models, the
verification habit, the done-check discipline, the prompt patterns in
`reference/PROMPT-PATTERNS.md`, the hype ledger, and the practice of keeping your own notes
outside the conversation. Layers 1 and 2 — the two that matter — are habits before they are
features.

Now go to [Did it work?](#did-it-work). Once that check passes, open
[BOOTSTRAP.md](BOOTSTRAP.md) and use the version headed "If your AI cannot read files" — it is
written for exactly this setup, and it tells you what to paste in at the start of a session and
what to save back out at the end so your progress survives. If you already pasted `CLAUDE.md` as
the standing instruction in step 1, skip that line of it and paste the rest.

---

## Did it work?

Ask this. It is a question the AI cannot answer correctly from general knowledge — only from
having actually read the folder.

```
Without guessing or searching the web: name the layers of the stack this
folder teaches, bottom to top. Say which two it claims carry most of the
value, and tell me exactly what it says about whether that split is a
measured number.
```

**A correct answer** names the layers from the bottom up — engine, then skills and loops, then
memory and state, then interface, then distribution — says that skills and loops plus memory
and state (layers 1 and 2) carry most of the value, and then says plainly that this is a claim
about priority rather than a measurement, and that nobody should hand you a percentage for it.
That last part is the real test. An AI that answers with a confident percentage is inventing it:
this folder deliberately refuses to give one, so a number is proof it has not read the file.

If you want a second, quicker check:

```
Which file in this folder should I read before I connect you to real work data?
```

The answer should be `curriculum/10-safety-privacy-and-trust.md`.

---

## If something is wrong

**It has not read the files.** Symptom: it answers the check question with a plausible-sounding
stack it clearly invented, or asks you what folder you mean. Fix: name files explicitly rather
than gesturing at the folder — "Read the file CLAUDE.md, then read curriculum/00-orientation.md,
then answer." If it says it cannot find them, it is not seeing your folder at all: check that
the folder you opened the AI in is the one containing `README.md` and `CLAUDE.md`, and in a
chat app, check the files actually finished uploading. Worst case, paste `CLAUDE.md` into the
chat directly — that always works, in every setup.

**It read them and is still being generic.** Symptom: correct answer to the check question,
then it goes straight back to cheerful summaries with no evidence and no teaching. This is
normal and it is fixable. Say:

```
You are not following CLAUDE.md. For the rest of this conversation: teach
while you answer, tell me when you are uncertain, and show me what you
checked before you tell me something is done. Confirm you will.
```

If it drifts again later in a long conversation, that is a context problem, not disobedience —
start a fresh conversation. `curriculum/02-the-context-window.md` explains why, and the
`/handoff` procedure exists to make the switch cheap.

**It tells you to open a brand new conversation.** Symptom: it reads the folder, proves what it
read, and then says not to continue there — open a new conversation and paste the ignition
prompt. That is correct behaviour, not a fault. The session that just read the whole harness is
carrying the whole harness, and every later turn re-reads it. Do what it says:
[BOOTSTRAP.md](BOOTSTRAP.md) has the prompt, and explains the reason.

**Slash commands do nothing.** Symptom: you type `/whats-possible` and it either does nothing
or the app's own menu appears. This is expected outside folder-reading agents. Ask for the
procedure by name instead:

```
Run the whats-possible procedure on me now, following the instructions in
.claude/skills/whats-possible/SKILL.md. If you cannot see that file, tell me
and I will paste it.
```

If it cannot see the file, open `.claude/skills/whats-possible/SKILL.md` in a text editor,
paste its contents in, and say "follow this now."

---

Once the check passes, go to [BOOTSTRAP.md](BOOTSTRAP.md), open a brand new conversation, and
paste its ignition prompt. That is the start of the course, and it is the step everything else
here was setting up for. If you would rather poke around than be taught, run `/whats-possible`
instead and use the map in [README.md](README.md) to pick what you read.
