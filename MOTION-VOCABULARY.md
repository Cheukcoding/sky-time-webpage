# The Motion Vocabulary

**15 effects to name in your prompt so your site stops looking like every other AI build.**

Most vibe-coded sites look generic for one reason: the prompt never named the motion. "Make it modern and animated" gets you a fade-in. Naming the actual technique gets you the thing you saw on Awwwards.

**How to use this:** pick 2–3 max. Copy the keyword string into your prompt verbatim. The designs you saw in my video were all designs I made on Variant (link in bio to try for free).

---

## Scroll-Driven

### 1. Sticky section stacking

Sections pin to the viewport and stack on top of each other like a deck of cards being dealt, each one sliding over the last.

- **Best for:** feature walkthroughs, product tiers, multi-step processes
- **Prompt keywords:** `sticky stacked scroll sections, position: sticky cards, each section pins and overlaps the previous with slight scale-down and shadow`
- **Stack:** CSS `position: sticky` alone, or GSAP ScrollTrigger for finer control

### 2. Scroll-velocity skew

Content subtly skews and stretches based on how fast you're scrolling, then settles when you stop. Almost invisible, but it makes the page feel like it has weight.

- **Best for:** editorial, portfolios, anything image-heavy
- **Prompt keywords:** `scroll velocity skew, momentum-based transform, lerp scroll position with easing, subtle skewY on fast scroll that returns to 0 on rest`
- **Stack:** Lenis + GSAP, or a custom `requestAnimationFrame` lerp

### 3. Depth-layered z-parallax

Not the usual background-moves-slower parallax — foreground, midground, and background move at genuinely different rates with blur applied to the far layer. Reads as actual depth.

- **Best for:** hero sections, landing pages with a strong central image
- **Prompt keywords:** `multi-layer z-depth parallax, three parallax planes at different scroll speeds, background layer with depth-of-field blur`
- **Stack:** GSAP ScrollTrigger, or CSS `perspective` + `translateZ`

### 4. Scroll-driven odometer counters

Numbers roll up like a slot machine or fuel pump when the stat block enters the viewport. Digit-by-digit, not a plain count-up.

- **Best for:** stats sections, pricing, "trusted by X" social proof
- **Prompt keywords:** `odometer number roll, digit-by-digit slot reveal on scroll into view, tabular-nums, staggered per-digit easing`
- **Stack:** GSAP + `IntersectionObserver`, or Framer Motion `useInView`

### 5. Pinned horizontal gallery

The page stops scrolling vertically and a gallery moves sideways instead, then vertical resumes. Different from horizontal parallax — this one hijacks the scroll entirely.

- **Best for:** case study collections, lookbooks, timelines
- **Prompt keywords:** `pinned horizontal scroll section, scroll-jacked sideways gallery with pin and release, ScrollTrigger horizontal panel translate`
- **Stack:** GSAP ScrollTrigger with `pin: true`

---

## Cursor & Hover

### 6. Magnetic elements

Buttons and links lean toward the cursor as it approaches, then snap back with a spring. The single highest ratio of "feels expensive" to "lines of code."

- **Best for:** CTAs, nav links, anything you want clicked
- **Prompt keywords:** `magnetic hover buttons, element translates toward cursor within proximity radius, spring return on mouse leave`
- **Stack:** GSAP `quickTo`, or Framer Motion springs

### 7. WebGL displacement hover

Images ripple, melt, or distort on hover using a noise texture. This is the one that separates studio sites from template sites.

- **Best for:** photography, fashion, one or two hero images (never a whole grid)
- **Prompt keywords:** `WebGL displacement map hover, shader-based image distortion with noise texture, RGB shift on hover, hover-driven uniform`
- **Stack:** Three.js or OGL with a fragment shader

### 8. Smoothed cursor with state morphing

A custom cursor that trails behind the real one with easing, and changes shape depending on what's underneath — a dot on text, a ring on links, "DRAG" on a carousel.

- **Best for:** portfolios, agency sites, interactive experiences
- **Prompt keywords:** `custom lerped cursor, cursor follows with easing delay, context-aware cursor states that morph on hover targets, mix-blend-mode: difference`
- **Stack:** Plain JS + `requestAnimationFrame`; add `mix-blend-mode` for the invert trick

### 9. Perspective tilt cards

Cards rotate in 3D following the cursor position, with a specular highlight sliding across the surface. Skip the highlight and it looks cheap.

- **Best for:** pricing cards, team grids, product tiles
- **Prompt keywords:** `3D perspective tilt on cursor position, rotateX/rotateY from mouse offset, moving specular gradient highlight, transform-style: preserve-3d`
- **Stack:** CSS transforms + JS, or Framer Motion `useMotionValue`

---

## Typography

### 10. Per-character stagger reveal

Text animates in letter by letter or word by word with a small delay between each, usually from a mask below the line. Not a fade — a rise from behind an invisible edge.

- **Best for:** headlines, section intros, taglines
- **Prompt keywords:** `split text per-character stagger, mask reveal rising from below baseline, overflow: hidden line wrapper, 0.03s stagger with power3.out easing`
- **Stack:** SplitType or GSAP SplitText + ScrollTrigger

### 11. Text scramble / decode

Characters cycle through random glyphs before locking into the real word, like a terminal decrypting. Restrained: one headline, one time.

- **Best for:** technical products, dev tools, anything with a hacker-adjacent brand
- **Prompt keywords:** `text scramble decode effect, randomized glyph cycling that resolves to final string, monospace character shuffle on load`
- **Stack:** Custom JS, or the classic ScrambleTextPlugin

### 12. Variable font weight on scroll

The headline's weight, width, or slant animates as you scroll past it — thin to black, condensed to expanded. Requires a variable font.

- **Best for:** editorial, type-forward brands, anything with a real typographic point of view
- **Prompt keywords:** `variable font axis animation on scroll, animate font-variation-settings wght and wdth, interpolate weight from scroll progress`
- **Stack:** CSS `font-variation-settings` + ScrollTrigger. Try Inter, Fraunces, or Roboto Flex

---

## Texture & Transition

### 13. Animated grain overlay

A film-grain texture sits over the whole page and shifts every few frames. Kills the flat, sterile, obviously-generated look faster than anything else on this list.

- **Best for:** literally any site that feels too clean
- **Prompt keywords:** `animated film grain overlay, SVG feTurbulence noise layer at 4-6% opacity, position: fixed, pointer-events: none, subtle frame-stepped drift`
- **Stack:** SVG filter or a tiled PNG with `@keyframes` position steps

### 14. Clip-path curtain transition

Page or section changes happen behind an expanding shape — a circle from the click point, a diagonal wipe, a set of vertical panels sweeping across.

- **Best for:** page transitions, modal opens, theme toggles
- **Prompt keywords:** `clip-path circle reveal from click origin, expanding curtain page transition, staggered vertical panel wipe, View Transitions API`
- **Stack:** Native View Transitions API where supported; GSAP `clipPath` otherwise

### 15. Shared element morph (FLIP)

Click a thumbnail and that exact image grows into the full page hero instead of the page reloading into a new layout. The element persists across the transition.

- **Best for:** portfolio grids → case studies, product grids → detail pages
- **Prompt keywords:** `FLIP shared element transition, morph thumbnail into hero image across route change, layoutId shared layout animation, first-last-invert-play`
- **Stack:** Framer Motion `layoutId` (easiest), GSAP Flip plugin, or View Transitions API
