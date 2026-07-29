# The Terminal

*What the terminal actually is, the honest case for and against it, and the six things you need to know so it stops being scary. Read time: about 20 minutes.*

---

## Start here, because this chapter is easy to misread

A lot of writing about the terminal is written by people who love it, for people who already
use it. That writing has a tone: the terminal is powerful, the terminal is real computing,
clicking is for amateurs. Some of it is true. The tone is not.

Here is the position this chapter is going to land on, stated up front so you can hold the rest
of it against this sentence:

> **You need enough terminal to not be afraid of it. You do not need mastery, and pursuing
> mastery is a bad use of your first year.**

"Enough" is a specific, finite list. Six things. You can have all six inside an hour, and after
that the terminal stops being a wall and becomes a room you can stand in while someone more
qualified does the work.

The rest — the flags, the pipes, the scripting, the thousand small utilities — is real
knowledge that some people need. You can ask for it, one command at a time, at the moment you
need it, forever. That is a legitimate way to operate and it is not cheating.

---

## Part 1 — What it actually is

A terminal is a window where you type an instruction to your computer as text, press enter, and
get text back. That is the whole idea.

Everything else on your computer is a picture drawn over the top of that same machinery. When
you drag a file into a folder, some software translates your drag into an instruction. The
terminal is you skipping the picture and giving the instruction directly.

### Three words people use interchangeably, and the difference that matters once

| Word | What it actually means | Why you care |
|---|---|---|
| **Terminal** | The window. The application you open. It draws text and takes your keystrokes. | This is what you launch. |
| **Shell** | The program running inside that window that reads your typed line and decides what to do with it. | Different shells understand different wording. This is the one that causes confusion. |
| **Command line** | The line you type on, and loosely, the whole way of working. | Just a name for the activity. |

The distinction matters exactly once, and then it matters constantly: **two people can open a
terminal that looks identical and be running different shells, which understand different
commands.** That is the single most common reason a command someone gave you does not work on
your machine. Hold that thought — Part 8 is about it.

### The shape of a command

Almost every command you will ever see has the same three parts:

```
<name>   <options>   <what to act on>
```

- The **name** is the program you are running.
- The **options** (also called flags or switches) modify how it behaves. They usually start
  with one or two dashes.
- The **target** is usually a file or a folder path.

You do not need to know the names. You need to recognize the shape, because it is how you will
spot a dangerous command in Part 6 without knowing what it does. Danger in a command line
usually lives in the options and the target, not in the name.

### The prompt, and why it looks like noise

Before you type, the shell prints something like a folder name, a machine name, and a symbol.
That is the **prompt**. It is the shell telling you who and where it thinks you are. It looks
like decoration. It is not — it is the answer to "where am I," which is one of your six things.

---

## Part 2 — The honest case for it

Five reasons, in the order they will actually matter to you.

**1. The most capable agent tools live there.** The AI setups that read a whole folder, run
things, check their own work, and act without you supervising every keystroke are usually
command-line programs. Browser and desktop assistants are excellent and improving, but if you
want the full version of what this harness teaches, at some point you will start one from a
terminal. See [Install](../INSTALL.md).

**2. It composes.** In a graphical app, features exist only if someone built a button for them.
On a command line, small programs hand their output to each other, so you can build a thing
nobody anticipated out of pieces that already exist. This is a genuine structural advantage and
it is why the terminal has outlived every prediction of its death.

**3. It repeats exactly.** A command is a piece of text. Text can be saved, pasted, put in a
file, run again next Tuesday, and sent to a colleague who will get the same result. A sequence
of clicks cannot be. This is the same argument as [Skills](05-skills.md): the value is in the
thing you can run again, not in the thing you did once.

**4. A command is a receipt.** When an AI tells you it did something, "I updated the files" is
an assertion. "I ran this exact command and here is the exact output" is evidence. The terminal
produces evidence by default, which makes it the natural home of everything in
[Verification](04-verification.md). Half the reason to be comfortable here is so you can read
receipts rather than take somebody's word.

