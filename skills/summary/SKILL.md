---
name: summary
description: A single-page HTML summary of a conversation, branch, work tree or set of user instructions, with optional modes for accessible (ADHD, autistic, dyslexia), artistic and animated, plus audience variants for a client or a handover. Visual and digestible, charts and diagrams over long explanations. Use when the user asks for a summary with something attached to it, such as a mode, a look, an audience or a feeling. Examples include "summary, make it ADHD friendly", "recap but make it look good", "summarise this for a client", "wrap up and animate it", "handover page". If they want the plain version with no options, use `simple-summary`. If they want an explanation in chat and no file at all, use `eli5-succinct`.
---

# summary

The one with options. Same page, same house style as `simple-summary`, plus modes and audience variants.

## Routing

This skill owns anything about how the page should look or feel.

| They say | Skill |
|---|---|
| "summary" with a mode, look or audience attached | this one |
| "simple summary", bare "summary" | `simple-summary` |
| "eli5 succinct on this function" (explain, no file) | `eli5-succinct` |

If you are already here and the user then asks for a mode, stay here. Do not re-route mid-task.

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
2. **At a glance.** Three to five short facts, states or numbers. Cards or a strip.
3. **The body.** The actual shape of the work, carried by visuals.
4. **Decisions made.** One line each, with the reason.
5. **Open and next.** Unresolved questions, then next steps. Omit either if empty.

**Reading patterns.** Top of page is scanned in a Z: title top-left, the single most important fact top-right, entry into the body along the diagonal. Below that, text-heavy sections are scanned in an F: front-load every heading and every bullet with the word that matters, because the right-hand end of each line does not get read.

**Visual over verbal.** Reach for the picture first:
- sequential → a flow or timeline
- quantity or change → a chart
- something that changed → two columns, before and after
- parallel items → a short table

If a paragraph is doing a diagram's job, replace it. Every section must earn its place. Cut anything that is only there for symmetry.

**Typography.**
- System font stack, unless the project has its own type. If it does, use the project's.
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

Suggest a mode when it would clearly help. Write the requested page first, then add one line at the end naming the mode and what it would change. Never ask before writing, never suggest more than one, and drop it if the user ignores it.

## Variants

- `summary for a client`: no internal jargon, no file paths, no ticket ids.
- `summary of the changes`: lead with before and after, then decisions.
- `summary for handover`: lead with current state and open questions.

## Step 3: write the file

Write to `summary-<slug>-<YYYY-MM-DD>.html` in the working directory, or where the user says.

## Step 4: reply

The file path, plus at most one line suggesting a mode. The page is the summary. Do not repeat it in chat.
