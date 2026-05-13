# HyperFrames Skills

Skills and instructions for creating vertical commercial videos with HyperFrames from real websites.

This package is designed around a reusable workflow:

1. Inspect a website through the DOM.
2. Extract real text, images, and components.
3. Build a HyperFrames composition in HTML.
4. Animate the user journey in 9:16 format.
5. Validate and render the final video.

The goal is to reproduce the feel of a real browsing session: the user enters
the site, scrolls to a section, interacts with cards, clicks products, sees
benefits, price, CTA, cart, and confirmation. The package prioritizes visual
fidelity to the reference website and motion polish, not slide-style videos.

## What's Included

- `skills/hyperframes-commercial-video`: main workflow for product-style commercial videos.
- `skills/mobile-dom-fidelity`: mobile-first inspection with DOM, console, and real selectors.
- `skills/hyperframes-motion-polish`: refinement for animations, clicks, scrolls, and transitions.
- `templates/project-brief/brief.md`: project brief template.
- `docs/workflow.md`: recommended end-to-end production workflow.
- `docs/motion-review.md`: review checklist for clicks, scrolls, transitions, and rhythm.

## Installation

Copy the folders inside `skills/` into your agent's skills directory.

Windows example:

```powershell
Copy-Item -Recurse .\skills\* $env:USERPROFILE\.codex\skills\
```

Then restart the agent so it loads the new skills.

## Recommended Usage

Use the skills in this order:

1. `mobile-dom-fidelity`
2. `hyperframes-commercial-video`
3. `hyperframes-motion-polish`

## Common HyperFrames Commands

```bash
npx hyperframes lint ./my-video
npx hyperframes validate ./my-video
npx hyperframes inspect ./my-video --samples 18
npx hyperframes render ./my-video --output final.mp4
```

## Legal Note

This package does not include assets, captures, cookies, tokens, MCP files,
inspection logs, or third-party proprietary material. When creating videos
based on real websites, only use content you have permission to reuse.