**5. You can watch.** When an agent works in a terminal, you can see each thing it decides to
do, usually before it does it. That visibility is how you build calibrated trust rather than
hopeful trust — see the trust ladder in
[Safety, privacy, and trust](10-safety-privacy-and-trust.md). A pretty interface that shows you
a spinner and then says "done" gives you nothing to trust or distrust.

---

## Part 3 — The honest case against it

This section gets equal weight, because a chapter that oversells the terminal to someone who
has never used one is a chapter that gets them hurt.

**1. It is unforgiving in a specific way: there is often no undo and no confirmation.** A file
deleted through your file manager usually goes to a recycle bin or trash. A file deleted from a
terminal frequently does not — it is unlinked, immediately, with no dialog, no "are you sure,"
and no five-second grace period. The terminal's design assumption is that you meant what you
typed. That assumption is load-bearing and it is not on your side while you are learning.

**2. It assumes knowledge it never tells you it is assuming.** A graphical app shows you what
is available: menus, buttons, greyed-out options. A blank command line shows you nothing. There
is no discoverability. You cannot browse your way to the answer, and nothing hints that the
command you are about to run has a mode that would have been safer.

**3. Error messages are written for people who already know.** They name internal concepts, cite
line numbers in files you have never seen, and frequently report a symptom three steps
downstream of the actual cause. A beginner reading a terminal error usually cannot tell whether
they broke something badly or made a trivial typo. Those two feel identical.

**4. Silence often means success.** Many commands print nothing at all when they work. So the
feedback you get for "it worked perfectly" and "it did nothing" is the same: an empty line and
a new prompt. You have to learn to check separately, which nobody tells you.

**5. There is invisible state, and it changes what your command does.** Which folder you are
standing in. Which shell you are running. Which account you are logged in as. What software is
installed. The exact same typed line can succeed on your colleague's machine and fail — or, far
worse, do something different — on yours, with nothing on screen to explain why.

**6. A typo is often a valid different command.** This is the one that actually causes
disasters. In a graphical app, dragging a file to slightly the wrong place produces a visible
wrong result you can drag back. On a command line, one stray space or one wrong character can
turn "delete these three temporary files" into "delete this entire folder," and the command will
execute it confidently, because it is a perfectly legal instruction. The machine has no concept
of what you meant.

**7. The real risk is not you writing commands. It is you pasting them.** In practice, beginners
rarely get hurt composing their own commands. They get hurt copying a line from a forum post, a
chat answer, a blog, or an AI, and running it because it looked like the fix. You are executing a
stranger's instruction with your own permissions on your own files. Part 5 exists entirely
because of this.

None of this makes the terminal bad. It makes it a sharp tool, and sharp tools have rules.

---

## Part 4 — "Enough": the six things, precisely

This is the whole requirement. Learn these six and you have cleared the fear, which is the
actual goal. Everything else, you ask for.

Notice what each of these has in common: none of them change anything. Five are read-only and
one is a stop button. That is deliberate. Your entire beginner competence should be made of
things that cannot break anything.

### 1. Open it

Every operating system ships one. It is an application with a name, findable through whatever
search or launcher your system has. You do not need to install anything to have a terminal.

Ask your AI: *"I am on [your operating system]. Tell me the exact name of the built-in terminal
application and the two ways to open it."*

### 2. Know where you are

A terminal is always "standing" in one folder, and every command you run acts relative to that
folder unless you say otherwise. Not knowing where you are standing is the root cause of a large
share of beginner accidents, because the command you thought would affect a small folder was
pointed at a big one.

There is a command that prints the folder you are currently in. Its name is different on
different systems. Learn yours, and make a habit of running it before anything that changes
files. It is free and it is read-only.

### 3. Move to a folder, and see what is in it

Two more read-only moves: change which folder you are standing in, and list what is inside the
current one. Between them, they are how you navigate. If you can do these, the terminal stops
being a void and becomes a place with rooms.

