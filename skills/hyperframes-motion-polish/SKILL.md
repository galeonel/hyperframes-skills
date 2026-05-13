---
name: hyperframes-motion-polish
description: Use to refine already functional HyperFrames videos by improving fluidity, CTR, clicks, scrolls, transitions, overlaps, rhythm, and visual focus without rewriting the whole project.
---

# HyperFrames Motion Polish

Use this skill when the video already exists but needs to feel more premium and fluid.

## Segment Diagnosis

Divide the timeline into 3- to 5-second blocks:

- What should the viewer understand in this segment?
- Which element receives focus?
- Does the cursor click the correct target?
- Has the component already appeared before the click?
- Is there a long pause without movement?
- Is any text or image cropped?

## High-Impact Adjustments

- Move click feedback closer to cursor contact.
- Reduce pauses between benefits and price.
- Use `power3.inOut` for UI scrolls.
- Use `power2.out` or `power3.out` for text and card entrances.
- Avoid child animations fighting the parent container scroll.
- Apply a small focus zoom on the click target, between `1.015` and `1.035`.
- Use a temporary shadow to guide the eye.

## Common Fixes

### Cursor clicks empty space

- Delay the click until the component finishes entering.
- Recalculate `x/y` from the DOM bounding box.
- If the container scrolls, validate position after the scroll, not before.

### Overlapping text

- Increase the interval between entrances.
- Reduce the block scale, not only the font size.
- Reduce visible copy per frame.
- Ensure fixed heights for cards and buttons.

### Lifeless carousel

- Make the carousel emerge with `y`, `opacity`, and light `scale`.
- Animate the horizontal axis with a pause on the central card.
- Apply subtle zoom to the selected card.
- Remove borders or shadows that do not exist on the original site.

### Static segment

- Turn pauses into micro-motion: light parallax, subtle breathing, cursor preparing the next action.
- Shorten holds where there is no important reading.
- Show benefits and price in a more compact sequence.

## CTR Checklist

- Product appears early.
- Benefit appears before price.
- Price appears on a clean screen.
- CTA receives visual focus.
- Cursor shows the journey without feeling random.
- Transition to checkout feels like a consequence of the click.

## Validation

Use `npx hyperframes inspect` with enough samples:

```bash
npx hyperframes inspect ./project --samples 18
```

If possible, generate snapshots at the seconds criticized by the client and review:

- first frame;
- first click;
- main product;
- benefits;
- price;
- checkout;
- confirmation.

Make surgical changes: adjust timings, easings, offsets, scale, and opacity before restructuring HTML.
