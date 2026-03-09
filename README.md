# Conversations Workflow
### Turning a recorded thinking session into a navigable artifact

This is the process behind [conversations.chee.se](https://conversations.chee.se). It's designed for anyone who records their thinking — alone, with one other person, or with a group — and wants to give that thinking a form that lets them see it differently.

A transcript is a record of what was said. This workflow produces something else: a structure that makes visible what the thinking was actually doing — its threads, its key moments, its unresolved tensions. Putting the same content in a different frame often reveals things that weren't apparent while speaking. That's the point.

---

## What this is

A **navigable thinking artifact**. The format makes the structure of recorded thought visible in a way that invites readers in rather than summarizing for them.

It works for a single voice working through an idea, two people in dialogue, or a group conversation. The number of voices changes the social texture of the piece; the workflow is the same.

A note on how to use Claude in this process: this works best when you treat it as a thinking partner, not a transcription tool. At each step, tell it what's working and what isn't. Ask whether there's another way of seeing something. Push back when its reading feels flat or wrong. The quality of the output is directly proportional to the quality of the back-and-forth.

The two cognitive modes in the pipeline are intentionally separate:

- **Speaking** (the recording) — low-stakes, generative, recursive. Best for surfacing what you actually think before you know how to say it.
- **Typing** (the Claude session) — iterative, no social cost to incomplete thoughts. Best for finding the structure hidden in the speaking.

Both matter. Neither replaces the other.

What this is not: an article production pipeline. Articles have conclusions. This format has tension. If you want a finished argument, this will frustrate you. If you want to make your thinking navigable, it's the right tool.

---

## Prerequisites

**A recording.** Voice memo, Zoom, phone call, whatever you had running. Quality doesn't need to be perfect — modern transcription handles background noise reasonably well.

**A transcript.** A few options depending on your setup:

- **Mac**: [MacWhisper](https://goodsnooze.gumroad.com/l/macwhisper) with the Parakeet model — local, fast, accurate. Voice Memos (built into macOS/iOS) has decent built-in transcription if you're already using it.
- **Windows / Linux**: [Vibe](https://github.com/thewh1teagle/vibe) — open source, Whisper-based, runs locally on all three platforms, GPU-accelerated where available.
- **Android**: Google Recorder (built into Pixel devices) transcribes automatically. For other Android devices, Vibe has mobile support in development; in the meantime any recording app plus uploading to a Whisper-based service works.
- **Any platform, no install**: Upload your audio file directly to Claude — it can transcribe short recordings. For longer recordings, Google Docs Voice Typing (free, browser-based) is a reliable fallback.

The built-in options (Voice Memos, Google Recorder) are fine for getting started. Local Whisper-based tools (MacWhisper, Vibe) tend to be more accurate, especially with multiple speakers or domain-specific vocabulary.

**A Claude Pro account** at [claude.ai](https://claude.ai).

**Optional**: a GitHub account for hosting (see `hosting-guide.md`).

---

## The steps

### Step 0 — Upload the transcript and ask for a reading

Drop the transcript into a new Claude chat and ask:

> *Tell me what you understand of this recording — the main threads, the key moments, what's generative in it — before we do anything else.*

Don't skip this step. The reading Claude gives back is the first diagnostic: if it misses something important or flattens a nuance, that tells you what needs more attention. Push back, correct it, add context. This is where the sensemaking actually starts.

Tell Claude upfront how many speakers there are and, if relevant, who they are. If it's a single voice, Claude will read it as a monologue developing an argument. If it's multiple voices, it will track how the thinking moves between them.

---

### Step 1 — Fidelity pass

Before building anything, Claude should ask you what got dropped or changed. A good transcript is still lossy — proper nouns disappear, specific references get generalized, the messiness that was actually the point gets smoothed over.

Claude should ask:

- Are there any proper nouns, place names, or specific references I missed?
- Any statements that feel mis-attributed or stripped of context?
- What's in the original recording that isn't in my reading of it?

Specificity is meaning. Saying someone studied traditional knowledge transmission "in rural Oaxaca" is different from saying they studied it "in Mexico" — the specificity signals fieldwork, not just general interest. Saying a medical diagnosis changed how someone related to time is different from saying it changed their outlook. Flag anything that changed the claim rather than just shortened it.

After you respond, Claude should update its reading and note anywhere the corrections affected the argument.

---

### Step 2 — Thread identification

Claude should propose 2–4 major themes running through the recording. These become the **sidebar threads** — the reading lenses that let someone follow one idea through the whole piece.

Good threads are:
- Distinct enough that they pull different passages to the foreground
- Named simply (3–5 words)
- Tested by the question: if you activated this thread, would a meaningfully different set of passages light up?

Push back if the threads feel too academic, too broad, or don't match how you were actually thinking.

---

### Step 3 — Annotation pass

Identify 5–8 key phrases worth expanding. Good annotation candidates include things the speaker already knows and references, but also moments where Claude can point toward things they haven't encountered yet:

- References to books, theorists, or frameworks that contextualize what's being said
- Claims that compress a lot of intellectual history — where did this idea come from?
- Adjacent work, research, or thinkers that speak to the same problem from a different angle
- Gaps or blind spots: ask Claude *what might this line of thinking be missing, or what would a skeptic say here?*
- Moments where a reader might want to go deeper

Each annotation is an expansion, not a correction — a post-it that opens a door rather than closes an argument. The best ones introduce something the speaker didn't know they were adjacent to.

---

### Step 4 — Build the page

Ask Claude to build the HTML. The spec:

- Single self-contained `.html` file (no external dependencies except Google Fonts)
- Dark background, serif body text, monospace metadata, handwriting font for annotations
- Sidebar with thread-organized key phrases as scroll-links
- Thread filter in the top bar — clicking a thread dims unrelated paragraphs
- Post-it annotation cards that open inline on click
- Diagram if the recording has a lineage or sequence worth visualizing
- Organizing frame summary at the end

See `for-claude.md` for the full technical spec to give Claude.

---

### Step 5 — Review and share

Share a draft with anyone else who was in the recording, or with one trusted reader outside it. Two different questions:

- **If there were other speakers:** Does this faithfully represent what you said and meant? Any words or context stripped that matter?
- **For any reader:** Does the structure make sense from the outside? Does the page surface something the conversation was actually doing?

This step is optional if you recorded alone and the piece is primarily for your own use. It becomes important if you're sharing publicly or with a group.

---

## What to build in next time

Things this workflow doesn't yet handle well:

- **Multi-session threading** — connecting ideas across multiple recordings into a single navigable body of work
- **Version history** — the artifact as first posted vs. after fidelity corrections
- **Reader response** — capturing what the page surfaces for people who read it
- **Process visibility** — the page shows the output of the thinking, but not the thinking itself; the back-and-forth that produced it disappears

---

## Files in this repo

| File | What it is |
|------|------------|
| `index.html` | The first conversation — Kenyatta and Tricia, March 2026 |
| `WORKFLOW.md` | This file |
| `hosting-guide.md` | How to host your own version |
| `for-claude.md` | Upload this to a new Claude chat to guide the build process |

---

*conversations.chee.se — started March 2026*
