# skills

Three skills for explaining and summarising work. They route between themselves on **what you want to end up holding**, not on which words you used.

| You want | Skill | You get |
|---|---|---|
| To understand something | [`eli5`](skills/eli5/SKILL.md) | A plain-language answer in chat. Never a file. |
| A page to look at or send | [`simple-summary`](skills/simple-summary/SKILL.md) | One HTML page. No options. |
| A page with a look or an audience | [`summary`](skills/summary/SKILL.md) | One HTML page, with modes. |

So `eli5 this regex` explains it in chat, `simple summary` writes a page, and `summary, make it ADHD friendly` writes a page in accessible mode.

## Modes

Only `summary` has these. They stack; accessible wins where it conflicts.

| Mode | Say | Spec |
|---|---|---|
| Accessible | "ADHD friendly", "autistic", "dyslexia", "accessible" | [`modes/accessible.md`](skills/summary/modes/accessible.md) |
| Artistic | "make it look good", "artistic", "designed" | [`modes/artistic.md`](skills/summary/modes/artistic.md) |
| Animated | "animate it", "make it move" | [`modes/animated.md`](skills/summary/modes/animated.md) |

## House style

`simple-summary` and `summary` build the same page, to the same spec:

> Create a single page HTML summary of the conversation, branch, work tree or user instructions. Make it visual and digestible without additional cognitive fatigue. Minimal text, clear flow of information. Opt for charts and diagrams over long explanations. Default to clean off-white background, `#333333` text. Create a flow for the user to follow and use typography design principles such as spacing, line height, balanced text, and Z and F reading patterns.

One self-contained file. No build step, no CDN, no framework, no external assets. `#FAF9F7` ground, `#333333` ink, one accent, system fonts, inline SVG, 65-character measure. Survives Print to PDF.

Both read the actual target before writing (`git status`, `git log`, `git diff`, the changed files) rather than summarising from memory.

## Install

```sh
cp -r skills/eli5 ~/.claude/skills/
cp -r skills/simple-summary ~/.claude/skills/
cp -r skills/summary ~/.claude/skills/
```

Install all three. The routing in each description depends on the others existing.

## Licence

MIT.