One useful, slightly reassuring fact: the command for changing folder happens to be spelled the
same way on nearly every system you will meet. The command for listing what is inside a folder
does not. Confirm both with your AI rather than assuming.

### 4. Run a thing

Type the name of a program, press enter, watch what it prints. This is how you will start an AI
agent, and honestly it may be most of what you ever do here. There is no ceremony to it.

Two things worth knowing when you do it. Some programs finish and give you your prompt back.
Others keep running and hold the window — a server, a watcher, an agent waiting for your next
instruction. A window that is not giving you a prompt back is usually not broken; it is busy on
purpose.

### 5. Stop a runaway

This is the one that converts fear into confidence, so learn it before you need it.

In most terminals, on every major desktop operating system, holding **Ctrl** and pressing **C**
sends an interrupt to whatever is currently running and stops it. Not the copy shortcut you may
be used to elsewhere — in a terminal, that key combination traditionally means stop. Confirm it
with your AI for your specific setup, because a few environments differ.

Knowing this is what makes it safe to try things. If something starts scrolling forever, or asks
you a question you do not understand, or appears to be doing more than you expected, you are not
trapped. You stop it.

Two supporting facts, both worth having:

- Closing the terminal window generally stops what was running in it. Crude, effective, fine.
- Stopping a command does not undo what it already did. Interrupt is a brake, not a reverse
  gear. This is exactly why the ask-first rule in Part 5 matters more than the stop key.

### 6. Read an error well enough to paste it somewhere useful

You do not have to understand the error. You have to be able to hand it over intact. That means
copying the whole thing, not a summary of it, and pasting it along with what you ran.

Part 9 gives you the exact wording. The skill is not interpretation. It is faithful reporting,
which is a thing you already know how to do.

**That is the list.** Open, locate, move, run, stop, report. Nothing on it can destroy anything.
Everything beyond it is optional and askable.

---

## Part 5 — The rule that keeps you safe

One rule. It is short, it is absolute, and it costs you about fifteen seconds.

> **Never run a command you do not understand. Ask first — every time, including when your
> own AI wrote it.**

The short version, for when you are mid-conversation and just need to say something. Learn this
one sentence by heart:

```
Explain what this command does, what it changes, and whether it can be undone - before
I run it.
```

That sentence alone will catch most of what would have hurt you. When the command looks
consequential, or you are about to run it somewhere that matters, use the long form instead.
Copy it somewhere you can reach quickly.

```
Before I run this, explain it to me:

<paste the command here>

Tell me, in plain language and in this order:
1. What it does, in one sentence.
2. Exactly which files or folders it will touch, and whether anything outside the
   folder I am standing in could be affected.
3. What it changes or deletes, and whether that change can be undone - and if it can,
   exactly how.
4. Whether anything in it is irreversible, needs administrator rights, downloads
   something, or runs something it downloaded.
5. The safest version of the same thing - a read-only or dry-run version I can run
   first to see what it would do without doing it.

If any part of it is risky, say so first, before the explanation. If you wrote this
command yourself, check it again as if a stranger had sent it to me.
```

That last line is doing real work. An AI that just wrote a command has the same problem a person
does: it is checking its own output against the same reasoning that produced it. That is the
core argument of [Cross-checking with many models](17-many-models.md), and it applies to a
one-line command as much as to a report.

### The standing instruction

Put this in your project instructions or your `CLAUDE.md` so you do not have to remember it
while tired:

```
Terminal safety rule.

Before you give me any command to run, or run one yourself, tell me in one line what
it changes and whether it can be undone. If it deletes anything, uses a force flag,
uses a wildcard, needs administrator rights, or runs something downloaded from the
internet, stop and say so explicitly before showing me the command.

Prefer the read-only or dry-run version first. Never chain a destructive step together
with a safe one in a single line.

I am not able to review these commands myself. Assume I will run whatever you give me.
```

