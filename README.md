# skills

Two summary skills. One is short, one has options. They route between themselves so you never pick manually.

| Skill | Say | You get |
|---|---|---|
| [`simple-summary`](skills/simple-summary/SKILL.md) | "simple summary", "eli5", "quick summary" | An ELI5 message in chat, plus one plain HTML file |
| [`summary`](skills/summary/SKILL.md) | "summary" + anything: a mode, a look, an audience | One HTML page, with modes |

Ask for a summary with nothing attached and you get the simple one. Attach something — "make it ADHD friendly", "make it look good", "animate it", "for a client" — and the full skill picks it up.

## Modes

Only `summary` has these. They stack; accessible wins where it conflicts.

| Mode | Say | Does |
|---|---|---|
| Accessible | "ADHD friendly", "autistic", "dyslexia", "accessible" | [`modes/accessible.md`](skills/summary/modes/accessible.md) |
| Artistic | "make it look good", "artistic", "designed" | [`modes/artistic.md`](skills/summary/modes/artistic.md) |
| Animated | "animate it", "make it move" | [`modes/animated.md`](skills/summary/modes/animated.md) |

## House style

Both skills produce one self-contained HTML file. No build step, no CDN, no framework, no external assets. Off-white `#FAF9F7` ground, `#333333` ink, one accent, system fonts, inline SVG. Survives Print to PDF.

## Install

Copy a skill folder into your skills directory:

```sh
cp -r skills/simple-summary ~/.claude/skills/
cp -r skills/summary ~/.claude/skills/
```

Install both — they are designed as a pair and the routing depends on each knowing the other exists.

## Licence

MIT.
