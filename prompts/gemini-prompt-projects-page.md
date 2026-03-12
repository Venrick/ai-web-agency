# Gemini Prompt — projects.html
> **Model:** Gemini Flash (in Antigravity — set model to Gemini Flash before running)
> **Mode:** Agent (not Planning)
> Copy everything inside the code block and paste it into Antigravity's chat input.

---

```
════════════════════════════════════════
SYSTEM
════════════════════════════════════════
You are a senior frontend developer working on the official website for EURL ETB Achouri Toufik, a construction company based in Blida, Algeria.

Your output will be integrated into a live multi-page static site. Every decision you make must be consistent with the existing design system. Deviation from the rules below is not acceptable.

HARD RULES — violations will break the site:
1. No npm, no bundler, no backend — static files only
2. No new CSS frameworks — Tailwind CDN + plain <style> blocks only
3. No icon libraries — inline SVGs only (viewBox="0 0 24 24", fill="none", stroke="#c19f5d", stroke-width="1.8")
4. No localStorage
5. No map libraries — the interactive map must be built in pure HTML/CSS/JS with NO Leaflet, Google Maps JS API, or any other library
6. Never switch fonts — Barlow Condensed + Barlow + Lato only
7. Always include the Tailwind config block with the exact custom colors below
8. All JS inside window.addEventListener('load', () => { ... })
9. GSAP + ScrollTrigger from cdnjs at version 3.12.2 exactly
10. Logo = text fallback only (real SVG added in integration step)

════════════════════════════════════════
TASK
════════════════════════════════════════
Build a complete, standalone projects.html page for this site. It must match the existing site exactly in design system, navbar, and footer. It also includes a custom-built interactive project map built entirely with HTML, CSS, and vanilla JavaScript — no external map libraries.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TECH STACK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Tailwind CSS via CDN: <script src="https://cdn.tailwindcss.com"></script>
- GSAP 3 + ScrollTrigger via CDN for scroll animations
- Google Fonts: Barlow (400,500,600), Barlow Condensed (700,800), Lato (300,400,700)
- NO Leaflet, Google Maps, or any other map library
- The map is a custom SVG or styled <div> with positioned pins built in pure CSS/JS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TAILWIND CONFIG
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
tailwind.config = {
  theme: {
    extend: {
      colors: {
        navy:       '#1e243c',
        'navy-dark':'rgb(15,19,35)',
        'navy-card':'#1a2036',
        gold:       '#c19f5d',
        'light-bg': '#f4f4f2',
        muted:      '#5a5f72',
      },
      fontFamily: {
        sans:      ['Lato', 'sans-serif'],
        barlow:    ['Barlow', 'sans-serif'],
        condensed: ['Barlow Condensed', 'sans-serif'],
      },
    }
  }
}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CUSTOM CSS (paste in <style> in <head>)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/* Blueprint grid */
.blueprint-subtle {
  background-image:
    linear-gradient(rgba(193,159,93,.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(193,159,93,.04) 1px, transparent 1px);
  background-size: 48px 48px;
}
/* Nav */
.nav-link { position: relative; padding-bottom: 4px; }
.nav-link.active { color: #fff !important; }
.nav-link.active::after { content: ''; position: absolute; bottom: -2px; left: 0; right: 0; height: 2px; background: #c19f5d; }
.hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; background: none; border: none; padding: 4px; }
.hamburger span { width: 24px; height: 2px; background: #fff; display: block; transition: all .3s; transform-origin: center; }
.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }
.nav-drawer { max-height: 0; overflow: hidden; transition: max-height .35s ease; background: #1e243c; }
.nav-drawer.open { max-height: 400px; }
.nav-drawer a { display: block; padding: 12px 24px; color: rgba(255,255,255,.75); text-decoration: none; font-size: 14px; font-weight: 500; letter-spacing: 1px; text-transform: uppercase; border-bottom: 1px solid rgba(193,159,93,.1); transition: color .2s; }
.nav-drawer a:hover, .nav-drawer a.active { color: #c19f5d; }
/* Project card hover */
.project-overlay { opacity: 0; transition: opacity .35s; }
.project-card:hover .project-overlay { opacity: 1; }
.project-card img { transition: transform .45s ease, filter .45s; filter: brightness(.88); }
.project-card:hover img { transform: scale(1.06); filter: brightness(.6); }
/* Footer */
.fnav-link { transition: color .2s, padding-left .2s; display: flex; align-items: center; gap: 0; }
.fnav-link::before { content: ''; width: 0; height: 1px; background: #c19f5d; display: inline-block; transition: width .2s, margin-right .2s; }
.fnav-link:hover { color: #fff !important; padding-left: 4px; }
.fnav-link:hover::before { width: 14px; margin-right: 6px; }
.footer-topline { height: 3px; background: linear-gradient(to right, transparent, #c19f5d 20%, #c19f5d 80%, transparent); }

/* ─── MAP STYLES ─── */
/* Map container */
#project-map {
  position: relative;
  width: 100%;
  height: 480px;
  background: #1a2036;
  border-radius: 4px;
  overflow: hidden;
  border: 1px solid rgba(193,159,93,0.15);
}
/* Subtle Algeria-shaped background using CSS (stylized region blocks) */
#project-map::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 80% 60% at 50% 55%, rgba(30,36,60,0.0) 60%, rgba(10,14,28,0.6) 100%),
    linear-gradient(rgba(193,159,93,.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(193,159,93,.03) 1px, transparent 1px);
  background-size: auto, 36px 36px, 36px 36px;
  pointer-events: none;
}
/* Stylized land mass (Algeria silhouette approximation using CSS shapes) */
.map-land {
  position: absolute;
  background: rgba(30,40,70,0.85);
  border: 1px solid rgba(193,159,93,0.08);
}
/* Map pin */
.map-pin {
  position: absolute;
  transform: translate(-50%, -100%);
  cursor: pointer;
  z-index: 10;
  transition: transform 0.2s ease;
}
.map-pin:hover { transform: translate(-50%, -100%) scale(1.2); }
.map-pin.active .pin-dot { background: #c19f5d; box-shadow: 0 0 0 6px rgba(193,159,93,0.25); }
.map-pin.active .pin-label { color: #c19f5d; font-weight: 700; }
/* Pin visual */
.pin-body {
  width: 28px;
  height: 36px;
  background: #1e243c;
  border: 2px solid #c19f5d;
  border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  transition: background 0.2s, box-shadow 0.2s;
  box-shadow: 0 4px 12px rgba(0,0,0,0.4);
}
.map-pin.active .pin-body {
  background: #c19f5d;
  box-shadow: 0 4px 20px rgba(193,159,93,0.5), 0 0 0 4px rgba(193,159,93,0.2);
}
.pin-body::after {
  content: '';
  position: absolute;
  bottom: -7px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 7px solid #c19f5d;
}
.map-pin.active .pin-body::after { border-top-color: #c19f5d; }
.pin-icon {
  width: 10px;
  height: 10px;
  background: #c19f5d;
  border-radius: 50%;
  transition: background 0.2s;
}
.map-pin.active .pin-icon { background: #1e243c; }
/* Pin label */
.pin-label {
  position: absolute;
  bottom: calc(100% + 4px);
  left: 50%;
  transform: translateX(-50%);
  font-family: 'Barlow Condensed', sans-serif;
  font-size: 10px;
  font-weight: 600;
  letter-spacing: 0.8px;
  text-transform: uppercase;
  color: rgba(255,255,255,0.65);
  white-space: nowrap;
  background: rgba(15,19,35,0.85);
  padding: 3px 7px;
  border-radius: 3px;
  pointer-events: none;
}
/* Info panel (slides in from right) */
#map-info-panel {
  position: absolute;
  top: 16px;
  right: 16px;
  width: 280px;
  background: rgba(15,19,35,0.96);
  border: 1px solid rgba(193,159,93,0.25);
  border-top: 3px solid #c19f5d;
  border-radius: 4px;
  padding: 20px;
  z-index: 20;
  transform: translateX(calc(100% + 24px));
  transition: transform 0.35s cubic-bezier(0.4,0,0.2,1), opacity 0.3s;
  opacity: 0;
  pointer-events: none;
}
#map-info-panel.visible {
  transform: translateX(0);
  opacity: 1;
  pointer-events: auto;
}
/* Progress bar */
.progress-bar-track {
  width: 100%;
  height: 5px;
  background: rgba(255,255,255,0.1);
  border-radius: 3px;
  overflow: hidden;
  margin-top: 4px;
}
.progress-bar-fill {
  height: 100%;
  background: #c19f5d;
  border-radius: 3px;
  transition: width 0.8s cubic-bezier(0.4,0,0.2,1);
  width: 0%;
}
/* Map city dots */
.map-city-dot {
  position: absolute;
  width: 4px;
  height: 4px;
  background: rgba(193,159,93,0.25);
  border-radius: 50%;
  transform: translate(-50%, -50%);
}

/* Filter buttons */
.filter-btn-active {
  background: #c19f5d !important;
  border-color: #c19f5d !important;
  color: #1e243c !important;
}

@media(max-width:768px) {
  .hamburger { display: flex; }
  .nav-desktop { display: none !important; }
  #project-map { height: 340px; }
  #map-info-panel { width: calc(100% - 32px); top: auto; bottom: 16px; right: 16px; }
}
@media(min-width:769px) { .nav-drawer { display: none !important; } }

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NAVBAR (same as index.html — active link: "Projects")
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Fixed, z-[100], two-row:
  1. Topbar: dark bg, phone + email left, social icons right
  2. Mainbar: navy, gold bottom border 3px, logo left, nav links right
Active link: Projects — add class "active" to the Projects <a> tag.
Logo fallback: <span class="font-condensed text-[22px] font-extrabold text-white tracking-[1px]">ETB <span class="text-gold">Achouri</span></span>

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PAGE HERO SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- bg-navy, min-height 340px, pt-[104px], blueprint-subtle overlay, gold bottom border (3px)
- Centered content, max-w-[1200px] mx-auto px-12
- Eyebrow: gold dash + "Our Portfolio" in font-condensed uppercase gold tracking-[3px]
- H1: "Our <span class='text-gold'>Project</span> Portfolio" — font-condensed, clamp(40px,6vw,64px), extrabold, text-white
- Subtext: "240+ completed projects across Algeria — residential, commercial, and industrial."
- Breadcrumb: Home / Projects

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
INTERACTIVE PROJECT MAP SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Layout: bg-[rgb(15,19,35)], py-20 px-12, blueprint-subtle overlay
Max-w-[1200px] mx-auto

Section header:
- Eyebrow: "Project Locations" + title: "Where We've Built"
- Subtitle: "Click any pin on the map to explore project details."
- Text-white for title, text-white/50 for subtitle

Map container: id="project-map" (full CSS defined above)

Inside the map, add:
  1. A stylized abstract Algeria map background using CSS div shapes:
     - A large div (.map-land) positioned to roughly represent the northern region of Algeria
       (top: 20%, left: 10%, width: 80%, height: 55%, border-radius: 30% 40% 25% 35% / 20% 35% 40% 30%)
     - Slightly lighter shade than the bg to suggest land vs sea
  2. A few .map-city-dot elements for unlabeled background city markers
  3. 8 .map-pin elements positioned using % left/top values (inside the map container)
  4. The #map-info-panel absolutely positioned (CSS above)

Map pin positions (use % for left/top so they scale):
  - Algiers:      left: 57%, top: 28%
  - Blida:        left: 54%, top: 34%
  - Oran:         left: 22%, top: 26%
  - Constantine:  left: 72%, top: 24%
  - Annaba:       left: 80%, top: 20%
  - Tizi Ouzou:   left: 63%, top: 26%
  - Setif:        left: 68%, top: 32%
  - Medea:        left: 55%, top: 38%

Each pin HTML:
<div class="map-pin" data-project="[slug]" style="left:[%]; top:[%];">
  <div class="pin-label">[City]</div>
  <div class="pin-body"><div class="pin-icon"></div></div>
</div>

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT DATA (used for the info panel and cards)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Store as a JS object/array. Each project has:
  - id/slug (string, matches data-project on pin)
  - name (string)
  - city (string)
  - category (commercial | residential | industrial)
  - year (string)
  - area (string — e.g. "4,200 m²")
  - status (string — e.g. "Completed" or "In Progress")
  - completion (number 0–100, percentage)
  - description (1–2 sentences)
  - image (Unsplash URL — construction-themed)

Projects:
1. slug: "algiers-tower"    | name: "Algiers Business Tower"       | city: Algiers      | category: commercial   | year: 2023 | area: 12,400 m² | status: Completed   | completion: 100 | description: "A 14-floor commercial tower in the heart of Algiers featuring modern façade engineering and smart building systems."
2. slug: "blida-complex"    | name: "Blida Residential Complex"    | city: Blida        | category: residential  | year: 2024 | area: 8,200 m²  | status: In Progress | completion: 74  | description: "72-unit residential complex with underground parking and landscaped communal areas."
3. slug: "oran-warehouse"   | name: "Oran Industrial Warehouse"    | city: Oran         | category: industrial   | year: 2022 | area: 18,500 m² | status: Completed   | completion: 100 | description: "High-capacity logistics and storage facility built to international industrial standards."
4. slug: "constantine-mall" | name: "Constantine Retail Centre"    | city: Constantine  | category: commercial   | year: 2023 | area: 9,700 m²  | status: Completed   | completion: 100 | description: "Multi-level retail and dining complex featuring open-plan floor layouts and natural lighting design."
5. slug: "annaba-residences"| name: "Annaba Coastal Residences"   | city: Annaba       | category: residential  | year: 2025 | area: 5,400 m²  | status: In Progress | completion: 38  | description: "Seaside residential development comprising 48 premium apartments with panoramic sea-facing balconies."
6. slug: "tizi-school"      | name: "Tizi Ouzou School Campus"     | city: Tizi Ouzou   | category: commercial   | year: 2022 | area: 6,100 m²  | status: Completed   | completion: 100 | description: "Two-block secondary school campus with sports facilities, built under a government infrastructure contract."
7. slug: "setif-factory"    | name: "Sétif Production Facility"   | city: Setif        | category: industrial   | year: 2024 | area: 22,000 m² | status: In Progress | completion: 61  | description: "Full-scale agri-food production and cold storage facility serving central Algeria's distribution network."
8. slug: "medea-villas"     | name: "Médéa Villa Compound"        | city: Medea        | category: residential  | year: 2023 | area: 3,800 m²  | status: Completed   | completion: 100 | description: "Gated community of 12 premium villas with private gardens, built with natural stone and timber elements."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MAP INFO PANEL (id="map-info-panel")
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
When a pin is clicked:
1. Add class "active" to the clicked pin, remove from others
2. Populate the panel with the matching project data
3. Add class "visible" to the panel (triggers CSS slide-in animation)
4. Animate the progress bar fill from 0% to completion% using setTimeout

Panel contents (using the CSS classes defined above):
- Category badge: font-condensed text-[9px] tracking-[2px] uppercase, bg-gold/20 text-gold, px-2 py-[3px] rounded-[2px]
- Project name: font-condensed text-[18px] font-bold text-white mt-2 mb-1
- City + year: text-[12px] text-white/50
- Divider: border-t border-white/10 my-3
- Area label + value: two small text rows, text-[11px]
- Status label + value: color code — "Completed" = text-green-400, "In Progress" = text-gold
- Completion label: text-[11px] text-white/50 mt-3
- Progress bar: .progress-bar-track > .progress-bar-fill (animate to % on open)
- Percentage text: text-[12px] font-bold text-gold text-right mt-1
- Close button (×): absolute top-3 right-3, text-white/40 hover:text-white, font-bold text-[16px]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROJECT CARDS SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Layout: bg-navy, py-20 px-12
Header row (flex, justify-between, items-end):
  - Left: gold dash + "Portfolio" eyebrow + h2 "Featured Projects" in text-white
  - Right: filter buttons (All | Commercial | Residential | Industrial)
    Filter buttons: font-condensed text-[11px] font-bold tracking-[1.5px] uppercase px-5 py-2 rounded-full
    Active style: bg-gold text-navy border-2 border-gold
    Inactive style: border border-white/20 text-white/60 hover:border-white/50 hover:text-white

Grid: grid-cols-3 gap-4, max-sm:grid-cols-1, max-md:grid-cols-2

For EACH of the 8 projects, generate a card:
- .project-card class (hover defined in CSS above)
- relative overflow-hidden rounded-[3px] aspect-[4/3] cursor-pointer
- data-category="[category]" attribute
- <img> with Unsplash URL (construction-themed, matching category)
- Overlay (.project-overlay):
  - absolute inset-0, bg-gradient-to-t from-[rgba(30,36,60,0.92)] to-transparent
  - flex flex-col justify-end p-6
  - Category badge: font-condensed text-[9px] tracking-[2px] uppercase text-gold mb-1
  - Project name: font-condensed text-[18px] font-bold text-white leading-[1.2] mb-1
  - City + Year: text-[12px] text-white/60 mb-2
  - Completion bar (mini): w-full h-[3px] bg-white/20 rounded → fill width=[completion]% bg-gold
  - Completion text: text-[10px] text-gold font-bold mb-3
  - "View Details" link: font-condensed text-[10px] font-bold tracking-[1.8px] uppercase text-gold + arrow SVG

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FILTER LOGIC (JavaScript)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Filter buttons filter both the project cards AND highlight matching pins on the map
- When filter = "all": show all cards, all pins visible at full opacity
- When filter = category: show only matching cards (others display:none or opacity:0), 
  non-matching pins fade to opacity: 0.25 and scale down slightly

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CTA SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- bg-gold, py-20 px-12, centered
- H2: "Have a Project in Mind?" — font-condensed, text-navy, extrabold
- Subtext: "Let's discuss your next build. Request a free consultation today."
- Buttons: "Contact Us →" (bg-navy text-white) + "Our Services" (border-navy outlined)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FOOTER (exact same as index.html)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Same structure, classes, and content. bg-[rgb(15,19,35)], blueprint-subtle, footer-topline, 4-column grid, bottom bar.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GSAP ANIMATIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
On window load, register ScrollTrigger, then:
- Hero: stagger fade+y on eyebrow, h1, subtext
- Map section header: y: 30, opacity: 0
- Map container: scale: 0.96, opacity: 0, duration: 0.8
- Map pins: stagger scale from 0, opacity: 0, each: 0.07
- Project cards: y: 55, opacity: 0, stagger: 0.1
- CTA: y: 40, opacity: 0
- Hamburger + drawer toggle script

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONSTITUTIONAL SELF-CHECK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Before outputting the final file, go through this checklist and confirm each item passes.
Do not output the file until all 10 pass.

□ 1. No npm, bundler, or backend references anywhere in the file
□ 2. No CSS framework other than Tailwind CDN
□ 3. No icon library imports — every icon is a hand-written inline SVG
□ 4. No localStorage usage anywhere in the JS
□ 5. Map is built in pure HTML/CSS/JS — no Leaflet, no Google Maps JS API, no external library
□ 6. Fonts are only Barlow Condensed, Barlow, and Lato
□ 7. Tailwind config block is present with all 6 custom colors (navy, navy-dark, navy-card, gold, light-bg, muted)
□ 8. All JavaScript is inside window.addEventListener('load', () => { ... })
□ 9. GSAP and ScrollTrigger are loaded from cdnjs at version 3.12.2
□ 10. Logo uses the text fallback span — no local file path referenced

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTPUT REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Single complete projects.html file
- All CDN scripts included: Tailwind, GSAP, ScrollTrigger
- All JS in a single <script> at the bottom inside window.addEventListener('load', ...)
- Active nav link: Projects
- Fully responsive (mobile-first)
- No Lorem Ipsum — use real project data provided above
- Logo fallback: <span class="font-condensed text-[22px] font-extrabold text-white">ETB <span class="text-gold">Achouri</span></span>
```
