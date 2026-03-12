# 📁 AI Prompt Library — EURL ETB Achouri Toufik Website
> Structured, reusable prompts for the AI-supervised development workflow.
> Every AI tool in the pipeline (Claude, Gemini, Antigravity) uses this folder as its reference.

---

## 🗂️ Prompt Index

| # | File | Step | Model | Task |
|---|------|------|-------|------|
| 01 | `01-component-generation.md`         | Planning  | Claude (this chat)        | Generate new HTML/CSS sections from scratch |
| 02 | `02-bug-fixing.md`                   | Any       | Claude (this chat)        | Diagnose and fix layout or styling bugs |
| 03 | `03-layout-improvement.md`           | Review    | Claude (this chat)        | Improve UX and visual design of a section |
| 04 | `04-responsive-fixing.md`            | Any       | Claude (this chat)        | Fix mobile/tablet responsiveness |
| 05 | `gemini-prompt-services-page.md`     | Generate  | Gemini Flash (Antigravity)| Build the full services.html page |
| 06 | `gemini-prompt-projects-page.md`     | Generate  | Gemini Flash (Antigravity)| Build the full projects.html page |
| 07 | `antigravity-step3-integration.md`   | Integrate | Claude Sonnet (Antigravity)| Integrate Gemini output into the site |
| 08 | `antigravity-step4-responsiveness.md`| QA        | Claude Sonnet (Antigravity)| Test and fix responsiveness at all breakpoints |

---

## ⚙️ Development Workflow

```
STEP 1 — Claude (this chat)
  └─► Plans the page, writes or selects the Gemini prompt
      Uses: 01-component-generation.md or gemini-prompt-[page].md

        ▼

STEP 2 — Antigravity / Gemini Flash
  └─► Open Antigravity → set model to Gemini Flash
      Paste prompt from gemini-prompt-[page].md → generates full HTML page
      ⚠️  Agent-assisted mode, not Planning mode
      ⚠️  Do NOT use Gemini Pro (High) — capacity issues, overkill for generation

        ▼  [MANUAL HANDOFF]
           Save Gemini's output as services.html or projects.html
           Drop the file into the workspace folder

        ▼

STEP 3 — Antigravity / Claude Sonnet 4.5
  └─► Switch model to Claude Sonnet 4.5 in Antigravity
      Paste prompt from antigravity-step3-integration.md
      Claude reads @prompts/README.md, audits the file, integrates
      nav/footer, fixes links, opens browser and verifies
      ⚠️  Agent mode (not Planning) — let it run autonomously

        ▼

STEP 4 — Antigravity / Claude Sonnet 4.5
  └─► Keep Claude Sonnet 4.5 in Antigravity
      Paste prompt from antigravity-step4-responsiveness.md
      Tests 5 breakpoints in browser, fixes responsive issues, re-verifies
      Outputs a report — flag anything needing design decisions

        ▼  [MANUAL HANDOFF]
           Paste Claude's output report back into this chat

        ▼

STEP 5 — Claude (this chat)
  └─► Reviews UX and layout from the report
      Uses: 03-layout-improvement.md or 02-bug-fixing.md
      Writes targeted fix instructions → back to Antigravity if needed
```

### Model Assignment Summary

| Model | Where | Used for |
|-------|-------|---------|
| Claude (claude.ai) | This chat | Planning, prompt writing, UX review |
| Gemini Flash | Antigravity Agent | Fast HTML/CSS generation — Steps 2 |
| Claude Sonnet 4.5 | Antigravity Agent | Careful integration + QA — Steps 3 & 4 |

> ⚠️ **Multi-agent automation note:** Antigravity does not currently support agents
> supervising other agents automatically. The two handoff points marked [MANUAL HANDOFF]
> above require you to copy the output and start the next agent conversation yourself.
> This takes ~30 seconds per handoff and is the only manual step in the pipeline.

---

## 🏗️ Full Tech Stack

> **This is the source of truth for all AI tools working on this project.**
> Every prompt must stay within this stack — no new libraries, no npm, no bundler.

### Core
| Layer | Technology | Notes |
|-------|-----------|-------|
| HTML | HTML5 | Semantic tags, no framework |
| CSS | CSS3 | Written in `<style>` blocks per page |
| JavaScript | Vanilla JS (ES6+) | No framework, no build step |
| Execution | Static files | Opened directly in browser — no server needed |

### CSS Framework
| Tool | How it's loaded | Purpose |
|------|----------------|---------|
| Tailwind CSS | CDN — `https://cdn.tailwindcss.com` | Utility classes for layout, spacing, colors, responsive |
| Custom `<style>` blocks | Inline in each HTML file | Animations, pseudo-elements, blueprint grid texture, custom scrollbar — anything Tailwind can't handle cleanly |