That last sentence is uncomfortable and you should include it anyway. It is true early on, and
telling your AI the truth about your ability to check its work is how you get appropriately
careful behavior. See [Verification](04-verification.md) on why the checker needs to know what
it is protecting against.

### What a good answer to that prompt looks like

A good answer names the target path explicitly, says what class of change it is, and states
reversibility without being asked twice. A bad answer says "this is a standard command, it is
safe" and moves on. "It is safe" is not an explanation and you should push back on it once,
with: *"Safe how? Name what it writes to and what happens if the path is wrong."*

---

## Part 6 — The command shapes that are genuinely destructive

You do not need to memorize commands to spot danger. You need to recognize **shapes**. Here are
the ones that account for most real damage, with the mechanism in each case — because knowing
why is what lets you spot the next one.

### Shape 1 — Recursive deletion

*A delete command, plus an option meaning "and everything underneath this."*

The mechanism: recursion means the command descends into the target folder, then into every
folder inside it, all the way down, deleting as it goes. It does not ask between levels. It does
not stop when the count gets surprising. And terminal deletion frequently bypasses the recycle
bin entirely, so there is nothing to restore from.

Why the damage is disproportionate: the blast radius is decided entirely by the target path, and
paths are one typo wide. A single wrong character can move the target from a small temporary
folder to your entire documents folder. The command executes both with identical enthusiasm.

### Shape 2 — Force flags

*An option, usually named force or spelled with an f, that removes confirmations.*

The mechanism: force flags exist specifically to switch off the safety behavior — the "are you
sure," the refusal to delete something protected, the stop-on-first-error. Someone who knows
what they are doing uses them to avoid answering a hundred prompts. Someone who does not is
switching off the exact mechanism that would have caught their mistake.

Treat force as a word that means *"I have already checked this carefully."* If you have not, you
should not be using it.

### Shape 3 — A wildcard anywhere near a destructive command

*A star or question mark standing in for "match anything."*

The mechanism, and this is the part that surprises people: the wildcard is expanded **before**
the command runs. The shell replaces the star with the actual list of matching files, then hands
that finished list over. So you never see what the command is actually going to receive. You are
approving a list you cannot read.

A stray space or a slightly different pattern changes that list completely, and the command has
no way to notice that the list is absurd. Wildcards are fine with read-only commands, where the
worst case is seeing too much output. Near anything that deletes, moves, or overwrites, they are
one of the sharpest edges in the whole tool.

Useful habit: run the same wildcard with a *listing* command first, so you can see exactly which
files match, before you point anything destructive at that pattern.

### Shape 4 — Downloading something and piping it straight into a shell

*Fetch a file from the internet, and feed it directly into the thing that executes commands,
without it ever touching your screen.*

You will see this recommended constantly as a one-line install. The mechanism of the risk: you
are executing a script you have never read, from a server you do not control, with your own
permissions, on your own machine. There is no review step because the content goes from the
network straight into execution.

Two specific reasons this is worse than it looks. The server can serve different content to
different requests, so the file somebody else inspected is not necessarily the file you will
receive. And the script can do anything your account can do — which, if you have added
administrator rights to the line, is everything.

The safer pattern, which costs you one extra step: download the file, open it and read it (or
have your AI read it and summarize what it does and what it touches), then run it. If a project
only offers the pipe-straight-in version, that is a small signal about the project.

### Shape 5 — Administrator or elevated rights

*A prefix or a mode that means "run this with full system privileges."*

The mechanism: normally your account cannot damage the operating system or other users' files.
That limitation is a safety feature. Elevation removes it. Every other shape on this list is
worse with elevation attached, because the boundary that would have contained the mistake is
gone.

Rule of thumb: if a command needs administrator rights and you do not know precisely why, that
is the moment to ask, not the moment to type your password.

### Shape 6 — Redirecting output into a file that already exists

*A single angle bracket pointing at a filename.*

