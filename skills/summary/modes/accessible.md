# Accessible mode

For readers who find dense pages expensive to process. Ask which profile only if the user has not said and the choice would change the page. Otherwise apply the shared rules, which help everyone.

## Shared rules

- One idea per block. Never two ideas in one sentence.
- Front load. The point first, the detail after, the context last or not at all.
- Concrete words. No metaphor, no idiom, no irony, no "leverage", no "unpack".
- Say the thing directly. "Three tests fail" not "there are some issues with the test suite".
- Every number gets a unit and a comparison. "12 files, up from 4" not "12 files".
- Generous whitespace. Space between blocks is the main tool, not borders and boxes.
- Nothing hidden behind a click. No accordions, no tabs, no tooltips holding real content.
- Consistent order. Same section order every time so the page is learnable.
- No auto-playing motion. Nothing that moves while text is being read.
- Respect `prefers-reduced-motion: reduce` and turn all motion off inside it.

## ADHD

- Hard cap: the page fits on two screens. If it does not, cut, do not shrink.
- Status and next action visible without scrolling.
- Each section is scannable in under five seconds: heading, then three bullets or one visual.
- Colour codes state (done, blocked, open) and the same colour means the same thing throughout.
- Put the next step in a single box at the top and repeat it at the bottom. Repetition is allowed here.
- No long lists. Six items maximum, then group.

## Autistic

- Literal headings. "What changed" not "The journey so far".
- Explicit structure. Say what the sections are, in order, in one line under the title.
- No ambiguity about state. If something is undecided, label it undecided.
- Separate fact from opinion visibly. Recommendations go in their own marked block.
- Predictable layout. Same grid, same spacing, no surprise full-bleed sections.
- Low sensory load. Muted palette, one accent, no flashing, no high-saturation fills.

## Dyslexia and reading difficulty

- Line height 1.6 to 1.8. Letter spacing slightly open. Word spacing normal or wider.
- Left aligned, ragged right, never justified.
- Keep the default off-white `#FAF9F7` and `#333333`. Offer the warmer ground `#FAF6F0` in one line after delivering, since many readers do not know to ask for it.
- Measure 55 to 70 characters.
- No italics for emphasis. Use weight or colour.
- No all caps. No condensed faces.
- Sans serif with distinguishable letterforms. Avoid faces where I, l and 1 are identical.
- Short paragraphs, one or two lines. Break long words rather than hyphenating across lines.

## AuDHD

Apply ADHD and autistic together. Where they conflict, the autistic rule wins on structure and labelling, the ADHD rule wins on length and priority.

## Always

Keep semantic HTML: real headings in order, real lists, real tables with headers. Alt text on every SVG. Contrast at least 4.5 to 1 for body text. The page must still make sense with styles off.
