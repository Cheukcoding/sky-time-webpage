# Skytime Website — Professional Improvement Audit

---

## 1. Conversion & Growth

### 1.1 No Real App Store Link
The "Download Free" and App Store buttons all point to `href="#"`. This is the single biggest revenue leak on the site. Every visitor who clicks gets nothing. **Add your real App Store URL immediately.**

### 1.2 No Email Capture
You have zero way to re-engage visitors who don't download immediately. Add a lightweight email capture — even just "Get notified when Android launches" — to build a list. Most visitors won't convert on the first visit; an email list lets you bring them back.

### 1.3 No Deep Link / QR Code
Desktop visitors can't easily get to the App Store on their phone. Add a QR code near the download CTA that opens the App Store listing directly. This is standard for mobile app landing pages and removes a massive friction point.

### 1.4 Social Proof Numbers Feel Fabricated
"10,000+ pilots" and "2.4M+ NM earned" with no source or context. If these are real, link to your App Store page or show a live counter. If they're aspirational, either remove them or replace with real metrics (even small ones feel more trustworthy than suspiciously round numbers).

---

## 2. Performance & Technical

### 2.1 Everything in One HTML File (~1,400 lines)
All CSS, JS, and HTML lives in a single file. This means:
- **Zero caching**: any content change forces re-downloading all CSS/JS
- **Render blocking**: the browser must parse everything before painting
- **Maintainability nightmare**: finding anything requires scrolling through 1,400+ lines

**Split into** `style.css`, `app.js`, and `index.html`. This is table stakes.

### 2.2 140 Particles on Every Page Load
The particle canvas runs on every frame, forever, even when scrolled far past the hero. This drains battery on mobile (your primary audience). Either:
- Pause the animation when not in the viewport
- Reduce particle count on mobile (140 is excessive for a phone)
- Use CSS-only subtle animation instead

### 2.3 No Image Optimization
Aircraft PNGs are served as-is with no `width`/`height` attributes, causing layout shift. No `<picture>` element, no WebP fallback, no lazy loading. Add `loading="lazy"` to all images below the fold. Serve WebP with PNG fallback. Specify dimensions.

### 2.4 External Font with No Fallback Strategy
Google Fonts (`DM Sans`) is loaded as render-blocking. If Google CDN is slow, your entire site stalls. Use `font-display: swap` and consider self-hosting the font files.

### 2.5 No `<meta og:image>`
Sharing the site on social media/messaging apps shows no preview image. Add an Open Graph image (1200x630) — this is critical for any viral/share-based growth.

---

## 3. User Experience & Design

### 3.1 The Page is Extremely Long
There are **15+ sections** on a single page. On desktop, this is a marathon scroll. Most users will never reach the Missions, Career, or FAQ sections. Consider:
- Moving secondary content (Career, Missions, Stats) to separate pages
- Using a more aggressive information hierarchy — hero + 3-4 key sections + CTA
- The collapsible sections on mobile help, but desktop users get no relief

### 3.2 "Locked" Aircraft Cards Are Confusing
Three aircraft show as "???" with a lock icon and "CLASSIFIED / Download to discover." The intent is intrigue, but the execution feels broken — like a loading error. Users can't tell if the site is bugged or if this is intentional. Add a subtle tooltip or hover text: "Download Skytime to unlock."

### 3.3 No Video or GIF of the Actual App
The three mini-phone mockups are clever but they're HTML recreations, not the real app. Users want to see the **actual product**. A 15-second screen recording or animated GIF of a real focus session would build 10x more trust than any mockup.

### 3.4 The Crash/Flight Recorder Diagram Needs Context
The SVG flight recorder in the "Crashed" panel is a great concept but it's tiny and unlabeled. Most users will glance past it. Make it larger, or add a brief caption like "Your flight aborted at 28% — no miles earned."

### 3.5 Mobile Sticky Bar Has No Link
The sticky download bar at the bottom on mobile says "Download Free" but the link goes to `#download` (the page section), not the App Store. On mobile, this should deep-link directly to the App Store.

