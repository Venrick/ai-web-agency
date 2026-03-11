# 📁 AI Prompt Library — Web Development
> A collection of structured, reusable prompts for AI-supervised web development.
> Designed for HTML/CSS projects — currently used for a construction company website.

---

## 🗂️ Prompt Index

| # | File | Task | Use When |
|---|------|------|----------|
| 01 | `01-component-generation.md` | Generate new HTML/CSS sections | Building a new page section from scratch |
| 02 | `02-bug-fixing.md` | Fix layout & styling bugs | Something looks broken or misaligned |
| 03 | `03-layout-improvement.md` | Improve UX & visual design | Section works but looks generic or unpolished |
| 04 | `04-responsive-fixing.md` | Make sections mobile/tablet ready | Desktop looks fine but mobile is broken |

---

## ⚙️ Workflow Overview

```
Supervisor (you)
    │
    ├─► Need a new section?      → Use 01-component-generation.md
    ├─► Something looks broken?  → Use 02-bug-fixing.md
    ├─► Looks bland or generic?  → Use 03-layout-improvement.md
    └─► Broken on mobile?        → Use 04-responsive-fixing.md
```

---

## 📋 How to Use These Prompts

1. Open the relevant `.md` file
2. Copy the prompt inside the code block
3. Fill in every `[PLACEHOLDER]` with your project details
4. Paste into your AI tool (Claude, ChatGPT, etc.)
5. Review the output — paste code into your project files
6. If needed, run `02-bug-fixing.md` on the output to refine

---

## 🏗️ Project Context (Update as needed)

```
Project:         Construction Company Website
Stack:           HTML5, CSS3 (no frameworks)
Primary color:   #FF6B00  (orange)
Secondary color: #0A1628  (dark navy)
Accent:          #FFFFFF  (white)
Heading font:    Oswald (Google Fonts)
Body font:       Inter (Google Fonts)
Breakpoints:     480px | 768px | 1024px | 1280px
```

---

## 📐 CSS Variables Reference
Add to your project's `styles.css` `:root` block and paste into prompts when asked:

```css
:root {
  /* Colors */
  --color-primary:    #FF6B00;
  --color-secondary:  #0A1628;
  --color-accent:     #FFFFFF;
  --color-bg:         #F5F5F5;
  --color-text:       #1A1A1A;
  --color-text-muted: #666666;

  /* Typography */
  --font-heading: 'Oswald', sans-serif;
  --font-body:    'Inter', sans-serif;

  /* Spacing */
  --spacing-xs:  8px;
  --spacing-sm:  16px;
  --spacing-md:  32px;
  --spacing-lg:  64px;
  --spacing-xl:  96px;

  /* Border radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;

  /* Shadows */
  --shadow-sm: 0 2px 8px rgba(0,0,0,0.08);
  --shadow-md: 0 4px 20px rgba(0,0,0,0.12);
  --shadow-lg: 0 8px 40px rgba(0,0,0,0.16);

  /* Max content width */
  --max-width: 1200px;
}
```

---

## 🗃️ Suggested Folder Structure

```
project/
├── index.html
├── styles.css
├── components/
│   ├── nav.html
│   ├── hero.html
│   ├── services.html
│   ├── projects.html
│   ├── testimonials.html
│   ├── cta.html
│   └── footer.html
├── images/
└── prompts/               ← This folder
    ├── README.md
    ├── 01-component-generation.md
    ├── 02-bug-fixing.md
    ├── 03-layout-improvement.md
    └── 04-responsive-fixing.md
```

---

## 🧠 Prompt Tips

- **Always paste real code** — never describe it without including it. AI fixes real code, not descriptions.
- **Be specific about what's wrong** — "it looks bad" gives poor results. "The cards stack vertically on desktop instead of a 3-column row" gives great results.
- **Run prompts in sequence** — Generate with 01 → improve with 03 → make responsive with 04 → fix bugs with 02.
- **Include CSS variables** — Always paste your `:root` variables so the AI uses your brand colors, not defaults.
- **Save versions** — Before running an improvement prompt, save your current file as `-v1` so you can roll back.