**Tailwind config block** (paste in every page's `<head>` after the CDN script):
```html
<script>
  tailwind.config = {
    theme: {
      extend: {
        colors: {
          navy:        '#1e243c',
          'navy-dark': 'rgb(15,19,35)',
          'navy-card': '#1a2036',
          gold:        '#c19f5d',
          'light-bg':  '#f4f4f2',
          muted:       '#5a5f72',
        },
        fontFamily: {
          sans:      ['Lato', 'sans-serif'],
          barlow:    ['Barlow', 'sans-serif'],
          condensed: ['Barlow Condensed', 'sans-serif'],
        },
      }
    }
  }
</script>
```

### Animation
| Tool | Version | CDN URL | Used for |
|------|---------|---------|---------|
| GSAP | 3.12.2 | `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js` | Hero entrance, fade/slide-in scroll animations, count-up stats |
| ScrollTrigger | 3.12.2 | `https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js` | Trigger animations on scroll |

All GSAP code lives inside `window.addEventListener('load', () => { ... })`.
`gsap.registerPlugin(ScrollTrigger)` is called at the top of every load handler.

### Typography
| Font | Weights | Used for |
|------|---------|---------|
| Barlow Condensed | 700, 800 | All headings, eyebrows, buttons, labels |
| Barlow | 400, 500, 600 | Navigation, UI elements |
| Lato | 300, 400, 700 | Body text, paragraphs, descriptions |

Google Fonts link (paste in every `<head>`):
```html
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@400;500;600&family=Barlow+Condensed:wght@700;800&family=Lato:wght@300;400;700&display=swap" rel="stylesheet"/>
```

### Icons
**Inline SVGs only — no icon library.**
All icons are hand-written `<svg>` elements directly in the HTML.

Standard icon attributes:
```html
<svg class="w-5 h-5" viewBox="0 0 24 24" fill="none" stroke="#c19f5d"
     stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
  <path d="..."/>
</svg>
```
- ViewBox: always `0 0 24 24`
- Fill: `none`
- Stroke: `#c19f5d` (gold) for decorative icons, `currentColor` for interactive ones
- Stroke-width: `1.8` (nav/UI: `2` or `2.2`)
- Stroke-linecap + linejoin: `round`

### Logo Files
| File | Used where |
|------|-----------|
| `Logo_Horizontal_Light.svg` | Navbar (main bar) and footer |
| `Logo_Light.svg` | Compact or square contexts |

```html
<!-- Navbar -->
<img src="Logo_Horizontal_Light.svg" alt="ETB Achouri Toufik" style="height:42px;">

<!-- Footer -->
<img src="Logo_Horizontal_Light.svg" alt="ETB Achouri Toufik" style="height:44px; margin-bottom:4px;">
```

> ⚠️ **For Gemini prompts only:** use a text fallback since Gemini can't access local files:
> `<span class="font-condensed text-[22px] font-extrabold text-white tracking-[1px]">ETB <span class="text-gold">Achouri</span></span>`
> Antigravity replaces this with the real SVG during Step 3 (integration).

### Media
| Type | Source | Status |
|------|--------|--------|
| Hero background video | Pexels video URLs | Placeholders — replace with real footage |
| Page photos (about, projects) | Unsplash URLs | Placeholders — replace with real photos |
| Hero video crossfade | JS + GSAP opacity transition | `vid1` ends → `vid2` fades in, loops |

### Maps
| Page | Implementation | Notes |
|------|---------------|-------|
| `contact.html` | Google Maps embed `<iframe>` | Standard embed, no API key needed |
| `projects.html` | Custom CSS/JS interactive map | No external library — pure HTML/CSS/JS pins + info panel |

### Browser APIs
| API | Used for | Notes |
|-----|---------|-------|
| `IntersectionObserver` | Scroll-spy navbar highlighting | Watches `section[id]` elements |

> ⚠️ `localStorage` was previously used for theme persistence — it has been **removed**. Do not re-introduce it.

---

## 📄 Pages

| File | Status | Notes |
|------|--------|-------|
| `index.html` | ✅ Complete | Hero video, about, stats, services preview, projects preview, contact form |
| `about.html` | ✅ Complete | Company story, team, values |
| `contact.html` | ✅ Complete | Contact form + Google Maps embed |
| `services.html` | 🔲 To build | Use `gemini-prompt-services-page.md` |
| `projects.html` | 🔲 To build | Use `gemini-prompt-projects-page.md` |

---

## 🎨 Design Tokens

```
Colors
  navy:       #1e243c   Primary dark — backgrounds, cards, navbar
  navy-dark:  rgb(15,19,35)  Deeper navy — footer, hero overlay
  navy-card:  #1a2036   Card backgrounds inside dark sections
  gold:       #c19f5d   Accent — borders, icons, highlights, CTAs
  light-bg:   #f4f4f2   Light section backgrounds
  muted:      #5a5f72   Body text on light backgrounds

Typography
  Heading XL: clamp(40px, 6vw, 64px)  — page heroes
  Heading LG: clamp(32px, 5vw, 52px)  — section headings
  Heading MD: clamp(28px, 4vw, 42px)  — sub-section headings
  Eyebrow:    11px, Barlow Condensed, tracking-[3px], uppercase, text-gold
  Body:       13.5px–15px, Lato, leading-[1.7]

Spacing
  Section:    py-24 px-12
  Max width:  max-w-[1200px] mx-auto

Borders
  Subtle gold:  border border-[rgba(193,159,93,0.2)]
  Full gold:    border border-gold
  Top accent:   border-t-[3px] border-t-gold  ← used on navbar, cards, CTAs

Shadows
  Card:   shadow-[0_2px_16px_rgba(30,36,60,0.06)]
  Hover:  shadow-[0_8px_32px_rgba(30,36,60,0.12)]
```

---

## 📐 Breakpoints

| Tailwind prefix | Width | Target |
|----------------|-------|--------|
| (default) | 0px+ | Mobile base |
| `sm:` | 640px+ | Large phones |
| `md:` | 768px+ | Tablets |
| `lg:` | 1024px+ | Laptops |
| `xl:` | 1280px+ | Large screens |
| `max-sm:` | <640px | Mobile-only overrides |
| `max-md:` | <768px | Mobile + tablet overrides |

---

## 🧱 Recurring Patterns

### Eyebrow label
```html
<div class="flex items-center gap-3 mb-4">
  <span class="w-8 h-[1px] bg-gold inline-block"></span>
  <span class="font-condensed text-[11px] font-bold tracking-[3px] uppercase text-gold">Label Here</span>
</div>
```

### Section heading — light background
```html
<h2 class="font-condensed text-[clamp(32px,5vw,52px)] font-extrabold text-navy leading-[1.1] tracking-[-0.5px] mb-4">
  Heading <span class="text-gold">Accent</span>
</h2>
```

### Section heading — dark background
```html
<h2 class="font-condensed text-[clamp(32px,5vw,52px)] font-extrabold text-white leading-[1.1] tracking-[-0.5px] mb-4">
  Heading <span class="text-gold">Accent</span>
</h2>
```

### Primary CTA button (gold fill)
```html
<a href="contact.html" class="bg-gold text-navy font-condensed text-[12px] font-bold tracking-[2px] uppercase px-8 py-4 hover:opacity-90 transition-opacity no-underline">
  Button Label &rarr;
</a>
```

### Outlined CTA button (dark background)
```html
<a href="#" class="border border-[rgba(255,255,255,0.4)] text-white font-condensed text-[12px] font-bold tracking-[2px] uppercase px-8 py-4 hover:border-gold hover:text-gold transition-all no-underline">
  Button Label
</a>
```

### Service / feature card
```html
<div class="service-card bg-white border border-[rgba(30,36,60,0.07)] rounded-[3px] p-9 flex flex-col shadow-[0_2px_16px_rgba(30,36,60,0.06)]">
  <div class="w-16 h-16 bg-navy rounded-[4px] flex items-center justify-center mb-7 flex-shrink-0">
    <svg class="w-7 h-7" viewBox="0 0 24 24" fill="none" stroke="#c19f5d" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">
      <!-- path here -->
    </svg>
  </div>
  <h3 class="font-barlow text-[17px] font-semibold text-navy mb-3">Title</h3>
  <p class="text-[13.5px] text-muted leading-[1.7] flex-1 mb-6">Description.</p>
  <a href="#" class="font-condensed text-[11px] font-bold tracking-[1.8px] uppercase text-navy hover:text-gold transition-colors no-underline flex items-center gap-2">
    Learn More
    <svg class="w-3 h-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round">
      <line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/>
    </svg>
  </a>
</div>
```

### Blueprint grid texture (dark sections)
```css
.blueprint-subtle {
  background-image:
    linear-gradient(rgba(193,159,93,.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(193,159,93,.04) 1px, transparent 1px);
  background-size: 48px 48px;
}
```
Usage: `<div class="blueprint-subtle absolute inset-0 pointer-events-none"></div>` inside any `relative overflow-hidden` section.

---

## ⚠️ Hard Rules for All AI Tools

1. **No npm, no bundler, no backend** — static files only, opened directly in a browser
2. **No new CSS frameworks** — Tailwind CDN + plain CSS `<style>` blocks only
3. **No icon libraries** — inline SVGs only, following the attribute spec above
4. **No `localStorage`** — intentionally removed, do not re-add it
5. **No map libraries** — Google Maps iframe on `contact.html`, custom CSS/JS on `projects.html`
6. **Never switch fonts** — always use the Google Fonts link with Barlow Condensed + Barlow + Lato
7. **Always include the Tailwind config block** — never rely on default Tailwind colors
8. **All JS inside `window.addEventListener('load', () => { ... })`**
9. **GSAP + ScrollTrigger from cdnjs at version 3.12.2 exactly**
10. **Logo = SVG files** — text fallback is for Gemini prompts only; Antigravity must replace it with the real SVG
