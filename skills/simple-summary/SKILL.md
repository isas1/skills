---
name: simple-summary
description: An ELI5, succinct summary — a short plain-language message in chat, plus one self-contained HTML file. No modes, no options, no styling choices. Use when the user says "simple summary", "eli5", "eli5 summary", "quick summary", "just summarise this", "keep it simple", or otherwise asks for a summary while signalling they want the short version. If the user asks for a summary with any styling, mode or audience attached — accessible, ADHD, artistic, animated, for a client, for handover — use the `summary` skill instead.
---

# simple-summary

The short one. A person who is tired, busy or new asks what happened. Tell them, in chat, in plain words. Then leave one HTML file behind so they can look at it later or send it on.

## Routing

This skill is the plain path. Hand off to `summary` the moment the user attaches anything to the request:

| They say | Skill |
|---|---|
| "simple summary", "eli5", "quick summary" | this one |
| "summary" with nothing attached | this one |
| "summary, make it ADHD friendly" | `summary` |
| "summary, make it look good" / "artistic" | `summary` |
| "animate it", "make it move" | `summary` |
| "summary for a client" / "for handover" | `summary` |

Do not offer modes. Do not mention that the other skill exists. If they want more, they will ask, and `summary` will pick it up.

## Scope

Ask nothing if the target is obvious. Default target, in order:

1. What the user explicitly named (a branch, a PR, a file, a topic)
2. The current session
3. The current repo or working tree

If two targets are equally plausible, pick one, say which in one line, and continue.

## The chat message

Write this first, before the file. It is the deliverable the user actually reads.

Rules:

- ELI5. Explain it the way you would to a smart person who has not seen any of this.
- No jargon. If a technical term is unavoidable, define it in the same sentence.
- Succinct. Aim for under 150 words.
- Lead with the answer. No preamble, no "here is a summary of".
- Never invent progress, status or numbers. "Not known" is a valid answer and belongs in the message.
- Write in the reader's own language — match how they have been talking to you in this session. Do not announce that you are doing this.

### Template

Start from this. Edit it freely — it is a shape, not a script. Drop any section that has nothing real in it.

```
**<What this is, one line.>**

<One short paragraph: what happened, in plain words.>

**Where it stands**
- <fact or state, under ten words>
- <fact or state, under ten words>
- <fact or state, under ten words>

**Still open**
- <the unresolved thing, and who decides it>

<One line: the single next step, or the file path.>
```

## The HTML file

One file. Self-contained. No build step, no CDN, no external assets, no framework.

Same content as the chat message, laid out to be read on a screen:

1. Title plus one line.
2. Three to five facts at a glance.
3. The body — a flow, a short table, or a before and after. Inline SVG only.
4. What is open or next. Omit if empty.

House style, fixed, not negotiable:

- Off-white background `#FAF9F7`, ink `#333333`, one accent colour. No pure white, no pure black, no gradients behind text.
- Supporting tones: muted text `#6B6B6B`, hairlines `#E5E2DE`, raised surfaces `#F2EFEB`.
- System font stack. Body 16px minimum, line height 1.5 or more, measure capped near 65 characters.
- Left aligned. Never justify.
- Must survive Print to PDF: no fixed viewport heights, no content that only appears on scroll.

No animation. No decoration. No dark variant.

## Output

Write to `summary-<slug>-<YYYY-MM-DD>.html` in the working directory, or where the user says.

Reply with the chat message, then the file path on its own line at the end. Nothing else — no mode suggestions, no offers, no next-steps list the user did not ask for.
