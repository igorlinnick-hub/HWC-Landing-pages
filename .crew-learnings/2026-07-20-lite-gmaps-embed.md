---
date: 2026-07-20
project: HWC-Landing-pages
tags: [google-maps, lite-embed, performance, accordion]
type: pattern
---

## What
Added per-location Google Maps widgets to /aloha as tap-to-expand accordions. Same philosophy as the lite-video pattern: no iframe in the DOM until first tap — JS reads `data-map-src` and injects the iframe once. Embed URL needs no API key: `https://www.google.com/maps?q=<encoded address>&z=16&output=embed`. Deep link for native app: `https://www.google.com/maps/dir/?api=1&destination=<encoded address>`. Frame styled with 1px gradient border (teal→coral) via padded wrapper, expansion animated with `grid-template-rows: 0fr → 1fr` (no fixed heights).

## Why it matters
Three Google Maps iframes on load cost ~1MB+ JS each; lite pattern keeps the link-in-bio page instant while still giving embedded maps.

## Next time
- Query the street address WITHOUT the suite number in `q=` (suite can confuse the geocoder pin); keep suite in the directions deep link.
- iOS Safari can ignore `border-radius` clipping on iframes — add `-webkit-mask-image: -webkit-radial-gradient(white, black)` + `position:relative; z-index:0` on the clipping wrapper.
- `<button>` may only contain phrasing content — use `<span style="display:block">`, not `<div>`, or the city/address lines collapse inline.

## Link
aloha/index.html — `.location-map` / `.map-frame` / "LOCATION MAPS" script block
