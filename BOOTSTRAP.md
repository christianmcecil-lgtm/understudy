# BOOTSTRAP — start here

*The one page that turns this folder into a teacher. Four minutes to read, and most of that is copying one block of text.*

You have been handed a folder. It is not a course you sit down and read. It is a set of
instructions for an AI, which then teaches you — one topic at a time, tracking what you
actually know, and quizzing you on the things you learned last month.

Three steps. No theory yet.

1. **Put the folder somewhere your AI can read it.** If you are unsure how, open
   [`INSTALL.md`](INSTALL.md) — it covers a browser, a desktop app, and a terminal.
2. **Open a brand new conversation.** Not one you have already been chatting in. Not the one
   that has been poking around inside this folder. A new, empty one. The reason is below, and
   it is your first lesson.
3. **Copy the ignition prompt below, fill in the one blank, and paste it as your first
   message.** That is the whole setup.

---

## The ignition prompt

Paste this whole block. The only thing you change is the line in angle brackets.

```
You are my teacher for a system called Understudy. It lives in this folder:

  <the folder location — the folder that contains README.md and CLAUDE.md>

Read exactly these four files from that folder, in this order, and nothing else
yet: CLAUDE.md, protocols/TEACHING-PROTOCOL.md, progress/LEARNER.md,
progress/MASTERY.md. Do not open the curriculum folder — we will open one
chapter later, when we need it.

Then run the section of protocols/TEACHING-PROTOCOL.md called "First-session
opening", exactly as written. The short version: you are my teacher, harness and
verifier. I am not technical. One topic per session. You never mark a topic
learned until I have explained it back in my own words AND used it on my own
real work.

Start me at the right place on the mastery track, not at topic 1 by default. If
progress/MASTERY.md has progress in it, resume there. If it is blank, ask me one
question about my actual job and pick the entry point from my answer.

This is already the fresh session BOOTSTRAP.md asks for, so teach me here — do
not send me to another new session. Do not lecture. Your first reply should be
short, should say where I am on the track, and should end with a question.

If you cannot open files at all, say so plainly instead of guessing, and tell me
to use the no-file-access version in BOOTSTRAP.md.
```

---

## The returning prompt (the one you will use most)

The prompt above is for your first session only. Every session after that, paste this:

```
Continue teaching me Understudy, in this folder:

  <the folder location>

Read CLAUDE.md, protocols/TEACHING-PROTOCOL.md, progress/LEARNER.md and
progress/MASTERY.md. Nothing else yet.

Then: quiz me on one or two topics I already passed, before we start anything
new. Tell me where I am on the track. Then pick up at the next topic. One topic
this session, no more. Teach me in this session — do not send me to a new one.
```

Keep it somewhere you can reach in five seconds — a note, a pinned message, a text file. The
friction of finding it is the main reason people stop.

---

## If your AI cannot read files

Some setups are chat-only: you can paste text in, but the AI cannot open a folder on your
machine. This still works. Here is exactly what is lost and what to do.

**What is lost:** the AI cannot update `progress/MASTERY.md` or `progress/LEARNER.md` on disk.
That means your record does not survive on its own — you have to carry it between sessions by
hand. Nothing else about the teaching changes.

**The workaround:** paste the files in at the start, and take the updated tracker back out at
the end. Every session.

```
You are my teacher for a system called Understudy. You cannot read my files, so
I am pasting in the parts you need.

[paste the full contents of CLAUDE.md]

[paste the full contents of protocols/TEACHING-PROTOCOL.md]

[paste the full contents of progress/MASTERY.md]

Run the "First-session opening" section of the teaching protocol and follow it
exactly. Teach me one topic, here, in this session — do not tell me to open a
new one, because I would only have to paste all of this in again. If you need a
curriculum chapter, tell me the exact filename and I will paste it in.

At the very end of this session, print the complete updated progress/MASTERY.md
back to me in one code block, so I can save it over my copy. Print the whole
file, not a summary of what changed — a summary is not something I can save.
```

Then actually save it. A tracker you did not paste back is a tracker that resets, and a course
with no memory of what you already know will teach you topic one forever.

If your tool has a project or workspace that holds uploaded files, upload this folder there
instead — that is closer to the full experience, and [`INSTALL.md`](INSTALL.md) explains it.

