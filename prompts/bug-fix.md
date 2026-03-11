# Prompt: Bug Fixing (Layout & Styling Issues)
> **Task:** Diagnose and fix a CSS or HTML layout/styling bug.
> **Use when:** A section looks broken, misaligned, overflowing, or not displaying as intended.

---

## 🔧 How to Use

Copy the prompt below, fill in every `[PLACEHOLDER]`, and paste it into your AI tool.
Always paste the **actual broken code** — never describe it without including the code.

---

## ✅ Prompt Template

```
You are a senior frontend developer and CSS debugging expert.

I have a layout/styling bug in a section of my [BUSINESS TYPE] website. Your job is to:
1. Identify the exact cause of the bug
2. Fix only the broken code (do not rewrite unaffected parts)
3. Explain what caused it and why the fix works

---

### BUG DESCRIPTION
Describe what you see happening:
"[DESCRIBE THE VISUAL BUG — e.g., The services section cards stack vertically on desktop instead of in a row. The nav overflows off screen on mobile. The hero text overlaps the image."]

Expected behavior:
"[DESCRIBE WHAT IT SHOULD LOOK LIKE — e.g., Three cards side by side on desktop, stacked on mobile]"

---

### ENVIRONMENT
- Browser(s) where bug appears: [e.g., Chrome, Safari, all browsers]
- Screen size where bug appears: [e.g., mobile only / desktop only / all sizes]
- Device type: [e.g., iPhone 14, Windows desktop, all]

---

### BROKEN CODE
Paste the full HTML and CSS for the affected section:

```html
[PASTE YOUR HTML HERE]
```

```css
[PASTE YOUR CSS HERE]
```

---

### CONSTRAINTS
- Do NOT change the HTML structure unless absolutely necessary
- Do NOT change class names or IDs
- Do NOT add new dependencies or JavaScript
- Keep any existing CSS variables and naming conventions intact
- Fix should be minimal — change only what's needed

---

### DELIVERABLES
1. The corrected HTML (if changed) with inline comment marking each fix → `<!-- FIXED: reason -->`
2. The corrected CSS with inline comment marking each fix → `/* FIXED: reason */`
3. A plain-English explanation (3–5 sentences) of:
   - What caused the bug
   - What the fix does
   - How to avoid this bug in future

---

### OUTPUT FORMAT
Return three sections:
1. Fixed HTML code block (```html)
2. Fixed CSS code block (```css)
3. Plain-English explanation section labeled **## 🔍 Bug Analysis**
```

---

## 📥 Input Checklist

Before running this prompt, confirm you have:
- [ ] A clear description of what looks broken
- [ ] A description of what it *should* look like
- [ ] The affected HTML pasted in
- [ ] The affected CSS pasted in
- [ ] Browser/device info noted

---

## 📤 Expected Output

| Output | Description |
|--------|-------------|
| Fixed HTML | Same structure with targeted corrections and `<!-- FIXED -->` comments |
| Fixed CSS | Minimal edits with `/* FIXED */` comments |
| Bug Analysis | 3–5 sentence plain-English explanation |

---

## 💡 Common Bug Types — Quick Reference

Use these descriptions in the **BUG DESCRIPTION** field:

| Symptom | What to Write |
|---------|--------------|
| Elements stacking instead of side by side | "Cards stack vertically on desktop — expected 3-column row" |
| Content overflowing screen horizontally | "Horizontal scroll appears on mobile — content overflows viewport" |
| Image not filling container | "Hero image doesn't cover the full background — shows white space" |
| Text overlapping another element | "Nav menu overlaps hero section on scroll" |
| Section has unexpected white gap | "Large white gap appears above the services section" |
| Button not centered | "CTA button aligns left instead of centered inside its container" |
| Flexbox items not wrapping | "Service cards don't wrap to next row on smaller screens" |
| Z-index overlap issue | "Dropdown menu appears behind the hero image" |

---

## 📁 File Naming Convention
Save fixed files as:
```
components/[section-name]-fixed.html
components/[section-name]-fixed.css
```
Or overwrite originals once confirmed working.
