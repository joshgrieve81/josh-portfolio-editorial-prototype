# Josh Grieve Editorial Collage Portfolio Implementation Plan

> **For Hermes:** Use subagent-driven-development skill to implement this plan task-by-task if moving from prototype into a real repo.

**Goal:** Translate the GPT Image 2.0 collage/poster portfolio concept into a performant, accessible, animation-rich portfolio using Josh's current site content.

**Architecture:** Use semantic DOM/CSS/SVG as the primary rendering layer, GSAP + ScrollTrigger for scroll choreography, and optional WebGL only for future high-cost texture/image distortion moments. Keep the system componentized: typography, paper/sticker collage assets, project cards, rail/navigation, and scroll sections.

**Tech Stack:** Next.js or Astro, GSAP + ScrollTrigger, Lenis optional, CSS variables/design tokens, AVIF/WebP image assets, SVG doodles and marks.

---

## Direction Summary

The design should feel like **a designer's process wall coming alive as you scroll**: precise product-design systems underneath, punk/editorial collage layered above. The current site content supplies credibility and clarity; the GPT concept supplies energy, depth, and section identity.

### Source Content Pulled From Current Site

- Name/title: Josh Grieve — UX/UI Designer
- Positioning: Senior Product Designer focused on systems and platforms
- Status/CTA: Open for work
- Email: joshgrieve@gmail.com
- Tags: Product Design, Systems, Strategy, Craft
- Featured work:
  - “Dolly” Design System — scalable design system for a leading social technology company in Menlo Park, CA
  - Kelley Blue Book Deal Advisor — clearer vehicle pricing insights for confident negotiation
  - Netgear Total Network Solution — enterprise networking platform launch for PR60X Pro router
- About:
  - Josh is a Senior Product Designer based in Orange County, CA
  - He brings structure and clarity to complicated systems
  - Collaborated with Meta, Netgear, Kelley Blue Book, CoxAuto, Oculus, Redbull, etc.
  - Core goal: taking something complicated and making it feel human

---

## Art Direction Rules

1. **Use giant condensed typography as the identity anchor.** Preserve massive section titles, clipping, and overprint blocks.
2. **Keep chaos structured.** Every section needs one dominant headline, one clear content hierarchy, and one primary CTA.
3. **Use collage as depth, not decoration sludge.** Paper/tape/stickers should reinforce meaning: open-for-work, process notes, project metadata, contact details.
4. **Real content remains semantic HTML.** Do not bake important body copy into images.
5. **Mobile is a reinterpretation.** Stack sections, reduce decoration, and avoid forced horizontal scroll.

---

## Component System

```txt
src/components/
  layout/
    SiteHeader.tsx
    SectionRail.tsx
    AvailabilitySticker.tsx
  typography/
    SplitHeadline.tsx
    Kicker.tsx
  collage/
    PaperCard.tsx
    Tape.tsx
    Sticker.tsx
    Doodle.tsx
    Barcode.tsx
    TextureOverlay.tsx
  sections/
    HeroSection.tsx
    WorkSection.tsx
    AboutSection.tsx
    ContactSection.tsx
  animation/
    useGsapContext.ts
    useReducedMotion.ts
    SplitTextReveal.tsx
    ParallaxLayer.tsx
src/data/
  projects.ts
  clients.ts
  profile.ts
src/styles/
  tokens.css
  typography.css
  collage.css
  motion.css
```

---

## Animation Architecture

### Global

- Register GSAP plugins once.
- Scope animations per component using `gsap.context()`.
- Clean up animations on unmount.
- Gate all non-essential movement behind `prefers-reduced-motion`.
- Animate only transform/opacity/clip-path where practical.

### Hero

1. Header fades/slides in.
2. Rail draws top-to-bottom.
3. Giant headline reveals via clip/y transform.
4. Neon purpose block wipes in.
5. Portrait paper stack enters from right with slight rotation.
6. Tape/stickers/doodles drop into place with stagger.
7. CTA appears last.
8. Mouse parallax moves portrait, paper, and doodles at different rates.

### Work

Desktop:

- Pin the work section.
- Drive `.work-track` horizontally with ScrollTrigger.
- Scale/brighten active cards.
- Move project images internally for parallax.
- Update progress meter.

Mobile:

- Use vertical stacked cards.
- Disable pinning.
- Preserve card treatments and line-draw reveals.

### About

- Headline slides in left.
- Blue block wipes underneath `ME`.
- Collage stack rises.
- Right-hand process/tools panel staggers in.
- Doodles draw on as SVG strokes.

### Contact

- Form panel rises with paper-card rotation.
- Contact card drops into place.
- Field focus animates underline and label color.
- Success state becomes a stamped sticker.

---

## Build Phases

### Phase 1 — Static Design System

- Create design tokens.
- Implement typography scale.
- Build reusable paper/sticker/tape components.
- Build static semantic sections.
- Verify responsive layout.

### Phase 2 — Hero Motion

- Add GSAP hero timeline.
- Add mouse parallax.
- Add SVG doodle draw-on.
- Verify reduced motion.

### Phase 3 — Work Section

- Build project data model.
- Implement cards.
- Add horizontal pinning on desktop.
- Add vertical fallback on mobile.
- Verify scroll performance.

### Phase 4 — About/Contact

- Add collage parallax.
- Add form states and validation.
- Add final CTA/contact card.

### Phase 5 — Production Hardening

- Optimize images.
- Audit accessibility.
- Check Lighthouse.
- Test keyboard/focus states.
- Test Safari/iOS.
- Remove unused experimental code.

---

## Practical Next Step

Use the included `index.html` prototype as a creative/motion reference. If approved, move into a real Vite/Next/Astro repo and implement Phase 1 + Phase 2 first, then the selected-work pinned section.
