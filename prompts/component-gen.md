# Prompt: Component Generation
> **Task:** Generate a complete HTML + CSS section/component for a website.
> **Use when:** You need to build a new page section from scratch (e.g., hero, services, team, footer).

---

## 🔧 How to Use

Copy the prompt below, fill in every `[PLACEHOLDER]`, and paste it into your AI tool.

---

## ✅ Prompt Template

```
You are a senior frontend developer building a professional website for [BUSINESS TYPE] (e.g., a construction company).

Generate a complete, production-ready HTML + CSS component for the **[SECTION NAME]** section.

---

### CONTEXT
- Website type: [BUSINESS TYPE] (e.g., construction, agency, law firm)
- Brand tone: [TONE] (e.g., bold and industrial / clean and corporate / warm and approachable)
- Primary color: [HEX OR COLOR NAME] (e.g., #FF6B00 orange, dark navy #0A1628)
- Secondary color: [HEX OR COLOR NAME]
- Font preference: [FONT NAME OR STYLE] (e.g., use Google Fonts — bold sans-serif)
- Existing CSS variables (if any):
  [PASTE YOUR :root CSS VARIABLES HERE, OR WRITE "none"]

---

### SECTION REQUIREMENTS
- Section name: [SECTION NAME] (e.g., Hero, Services, Projects, Testimonials, CTA, Footer)
- Content to include:
  [LIST CONTENT ITEMS — e.g., headline, subheadline, CTA button, background image slot, 3 service cards with icon + title + description]
- Layout style: [LAYOUT PREFERENCE] (e.g., full-width, two-column grid, card row, centered)
- Any special behavior: [INTERACTIONS OR ANIMATIONS] (e.g., hover effects on cards, sticky nav, parallax, none)

---

### DELIVERABLES
1. Full HTML block for the section (semantic tags: <section>, <header>, <article>, etc.)
2. Scoped CSS for the section only (no global resets — only styles for this component)
3. Use CSS custom properties (variables) for colors and fonts
4. All classes must be prefixed with the section name to avoid collisions (e.g., .hero-title, .services-card)
5. The component must be mobile-first and responsive (include at least one @media breakpoint for 768px)
6. Add placeholder image paths where needed (e.g., src="images/hero-bg.jpg")
7. Add a short HTML comment at the top identifying the section

---

### OUTPUT FORMAT
Return the response in two clearly labeled code blocks:
- ```html  → the HTML
- ```css   → the CSS

Do not include a full HTML page wrapper (<html>, <head>, <body>). Return the section only.
```

---

## 📥 Input Checklist

Before running this prompt, confirm you have:
- [ ] Business type defined
- [ ] Brand tone described
- [ ] Color values ready
- [ ] Font choice decided
- [ ] Section content listed (what text/items go inside)
- [ ] Layout preference noted

---

## 📤 Expected Output

| Output | Description |
|--------|-------------|
| `HTML block` | One `<section>` with semantic structure and placeholder content |
| `CSS block` | Scoped styles with variables, flexbox/grid layout, hover effects |
| `Responsiveness` | Mobile-first with at least one media query at 768px |
| `Prefixed classes` | e.g., `.hero-`, `.services-`, `.projects-` |

---

## 💡 Example: Pre-filled Prompt (Construction Company Hero)

```
You are a senior frontend developer building a professional website for a construction company.

Generate a complete, production-ready HTML + CSS component for the **Hero** section.

### CONTEXT
- Website type: Construction company
- Brand tone: Bold and industrial
- Primary color: #FF6B00
- Secondary color: #0A1628
- Font preference: Google Fonts — "Oswald" for headings, "Inter" for body
- Existing CSS variables: none

### SECTION REQUIREMENTS
- Section name: Hero
- Content to include: Full-width background image overlay, large headline "Building the Future", subheadline "Quality construction you can trust", one CTA button "View Our Projects", one secondary link "Learn More ↓"
- Layout style: Full-width centered
- Any special behavior: Subtle fade-in animation on text load

### DELIVERABLES
[Same as template above]
```

---

## 📁 File Naming Convention
Save generated components as:
```
components/[section-name].html
components/[section-name].css
```
Example: `components/hero.html`, `components/hero.css`
