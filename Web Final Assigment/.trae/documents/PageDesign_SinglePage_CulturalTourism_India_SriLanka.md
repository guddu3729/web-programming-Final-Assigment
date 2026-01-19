# Cultural Tourism Site (India & Sri Lanka) — Page Design Spec (Home + Destination Details + Contact)

## A. Desktop-first layout & responsive rules
- **Primary layout system:** CSS Grid for section-level columns; Flexbox for nav, card rows, and small alignment.
- **Desktop baseline:** 1200px content max-width; 24px gutter; 72–96px vertical section padding.
- **Breakpoints:**
  - ≥1024px: 3-up highlight cards; 3-column gallery grid.
  - 768–1023px: 2-up cards; 2–3 column gallery.
  - <768px: stacked nav (menu button optional), 1-up cards; 1–2 column gallery.
- **Spacing logic:** 8px spacing scale; section padding uses 8×9 (72px) or 8×12 (96px).

## B. Meta information (by page)
- **Home (/)**
  - Title: Cultural Trails: India & Sri Lanka
  - Description: A curated cultural journey across India and Sri Lanka—heritage sites, food, landscapes, and local arts.
  - Open Graph: og:title = Cultural Trails: India & Sri Lanka; og:description = Curated categories, gallery, and local media; og:image = ./Hero Banner/india-sri-lanka-hero.jpg.png
