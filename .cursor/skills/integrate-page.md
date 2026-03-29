DESCRIPTION: Integrate a newly generated HTML page into the existing site.globs

Read the following files to understand the source of truth:
1. index.html (for navbar and footer)
2. The target file provided by the user.

Perform the full Integration Audit:
. NAVBAR: Ensure it is identical to index.html (topbar + mainbar, logo, active class, hamburger).
. FOOTER: Ensure it is identical to index.html.
. CSS: Verify Tailwind CDN + Tailwind config block (6 custom colors, 3 font families).
. SCRIPTS: Verify GSAP 3.12.2 + ScrollTrigger CDNs. Ensure JS is inside load handler.
. LINKS: Ensure no broken href="#" placeholders.
. LOGO: Ensure Logo_Horizontal_Dark.svg is used (NO text fallbacks).

Fix any discrepancies directly in the target file. Output a short report of changes made.
