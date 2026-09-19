---
name: summary
description: A single-page HTML summary of a conversation, branch, work tree or set of user instructions. Visual and digestible, charts and diagrams over long explanations. Use whenever the user asks for a summary, recap, wrap-up or handover page, plain or with something attached. Bare asks like "summary", "simple summary", "quick summary", "just summarise this" build the plain page. Attached asks like "summary, make it ADHD friendly", "recap but make it look good", "summarise this for a client", "wrap up and animate it", "handover page" build the same page in the matching mode or audience variant (accessible for ADHD, autistic or dyslexia; artistic; animated). If they want an explanation in chat and no file at all, use `eli5-succinct`.
---

# summary

The page skill. One self-contained HTML page, built to one house style. A bare ask builds the plain page; a mode, look or audience attached builds the same page dressed for it.

## Routing

This skill owns every summary that ends in a page. The only thing it does not own is an explanation the user wants in chat with no file.

| They say | Skill |
|---|---|
| "summary", "simple summary", "quick summary", bare "summarise this" | this one, plain (see **Plain vs attached**) |
| "summary" with a mode, look or audience attached | this one, that mode |
| "eli5 succinct on this function" (explain, no file) | `eli5-succinct` |

If you are already here and the user then asks for a mode, stay here. Do not re-route mid-task.

## Plain vs attached

The page and its spec are identical either way. What changes is only the reply and whether modes come up.

- **Plain** (nothing attached): build the default page, hand over the path, say one short plain-language thing about it. Do not offer or mention modes. If they want more, they will ask.
- **Attached** (a mode, look or audience named): build the page in that mode, then you may suggest at most one complementary mode in a single closing line.

## Target

Ask nothing if the target is obvious. Default, in order:

1. What the user explicitly named, such as a branch, a PR, a file, a topic
2. The current session or conversation
3. The current repo or working tree

If two targets are equally plausible, pick one, say which you picked in one line, and continue.

## Step 1: gather

Before writing anything, go and look. Do not summarise from memory of the conversation alone.

- **Working tree or repo:** `cd` to the directory. Run `git status`, `git log --oneline -20`, `git diff --stat`. Read the files that actually changed.
- **Branch:** diff it against its base. `git log --oneline <base>..HEAD` and `git diff --stat <base>...HEAD`.
- **Conversation or session:** use what is in front of you.
- **User instructions:** read the actual instructions file, do not paraphrase from memory.

Never invent progress, status or numbers. Unknown is a valid value and should be shown as such.

## Step 2: build the page

> Create a single page HTML summary of the conversation, branch, work tree or user instructions. Make it visual and digestible without additional cognitive fatigue. Minimal text, clear flow of information. Opt for charts and diagrams over long explanations. Default to clean off-white background, `#333333` text. Create a flow for the user to follow and use typography design principles such as spacing, line height, balanced text, and Z and F reading patterns.

Concretely, that means:

**One file.** Self-contained HTML. No build step, no CDN, no external assets, no framework. Inline SVG only.

**Flow.** The page is a path, not a pile. Each section answers the question the previous one raised. Start with the answer, never a preamble.

1. **Title plus one line.** What this is, in a sentence.
2. **At a glance.** Three to five numbers or states, set large. Numerals, not sentences.
3. **The body.** The actual shape of the work, carried by drawings. This is most of the page.
4. **Decisions made.** At most five, one short line each, every one paired with a mark showing its state. More than five means chart them instead.
5. **Open and next.** Status marks with a few words beside them. Omit either if empty.

Sections 4 and 5 are where pages turn into documents. Keep them visual or keep them out.

**Reading patterns.** Top of page is scanned in a Z: title top-left, the single most important fact top-right, entry into the body along the diagonal. Below that, text-heavy sections are scanned in an F: front-load every heading and every bullet with the word that matters, because the right-hand end of each line does not get read.

**A table is not a visual.** It is text arranged in a grid. So are bullets. If the page is mostly tables and bullets, the skill has failed, however tidy it looks.

**Visual over verbal.** Reach for the drawing first:
- sequential → a flow or a timeline
- quantity or change → a bar, line or dot chart
- proportion or share → a stacked bar or a dot grid
- something that changed → two columns, before and after
- state across several items → a grid of marks, not words
- how things connect → a node diagram
- one number that matters → set it enormous, on its own

At most one table per page, and only for genuinely parallel short items. If you want a second table, draw it instead.

If a paragraph is doing a diagram's job, replace it. Every section must earn its place. Cut anything that is only there for symmetry.

**Budget.** These are hard limits, not suggestions. The goal is a page carried by pictures, where prose is captions between drawings, not the other way round. Run this checklist against the finished markup **before you write the file**, and if any line fails, fix it and check again:

