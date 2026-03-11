# Prompt: Layout Improvement (UX & Design)
> **Task:** Improve the visual design, user experience, and layout of an existing section.
> **Use when:** A section works but looks generic, cluttered, or could be more polished and professional.

---

## 🔧 How to Use

Copy the prompt below, fill in every `[PLACEHOLDER]`, and paste it into your AI tool.
Include your current code and be specific about what feels "off" — the more context, the better the output.

---

## ✅ Prompt Template

```
You are a senior UX designer and frontend developer specializing in professional business websites.

Review the following [SECTION NAME] section from a [BUSINESS TYPE] website and improve its layout, visual design, and user experience — without changing its core content or purpose.

---

### CONTEXT
- Website type: [BUSINESS TYPE] (e.g., construction company, law firm, agency)
- Target audience: [WHO VISITS THIS SITE — e.g., homeowners, business owners, contractors]
- Brand tone: [TONE] (e.g., trustworthy and professional / bold and modern / warm and approachable)
- Primary color: [HEX] | Secondary color: [HEX]
- Font: [FONT NAME]

---

### CURRENT STATE
This is the current section code:

```html
[PASTE CURRENT HTML]
```

```css
[PASTE CURRENT CSS]
```

---

### WHAT FEELS OFF
[BE SPECIFIC — choose one or more]:
- "It looks too plain / generic"
- "The spacing feels too tight / too loose"
- "The typography hierarchy is weak — nothing stands out"
- "It feels unbalanced — too much on one side"
- "It doesn't feel trustworthy / professional enough"
- "The cards all look the same — no visual interest"
- "The CTA button doesn't stand out"
- [OR WRITE YOUR OWN DESCRIPTION]

---

### IMPROVEMENT GOALS
Choose or write your priorities (ranked 1 = most important):
1. [e.g., Stronger visual hierarchy — headline should dominate]
2. [e.g., Better spacing and breathing room between elements]
3. [e.g., Make the CTA button more prominent]
4. [e.g., Add a subtle background treatment to differentiate the section]
5. [e.g., Improve card design — add icons, borders, or hover states]

---

### CONSTRAINTS (do not change these)
- Keep all existing HTML class names and IDs
- Do not add new libraries or JavaScript
- Do not change the written text content
- Stay within the existing color palette
- Must remain responsive (mobile + desktop)

---

### DELIVERABLES
1. Improved HTML — with a comment `<!-- IMPROVED: reason -->` next to any structural changes
2. Improved CSS — with a comment `/* IMPROVED: reason */` next to key changes
3. A **## 🎨 Design Decisions** section explaining:
   - What changes were made and why
   - What UX principle each change supports
   - Any optional enhancements that could be added next

---

### OUTPUT FORMAT
Return three labeled sections:
1. Improved HTML → ```html code block
2. Improved CSS → ```css code block  
3. Design Decisions → plain-text section
```

---

## 📥 Input Checklist

Before running this prompt, confirm you have:
- [ ] Current working HTML and CSS for the section
- [ ] Clear description of what feels "off"
- [ ] Ranked list of improvement goals
- [ ] Constraints listed (what must stay the same)

---

## 📤 Expected Output

| Output | Description |
|--------|-------------|
| Improved HTML | Minimal structural changes with labeled comments |
| Improved CSS | Enhanced spacing, typography, color use, and effects |
| Design Decisions | Explanation of changes tied to UX principles |

---

## 💡 UX Improvement Areas — Quick Reference

Use these in the **IMPROVEMENT GOALS** field:

| Area | What to Ask For |
|------|----------------|
| Typography hierarchy | "Make headline significantly larger and bolder. Add visual weight contrast." |
| Whitespace & rhythm | "Add more breathing room between elements. Use consistent vertical spacing." |
| Color contrast | "Increase contrast between text and background for readability." |
| CTA prominence | "Make the primary button stand out with size, color, and shadow." |
| Card design | "Add visual separation between cards — border, shadow, or background color." |
| Section differentiation | "Add a subtle background (light gray, pattern, or gradient) to separate this section." |
| Icon use | "Add simple SVG or emoji icons to each service card to improve scannability." |
| Trust signals | "Add a stat bar (e.g., '200+ projects completed') to build credibility." |
| Visual focus | "Add a focal element — a bold number, large icon, or accent line to draw the eye." |

---

## 📁 File Naming Convention
```
components/[section-name]-v2.html
components/[section-name]-v2.css
```
Keep the original version before overwriting, so you can compare.
