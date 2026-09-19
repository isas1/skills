# Animated mode

Motion guides the eye. It never gates the information.

## The rule that decides everything

The page must be fully readable with JavaScript off, animation off, and at the moment of first paint. Write the finished page first, then add motion on top. If removing every animation loses meaning, the motion was carrying content and that is a bug.

## No libraries

Use CSS and SVG only. Both are already in the browser, both are zero bytes, both print.

- Transitions and `@keyframes` for anything that moves, fades or scales.
- `stroke-dasharray` and `stroke-dashoffset` for drawing lines, paths and progress arcs.
- CSS counters or a simple `@keyframes` on a clipped column for counting numbers up.
- `animation-delay` for staggering a list or a row of cards.
- `IntersectionObserver` in a dozen lines of inline script only if you need a reveal on scroll, and only to add a class. Content is in the DOM either way.

Do not add GSAP, anime.js, Motion, Lottie or anything else. A CDN link breaks the one-file rule and dies offline, and a page that summarises work should still open in five years.

## What to animate

- The single number that matters: count it up once, then stop.
- A flow or timeline: draw the connecting line left to right, once.
- A chart: grow bars or draw the line from zero, once, in under 600ms.
- Sections: fade and rise 8px as they enter, staggered by 60ms.
- State: a slow calm pulse on anything blocked or waiting. Nothing else loops.

## What not to animate

- Body text. Never fade in a paragraph.
- Anything above the fold that delays the headline or the status.
- More than one thing at a time in the same area.
- Anything on a loop that is not communicating a live state.

## Budget

- Entrance animations finish within 1 second of load, total.
- `transform` and `opacity` only. No animating layout properties.
- Easing: `cubic-bezier(0.22, 1, 0.36, 1)` for entrances, linear for loops.

## Required

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

@media print {
  *, *::before, *::after { animation: none !important; transition: none !important; }
}
```

Every animated element must have its final state as its default style, with the animation moving it from an offset back to that state. Never leave an element at `opacity: 0` waiting for JavaScript.
