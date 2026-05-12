# Scroll Animations — Design Spec
**Date:** 2026-05-11
**Project:** ruska-media-site

## Goal
Add scroll-triggered reveal animations to all text headings and a subtle parallax float to key sections, sitewide.

## Implementation

### 1. Scroll-Reveal (IntersectionObserver)
- **Target**: all `h2`, `h3` elements auto-targeted globally; any element with `.reveal` class
- **Initial state**: `opacity: 0; transform: translateY(28px)`
- **Triggered state**: `opacity: 1; transform: translateY(0)` — transition `0.65s cubic-bezier(0.22, 1, 0.36, 1)`
- **Reset on exit**: yes — elements return to hidden when scrolled past, so effect replays in both directions
- **Stagger**: `.reveal-delay-1` (0.1s), `.reveal-delay-2` (0.2s), `.reveal-delay-3` (0.3s) for manual staggering
- **Threshold**: `0.12` — triggers when 12% of element is visible

### 2. Parallax Float (scroll + rAF)
- **Target**: elements with `.parallax` class
- **Effect**: subtle vertical translate based on scroll position, speed controlled by `data-parallax-speed` attribute (default `0.07`)
- **Range**: element floats ±~40px relative to its natural position
- **Performance**: `requestAnimationFrame` loop, `will-change: transform`, only runs when section is near viewport

### 3. Where classes are added
- **Auto** (no manual work needed): all `h2`, `h3` on every page
- **Manual `.reveal`**: paragraphs and cards where scroll-in effect is desired
- **Manual `.parallax`**: review sections, team section, large content blocks

### 4. Code location
- CSS classes + keyframes → `src/styles/global.css`
- IntersectionObserver + parallax script → `<script>` in `src/layouts/Layout.astro`

### 5. Constraints
- `prefers-reduced-motion`: all animations disabled via existing CSS rule
- Astro ViewTransitions: re-init observers on `astro:page-load` event
- No external libraries