1. **Count the body words.** Strip headings, labels, axis text and figures; count what is left. Over 200 means cut until it is under. Do not write the file first and count later.
2. **Every section has a drawing.** Point at the chart, diagram, timeline or mark in each one. A section that is only words is a failed section: draw it or cut it.
3. **No three text blocks in a row.** If you find three, one becomes a picture.
4. **No continuous prose longer than two sentences**, anywhere.
5. **More drawings than paragraphs, overall.** If you can count more `<p>` blocks than distinct visuals, the balance is wrong.

If the content genuinely resists being drawn, that is a sign the page has too many sections, not that it needs more words. Cut the section, do not pad it.

**Typography.**
- Use the project's own type if it has one. Otherwise use an explicit stack with real fallbacks, so the page looks the same on macOS, Windows and Linux rather than dropping to DejaVu Sans on Linux:
  - Text: `font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Noto Sans", "Liberation Sans", Helvetica, Arial, sans-serif;`
  - Data, labels and figures: `font-family: ui-monospace, "SF Mono", "Cascadia Code", "Roboto Mono", "DejaVu Sans Mono", Menlo, Consolas, monospace;`
- A bare `system-ui` or `sans-serif` is not enough: name the fallbacks so Linux lands on Roboto or Noto, not DejaVu.
- Body 16px minimum. Line height 1.5 or more.
- Measure capped near 65 characters. This is what "balanced text" means here, and long lines are the main cause of reading fatigue.
- One large title, clear section headings, nothing competing in between.
- Left aligned. Never justify, because justification opens rivers of white space that break scanning.
- Generous spacing. Space between sections should be clearly larger than space within them, so the eye gets the grouping without a border.
- Clean and plain is the default look. Ornament is opt in via artistic mode.

**Colour.**
- Background `#FAF9F7`. Ink `#333333`. One accent.
- Supporting tones: muted text `#6B6B6B`, hairlines `#E5E2DE`, raised surfaces `#F2EFEB`.
- No pure white, no pure black, no gradients behind text.

**Constraints.** No paragraph longer than two sentences. Bullets under ten words. Must survive Print to PDF, so no fixed viewport heights and nothing that only appears on scroll. Light by default; add a dark variant only when the page will be viewed inside a container with its own theme setting.

**Drawing quality.** A drawing that overlaps or clips its own labels is worse than a table. You are writing SVG blind, so build the geometry so collisions cannot happen, rather than hoping they do not:

- Give every SVG an explicit `viewBox` and pad it. Leave a margin at least the height of one label on every side so nothing sits against the edge.
- Donut and pie labels go outside the arc, joined by a leader line if needed, never on top of the stroke. If two segments are too thin to label apart, merge them or switch to a bar.
- Bar and dot labels sit clear of the mark, in a reserved gutter, not floating over it.
- Text over a stroke or fill is only allowed when it is on its own reserved band with no mark behind it.
- Long axis labels rotate or wrap; they never run past the plot into the next element.
- Compute positions from the values; do not hand-place magic numbers that only work for today's data.

**Look at what you made.** SVG written blind is often wrong. If you can open or render the file, do it and check for overlapping text, clipped marks, labels off the edge, and marks with no gap between them. Fix what you see before handing over. If you cannot render it, re-read every SVG against the rules above as your check.

## Write in the reader's own language

The page is for one person. Write it the way they write.

Use whatever you already know about them: memory, project files, their instructions file, the way they have been talking to you in this session. Match their register, their vocabulary, their sentence length, their spelling. If they use a particular word for a thing, use that word, not the textbook one.

If you know nothing about them, write plainly: short sentences, common words, no jargon, no corporate filler.

Do not announce that you are doing this.

## Modes

Everything above is the default. Modes are optional. Read the file only if the user asks for that mode by name or clearly describes it.

| Mode | Say | Read |
|---|---|---|
| Accessible | "make it ADHD friendly", "autistic", "dyslexia", "accessible" | `modes/accessible.md` |
| Artistic | "make it look good", "artistic", "designed", "Forever" | `modes/artistic.md` |
| Animated | "animate it", "make it move" | `modes/animated.md` |

Modes stack. Accessible always wins where it conflicts with artistic or animated.

Suggest a mode only on the attached path, and only when it would clearly help. Write the requested page first, then add one line at the end naming the mode and what it would change. Never ask before writing, never suggest more than one, and drop it if the user ignores it. On the plain path, say nothing about modes at all.

## Variants

- `summary for a client`: no internal jargon, no file paths, no ticket ids.
- `summary of the changes`: lead with before and after, then decisions.
- `summary for handover`: lead with current state and open questions.

## Step 3: write the file

Write to `summary-<slug>-<YYYY-MM-DD>.html` in the working directory, or where the user says.

## Step 4: reply

The page is the summary. Do not repeat it in chat.

- **Plain path:** a short plain-language note, then the path. Under 100 words, no jargon, lead with the answer. This is just so they know what they are opening. No mode suggestions, no offers, no next-steps list they did not ask for.

  ```
  <One line: what the page covers.>

  <Two or three sentences: what it found, in plain words.>

  <path/to/summary-slug-date.html>
  ```

- **Attached path:** the file path, plus at most one line suggesting a complementary mode.