The mechanism: this replaces the file's entire contents with whatever is being written. No
warning, no prompt, no backup — even if the file was a hundred pages long and the new content is
one line. It is one of the quietest ways to destroy work, because nothing about it looks like
deletion.

### Shape 7 — Changing permissions or ownership across a whole tree

*A permission command with a recursive option pointed at a large folder.*

The mechanism: this rarely deletes anything, which is why people underestimate it. It changes
who can read, write, or run every file underneath. Applied too broadly it can break software
subtly, expose things that were private, or lock you out of your own files. It is also
genuinely hard to reverse, because the original settings were not identical for every file and
nothing recorded what they were.

### Shape 8 — Anything aimed at a disk, a drive, or the top of the filesystem

*Formatting, partitioning, imaging, or writing directly to a device.*

If you see a command that names a whole drive rather than a folder, stop. These are not
recoverable by ordinary means and there is no reason a normal task needs one.

### The pattern under all eight

Look at what they share. Every one of them either **removes a safety net** (force, elevation),
**acts on more than it appears to** (recursion, wildcards, redirect), or **executes something
you never read** (pipe-to-shell). Those three mechanisms are the whole taxonomy. A new dangerous
command you have never seen will be dangerous for one of those three reasons, and now you can
name which.

### Two practical protections

**Paste into a text editor first.** Pasted text can contain a hidden newline, which means the
line executes the instant it lands, before you have read it. It can also contain characters that
do not display the way they behave. Paste into a plain text editor, look at it, then paste the
checked version into the terminal. This takes five seconds and eliminates an entire category of
accident.

**Have a floor to fall back to.** If a folder's contents matter, it should be under version
control before you or an agent starts changing things — that is the entire argument of
[Git](15-git.md), and it is the difference between "I lost an afternoon" and "I lost the work."
Version control does not protect against every shape above, but it protects against the common
ones, and it costs nothing to have in place first.

---

## Part 7 — When the graphical interface is simply better

Some people treat the terminal as a virtue. It is not a virtue. It is a tool with a shape, and
plenty of tasks have a different shape.

| Task | Better tool | Why |
|---|---|---|
| Looking at photos, images, or design files | The graphical app | You are evaluating something visual. Text cannot show it to you. |
| Reorganizing a handful of files you can see | The file manager | Drag, drop, undo. Faster and reversible by design. |
| Renaming one thing | Either | Not worth an argument. Use whichever is already open. |
| Reading a long document | A document viewer | Scrolling, searching, and formatting are solved problems there. |
| Anything you do once and never again | Whichever you already know | The terminal's advantage is repeatability. A one-off has nothing to repeat. |
| Exploring an unfamiliar system | The graphical app | Menus show you what exists. A blank prompt does not. |
| Working while tired, rushed, or on someone else's machine | The graphical app | The undo behavior is more forgiving, and that is when you need forgiveness. |
| The same file operation across two hundred files | The terminal | This is exactly what it is for. |
| Anything you will need to do again next month | The terminal | Because you can save the command. |
| Anything you need a record of having done | The terminal | The command and its output are the record. |
| Running or watching an AI agent | The terminal | Visibility, control, and a stop key. |

The honest summary: **the terminal wins on repetition, precision, scale, and evidence. The
graphical interface wins on discovery, visual judgment, and forgiveness.** Choosing by which one
makes you feel more competent is how people end up doing a two-minute drag-and-drop as a
twenty-minute exercise in looking serious.

There is a real intermediate position, too, and it is where most people in your situation
should live: use the graphical tools for your own work, and use the terminal for the specific
thing that needs it, which is usually running an AI agent and watching what it does.

---

## Part 8 — Terminals are not the same everywhere, and this will bite you

Do not trust commands written in a document. Including this one — which is why this chapter has
deliberately not printed any.

Here is what varies between systems, and it is more than people expect:

- **The commands themselves.** Different operating systems, and different shells on the *same*
  operating system, use different names for the same action. Some overlap. Many do not.
- **How paths are written.** Which slash separates folders, whether capitalization matters,
  what the top of the filesystem is called, where your personal folder lives.
