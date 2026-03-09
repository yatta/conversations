# For Claude: Guide me through building a semantic conversation page

## What this is

I want to take a recorded conversation transcript and turn it into a designed, interactive web page — a navigable thinking artifact that makes the structure of recorded thought visible.

This file is a set of instructions for you (Claude) to guide me through the process step by step. Please read through it fully, then wait for me to share my transcript before doing anything.

---

## The output I'm looking for

A single self-contained HTML file that:

- Presents a lightly edited recording in a clean, typographically considered format
- Has a **sidebar** listing key phrases organized into 2–3 "reading threads" (thematic lenses)
- Has **inline annotations** on key phrases — clicking them opens a post-it-style card with context, references, or expansions
- Has a **thread filter** in the top bar — clicking a thread dims unrelated paragraphs so readers can follow one idea through the whole piece

The visual design should fit the content and the person — we'll figure that out together in Step 2 before writing any code.

---

## Step 0 — Read the transcript first, build nothing

When I share the transcript, please:

1. Read it carefully and give me a 3–5 paragraph summary of what you understand it to be about
2. Identify the **main intellectual threads** running through it (usually 2–4 distinct themes)
3. Identify the **key phrases or moments** that anchor each thread
4. Note any **references or concepts** mentioned (books, theorists, frameworks) that could be expanded in annotations
5. Note the **voice or voices** — how many speakers are there, and how do their registers differ? If it's a single voice, how does the thinking develop and shift across the recording?

Ask me if your reading seems right before moving to any next step. This is a thinking partnership — tell me where my reading feels flat, wrong, or incomplete, and I'll update it before we go further.

---

## Step 1 — Fidelity check (important — don't skip)

After sharing your reading, ask me:

> *Before we build anything, I want to check what might have been lost or changed in transcription. Can you look at what I've described and flag: any proper nouns, place names, or specific references I missed? Any statements that feel mis-attributed or stripped of context? What's in the original recording that isn't in my reading of it?*

Specificity is meaning. A researcher who did fieldwork "in rural Oaxaca" is making a different claim than one who worked "in Mexico." Someone who says a diagnosis changed "how they related to time" is saying something different from someone who says it "changed their perspective." Flag anything that changed the claim rather than just shortened it.

After I respond, update your reading and note anywhere the corrections affected the argument.

---

## Step 2 — Design direction

Before writing any code, I want to find a look and feel that fits this particular recording and person. Please ask me:

1. **Reference points**: Name 2–3 things — publications, websites, book covers, designers, apps, physical objects — whose visual feel you like or that seem adjacent to this recording. They don't need to be related to the content.
2. **Physical analogy**: If this recording were a physical object, what would it be — a field notebook, a letter, a broadsheet, a zine, a legal brief, a lecture handout, something else?
3. **Reader**: Who's the primary audience — just you, a close group, or anyone who finds it?

From those answers, propose a design direction in words before writing a line of code — something like "I'm thinking muted newsprint tones, editorial serif, low visual noise — closer to a Granta essay than a tech blog" — and ask if that resonates. Adjust based on feedback, then build.

Don't default to dark backgrounds and serif fonts unless that's what fits. The design should feel inevitable for this particular content, not like a template.

---

## Step 3 — Build the HTML

Build a single `index.html` file with the design direction established in Step 2.

### Required structural elements (adapt visually to the aesthetic)

**Top bar (sticky)**
- Site or project name on the left, thread pill buttons on the right (one per thread, colored dot + label)

**Sidebar (sticky left column)**
- Thread sections with colored labels
- Key phrases as anchor links
- Fades non-active threads when a thread filter is on

**Main column**
- Masthead: recording identifier + date
- Title and subtitle
- Speaker key if there are multiple voices
- Section markers
- Dialogue or monologue body, sectioned as appropriate
- Pull quotes for the strongest lines
- SVG diagram if there's a sequence or lineage worth visualizing
- Organizing frame summary at the end
- Closing mark and colophon

### Technical requirements (these don't change regardless of aesthetic)

**Use `<span class="graf">` with `display: block`, never `<p>` tags for body paragraphs.** Browsers auto-close `<p>` tags when a `<div>` is nested inside them, which strips the CSS thread classes and breaks the salience filter. This is a known browser parsing issue, not something that can be worked around.

**Thread system:** Tag each logical paragraph with its thread(s):
```html
<span class="graf th1">paragraph text here</span>
```
Adding `thread-th1` to `<body>` dims all `.graf` elements that don't carry `.th1`. Transition: `0.4s ease`.

**Annotation system:**
- Trigger: `<span class="ann th2" data-id="postit-id">phrase</span>`
- Card: `<div class="postit th2" id="postit-id">` placed after its `.graf` span in the DOM, revealed by JS on click
- Each card: thread label, title, body text, optional reference line, close button

**Font sizes:** Base `html { font-size: 18px; }`. Body text `clamp(1.08rem, 1.5vw, 1.22rem)`. Nothing visible below 0.65rem — this gets read on phones.

---

## Step 4 — Annotation depth

After building the first version, go back through the annotations and push further:

- For each annotation, ask: is there adjacent work, research, or a thinker the speaker may not have encountered that speaks to the same problem from a different angle?
- Are there gaps or blind spots in the argument worth naming? What would a skeptic say here?
- What is this line of thinking *not* accounting for?

Annotations that introduce something the speaker didn't know they were adjacent to are more valuable than ones that just define what they already know.

---

## Step 5 — Iterate

Ask after the first build:

1. Does the recording feel faithfully represented?
2. Are the thread assignments right?
3. Are the annotations at the right level — too academic, too casual, too obvious?
4. Anything too small to read?
5. Does the diagram (if any) make sense?
6. Does the design feel right for this content, or does something need to shift?

Expect 3–4 rounds. The most common fixes: font sizes, annotation text, thread reassignments, sidebar items, design tone adjustments.

---

## Ready

When I share the transcript, start with Step 0. Summarize and ask questions before building anything.
