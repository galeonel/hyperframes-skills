---
name: mobile-dom-fidelity
description: Use when recreating a real website's mobile-first experience in HyperFrames by inspecting DOM, console, selectors, text, images, and components before creating animations or videos.
---

# Mobile DOM Fidelity

Use this skill before writing the composition. The source of truth is the real
site in a mobile viewport, not a static screenshot.

## Workflow

1. Open the URL in a browser with a mobile viewport.
2. Define a reference breakpoint, usually `390x844`, `393x852`, `414x896`, or nearby.
3. Inspect the DOM sections that will appear in the video.
4. Extract text, `href`, `src`, `alt`, main classes, roles, and interactive states.
5. Map click coordinates only after confirming the component is visible.
6. List relevant states: before click, after click, after scroll, cart, checkout, or confirmation.

## MCP DevTools / console

When MCP DevTools is available, use it to query the real DOM through the
console. Examples of data to extract:

```js
const el = document.querySelector("SECTION_SELECTOR");
const rect = el.getBoundingClientRect();
({
  text: el.innerText,
  rect: { x: rect.x, y: rect.y, width: rect.width, height: rect.height },
  classes: el.className,
  images: [...el.querySelectorAll("img")].map((img) => ({
    src: img.currentSrc || img.src,
    alt: img.alt,
    width: img.naturalWidth,
    height: img.naturalHeight,
  })),
  links: [...el.querySelectorAll("a")].map((a) => ({
    text: a.innerText,
    href: a.href,
    classes: a.className,
  })),
});
```

To validate a click:

```js
const target = document.querySelector("TARGET_SELECTOR");
const r = target.getBoundingClientRect();
({ centerX: r.x + r.width / 2, centerY: r.y + r.height / 2, visible: r.width > 0 && r.height > 0 });
```

Use these values to define cursor timing and position in the composition.

## What to Capture

- Exact product names.
- Benefits exactly as they appear.
- Prices and conditions.
- Buttons and CTAs.
- Main images.
- Carousel cards.
- Stable selectors for click validation.

## Rules

- Do not invent copy if the DOM provides the text.
- Do not click components before they appear in the timeline.
- Do not use screenshots as the only source of structure.
- Do not publish snapshots, cookies, logs, or inspection files.
- If the site uses lazy loading, wait for images to load before extracting `src`.

## Expected Handoff

Produce a short map:

```text
Scene: Product carousel
Selector: .rf-cards-scroller-platter
Visible at: 2.0s
Action: horizontal scroll
Click target: card link, center x/y after card returns to center
Required text: ...
Required images: ...
```

Use this map to guide the HyperFrames composition.

## Fidelity Criteria

Consider the section faithful only when:

- text matches the original DOM;
- images are the same or permitted equivalents;
- spacing follows the mobile hierarchy;
- cards, buttons, and labels use the same visual order;
- click happens inside the real component bounding box;
- component is rendered before the cursor action.
