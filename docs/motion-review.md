# Motion Review

Use this checklist when the video already renders but still needs to feel like
it was produced by a senior design and motion team.

## Second-by-Second Review

Create a simple table:

```text
Time     Intent                  Risk                     Fix
0-3s     Intro + first context    Text too fast            hold title + delay carousel
3-6s     Carousel movement        Empty bottom area        extend cards or adjust crop
8-12s    Product selection        Click before component   move click after entrance
12-16s   Price + CTA              CTA too high/cropped     reposition summary block
16-21s   Second product flow      Scroll feels stuck       shorten holds + power3.inOut
```

## Professional Click

A convincing click has four layers:

1. Cursor moves with natural easing.
2. Component is already visible and stable.
3. Ripple or press appears at the exact point.
4. Clicked region gets a light zoom and temporary shadow.

Use a small zoom:

```text
scale: 1.015 a 1.035
duration in: 0.16 a 0.22s
duration out: 0.28 a 0.40s
ease: power2.out or power3.out
```

## Professional Scroll

- Use `power3.inOut` for UI scrolls.
- Avoid long scrolls with no intermediate events.
- Do not animate children in the opposite direction while the container scrolls.
- After an important choice, hold for at least a few frames before the next scroll.

## Carousel

The carousel should feel like a living area of the site:

- entrance emerging onto the screen;
- continuous horizontal movement;
- cards without artificial borders if the original site does not use them;
- subtle zoom when the main card reaches the center;
- precise return to the card that will be clicked;
- click only after the card stabilizes.

## Screen Transitions

To simulate navigation:

- prefer lateral entrance from right to left;
- add a light flash or short fade only as support;
- do not cut off the previous click feedback;
- let the new screen enter with the first component already recognizable.

## Low-Quality Signals

Fix before delivery:

- cursor clicking empty space;
- text over image without contrast;
- card cropped unintentionally;
- button partially outside the screen;
- frame static for more than 1 second without reason;
- benefits appearing and disappearing too quickly;
- transition with inconsistent direction.
