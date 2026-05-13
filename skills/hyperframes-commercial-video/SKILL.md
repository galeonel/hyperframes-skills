---
name: hyperframes-commercial-video
description: Use to create a 9:16 commercial video in HyperFrames from a website or product page, with user journey, carousel, benefits, price, CTA, and final render.
---

# HyperFrames Commercial Video

Use this skill after inspecting the site with `mobile-dom-fidelity`.

## Video Structure

1. Intro with a short headline.
2. Scroll or entrance to the carousel.
3. Main product highlight.
4. Simulated product click.
5. Main benefits.
6. Price.
7. User choices.
8. Cart or checkout.
9. CTA or final confirmation.

## Interactive Journey

The video should feel like a real browsing session, not a slide sequence.
Model each action as cause and effect:

- scroll reveals the section;
- carousel moves through products;
- main card returns to the center;
- cursor clicks the card;
- product page enters;
- benefits appear;
- price and CTA receive focus;
- click leads to cart or checkout;
- final shows conclusion or approval.

## Composition Rules

- Vertical format: `1080x1920`.
- Use real text extracted from the DOM.
- Use local assets or permitted URLs.
- Register paused GSAP timelines in `window.__timelines`.
- Avoid render-time fetches.
- Avoid non-deterministic `Date.now()` and `Math.random()`.
- Every animated click must hit a visible component.

## Animation Patterns

- Titles: smooth type-in, without aggressive speed.
- Cards: entrance with `y`, `opacity`, and light `scale`.
- Carousel: horizontal movement with a pause on the main card.
- Click: cursor, ripple, micro-zoom, and focus shadow.
- Screen change: lateral transition from right to left.
- Product: light zoom on the main image and staggered benefit entrance.

## Click Mapping

Before animating a click, register:

```text
target selector:
visible from:
click time:
target rect:
click x/y:
post-click scene:
```

Do not accept the click if:

- the target is still invisible;
- the target is outside the viewport;
- another overlay covers the target;
- the cursor arrives before the entrance animation finishes.

## Required Validation

Before delivery:

```bash
npx hyperframes lint ./project
npx hyperframes validate ./project
npx hyperframes inspect ./project --samples 18
```

If there are simulated clicks, also validate:

- target exists;
- target is visible at the click timestamp;
- click center is inside the bounding box;
- no broken images;
- no overlapping text in key frames.

## Expected Output

- composition `index.html`;
- rendered MP4 video;
- validation summary;
- clean handoff folder, if needed.
