---
name: summary
description: A single-page, self-contained HTML summary of a conversation, branch, work tree, repo or session, with optional modes — accessible (ADHD, autistic, dyslexia), artistic, animated — and audience variants for a client or a handover. Visual and digestible, diagrams and charts instead of long explanations. Use when the user asks for a summary with something attached to it: a mode, a look, an audience, a feeling. Examples: "summary, make it ADHD friendly", "recap but make it look good", "summarise this for a client", "wrap up and animate it", "handover page". If the user just wants the short plain version — "simple summary", "eli5", "quick summary" — use the `simple-summary` skill instead.
---

# summary

Turn whatever just happened into one HTML page a tired person can read in thirty seconds.

## Routing

This skill is the one with options. It owns modes, audience variants, and anything about how the page should look or feel.

If the request is bare — "simple summary", "eli5", "quick summary", or a summary with nothing attached — that is `simple-summary`, not this. Hand it over rather than producing a richer page than was asked for.

If you are already here and the user then asks for a mode, stay here. Do not re-route mid-task.

## Scope

Ask nothing if the target is obvious. Default target, in order:

1. What the user explicitly named (a branch, a PR, a file, a topic)
2. The current session
3. The current repo or working tree

If two targets are equally plausible, pick one, say which you picked in one line, and continue.

## Core rules

- One file. Self-contained HTML. No build step, no CDN, no external assets, no framework.
- Minimal text. No paragraph longer than two sentences. Bullets under ten words.
- Prefer a diagram, timeline, chart or table over a paragraph. Inline SVG only.
- Every section must earn its place. Cut anything that is only there for symmetry.
- Never invent progress, status or numbers. Unknown is a valid value and should be shown as such.
- Must survive Print to PDF: no fixed viewport heights, no content that only appears on scroll.
- Light by default. Add a dark variant only when the page will be viewed inside a container with its own theme setting.

## Write in the reader's own language

The page is for one person. Write it the way they write.

Use whatever you already know about them: memory, project files, their instructions file, the way they have been talking to you in this session. Match their register, their vocabulary, their sentence length, their spelling. If they write in short blunt lines, the page is short and blunt. If they use a particular word for a thing, use that word, not the textbook one.

If you know nothing about them, write plainly: short sentences, common words, no jargon, no corporate filler.

Do not announce that you are doing this.

## Typography

- System font stack unless the project has its own type. If it does, use the project's.
- Clean and plain is the default look. Ornament is opt in via artistic mode.
- Body text 16px minimum, line height 1.5 or more, measure capped near 65 characters.
- Real hierarchy: one large title, clear section headings, nothing in between competing.
- Off-white background `#FAF9F7`, ink `#333333`, one accent colour. No pure white, no pure black, no gradients behind text.
- Supporting tones: muted text `#6B6B6B`, hairlines `#E5E2DE`, raised surfaces `#F2EFEB`.
- Left aligned. Never justify.

## Structure

Start with the answer, not the preamble.

1. **Title plus one line.** What this is, in a sentence.
2. **At a glance.** Three to five short facts, states or numbers. Cards or a strip.
3. **The body.** The actual shape of the work, carried by visuals:
   - a flow or timeline for anything sequential
   - a chart for anything with quantity or change
   - a two-column before and after for anything that changed
   - a short table for anything with parallel items
4. **Decisions made.** One line each, with the reason.
5. **Open and next.** Unresolved questions, then next steps. Omit either if empty.

## Modes

The default above is the whole skill. Modes are optional. Read the file only if the user asks for that mode by name or clearly describes it.

| Mode | Say | Read |
|---|---|---|
| Accessible | "make it ADHD friendly", "autistic", "dyslexia", "accessible" | `modes/accessible.md` |
| Artistic | "make it look good", "artistic", "designed", "Forever" | `modes/artistic.md` |
| Animated | "animate it", "make it move" | `modes/animated.md` |

Modes stack. Accessible always wins where it conflicts with artistic or animated.

Suggest a mode when it would clearly help. Write the requested page first, then add one line at the end naming the mode and what it would change. Never ask before writing, never suggest more than one, and drop it if the user ignores it.

## Output

Write to `summary-<slug>-<YYYY-MM-DD>.html` in the working directory, or where the user says.

Then reply with the file path, plus at most one line suggesting a mode. The page is the summary. Do not repeat it in chat.

## Variants

- `summary for a client`: no internal jargon, no file paths, no ticket ids.
- `summary of the changes`: lead with before and after, then decisions.
- `summary for handover`: lead with current state and open questions.
