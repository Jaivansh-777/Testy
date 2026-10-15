# Wolf Edition — BMW M8 Competition Cinematic Customisation

## Overview

A production-quality, static automotive customisation website built from scratch using HTML5, modern CSS, vanilla JavaScript, and GSAP ScrollTrigger. The experience is driven by the existing `gemini_generated_video_7a13c85f.mp4` video asset, treated as one continuous 10s cinematic film combining the reveal and transformation.

## Files Created

| File | Description |
|------|-------------|
| `index.html` | Main HTML structure with 6 chapters, film hero, navigation, and all asset references |
| `styles.css` | Visual design system: obsidian-black backdrop, icy-blue accents, Archivo/Inter typography, GSAP-driven reveals, responsive grid, reduced-motion fallback |
| `script.js` | Core interactivity: video setup, GSAP timelines (scrubbed desktop, autoplay-loop mobile), flow reveals for chapters 3–6, progress bar, nav scroll state, play-fallback |
| `assets/frame-poster.jpg` | Extracted poster frame (t=2.0s) from the video |
| `assets/frame-front.jpg` | Extracted front frame (t=1.0s) |
| `assets/frame-rear.jpg` | Extracted rear frame (t=7.6s) |
| `assets/frame-side.jpg` | Extracted side frame (t=5.6s) |
| `assets/frame-side2.jpg` | Extracted side2 frame (t=9.6s) |
| `assets/crop-wolf.jpg` | Close-up crop of the wolf graphic (from detail frame) |
| `assets/crop-wheel.jpg` | Close-up crop of alloy wheel (from detail frame) |
| `assets/crop-glow.jpg` | Close-up crop of electric-blue underglow (from detail frame) |
| `assets/crop-hood.jpg` | Close-up crop of glossy hood/roofline (from poster frame) |

## Media Usage

- **Primary video**: `gemini_generated_video_7a13c85f.mp4` — 10.027s, 1280×720, 24fps, h264/mp4a. Located at root; never moved, overwritten, or duplicated.
- **Poster/image assets**: 6 extracted frames + 4 close-up crops, all derived from the video using ffmpeg. Never claim these are from outside the source footage.
- **No new video footage** is generated or fabricated. All visuals either come from the real video or are tasteful CSS/CGP compositions referencing the real frames.

## Chapters / Scroll-Led Narrative

| Chapter | Section | Key Elements |
|---------|---------|-------------|
| 01 — The Reveal | `.chapter--one` | Near-black transition into video, "WOLF EDITION" title, "BMW M8 Competition · Coupé" descriptor, minimal scroll cue. Video remains the visual focus. |
| 02 — The Transformation | `.chapter--two` | Pinned transformation blocks: Precision / Protection / Personalisation. Short copy animated via GSAP. Same video timeline. |
| 03 — The Wolf Identity | `#identity` | "BUILD TO STAND APART / BLACK. ICE. INSTINCT." editorial. Close-up of wolf graphic (real crop). Concept artwork only. |
| 04 — Protection & Finish | `#finish` | Paint correction, ceramic top coat, self-healing PPF. Service details as concept placeholders. |
| 05 — Wheels & Light | `#wheels` | Dark multi-spoke alloys, electric-blue underglow, brake detailing. Visual emphasis over generic card grids. |
| 06 — The Final Form | `#contact` | Full-car composition from real video frame. Contact CTA, service navigation, footer with configurable placeholders. |

## Technology Stack

- **HTML5** with semantic elements, correct viewport metadata, accessible descriptions
- **Modern CSS** with CSS custom properties (design tokens), `@media` responsive queries, `prefers-reduced-motion` support
- **Vanilla JavaScript** — no React, no build system, no TypeScript
- **GSAP 3.12.5** + **ScrollTrigger** via reliable CDN (no local build dependency)
- **ffmpeg** (locally installed during development only) for frame extraction — not a runtime dependency

## Scroll Behavior

- **Desktop (≥769px, no reduced motion)**: Full scroll-driven scrub. Film height 340vh; video time mapped to scroll progress with lerp smoothing. Chapters 1–2 animate out, chapters 3–6 animate in as user scrolls. Progress bar at top. Navigation shadow on scroll.
- **Mobile (<769px)**: Film height 100vh (graceful non-pinned fallback). Video autoplay muted loop. Overlays animated with a time-based looping timeline (~10s) that stays in sync with the video. User scrolls normally to chapters 3–6. No horizontal overflow.
- **Reduced motion**: `.reduced` class added; film height 100vh; video shows poster with no autoplay; all content visible static; no GSAP animations.

## Accessibility & Quality

- `skip-link` to main content
- `focus-visible` styles on all interactive elements
- Video: `muted`, `playsinline`, `preload="auto"`, poster fallback on error
- `clipPath` reveals for imagery; `clipPath` string animation supported by GSAP
- Keyboard navigation throughout
- No console errors on standard desktop/mobile loads
- All relative asset paths verified correct

## Configuration Before Launch

Placeholders that must be replaced:

| Placeholder | Location | Example Replace |
|------------|----------|-----------------|
| Studio address / phone / email | Footer `.footer__col` | `123 Design District, 54321` / `+44 20 1234 5678` / `studio@wolfedition.com` |
| Testimonials / pricing | Not fabricated — leave as "Configure before launch" | N/A |
| Business name "Wolf Edition Studio" | Footer | Keep or replace if branding differs |
| Contact CTA `mailto:` link | `.final__cta-copy` | `mailto:studio@example.com?subject=Wolf%20Edition%20commission%20enquiry` |

## Run & Preview Instructions

1. Start a local server from the workspace root:
   ```bash
   python3 -m http.server 8082
   ```
   Then open `http://localhost:8082` in a browser.

2. Or open `index.html` directly (some GSAP features may require a server for CDN module resolution).

3. Verify:
   - Film hero loads with video poster, then transitions into the video.
   - Scroll-driven reveals work on desktop (≥769px).
   - Mobile viewport (<769px) shows autoplay video loop with chapter overlays.
   - Reduced-motion preference (`prefers-reduced-motion: reduce`) strips animations and shows static content.
   - All navigation links and CTA buttons are functional.
   - No console errors.

## Summary of Changes

- **Created**: `index.html`, `styles.css`, `script.js`
- **Generated from video**: 10 asset files in `assets/` (6 poster frames + 4 close-up crops) using ffmpeg
- **Source video used**: `gemini_generated_video_7a13c85f.mp4` — 3.86MB, 10.027s, 1280×720, never moved or overwritten
- **No nonexistent assets**: every `src`/`href` in `index.html` references an actual file present in the workspace
- **Files that would have been overwritten/deleted**: none — the source video is preserved at its original path