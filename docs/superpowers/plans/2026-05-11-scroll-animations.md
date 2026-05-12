# Scroll Animations Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add scroll-triggered reveal animations for h2/h3 headings and a subtle parallax float effect on key sections, sitewide.

**Architecture:** A small vanilla JS script in Layout.astro initializes an IntersectionObserver (auto-targets all h2/h3 + any `.reveal` element) and a rAF-based parallax loop (targets `.parallax` elements). CSS classes in global.css control the visual states. No external libraries.

**Tech Stack:** Vanilla JS, IntersectionObserver, requestAnimationFrame, CSS transitions, Astro

---

### Task 1: Add scroll-reveal CSS to global.css

**Files:**
- Modify: `src/styles/global.css`

- [ ] **Step 1: Add the reveal initial + visible states after the existing `@keyframes fadeUp` block**

Open `src/styles/global.css`. After the `.anim-delay-3` rule (line ~248), add:

```css
/* ── Scroll-reveal ──────────────────────────── */
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition:
    opacity 0.65s cubic-bezier(0.22, 1, 0.36, 1),
    transform 0.65s cubic-bezier(0.22, 1, 0.36, 1);
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }

/* ── Parallax ───────────────────────────────── */
.parallax {
  will-change: transform;
}
```

- [ ] **Step 2: Verify the `prefers-reduced-motion` block still covers these classes**

Check that the existing rule at the bottom of global.css reads:
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```
This already covers `.reveal` via the `*` selector — no change needed.

- [ ] **Step 3: Commit**

```bash
git add src/styles/global.css
git commit -m "feat(animations): add scroll-reveal and parallax CSS classes"
```

---

### Task 2: Add IntersectionObserver + parallax script to Layout.astro

**Files:**
- Modify: `src/layouts/Layout.astro`

- [ ] **Step 1: Add the script block before the closing `</body>` tag in Layout.astro**

Open `src/layouts/Layout.astro`. Before `</body>`, add:

```astro
<script>
  /* ── Scroll animations — init on every page load (incl. ViewTransitions) ── */
  function initScrollAnimations() {

    /* 1. Scroll-reveal: auto-target h2, h3 and any .reveal element */
    const revealTargets = document.querySelectorAll<HTMLElement>(
      'h2:not(.no-reveal), h3:not(.no-reveal), .reveal'
    );

    revealTargets.forEach(el => el.classList.add('reveal'));

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
          } else {
            entry.target.classList.remove('visible');
          }
        });
      },
      { threshold: 0.12, rootMargin: '0px 0px -40px 0px' }
    );

    revealTargets.forEach(el => observer.observe(el));

    /* 2. Parallax: targets .parallax elements */
    const parallaxEls = Array.from(
      document.querySelectorAll<HTMLElement>('.parallax')
    );

    if (parallaxEls.length === 0) return;

    let ticking = false;

    function updateParallax() {
      parallaxEls.forEach(el => {
        const rect = el.getBoundingClientRect();
        const vh = window.innerHeight;
        // Only run when element is near viewport
        if (rect.bottom < -200 || rect.top > vh + 200) return;
        const speed = parseFloat(el.dataset.parallaxSpeed ?? '0.07');
        const center = rect.top + rect.height / 2 - vh / 2;
        el.style.transform = `translateY(${center * speed}px)`;
      });
      ticking = false;
    }

    function onScroll() {
      if (!ticking) {
        requestAnimationFrame(updateParallax);
        ticking = true;
      }
    }

    window.addEventListener('scroll', onScroll, { passive: true });
    updateParallax();
  }

  /* Run on initial load and after every Astro ViewTransition */
  document.addEventListener('astro:page-load', initScrollAnimations);
</script>
```

**Important:** `h2:not(.no-reveal)` means any `h2` that should be excluded (e.g. inside the nav) can have `class="no-reveal"` added to it.

- [ ] **Step 2: Commit**

```bash
git add src/layouts/Layout.astro
git commit -m "feat(animations): add IntersectionObserver reveal + parallax rAF script"
```

---

### Task 3: Add .parallax class to key sections in index.astro

**Files:**
- Modify: `src/pages/index.astro`

- [ ] **Step 1: Add `.parallax` to the reviews section**

Find the line:
```html
<section style="background-color:#0e0e0e; padding:90px 20px;">
```

Change to:
```html
<section class="parallax" style="background-color:#0e0e0e; padding:90px 20px;">
```

- [ ] **Step 2: Add `.parallax` to the center text block in service grid row 2**

Find:
```html
<div class="flex flex-col items-center justify-center text-center" style="height: 785px; background-color: #1e1e1e; padding: 40px 50px;">
```

Change to:
```html
<div class="flex flex-col items-center justify-center text-center parallax" style="height: 785px; background-color: #1e1e1e; padding: 40px 50px;">
```

- [ ] **Step 3: Commit**

```bash
git add src/pages/index.astro
git commit -m "feat(animations): apply parallax to index review and team sections"
```

---

### Task 4: Verify in browser

**Files:** none

- [ ] **Step 1: Start the dev server**

```bash
cd ruska-media-site && npm run dev
```

Open `http://localhost:4321` (or whichever port Astro uses).

- [ ] **Step 2: Check scroll-reveal on h2 elements**

Scroll down past the service grid. Each `h2` card title (Filmi & Video, Lyhytvideot, Valokuvaus jne.) should fade up into view as it enters the viewport. Scrolling back up should reset them to hidden so they animate again on the way back down.

- [ ] **Step 3: Check parallax float**

The reviews section and the center text block should drift slightly as you scroll — rising gently as you approach, settling as you pass. The effect should be subtle (~20–40px range), not jarring.

- [ ] **Step 4: Check .no-reveal escape hatch works**

The Nav `h2` or any heading inside the nav should NOT animate (none exist currently, but confirm no unintended elements are targeted).

- [ ] **Step 5: Check reduced motion**

In browser DevTools → Rendering → Emulate CSS media: `prefers-reduced-motion: reduce`. All animations should be disabled — elements appear instantly without transitions.

- [ ] **Step 6: Check a service page (e.g. /lyhytvideo)**

Navigate to a service page. H2/H3 headings should reveal on scroll there too, since Layout.astro wraps all pages.

- [ ] **Step 7: Final commit if all looks good**

```bash
git add -p
git commit -m "feat(animations): scroll-reveal and parallax animations complete"
```
