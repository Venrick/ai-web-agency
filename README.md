# EURL ETB Achouri Toufik — Company Website

Official website for EURL ETB Achouri Toufik, a construction company based in Algeria.
Built and maintained using an AI-supervised development workflow.

---

## 📄 Pages

| File | Status |
|------|--------|
| `index.html` | ✅ Complete |
| `about.html` | ✅ Complete |
| `contact.html` | ✅ Complete |
| `services.html` | 🔲 In progress |
| `projects.html` | 🔲 In progress |

---

## 📁 Folder Structure

```
eurletb/
├── index.html
├── about.html
├── contact.html
├── services.html
├── projects.html
├── style.css
├── scripts.js
├── images/
├── prompts/          ← AI prompt library + tech stack reference
│   ├── README.md
│   ├── component-gen.md
│   ├── bug-fix.md
│   ├── layout-improvement.md
│   ├── responsive-fixing.md
│   ├── gemini-prompt-services-page.md
│   ├── gemini-prompt-projects-page.md
│   ├── antigravity-step3-integration.md
│   └── antigravity-step4-responsiveness.md
└── workflow/         ← Development pipeline documentation
    └── blueprint.md
```

---

## 🤖 AI Development Workflow

This site is built using a multi-agent AI pipeline — no manual coding by the supervisor.

| Step | Tool | Model | Task |
|------|------|-------|------|
| 1 — Plan | claude.ai | Claude Sonnet | Plan pages, write prompts |
| 2 — Generate | Antigravity | Gemini Flash | Generate HTML/CSS |
| 3 — Integrate | Antigravity | Claude Sonnet 4.5 | Integrate into site, verify in browser |
| 4 — QA | Antigravity | Claude Sonnet 4.5 | Fix responsiveness at all breakpoints |
| 5 — Review | claude.ai | Claude Sonnet | UX and layout review |

→ Full pipeline details: [`workflow/blueprint.md`](workflow/blueprint.md)
→ Tech stack rules and prompt index: [`prompts/README.md`](prompts/README.md)

---

## 🏗️ Tech Stack

- **HTML5 / CSS3 / Vanilla JS** — no framework, no build step
- **Tailwind CSS** via CDN
- **GSAP 3.12.2** + ScrollTrigger for animations
- **Google Fonts** — Barlow Condensed, Barlow, Lato
- Static files — opens directly in a browser, no server needed