---

## Why a brand new session

This is your first lesson, and you are already inside it.

An AI has no memory between turns. Every time it replies, it re-reads the entire conversation
from the beginning — every file it opened, every wall of text it printed, everything you both
typed. That re-read is what it thinks with.

So a session that has just read this whole folder is now carrying the whole folder. Every later
turn re-reads all of it. It costs more, it is slower, and — the part that actually hurts — the
thing that matters most in the room, which is you, is competing for attention with a hundred
pages of documentation about how to teach you.

A fresh session that loads only the rules, your record, and your tracker is a clean desk.

That is the entire idea behind [`curriculum/02-the-context-window.md`](curriculum/02-the-context-window.md),
and you just used it before anyone explained it to you. When your teacher gets to that chapter,
tell it you already did this. It will connect faster than the explanation would have.

---

## How to tell it worked

A correctly ignited session does four things in its first reply, and only those four:

- It **names the files it loaded** in one line, and says it loaded nothing else. Four filenames,
  not forty. This is the cheapest proof you have that it read rather than improvised.
- It greets you **briefly**. Two or three sentences at most.
- It **tells you where you are on the mastery track** — either the topic it is resuming, or
  that the track is blank and it needs one answer from you first.
- It **asks you a question** and stops.

That is the whole signature. Accounted for, short, oriented, ends with a question.

**It did not read the harness if** its first reply explains what AI is, gives you a tour of the
folders, lists the five layers of anything, summarises the curriculum, or produces several
paragraphs before you have said a word. Any of those means it is improvising from general
knowledge rather than following the files. Stop it and paste:

```
Stop. You did not follow the ignition prompt. Read CLAUDE.md,
protocols/TEACHING-PROTOCOL.md, progress/LEARNER.md and progress/MASTERY.md
from the harness folder, and nothing else. Say which files you loaded, then run
the "First-session opening" section of the teaching protocol exactly as
written, and give me a short reply that ends with a question.
```

---

## Troubleshooting

| What happened | What it means | What to do |
|---|---|---|
| "I cannot find that folder" / "I do not have access to files" | Either the path is wrong or your tool genuinely has no file access | Check the path first by asking it to list what is in the folder. If it truly cannot read files, use the no-file-access version above. |
| "`progress/MASTERY.md` does not exist" | The tracker has not been created yet, or you are working from a partial copy | Tell it: `Create progress/MASTERY.md from the format described in protocols/TEACHING-PROTOCOL.md, with everything unmarked, then carry on.` If it cannot write files, keep the tracker in a note of your own. |
| It reads the files and then tells you to open *another* new session and paste the prompt again | It has picked up the harness's own first-contact handoff and applied it to a session that is already the fresh one | Say: `This is the fresh session. Do not hand off again — run the "First-session opening" section here.` If it loops a second time, it is not following the files; use the correction prompt above. |
| It starts teaching in the same session that read the whole folder | It skipped the handoff step | Do not continue there. Open a new session and paste the ignition prompt. You will get sharper answers immediately, and that difference is the lesson. |
| It teaches three topics in one sitting and you feel great | You have been shown three things and taught none | Say: `Stop. One topic per session. Go back to the first one and make me use it on my own work.` Coverage is not learning, and the tracker is about to lie to you. |
| It marks something learned that you could not explain to a colleague | It graded exposure instead of understanding | Say: `Un-check that. I cannot explain it yet.` A tracker that only goes up is a tracker you cannot trust. Your teacher is required to accept this. |

---

## Where the rest of it is

You do not need any of this to start. It is here for when you want it.

- [`README.md`](README.md) — what this folder is, and the reading order if you would rather read
  than be taught.
- [`CLAUDE.md`](CLAUDE.md) — the rules your AI is operating under. Worth reading once, so you can
  tell when it is not following them.
- [`protocols/TEACHING-PROTOCOL.md`](protocols/TEACHING-PROTOCOL.md) — how the teaching works,
  including exactly what evidence is required before anything gets marked as learned.
- [`progress/MASTERY.md`](progress/MASTERY.md) — your report card. Open it any time. It is yours,
  it is plain text, and you are allowed to argue with it.

Go paste the prompt.
