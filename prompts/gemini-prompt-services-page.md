# Gemini Prompt — services.html
> Copy everything inside the code block and paste it directly into Gemini.

---

```
You are a senior frontend developer. Your job is to build a complete, standalone services.html page for a construction company website called "EURL ETB Achouri Toufik".

This page must be pixel-perfect consistent with the existing site. I will give you the full design system, navbar, footer, and all patterns to follow.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TECH STACK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Tailwind CSS via CDN: <script src="https://cdn.tailwindcss.com"></script>
- GSAP 3 + ScrollTrigger via CDN for scroll animations
- Google Fonts: Barlow (400,500,600), Barlow Condensed (700,800), Lato (300,400,700)
- No other libraries or frameworks

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TAILWIND CONFIG (paste inside a <script> tag after the CDN)
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
CUSTOM CSS CLASSES (paste in a <style> tag in <head>)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
/* Blueprint grid */
.blueprint-subtle {
  background-image:
    linear-gradient(rgba(193,159,93,.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(193,159,93,.04) 1px, transparent 1px);
  background-size: 48px 48px;
}
/* Nav active underline */
.nav-link { position: relative; padding-bottom: 4px; }
.nav-link.active { color: #fff !important; }
.nav-link.active::after {
  content: ''; position: absolute; bottom: -2px; left: 0; right: 0;
  height: 2px; background: #c19f5d;
}
/* Hamburger */
.hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; background: none; border: none; padding: 4px; }
.hamburger span { width: 24px; height: 2px; background: #fff; display: block; transition: all .3s; transform-origin: center; }
.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }
/* Mobile drawer */
.nav-drawer { max-height: 0; overflow: hidden; transition: max-height .35s ease; background: #1e243c; }
.nav-drawer.open { max-height: 400px; }
.nav-drawer a { display: block; padding: 12px 24px; color: rgba(255,255,255,.75); text-decoration: none; font-size: 14px; font-weight: 500; letter-spacing: 1px; text-transform: uppercase; border-bottom: 1px solid rgba(193,159,93,.1); transition: color .2s; }
.nav-drawer a:hover, .nav-drawer a.active { color: #c19f5d; }
/* Service card hover: gold top bar sweep */
.service-card { transition: transform .25s, box-shadow .25s; position: relative; }
.service-card::before { content: ''; position: absolute; top: 0; left: 0; height: 3px; width: 0; background: #c19f5d; transition: width 0.4s ease; }
.service-card:hover::before { width: 100%; }
.service-card:hover { transform: translateY(-4px); box-shadow: 0 8px 32px rgba(30,36,60,.12); }
/* Footer nav link hover */
.fnav-link { transition: color .2s, padding-left .2s; display: flex; align-items: center; gap: 0; }
.fnav-link::before { content: ''; width: 0; height: 1px; background: #c19f5d; display: inline-block; transition: width .2s, margin-right .2s; }
.fnav-link:hover { color: #fff !important; padding-left: 4px; }
.fnav-link:hover::before { width: 14px; margin-right: 6px; }
/* Footer topline */
.footer-topline { height: 3px; background: linear-gradient(to right, transparent, #c19f5d 20%, #c19f5d 80%, transparent); }
/* Input focus */
input:focus, textarea:focus { outline: none; border-color: #c19f5d !important; background: rgba(193,159,93,.05) !important; }
@media(max-width:768px) {
  .hamburger { display: flex; }
  .nav-desktop { display: none !important; }
}
@media(min-width:769px) { .nav-drawer { display: none !important; } }

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
NAVBAR (copy exactly — only change the active nav link)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
The active page link is "Services" — add class "active" to the Services <a> tag.
The navbar is fixed (position fixed, z-[100]).
It has two parts:
  1. Top bar: dark bg (rgb(15,19,35)), 36px height, phone + email on left, social icons on right
  2. Main bar: navy bg (#1e243c), 68px height, gold bottom border (3px), logo left, nav links right
     Nav links: Home, About, Services, Projects, Contact — plus a "Get a Quote" outlined gold button
Mobile: show hamburger button, hide nav-desktop, show nav-drawer below main bar.

Use this exact nav structure from the existing site (replicate it in full — do not simplify).

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PAGE HERO SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Full-width, bg-navy, min-height 360px
- Blueprint-subtle overlay (absolute, pointer-events-none)
- Gold bottom border (3px)
- Top padding: pt-[104px] (accounts for fixed navbar)
- Content centered, max-w-[1200px] mx-auto px-12
- Eyebrow: gold line (w-10 h-[1px]) + "Our Expertise" in font-condensed text-[11px] tracking-[3px] uppercase text-gold
- H1: font-condensed, clamp(40px,6vw,64px), font-extrabold, text-white, leading-[1.1]
  Text: "Comprehensive <span class='text-gold'>Construction</span> Services"
- Subheading: text-[15px] text-white/55 max-w-[560px] mx-auto mt-4 text-center leading-[1.75]
  Text: "From residential homes to large-scale industrial facilities, we deliver tailored solutions with precision and integrity."
- Breadcrumb: Home / Services — small text-white/35, font-condensed, with gold separator "/"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SERVICES GRID SECTION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- bg-light-bg (#f4f4f2), py-24 px-12
- Max-w-[1200px] mx-auto
- Section label above the grid (centered): gold line + "What We Offer" + main heading "Built for Every Scale"
- 3-column grid on desktop, 2-column on tablet, 1-column on mobile
- gap-6

Build 8 service cards using this exact card style:
  - bg-white, border border-[rgba(30,36,60,0.07)], rounded-[3px], p-9, flex flex-col, shadow-[0_2px_16px_rgba(30,36,60,0.06)]
  - Icon block: w-16 h-16 bg-navy rounded-[4px] flex items-center justify-center mb-7 flex-shrink-0
  - Icon: w-7 h-7, stroke="#c19f5d", stroke-width="1.8", stroke-linecap="round"
  - Title: font-barlow text-[17px] font-semibold text-navy mb-3
  - Description: text-[13.5px] text-muted leading-[1.7] flex-1 mb-6
  - "Learn More" link: font-condensed text-[11px] font-bold tracking-[1.8px] uppercase text-navy hover:text-gold + arrow SVG

Services to include:

1. Residential Construction
   Icon: house SVG (path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z" + polyline points="9 22 9 12 15 12 15 22")
   Description: Custom single-family homes, multi-unit residential complexes, and apartment buildings crafted with premium materials and modern architectural design standards.

2. Commercial & Industrial Buildings
   Icon: building/office SVG (rect x="2" y="7" width="20" height="14" rx="2" + path d="M16 7V5a2 2 0 00-2-2h-4a2 2 0 00-2 2v2")
   Description: Large-scale office complexes, warehouses, retail spaces, and industrial facilities engineered for maximum operational efficiency and long-term durability.

3. Renovation & Remodeling
   Icon: wrench SVG (path d="M14.7 6.3a1 1 0 000 1.4l1.6 1.6a1 1 0 001.4 0l3.77-3.77a6 6 0 01-7.94 7.94l-6.91 6.91a2.12 2.12 0 01-3-3l6.91-6.91a6 6 0 017.94-7.94l-3.76 3.76z")
   Description: Structural reinforcements, interior remodeling, and full-scale refurbishment of existing buildings, breathing new life into aging infrastructure with modern finishes.

4. General Contracting & Project Management
   Icon: clipboard/checklist SVG
   Description: End-to-end project coordination from procurement to final handover. We manage timelines, subcontractors, materials, and quality control at every phase.

5. Heavy Machinery & Earthmoving
   Icon: truck SVG (rect x="1" y="3" width="15" height="13" + path d="M16 8h4l3 3v5h-7V8z" + circles for wheels)
   Description: Site clearing, excavation, grading, and earthmoving operations using a modern fleet of heavy equipment operated by certified professionals.

6. Structural Engineering & Design
   Icon: blueprint/ruler SVG
   Description: Detailed structural calculations, architectural plans, and technical drawing services ensuring every build meets national and international engineering codes.

7. Infrastructure & Civil Works
   Icon: road/bridge SVG
   Description: Road construction, drainage systems, retaining walls, and site infrastructure projects delivered on schedule with precise civil engineering expertise.

8. Maintenance & Facility Management
   Icon: shield-check SVG (path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" + path d="M9 12l2 2 4-4")
   Description: Preventive and corrective maintenance programs for residential, commercial, and industrial facilities, keeping your assets in peak condition year-round.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PROCESS SECTION (between Services Grid and CTA)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- bg-navy, py-24 px-12, blueprint-subtle overlay
- Section header (centered, text-white): eyebrow "How We Work" + title "Our Construction Process"
- 4-step horizontal process (flex row, gap-8, on mobile: flex-col)
- Each step:
  - Step number: large font-condensed text-[64px] font-extrabold text-gold/20 leading-none
  - Step label: font-condensed text-[11px] font-bold tracking-[3px] uppercase text-gold mt-[-10px]
  - Title: font-barlow text-[17px] font-semibold text-white mt-3 mb-2
  - Description: text-[13px] text-white/50 leading-[1.65]
  - Connector line between steps: flex-1 h-[1px] bg-gold/20 (hide on mobile)

Steps:
  01 — Site Assessment: Detailed on-site evaluation, soil analysis, and feasibility study to establish accurate project scope and timeline.
  02 — Planning & Design: Architectural drawings, structural calculations, and material selection aligned with your requirements and budget.
  03 — Construction: Mobilization of our certified workforce and machinery, with daily progress reporting and strict quality control.
  04 — Handover & Support: Final inspection, documentation delivery, and ongoing maintenance support to ensure long-term performance.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CTA SECTION (bottom of page, before footer)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- bg-gold (the gold section is a signature CTA element in this brand)
- py-20 px-12
- Centered content, max-w-[800px] mx-auto
- Headline: font-condensed text-[clamp(32px,5vw,52px)] font-extrabold text-navy leading-[1.1]
  Text: "Ready to Start Your Next Project?"
- Subtext: text-[15px] text-navy/70 mt-4 mb-10
  Text: "Our team is ready to deliver — from blueprint to final inspection. Contact us today for a free consultation and quote."
- Two buttons side by side:
  1. Primary: bg-navy text-white font-condensed text-[12px] font-bold tracking-[2px] uppercase px-10 py-4 hover:opacity-90
     Label: "Get a Free Quote →" — href="contact.html"
  2. Secondary: border-2 border-navy text-navy font-condensed text-[12px] font-bold tracking-[2px] uppercase px-10 py-4 hover:bg-navy hover:text-white transition-all
     Label: "View Our Projects" — href="projects.html"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
FOOTER (copy exactly from index.html)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
bg-[rgb(15,19,35)], blueprint-subtle overlay, footer-topline at top.
4-column grid: Brand info + address | Navigation links | Services links | Newsletter signup box
Bottom bar: copyright left, social icons right.
Use exact same structure, classes, and content as index.html footer.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
GSAP ANIMATIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Register ScrollTrigger. Apply these on window load:
- Hero content: fade + y: 40 stagger on eyebrow, h1, p, breadcrumb
- Service cards: y: 55, opacity: 0, stagger: 0.1, trigger: when grid enters viewport 82%
- Process steps: x: -30, opacity: 0, stagger: 0.15, trigger: when section enters viewport 78%
- CTA section: y: 40, opacity: 0, trigger: when section enters viewport 80%

Also include:
- Hamburger toggle script (same as index.html)
- Active nav link highlighting for "services.html"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTPUT REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Output a single complete services.html file
- Include <!DOCTYPE html>, <html lang="en">, <head> with all CDN links, <body>, and all scripts at the bottom
- Use placeholder logo: replace local logo path with a text-based logo fallback: <span class="font-condensed text-[22px] font-extrabold text-white tracking-[1px]">ETB <span class="text-gold">Achouri</span></span>
- Use Unsplash images for any visual backgrounds (construction-themed)
- Do NOT use Lorem Ipsum — use the real content provided above
- All sections must be fully responsive (mobile-first)
- Active nav link: Services
```