- **Destination Detail (/destinations/:slug)**
  - Title template: {Destination Name} — Cultural Trails
  - Description template: Short static summary of the destination.
  - Open Graph: og:image MUST be the destination’s local Gallery/* image.
- **Contact (/contact)**
  - Title: Contact — Cultural Trails
  - Description: How to reach the trip planners (static info; no map embeds).

## C. Global styles (design tokens)
- **Background:** #0B1220 (deep navy) for body; sections can use #0F1A2E to alternate.
- **Text:** #EAF0FF primary; #B9C4E3 secondary.
- **Accent (CTA):** #F4B63A (saffron gold).
- **Secondary accent:** #37B6A6 (teal) for links/active states.
- **Typography:**
  - H1: 48–56px / 1.05, semi-bold
  - H2: 32–36px / 1.15
  - Body: 16–18px / 1.6
- **Buttons:**
  - Primary: gold background + dark text; hover: slight darken + lift (translateY -2px).
  - Secondary: transparent + 1px border; hover: background tint.
- **Links:** underline on hover; active nav uses accent color and underline indicator.
- **Effects (mandated):**
  - Smooth scrolling for anchor links.
  - Scroll-reveal: sections fade+translate up when entering viewport.
  - Hover transitions on cards and gallery tiles (shadow + slight scale).
  - Lightbox modal: fade in backdrop + scale in panel.

## D. Page structure
### Home page (/)
Top-to-bottom stacked sections with a sticky header:
1) Header / Navigation
2) Hero
3) About
4) Travel Categories (Culture / Business / Entertainment)
5) Destinations Gallery
6) Culture Media
7) Footer

### Additional pages
- Destination Detail page (/destinations/:slug)
- Contact page (/contact)

## E. Sections & components

### 1) Header / Navigation (sticky)
- **Layout:** full-width bar; centered container; left logo, right nav.
- **Logo asset:** <img src="./Logo/logo.png" alt="Site logo" style="height:40px" />
- **Nav items:** Home (Hero, About, Categories, Gallery, Media) + Contact. (Optional: “Destinations” dropdown/listing that links to detail pages.)
- **Interactions:**
  - Sticky after scroll (or always sticky).
  - Active-section highlighting while scrolling (IntersectionObserver recommended).
  - Clicking nav uses smooth scroll to anchors.

### 2) Hero section (#hero)
- **Background asset:** <img src="./Hero Banner/india-sri-lanka-hero.jpg.png" alt="India and Sri Lanka hero" style="width:100%" />
- **Structure:** two-layer layout:
  - Background image (cover) + gradient overlay.
  - Foreground content block (max 560px) aligned left.
- **Content:**
  - H1: “Cultural Trails: India & Sri Lanka”
  - Subcopy: 1–2 lines about heritage, flavors, and living traditions.
  - Primary CTA: “Explore the Gallery” (scroll to #gallery)
  - Secondary CTA: “Watch Culture Video” (scroll to #media)
- **Effect:** subtle parallax-like feel via fixed background or slow translate on scroll (optional) while keeping performance safe.

### 3) About section (#about)
- **Layout:** 2-column grid (text left, compact “What you’ll discover” list right).
- **Content blocks:**
  - Short paragraph: cultural focus across both countries.
  - Bullet list (3 items): heritage sites, local food, coastal & inland culture.
- **Effect:** scroll-reveal on entry.

### 4) Travel Categories (#categories)
- **Layout:** 3 cards in a row (desktop), equal height.
- **Goal:** Add the requested Business + Entertainment categories while staying strictly asset-driven.
- **Category cards (x3, must reuse local files):**
  1. **Culture** — Asset: ./Features/temple-stupa.png
  2. **Business** — Asset: ./Features/tea-plantation-workers.png
  3. **Entertainment** — Asset: ./Features/street-food-thali.png
- **Interactions:**
  - Hover state: lift + shadow; image slightly zooms.
  - Click: scroll to a curated area of the Gallery OR apply a simple client-side highlight state (no remote data).

### 5) Destinations Gallery (#gallery)
- **Layout:** masonry-like grid is optional; default is uniform 3-column grid on desktop.
- **Tile actions (per destination):**
  - Click image opens lightbox (fast visual browsing)
  - “View details” opens the destination detail page (/destinations/:slug)
- **Tiles (6), using provided assets:**
  - ./Gallery/tajmahal.jpg — caption: “Taj Mahal (India)”
  - ./Gallery/Golden_Temple.jpg — caption: “Golden Temple (India)”
  - ./Gallery/Sree_Padmanabhaswamy_Temple.jpg — caption: “Sree Padmanabhaswamy Temple (India)”
  - ./Gallery/kerala-backwaters.png — caption: “Kerala Backwaters (India)”
  - ./Gallery/sigiriya-lion-rock.jpg — caption: “Sigiriya Lion Rock (Sri Lanka)”
  - ./Gallery/galle-fort-lighthouse.jpg — caption: “Galle Fort Lighthouse (Sri Lanka)” 
- **Lightbox modal (mandated interaction):**
  - Opens on tile click with image, caption, and next/prev.
  - Keyboard: Esc closes; left/right arrows navigate.
  - Backdrop click closes.

### 6) Culture Media section (#media)
- **Layout:** 2-column grid on desktop (video left, audio right).
- **Video module:**
  - Source: ./Media/culture.mp4
  - Controls visible; no autoplay.
  - Caption: “A glimpse of dance, color, and street life.”
- **Audio module:**
  - Source: ./Media/folk.mp3
  - Title: “Folk Rhythm”
  - Supporting line: “Listen while you browse destinations.”

### 7) Footer (#footer)
- **Layout:** 3-column footer grid: quick links, credits/assets note, CTA.
- **Credits / constraints note:** explicitly state “All media shown are local project assets.”
- **CTA:** “Back to top” (scrolls to #hero) and “Explore Gallery” (#gallery).

## F. Accessibility & UX essentials
- Provide alt text for every image.
- Ensure focus states for nav, buttons, and lightbox controls.
- Ensure sufficient contrast for overlay text on hero.
- Respect reduced-motion preferences (disable scroll-reveal transitions if prefers-reduced-motion).

## G. Destination Detail Page (/destinations/:slug) — Design (template)
### Layout
- Desktop-first, centered container (max 1200px). Use CSS Grid: main content + right rail for facts (optional).

### Page structure & components
1) **Header / Navigation** (same as Home)
2) **Breadcrumbs**: “Home / {Destination Name}”
3) **Destination hero**: local Gallery image (cover) + title overlay
4) **Quick facts**: Country tag (India/Sri Lanka) + 3–5 short facts
5) **Story**: 1–2 short paragraphs
6) **Related destinations**: 2–3 cards (reuse Gallery assets) linking to other detail pages
7) **Footer**

### Slug + asset mapping (must be local)
- /destinations/taj-mahal -> ./Gallery/tajmahal.jpg
- /destinations/golden-temple -> ./Gallery/Golden_Temple.jpg
- /destinations/sree-padmanabhaswamy-temple -> ./Gallery/Sree_Padmanabhaswamy_Temple.jpg
- /destinations/kerala-backwaters -> ./Gallery/kerala-backwaters.png
- /destinations/sigiriya-lion-rock -> ./Gallery/sigiriya-lion-rock.jpg
- /destinations/galle-fort-lighthouse -> ./Gallery/galle-fort-lighthouse.jpg

## H. Contact Page (/contact) — Design
### Layout
- Two-column grid on desktop: left “Contact info”, right “Message form”. Stack on mobile.

### Sections & components
1) **Header / Navigation**
2) **Page heading**: “Contact” + short line
3) **Contact info**: email link + simple address line (text-only; no external embeds)
4) **Message form (non-persistent)**: Name, Email, Message + Submit button
5) **Footer**

### Asset-driven rule reminder (UI)
- Do not introduce new images/icons/fonts; all visuals must come from existing local folders or CSS-only shapes/colors.