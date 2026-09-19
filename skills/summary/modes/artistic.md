# Artistic mode

The page still has to be read in thirty seconds. Design is in service of that, not on top of it.

## The test this mode has to pass

**If the artistic page could be mistaken for the default page, it has failed.** Someone should be able to tell the two apart from across the room, before reading a word.

Restraint is the default skill's job. This mode is not "the default, but tidier". It is allowed to be striking.

## One organising idea

Pick a single visual motif and let it run through the whole page. Not five ideas, one.

The motif has to come from the data, not from a mood board. Work out what shape the content actually is, then let that shape become the page:

- three things that must stay identical, so three columns locked to one rule
- something nearly full, so a vessel filling
- a sequence with a point of no return, so a line that changes at that point
- a thing measured against a limit, so the limit drawn as a hard edge everything sits against

Name the motif to yourself in one sentence before you write any markup. If you cannot, you do not have one yet.

## Scale

Flat scale is what makes a page read as a document.

- **One element must be at least five times the body size.** A number, a word, a mark. It is the first thing seen and it carries the headline fact.
- Set the second level well below it. Big gaps between levels, not a gentle ramp.
- A page where everything sits between 13px and 40px has no hierarchy, only sections.

## Ornament is data or it is nothing

Every mark on the page encodes something. No decoration that carries no information.

A field of hairlines where the count is the commit count. A dot grid where the filled dots are the finished items. An arc whose sweep is the percentage. Rules whose weight tracks importance. If you cannot say what a mark means, delete it.

## Break the grid

- Let at least one element bleed to the edge of the page.
- Asymmetry over symmetry. Weight to one side, space on the other.
- Overlap is allowed: type over rule, number behind label, a mark crossing a section boundary.
- Vary the rhythm. A tall quiet section next to a dense one reads better than six even ones.

## Colour

You may use real colour here, which the default skill does not.

- Keep the off-white ground and the dark ink. Everything else is yours.
- Three or four hues maximum, and each one means something specific and consistent.
- Tints and washes are allowed as surfaces. Never behind body text.
- Monochrome is still a valid answer, but choose it, do not default into it.

## Texture

Reach for these before reaching for more words:

- hairline fields and dot grids
- SVG `feTurbulence` as a fine grain at low opacity
- overprint, using `mix-blend-mode: multiply` on a tint
- a single continuous stroke drawn as one path, no visible seams

## Type

- A display face for the title if one is available locally. Otherwise the system stack at a weight and size the default page would never use.
- Contrast the display face against mono for data and labels. That pairing does most of the work.
- Never load a webfont from a CDN. Vendor it or use what is there.

## Motion

Optional. If used, it is slow, seamless, and ignorable after the first look. A reveal on load, a loop long enough not to distract. It must never be required to understand the page, and it must vanish cleanly in print.

## Optional reference

If you can reach it, [Forever AI Components](https://github.com/isas1/forever-ai-components) is a catalogue of zero-dependency single-file components. Read the index, open two or three that fit, take the craft and rewrite it inline. Never add a dependency. Two borrowed elements maximum.

This is a garnish, not the brief. The motif above is the brief.

## Still true

Everything in the core skill still applies, with one exception: the budget gets tighter here, not looser. Self contained, one file, print safe, under 200 words of prose, and every section carries a drawing. A beautiful page that hides the status has failed.
