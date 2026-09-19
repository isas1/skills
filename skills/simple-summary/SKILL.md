---
name: simple-summary
description: One single-page HTML summary of a conversation, branch, work tree or set of user instructions — visual, digestible, no modes and no options. Plus a short plain-language note in chat. Use when the user says "simple summary", "quick summary", "just summarise this", "keep it simple", or asks for a summary with nothing attached to it. If they attach a mode, a look or an audience — accessible, ADHD, artistic, animated, for a client, for handover — use `summary` instead. If they want an explanation in chat and no file at all, use `eli5`.
---

# simple-summary

The plain one. Build the page, hand over the path, say one short thing about it. No choices offered.

## Routing

| They say | Skill |
|---|---|
| "simple summary", "quick summary", bare "summary" | this one |
| "summary, make it ADHD friendly" / "artistic" / "animate it" | `summary` |
| "summary for a client" / "for handover" | `summary` |
| "eli5 this function" — explain, no file | `eli5` |

Do not offer modes. Do not mention the other skills. If they want more, they will ask.

## Target

Ask nothing if the target is obvious. Default, in order:

1. What the user explicitly named — a branch, a PR, a file, a topic
2. The current session or conversation
3. The current repo or working tree

If two targets are equally plausible, pick one, say which in one line, and continue.

## Step 1 — gather

Before writing anything, go and look. Do not summarise from memory of the conversation alone.

- **Working tree or repo:** `cd` to the directory. Run `git status`, `git log --oneline -20`, `git diff --stat`. Read the files that actually changed.
- **Branch:** diff it against its base. `git log --oneline <base>..HEAD` and `git diff --stat <base>...HEAD`.
- **Conversation or session:** use what is in front of you.
- **User instructions:** read the actual instructions file, do not paraphrase from memory.

Never invent progress, status or numbers. "Not known" is a real finding and belongs on the page.

## Step 2 — build the page

> Create a single page HTML summary of the conversation, branch, work tree or user instructions. Make it visual and digestible without additional cognitive fatigue. Minimal text, clear flow of information. Opt for charts and diagrams over long explanations. Default to clean off-white background, `#333333` text. Create a flow for the user to follow and use typography design principles — spacing, line height, balanced text, and Z and F reading patterns.

Concretely, that means:

**One file.** Self-contained HTML. No build step, no CDN, no external assets, no framework. Inline SVG only.

**Flow.** The page is a path, not a pile. Each section answers the question the previous one raised. Start with the answer, never a preamble.

1. Title plus one line — what this is
2. At a glance — three to five facts, states or numbers
3. The body — carried by visuals, not paragraphs
4. What is open or next — omit if genuinely empty

**Reading patterns.** Top of page is scanned in a Z: put the title top-left, the single most important fact top-right, and the entry into the body along the diagonal. Below that, text-heavy sections are scanned in an F: front-load every heading and every bullet with the word that matters, because the right-hand end of each line does not get read.

**Visual over verbal.** Reach for the picture first:
- sequential → a flow or timeline
- quantity or change → a chart
- something that changed → two columns, before and after
- parallel items → a short table

If a paragraph is doing a diagram's job, replace it.

**Typography.**
- System font stack.
- Body 16px minimum. Line height 1.5 or more.
- Measure capped near 65 characters — this is what "balanced text" means here; long lines are the main cause of reading fatigue.
- One large title, clear section headings, nothing competing in between.
- Left aligned. Never justify — justification opens rivers of white space that break scanning.
- Generous spacing. Space between sections should be clearly larger than space within them, so the eye gets the grouping without a border.

**Colour.**
- Background `#FAF9F7`. Ink `#333333`. One accent.
- Supporting tones: muted text `#6B6B6B`, hairlines `#E5E2DE`, raised surfaces `#F2EFEB`.
- No pure white, no pure black, no gradients behind text.

**Constraints.** No paragraph longer than two sentences. Bullets under ten words. Must survive Print to PDF — no fixed viewport heights, nothing that only appears on scroll. No animation, no decoration, no dark variant.

## Step 3 — write the file

Write to `summary-<slug>-<YYYY-MM-DD>.html` in the working directory, or where the user says.

## Step 4 — reply

A short plain-language note, then the path. Keep it under 100 words, no jargon, lead with the answer. The page is the deliverable; this is just so they know what they are opening.

```
<One line: what the page covers.>

<Two or three sentences: what it found, in plain words.>

<path/to/summary-slug-date.html>
```

Nothing else. No mode suggestions, no offers, no next-steps list they did not ask for.