---

## 4. Content & Messaging

### 4.1 The Value Proposition Takes Too Long
The hero says "Your Screen Time, Reimagined" — which is vague. The real hook ("stay off your phone and earn virtual flights") is buried in the subtitle. Lead with the concrete benefit: **"Put your phone down. Earn flights."** or **"Every minute offline earns you a mile."**

### 4.2 "How It Works" Should Be Simpler
Three animated phones are visually impressive but overwhelming. The core loop is dead simple: **Set timer → Stay focused → Earn rewards.** This could be communicated in 3 icons + 1 sentence each. The phone mockups can stay, but add a TL;DR above them.

### 4.3 Too Many Numbers, Not Enough Story
"58 aircraft, 60 routes, 50 airlines, 8 tiers, 10 ranks" — these are features, not benefits. A user doesn't care about 50 airlines until they're already invested. Lead with the *feeling*: "Build a career from student pilot to ace" is more compelling than "10 ranks."

### 4.4 FAQ Has 21 Questions
This is too many. Keep the top 6-8 on the main page. Move the rest to a dedicated FAQ/support page. A 21-question FAQ signals that your product is confusing, not that you're thorough.

### 4.5 Afterburner Positioning is Unclear
The Afterburner section shows "2X Nautical Miles" with rotating phrases but never states the price or what exactly is included in a clear list format. Users need to know: Is this a subscription? One-time purchase? What's the price? Transparency builds trust.

---

## 5. SEO & Accessibility

### 5.1 No Structured Data
Add JSON-LD structured data for `SoftwareApplication` type. This helps Google show rich results (star ratings, download link, price) in search.

### 5.2 Heading Hierarchy is Broken
Multiple `<h2>` tags, no clear `<h1>` → `<h2>` → `<h3>` hierarchy within sections. Screen readers and search engines use heading structure to understand content. Clean this up.

### 5.3 Interactive Elements Lack ARIA Labels
The rank bar nodes, FAQ toggles, and hamburger menu use `onclick` handlers with no `role`, `aria-label`, or `tabindex`. Keyboard users can't navigate these. At minimum, add `role="button"` and `tabindex="0"` to all clickable non-button elements.

### 5.4 No `alt` Text Strategy
Some images have meaningful alt text (`alt="SR-71"`), others are decorative (`alt="Skytime"`). Decorative images should use `alt=""` and informational images should describe what's shown.

---

## 6. Trust & Credibility

### 6.1 No Real App Store Reviews
The social proof section quotes "App Store Review," "Reddit," and "Twitter" with no links or usernames. These feel manufactured. Either link to real reviews or embed actual App Store review widgets.

### 6.2 No Team / Company Info
There's no "About" page, no team info, no company name beyond "Skytime." For a productivity app that asks users to trust it with their focus time, some human credibility goes a long way. Even a one-liner: "Built by [name] in Hong Kong."

### 6.3 Privacy Policy Page Exists but Terms Page is Empty
`Terms` links to `#` — a dead link. If you have a privacy page, you need real terms of service, especially for an app with in-app purchases.

---

## 7. Quick Wins (< 1 hour each)

| Priority | Task | Impact |
|----------|------|--------|
| **P0** | Add real App Store link | Direct downloads |
| **P0** | Add `og:image` meta tag | Social sharing |
| **P1** | Add `loading="lazy"` to images | Page speed |
| **P1** | Add QR code for desktop → mobile | Conversion |
| **P1** | Fix Terms of Service link | Trust |
| **P2** | Reduce FAQ to 8 questions | Cleaner UX |
| **P2** | Pause particles when off-screen | Battery/perf |
| **P2** | Add `font-display: swap` | Perceived speed |
| **P3** | Split CSS/JS into separate files | Maintainability |
| **P3** | Add structured data (JSON-LD) | SEO |

---

*Audit conducted February 2026. Based on review of `index.html` (single-page application, ~1,400 lines).*
