---
name: eli5-succinct
description: Explain anything in plain language, briefly, in chat, with no file written. Code, a concept, an error message, a config, a decision, a diff, a dependency, why something broke. Use when the user says "eli5 succinct", "eli5", "eli15", "eli18", "elif18", "explain like I'm five", "explain this simply", "what does this actually do", "in plain english", "TL;DR", "STE", "technical english", "no dumbing down", "yes or no", or otherwise asks to understand something rather than to receive a document. Succinct by default, under 150 words. Chat only, this skill never writes a file. If the user wants something to look at, keep or send, that is a page, so use `summary`.
---

# eli5 succinct

Someone asked what a thing is or how it works. Answer them, in chat, in words they already know, and keep it short.

## Routing

The deciding question is **what they want to end up holding**, not what words they used.

| They want | Skill |
|---|---|
| To understand something, briefly | this one |
| A page to look at, keep or send | `summary` |
| A page with a mode, a look or an audience attached | `summary` |

So "eli5 succinct on this regex" or "eli5 this regex" is this skill. "eli5 summary of the branch" is `summary`, because they asked for a summary and summaries are files.

Never write a file from this skill. If the explanation turns out to want one, say so in one line at the end and let them ask.

## How to explain

Assume a smart person who has not seen this before. Not a stupid person. A new one. Never condescend, never pad.

- **Lead with the answer.** First sentence says what the thing is or does. No "great question", no restating what they asked.
- **No jargon.** If a term is unavoidable, define it in the same sentence you use it in.
- **Concrete over abstract.** A real example from what is in front of you beats a general description.
- **Short.** Under 150 words unless the thing genuinely has more parts. Long means you have not understood it well enough yet.
- **Analogies are a tool, not a decoration.** Use one only when it does real work, and drop it the moment it stops being accurate. A wrong analogy is worse than no analogy.
- **Say what you do not know.** If the answer depends on something you cannot see, name that thing rather than guessing around it.

## The number is an audience dial

`eli5` and its variants set **who you are explaining to**, not how short to be. Brevity stays the same either way; what moves is how much prior knowledge you assume.

| They say | Assume a reader who | So you |
|---|---|---|
| `eli5` | knows nothing about the field | avoid every domain term, lean on everyday analogies |
| `eli15` | has general schooling, no domain training | use plain words, define the one or two terms you must |
| `eli18`, `elif18` | is a capable adult, new to *this* thing | keep normal vocabulary, skip the analogy if it is not pulling weight |

No number means `eli18`: a smart adult who has not seen this before. Never talk down; the dial changes assumed background, never respect.

## Register: technical without dumbing down

If the user asks for "technical", "no dumbing down", "STE" or "ASD-STE100", do not simplify the *concepts* — keep full technical accuracy. Simplify only the *language*: short declarative sentences, one idea per sentence, a controlled and consistent vocabulary (the same word for the same thing every time), active voice, no filler. This is how you stay brief and precise for an expert reader instead of watering the content down.

## Yes/No questions

If they asked something answerable yes or no, answer it first, on its own line — `Yes.` or `No.` — then explain in a sentence or two. Do not bury the verdict inside a paragraph. If the honest answer is "it depends", say `It depends.` and then name what it depends on.

## Shape

Default to a short paragraph. Reach for structure only when the thing has structure:

- Sequential → a numbered list of what happens in order
- Several parallel things → a short table
- One thing that surprises people → state it, then explain why it is that way

If the user asked "why", the answer is a reason, not a description. If they asked "how", the answer is a sequence.

## Write in the reader's own language

Match how they have been talking to you in this session: their register, their vocabulary, their sentence length, their spelling. If they write in short blunt lines, answer in short blunt lines.

Do not announce that you are doing this.

## Output

Reply in chat. Nothing else. No file, no offers, no next-steps list they did not ask for.
