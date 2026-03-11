# Prompt: Responsive Fixing (Mobile, Tablet & Desktop)
> **Task:** Make an existing section fully responsive across all screen sizes.
> **Use when:** A section looks fine on desktop but breaks, overflows, or looks poor on mobile or tablet.

---

## 🔧 How to Use

Copy the prompt below, fill in every `[PLACEHOLDER]`, and paste it into your AI tool.
Paste the full current code — responsiveness issues often require full context to fix correctly.

---

## ✅ Prompt Template

```
You are a senior frontend developer specializing in responsive web design.

Make the following [SECTION NAME] section from a [BUSINESS TYPE] website fully responsive for mobile, tablet, and desktop — without changing its desktop design.

---

### CONTEXT
- Website type: [BUSINESS TYPE]
- Section name: [SECTION NAME] (e.g., Services, Hero, Projects Grid, Nav)
- Current approach: [e.g., CSS Flexbox / CSS Grid / none]

---

### CURRENT CODE
```html
[PASTE CURRENT HTML]
```

```css
[PASTE CURRENT CSS — include all existing media queries if any]
```

---

### RESPONSIVE ISSUES TO FIX
[List what's broken — check all that apply]:
- [ ] Content overflows horizontally on mobile (scroll appears)
- [ ] Text is too large / too small on mobile
- [ ] Cards or columns don't stack vertically on small screens
- [ ] Images are stretched, cropped wrong, or don't scale
- [ ] Navigation breaks on mobile (items overflow or overlap)
- [ ] Buttons are too small to tap comfortably on mobile
- [ ] Padding/margins are too large on mobile (wastes space)
- [ ] Section looks fine on mobile but breaks on tablet (768px–1024px)
- [ ] Other: [DESCRIBE]

---

### BREAKPOINT TARGETS
Apply styles for these breakpoints (mobile-first approach):

| Breakpoint | Width | Target Device |
|------------|-------|---------------|
| Default (no query) | 0px+ | Mobile (base styles) |
| Small tablet | 480px+ | Large phones |
| Tablet | 768px+ | Tablets, small laptops |
| Desktop | 1024px+ | Laptops and desktops |
| Wide desktop | 1280px+ | Large screens (optional) |

---

### LAYOUT RULES PER BREAKPOINT

Mobile (default):
- [ ] Single column layout
- [ ] Full-width elements
- [ ] Font sizes: H1=[SIZE]px, H2=[SIZE]px, body=[SIZE]px
- [ ] Touch targets minimum 44px height for buttons/links
- [ ] Horizontal padding: 16px–24px on sections

Tablet (768px+):
- [ ] [e.g., 2-column grid for cards]
- [ ] [e.g., Nav items in a row]
- [ ] Font sizes: H1=[SIZE]px, H2=[SIZE]px

Desktop (1024px+):
- [ ] [e.g., 3-column grid for cards]
- [ ] [e.g., Side-by-side two-column layout]
- [ ] Font sizes: H1=[SIZE]px (keep existing desktop styles)

---

### CONSTRAINTS
- Do NOT change the desktop appearance (1024px+ should look identical to the original)
- Do NOT change class names or IDs
- Do NOT add JavaScript or new dependencies
- Use only CSS media queries (no frameworks)
- Keep all existing CSS variables and color values
- Use mobile-first CSS (min-width queries, not max-width)

---

### DELIVERABLES
1. Updated HTML (only if structural changes are needed for mobile)
2. Updated CSS with:
   - Base (mobile-first) styles
   - Clearly labeled `@media` blocks for each breakpoint
   - Comment at the top of each media block: `/* === TABLET 768px+ === */`
3. A **## 📱 Responsive Notes** section with:
   - Summary of what changed at each breakpoint
   - Any mobile UX improvements added (e.g., larger tap targets)
   - Anything that couldn't be fixed with CSS alone

---

### OUTPUT FORMAT
Return:
1. Updated HTML → ```html code block (or "No HTML changes needed")
2. Updated CSS → ```css code block with labeled media queries
3. Responsive Notes → plain-text summary
```

---

## 📥 Input Checklist

Before running this prompt, confirm you have:
- [ ] Full HTML for the section
- [ ] Full CSS including any existing media queries
- [ ] A list of the specific responsive issues you're seeing
- [ ] The breakpoints you're targeting
- [ ] Confirmation of what the desktop layout should continue to look like

---

## 📤 Expected Output

| Output | Description |
|--------|-------------|
| Updated CSS | Mobile-first with clearly labeled @media breakpoints |
| Media queries | At minimum: 768px (tablet), 1024px (desktop) |
| Touch targets | Buttons/links minimum 44px height on mobile |
| No desktop changes | Desktop layout (1024px+) stays identical to original |

---

## 💡 Common Responsive Fixes — Quick Reference

| Issue | CSS Fix |
|-------|---------|
| Cards not stacking on mobile | `flex-direction: column` at base, `row` at 768px+ |
| Grid not collapsing | `grid-template-columns: 1fr` at base, restore at 768px+ |
| Oversized heading on mobile | `font-size: clamp(1.5rem, 5vw, 3rem)` |
| Horizontal overflow | `overflow-x: hidden` on parent + check for fixed widths |
| Images stretching | `max-width: 100%; height: auto` on `<img>` |
| Nav overflowing | `flex-wrap: wrap` or hide/show with a hamburger menu |
| Too-small buttons | `padding: 14px 24px; min-height: 44px` |
| Section padding too large | Reduce `padding` at mobile base to `40px 16px` |
| Two columns too narrow on tablet | Use `grid-template-columns: repeat(auto-fit, minmax(240px, 1fr))` |

---

## 📁 File Naming Convention
```
components/[section-name]-responsive.css
```
Or add media queries directly into the main CSS file with a clear comment block:
```css
/* ============================================
   RESPONSIVE STYLES — [SECTION NAME]
   ============================================ */
```