- **Quoting and spaces.** A file with a space in its name needs different handling in different
  shells, and getting it wrong is a classic way to accidentally target two things instead of one.
- **Which programs exist.** A command that is standard on one system is simply absent on another
  until installed.
- **What the same word does.** This is the dangerous one. In rare cases, a command name exists
  on two systems and behaves differently. A command that fails loudly is a nuisance. A command
  that succeeds at something you did not intend is the actual problem.

So: **tell your AI which system you are on, before you ask for anything.** Not once — at the
start of any session where commands are going to appear.

```
Context for anything terminal-related in this conversation:

I am on [Windows / macOS / Linux, and the version if you know it].
I am using [the terminal application you opened, if you know its name].
I do not know which shell I am running.

First: give me a single read-only command that will tell you which shell I am in, and
tell me what to look for in the output. I will run it and paste the result back.

After that, every command you give me must be correct for that shell specifically. If
a command differs between shells, say so rather than giving me the most common
version. If you are not certain which form applies to my setup, say you are not
certain instead of guessing.
```

That last instruction matters more than it looks. The failure mode is not an AI that refuses to
help — it is an AI that confidently gives you the version that is most common in its training
data, which may not be the one on your machine. Ask for uncertainty to be stated, and you
usually get it.

Write the answer down once you have it. Your operating system and shell belong in a
[decisions log](../progress/DECISIONS.md) or wherever your AI reads your standing context, so
you never have to establish it again.

---

## Part 9 — Reading an error, well enough to be useful

You are not going to interpret errors. You are going to relay them faithfully, which is a
different and much easier skill.

### What an error is trying to tell you

Most errors contain three things, somewhere: **what failed**, **where it failed**, and **why**.
They are rarely in that order and are often buried in text meant for whoever wrote the program.

Two habits that help more than they should:

- **Read the last line first.** In many tools, the final line is the actual summary. The wall
  above it is the trail of how the program got there.
- **Then read the first line.** The first and last lines together usually contain the real
  message. The middle is frequently noise for your purposes.

If those two lines mention a file path, look at whether the path is one you recognize. That
alone often tells you whether you mistyped something or hit a genuine problem.

### What to paste, and what to say

Give the whole thing. Not a paraphrase, not the part that looked important. The line you decided
was irrelevant is regularly the one that identifies the cause.

```
A command failed. Here is everything.

What I was trying to do:
[one sentence, in plain language]

The exact command I ran:
[paste it]

The full output, including everything above and below the error:
[paste all of it]

My system: [operating system], [shell, if you know it]

Tell me:
1. What this error actually means, in plain language.
2. Whether anything was changed or damaged before it failed, or whether it stopped
   cleanly.
3. The most likely cause, and how confident you are.
4. What to try next - the smallest, safest, most reversible thing first.

Do not give me a command to run until you have answered point 2.
```

Point 2 is the one people forget and the one that matters most. "Did it fail before or after it
changed something" determines whether you have a puzzle or a problem, and it is the first thing
you want to know.

### Before you paste: check what is in the error

Error output can contain things you did not mean to share — file paths that reveal client names,
tokens, keys, internal addresses, fragments of data. Scan for those before pasting, especially
into a tool that is not your organization's approved one. This is a direct application of
[Safety, privacy, and trust](10-safety-privacy-and-trust.md), and error output is one of the
sneakiest leak paths there is, precisely because it looks like meaningless technical noise.

### When the answer is wrong

Sometimes an AI will confidently misdiagnose a terminal error. The tell is that its fix does not
change the error at all, or changes it into a different error in the same place. When that
happens twice, stop iterating and change the approach: paste the same error into a different
model, with no reference to what the first one already tried. See
[Cross-checking with many models](17-many-models.md). Repeating a failed line of reasoning is
not persistence; it is a loop with no done-check, which is its own
[failure mode](../protocols/FAILURE-MODES.md).

---

