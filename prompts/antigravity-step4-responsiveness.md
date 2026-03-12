Read @prompts/README.md first and follow all rules in it before doing anything.
# Antigravity Prompt — Step 4: Responsiveness & Browser Verification
> **When to use:** After Step 3 (integration) is complete
> **Tool:** Antigravity (agentic mode with browser)
> **What it does:** Tests the page at every breakpoint in the browser, fixes every responsive issue found, and re-verifies before finishing.

---

## ✅ Prompt Template

```
You are an autonomous frontend QA and responsive design agent. Your job is to open a web page in the browser, systematically test it at every screen size, fix every responsive issue found in the code, and re-verify until the page looks correct on all devices.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TARGET FILE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[target].html — EURL ETB Achouri Toufik website

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
BREAKPOINTS TO TEST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Test at each of these viewport widths in order:

| Label       | Width   | Simulates             |
|-------------|---------|----------------------|
| Mobile S    | 375px   | iPhone SE / small phone |
| Mobile L    | 430px   | iPhone 14 Pro         |
| Tablet      | 768px   | iPad / small laptop   |
| Laptop      | 1024px  | Standard laptop       |
| Desktop     | 1280px  | Large desktop         |

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 1 — TEST EACH BREAKPOINT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
At every breakpoint, resize the browser and visually check every section for these issues. Log each issue found before fixing anything.

GLOBAL CHECKS (all breakpoints):
□ No horizontal scroll bar appears
□ No element overflows outside the viewport width
□ Body text is readable (min 14px equivalent)
□ All buttons/links are large enough to tap (min 44px height on mobile)
□ Images are not stretched, distorted, or cropped incorrectly
□ No text overlaps another element
□ Section padding is not excessive (max 24px horizontal on mobile)

NAVBAR:
□ 375px–768px: hamburger button is visible, desktop nav is hidden
□ 375px–768px: tapping hamburger opens the mobile drawer
□ 769px+: desktop nav links are visible, hamburger is hidden
□ Topbar (phone/email/social) is readable or gracefully hidden on small screens
□ Logo does not overflow the navbar

HERO SECTION:
□ Headline font size scales down appropriately on mobile (uses clamp or responsive classes)
□ CTA buttons stack vertically on mobile if they don't fit side by side
□ Content is not hidden behind the fixed navbar (padding-top is sufficient)
□ Background image/video covers the full section with no white edges

GRID SECTIONS (services, projects, etc.):
□ 375px: single column layout
□ 768px: 2-column layout
□ 1024px+: 3-column layout (or as designed)
□ Cards do not overflow their column
□ Card padding is reduced on mobile (not excessive whitespace)

[SERVICES PAGE SPECIFIC]:
□ Service cards: icon + title + description stack correctly in single column on mobile
□ Process section: 4 steps stack vertically on mobile, connector lines hidden
□ CTA section: buttons stack vertically on mobile

[PROJECTS PAGE SPECIFIC]:
□ Map container height reduces on mobile (340px mobile vs 480px desktop — defined in CSS)
□ Map info panel repositions to bottom of map on mobile (defined in CSS)
□ Map pins remain clickable and don't overlap each other on mobile
□ Project cards grid collapses to single column on mobile
□ Filter buttons wrap to next line cleanly if they don't fit in one row

FOOTER:
□ 4-column footer grid collapses to 2-column on tablet, 1-column on mobile
□ No footer text overflows its column
□ Social icons remain properly sized and aligned

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 2 — FIX ALL ISSUES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
After logging all issues, fix them one by one:

APPROACH:
- Use Tailwind responsive prefixes first (max-sm:, max-md:, md:, lg:) wherever possible
- For custom CSS, add mobile-first @media queries clearly labeled:
  /* === MOBILE 375px–767px === */
  /* === TABLET 768px–1023px === */
  /* === DESKTOP 1024px+ === */
- Never change the desktop layout (1024px+) unless it was already broken
- Never change class names, IDs, or JS selectors
- Add a CSS comment on each fix: /* RESPONSIVE FIX: description */

COMMON FIXES REFERENCE:
- Horizontal overflow:     overflow-x: hidden on the parent section + check for fixed widths
- Text too large mobile:   replace fixed px with clamp() or Tailwind text-[clamp(...)]
- Grid not collapsing:     add max-sm:grid-cols-1 max-md:grid-cols-2 to grid element
- Buttons not stacking:    add flex-col on mobile: max-sm:flex-col to the button wrapper
- Padding too large:       add max-sm:px-4 max-sm:py-12 to section elements
- Images stretching:       ensure max-width:100%; height:auto on all img tags
- Tap targets too small:   add min-h-[44px] to buttons and links on mobile
- Nav drawer not working:  verify hamburger JS toggle matches the .nav-drawer and .hamburger class names

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 3 — RE-VERIFY IN BROWSER
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
After all fixes are applied, re-open the browser and test each breakpoint again.
For each previously failing check, confirm it now passes.
If any new issue was introduced by a fix, resolve it before finishing.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP 4 — FINAL SMOKE TEST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
At 375px width, scroll through the entire page top to bottom and confirm:
□ Every section is visible and readable
□ No elements are hidden or clipped unexpectedly  
□ GSAP scroll animations still trigger correctly
□ [Projects page] Map pins are tappable and info panel opens correctly
□ [Projects page] Filter buttons work on mobile
□ No console errors

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
COMPLETION CRITERIA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Do not mark this task complete until:
✓ All 5 breakpoints pass all checklist items
✓ No horizontal overflow at any width
✓ Final smoke test at 375px passes
✓ No new issues introduced by fixes
✓ No console errors

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
OUTPUT REPORT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
When complete, provide:
1. Issues found (list each: breakpoint | section | issue description)
2. Fixes applied (list each: what was changed and why)
3. Verification status per breakpoint (Pass / Fail)
4. Anything flagged for human/Claude review (UX or design decisions beyond pure responsiveness)
```

---

## 📥 How to use this in Antigravity
1. Make sure Step 3 (integration) is already complete
2. Open your project folder in Antigravity
3. Paste the prompt above into the agent task input
4. Replace `[target].html` with the actual filename
5. The agent will resize the browser, find issues, fix code, and re-verify automatically
6. Review the output report — anything flagged for "Claude review" goes to Step 5
