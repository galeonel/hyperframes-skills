# Production Workflow

## 1. Brief

Fill out `templates/project-brief/brief.md` with:

- Website URL.
- Main product.
- Target audience.
- CTA.
- Desired duration.
- Delivery format.

## 2. Mobile-First Inspection

Use the vertical breakpoint as the source of truth. For 9:16 videos, prioritize
the mobile experience:

- reference width: 390 to 430 px;
- reference height: 844 to 932 px;
- components visible before the click;
- real DOM text;
- real images used by the page.

When MCP DevTools or browser automation is available, use the DOM and console to
inspect the real structure. Do not base the reconstruction only on screenshots.
At minimum, extract:

- section selector;
- main div hierarchy;
- visible text;
- link `href` values;
- image `src` and `alt` values;
- classes for cards, buttons, carousels, and selectors;
- bounding boxes for click targets;
- state before and after scrolls or clicks.

## 3. Journey Storyboard

Organize the video as real navigation:

1. Site entry.
2. Scroll to the carousel or product section.
3. Product click.
4. Main benefits.
5. Price.
6. User choices.
7. Cart or checkout.
8. Confirmation or final CTA.

## 4. HyperFrames Composition

Create an `index.html` with:

- `data-duration`;
- 1080x1920 dimensions;
- scenes separated by logical regions;
- paused GSAP timeline;
- registered `window.__timelines`.

## 5. Polish

Validate fluidity:

- no clicks on empty space;
- no text overlap;
- no unintended image cropping;
- no stuck scrolls;
- transitions with consistent direction;
- focus zoom on important clicks.

For journey videos, review second by second:

- the component appears before the cursor arrives;
- the cursor touches the visual center of the target;
- click feedback happens immediately;
- the next screen enters as a consequence of the click;
- benefits and price do not stay static for too long;
- carousel movement pauses on the main card;
- lateral transitions preserve spatial orientation.

## 6. Validation

Run:

```bash
npx hyperframes lint ./project
npx hyperframes validate ./project
npx hyperframes inspect ./project --samples 18
```

Fix errors before rendering.