## Part 10 — The real reason you are here: watching an agent work

For most readers of this harness, the terminal's actual purpose is a window onto what an AI
agent is doing on your behalf.

When an agent runs in a terminal, you see the sequence: it says what it intends, it runs
something, the output appears, it reacts. Many setups pause and ask before anything that changes
files or reaches the network. That pause is your control point, and it is where the material in
[Tools and MCP](07-tools-and-mcp.md) becomes concrete rather than theoretical — you are watching
the tool-call loop happen, one call at a time.

Three things to actually do while watching:

**Read what it is about to run, not just whether it wants to run something.** An approval prompt
you always say yes to is not a safeguard; it is a formality with extra keystrokes. If you do not
understand the command, that is what Part 5's prompt is for, and asking mid-run is completely
normal.

**Notice the target path.** Far more often than not, the risk is not the command itself — it is
what the command is pointed at. You do not need to understand the command to notice that it is
aimed somewhere broader than the task requires.

**Treat the visible output as your receipts.** When the agent later tells you it finished, you
have the actual record of what happened sitting in the window above. That is exactly the evidence
[Verification](04-verification.md) asks for, available for free, and it is the main reason people
who work this way trust their agents appropriately rather than optimistically.

---

## Try this now

Copy this whole block into your AI. It gives you all six things, correct for your actual machine,
in about ten minutes, without running anything that can change a single file.

```
I have never used a terminal, or barely have. Teach me exactly six things and nothing
more. Do not teach me anything that changes, moves, or deletes files - every command
you ask me to actually run in this session must be read-only or a stop key.

First, ask me which operating system I am on. Wait for my answer. Then give me one
read-only command that reveals which shell I am running, and tell me what to look for
in the output. Wait while I run it and paste the result back.

Then, one at a time, waiting for me to actually do each before moving on:

1. How to open the terminal on my system - the exact application name and two ways to
   launch it.
2. The command that shows which folder I am currently standing in.
3. The command that lists what is inside the current folder, and the command that moves
   me into a different one.
4. How to run a program by name, and how to tell the difference between one that has
   finished and one that is still running on purpose.
5. How to stop something that is running, confirmed for my specific setup - and tell me
   plainly whether stopping it undoes what it already did.
6. A deliberately broken command that produces a harmless error, so I can practice
   reading one. Then have me tell you which line of the output actually mattered and
   why, before you explain it.

After all six, quiz me. You write three commands - not me - purely for me to look at
and judge on screen. Say clearly that these are for identification only and that I must
not run any of them. Make one genuinely dangerous, one harmless, and one that looks
alarming but is fine. Ask me which ones I should refuse to run without an explanation,
and what specifically makes each one risky. Tell me if I get it wrong and why.

Finally, write me four lines I can save: my operating system, my shell, the command
that tells me where I am, and the key that stops a runaway.
```

Save those four lines. They are, honestly, most of what you will need for a long time.

---

## What you should now be able to do

- Open a terminal, tell where you are standing, move between folders, run a program, stop
  something that is running away, and copy an error out faithfully — and treat that as the
  complete requirement rather than as the first chapter of a longer study.
- Refuse to run any command you have not had explained, using a specific prompt that asks what
  it touches, what it changes, and whether it can be undone — including for commands your own AI
  just wrote.
- Recognize the destructive command shapes by mechanism rather than by memorizing them:
  recursion, force flags, wildcards near anything that deletes, downloads piped straight into a
  shell, elevated rights, and output redirected over a file that already exists.
- Choose the graphical interface without embarrassment when the task is visual, one-off, or
  exploratory, and choose the terminal when the task is repeated, precise, large, or needs a
  record.
- State your operating system and shell to your AI before asking for any command, and treat
  commands written in any document — this one included — as needing confirmation for your
  specific setup.

---

Next: [Git](15-git.md) — the thing that makes it safe to let an AI change your files.
Then: [Cross-checking with many models](17-many-models.md) — why a second opinion has to come
from somewhere else.
