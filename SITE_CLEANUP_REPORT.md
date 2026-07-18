# Open Chronicles site cleanup report

**Date:** 2026-07-18
**Scope:** Conservative publication-quality audit, independent review of the prior cleanup, and authorized publication
**Site:** https://openchronicles.org
**Deployment:** Published from the reviewed master commit after all checks below passed

## 1. Executive summary

Open Chronicles is a plain HTML and CSS site published from the repository-root master branch by GitHub Pages, with the custom domain in CNAME. There is no application framework, package manager, generated site tree, or normal build command.

The prior cleanup was directionally good: it corrected obsolete launch wording, added page-specific metadata, improved publication status labels, linked Corrections more consistently, added a custom 404 page, and improved the long-form edition chrome without rewriting the edition text.

An independent review found and fixed several items the first pass missed:

- internal Home and logo links still pointed to the noncanonical /index.html URL;
- the About and License wording blurred the source-faithful and reader's-edition credit lines;
- the correction introduction claimed an in-edition "colophon history" that is not present;
- Book JSON-LD guessed that Open Chronicles was an Organization publisher, so that uncertain property was removed;
- smooth scrolling made cold deep links on the long editions land many thousands of pixels past their targets;
- mobile fragment offsets were shorter than the wrapped sticky headers;
- overflow-x: hidden concealed overflow instead of addressing it;
- the W3C validator found invalid ARIA/heading markup in the brand archive and one mis-nested emphasis tag in the source-faithful glossary;
- .nojekyll caused repository documentation and operational notes to be served as site files.

All known local link, fragment, HTML validation, targeted accessibility, responsive layout, PDF consistency, and publication-text safeguards now pass. Peter Tudebode remains the only published project. Fidentius of Padua, Robert of Auxerre, and William of Tyre remain clearly labeled "In preparation."

## 2. Confirmed problems found

| ID | Problem | Resolution |
|---|---|---|
| A | About said the library "will open" after Tudebode was already published | Corrected |
| B | Method said editions "will be made" when the method was already in use | Corrected |
| C | License said "Nothing is published yet" | Corrected |
| D | Home described dual editions only in future launch terms | Corrected |
| E | Empty footer list items and missing Corrections links | Corrected |
| F | Thin page metadata and missing edition canonicals/descriptions | Corrected |
| G | Branding archive was indexed in the sitemap | Removed from sitemap; page marked noindex |
| H | No custom 404 page | Added |
| I | Missing edition skip links, focus treatment, and useful print rules | Corrected |
| J | Home/logo links created noncanonical /index.html navigation | Corrected to / |
| K | About and License credit copy conflated the two edition types | Corrected |
| L | Correction introduction referred to a nonexistent colophon history | Corrected without changing any errata entry |
| M | Smooth scrolling broke cold deep-fragment landing on long editions | Removed; native fragment navigation now passes |
| N | Sticky-header fragment clearance was too small on mobile | Corrected with responsive scroll padding |
| O | CSS hid horizontal overflow globally | Removed; actual narrow-width defects were addressed |
| P | W3C validation errors in branding and one nested emphasis sequence | Corrected without changing displayed publication text |
| Q | Repository docs were served by GitHub Pages | Excluded through minimal _config.yml |
| R | Live site was behind the reviewed working tree | Resolved by the authorized deployment |

## 3. Files changed

| File | Action |
|---|---|
| .nojekyll | Removed so GitHub Pages exclusions are honored |
| _config.yml | Added; excludes repository-only documentation from the Pages artifact |
| 404.html | Added |
| SITE_CLEANUP_REPORT.md | Added; excluded from the Pages artifact |
| index.html | Status wording, metadata, structured data, canonical Home links, Corrections link |
| about.html | Present-tense status, metadata, edition-specific credit wording, canonical Home links |
| library.html | Published status, metadata, Latin language markup, responsive table wrapper, canonical Home links |
| method.html | Present tense, clearer two-form wording, metadata, canonical Home links |
| license.html | Present tense, separate edition attribution forms, metadata, canonical Home links |
| corrections.html | Metadata, accurate version-process wording, safe external-link relation, canonical Home links |
| branding.html | Noindex, sitemap exclusion, valid semantic/ARIA markup, footer and Home links |
| books/tudebode/index.html | Metadata, conservative Book JSON-LD, published/version information, heading hierarchy, Corrections link, canonical Home links |
| books/tudebode/the-journey-to-jerusalem.html | Head/header/footer chrome, skip link, canonical metadata, version label, text-neutral tag-nesting repair |
| books/tudebode/the-road-to-jerusalem.html | Head/header/footer chrome, skip link, canonical metadata, version label |
| css/site.css | Focus, reduced motion, responsive table/fragment behavior, print rules |
| books/assets/edition.css | Edition focus, sticky header, fragment offsets, overflow handling, print rules |
| sitemap.xml | Removed nonindexable branding archive |
| README.md | Current stack and page inventory |
| HOW_TO_VIEW.txt | Current preview instructions |

Unchanged publication artifacts: both PDFs, image assets, CNAME, DNS.md, robots.txt, and the errata entries themselves.

## 4. Exact fixes made

### Content and status

- Tudebode is labeled Published.
- Fidentius, Robert of Auxerre, and William of Tyre remain non-clickable In preparation rows.
- About, Method, License, and Home now describe the active publication in the present tense.
- About now assigns the translation credit specifically to source-faithful translations.
- License supplies distinct source-faithful and reader's-edition attribution forms.
- Corrections now says the current version is shown in the colophon; no errata entry was edited.
- The Tudebode page exposes both current versions and links directly to Corrections.

### Navigation and URL convention

- Canonical convention: / for Home, .html for site pages, /books/tudebode/ for the work landing page, and .html for browser editions.
- Brand and Home links now resolve to /, not /index.html.
- Primary navigation order is identical on every full-chrome page.
- Corrections is available from all footers and the work/edition chrome.
- Both editions link to the canonical volume page, Library, Corrections, and Home.

### Metadata

- Every indexable HTML page has a unique title and description, HTTPS canonical, required Open Graph baseline, UTF-8 charset, viewport, and lang="en".
- Twitter summary metadata is present without an invented image.
- Homepage JSON-LD uses WebSite.
- Tudebode JSON-LD uses supported Book, workExample, version, editor, and license properties. The uncertain publisher-organization claim was removed.
- robots.txt allows normal crawling and names the sitemap.
- sitemap.xml contains exactly the nine indexable canonical HTML URLs.

### Accessibility and display

- Skip links are the first focusable control and visibly focus at the top of the viewport.
- :focus-visible is present without suppressing other native focus behavior.
- Axe-core reports no violations on all ten public/error pages at mobile and desktop widths.
- Native fragment navigation replaces smooth scrolling on the very long editions.
- Responsive scroll padding keeps direct and clicked targets below sticky headers.
- Tables scroll locally where necessary; the page body no longer hides overflow.
- Print CSS hides chrome and leaves edition pages within the print viewport.

### Publication-output separation

GitHub Pages now uses Jekyll only as an exclusion step. _config.yml prevents these repository-only files from entering the website artifact:

- DNS.md
- HOW_TO_VIEW.txt
- README.md
- SITE_CLEANUP_REPORT.md

The HTML and CSS remain static; there is no framework migration or content-generation step.

## 5. Content wording changed (before -> after)

### About

> "Published English will use the credit line:"

->

> "Published source-faithful translations use the credit line:"

> "The library will open when the first source-faithful translation and reader's edition are frozen for release."

->

> "The library currently begins with that volume."

### Method

> "How editions will be made and labeled when the library opens."

->

> "How editions are made and labeled."

> "Each completed work is planned as:"

->

> "Each work is prepared in two forms:"

> "Published volumes will use CC BY 4.0"

->

> "Published volumes use CC BY 4.0"

### License

> "Published volumes will use Creative Commons Attribution 4.0. Nothing is published yet."

->

> "Published volumes use Creative Commons Attribution 4.0."

One combined attribution template was replaced with separate source-faithful and reader's-edition templates matching the two published colophons.

### Home

> "When a book launches, it will appear in both forms--clearly labeled."

->

> "Each published work appears in both forms--clearly labeled."

### Corrections introduction

> "the change is recorded below and in the edition's colophon history"

->

> "the change is recorded below, and the edition's colophon is updated to show the current version"

The errata log beginning at "Errata log" remains byte-for-byte unchanged.

## 6. Link and file audit

- 243 local href/src/stylesheet references checked.
- All local targets resolve with exact case.
- All local fragment targets exist and are unique.
- No empty href, href="#", local filesystem URL, doubled URL slash, or missing asset was found.
- Table-of-contents targets were tested by both cold direct URL and real link activation.
- Creative Commons, GitHub Issues, and British Library endpoints returned HTTP 200 during review.
- Gallica returned HTTP 403 to command-line automation; the generic browser link was retained rather than replaced with an unverified scholarly URL.
- Both PDF filenames, HTML labels, versions, and landing-page links agree.

## 7. Metadata and sitemap work

Indexable canonical pages: 9.

1. /
2. /library.html
3. /method.html
4. /license.html
5. /about.html
6. /corrections.html
7. /books/tudebode/
8. /books/tudebode/the-journey-to-jerusalem.html
9. /books/tudebode/the-road-to-jerusalem.html

Excluded: branding.html, 404.html, PDFs, repository docs, and this report. No invented last-modified dates, ISBN, ratings, review data, or social image were added.

## 8. Accessibility work

| Check | Result |
|---|---|
| Skip link first and keyboard-operable | Pass on 10 pages |
| One h1 and one main landmark | Pass |
| Primary navigation accessible name/order | Pass |
| Current-page state where the current page is represented | Pass |
| Visible focus treatment | Pass |
| Axe-core default rules | 0 violations across 20 page/viewport runs |
| Sticky-header fragment clearance | Pass for 6 direct/click tests |
| Informative/decorative image alternatives | Pass |
| Mobile reflow and no page-level horizontal scroll | Pass |
| Print chrome/overflow | Pass on both editions |
| Reduced-motion treatment for site transitions | Present |

This is a practical automated and browser audit, not a formal WCAG conformance certification.

## 9. Responsive and visual work

Playwright/Chromium checked all ten representative pages at 390, 768, and 1440 CSS pixels, plus five high-pressure checks at 320 CSS pixels. Results:

- 35 page/viewport layout checks passed;
- no page-level horizontal overflow;
- no brand/navigation overlap;
- no failed images, console errors, page errors, or failed local requests;
- no clipped edition controls at 390 pixels;
- long-edition tables remain locally scrollable when needed;
- representative mobile screenshots were inspected before temporary audit files were removed.

## 10. Validation and test commands run

- git status --short --branch
- git diff --check
- custom Python/BeautifulSoup link, fragment, metadata, nav, sitemap, and publication-text audit
- W3C Nu HTML validator for all HTML files
- Playwright Chromium layout, keyboard, fragment, print, console, and request checks
- axe-core 4.10.3 injected locally for the audit
- pdfinfo, pdftotext, git hash-object, and SHA-256 checks
- curl checks for live routes, redirects, external links, and post-deployment behavior
- GitHub public deployment API checks

Temporary screenshots and axe.min.js were removed after testing.

## 11. Results

| Check | Result |
|---|---|
| Static HTML inventory | 11 files; 9 indexable |
| Local reference audit | 243 references, 0 failures |
| Duplicate IDs / missing fragments | 0 |
| Metadata/canonical/sitemap parity | Pass |
| Canonical source-faithful main text | Unchanged, 223,651 parsed text characters |
| Canonical reader's-edition main text | Unchanged, 177,541 parsed text characters |
| Errata records | Unchanged |
| PDF Git object hashes | Unchanged |
| PDF internal title/version/date/license | Consistent: 1.0.0 and 1.1.1, 2026-07-17, CC BY 4.0 |
| W3C Nu validation | 0 messages across 11 HTML files |
| Browser layout | 35 checks, 0 failures |
| axe-core | 20 checks, 0 violations |
| Keyboard skip links | 10 checks, 0 failures |
| Direct/clicked fragments | 6 checks, 0 failures |
| Print layout | 2 checks, 0 failures |
| Production routes after Pages deploy | Pass |
| Repository-only docs on production | 404 after deploy |

## 12. Remaining unresolved issues

1. The source-faithful colophon says the Hill & Hill post hoc comparison is "documented separately on openchronicles.org," but no such page exists in this repository.
2. British Library and Gallica links are generic institutional entry points rather than verified manuscript-specific records.
3. Google Fonts remain as a pre-existing third-party stylesheet dependency. They were not added or changed.
4. The reader's adaptation note says the full translation is preserved "with its Latin text." The published source-faithful HTML is English with notes and glossary, not a parallel Latin text. This remains for editorial review.
5. The repository publishes HTML and PDF only; no EPUB or DOCX is offered or labeled.
6. branding.html remains directly reachable but is noindex and absent from the sitemap.
7. Lighthouse was not run; W3C validation, axe-core, and targeted Chromium tests were run instead.

## 13. Intentionally not changed

- No wording in the source-faithful translation, its notes, or glossary.
- No wording in the reader's edition, its notes, adaptation note, chapters, or afterword.
- The only in-main edition change beyond Grok's lang attribute is a text-neutral nesting repair from strong/em mis-nesting to valid nesting.
- No PDF binary.
- No errata record.
- No medieval religious or military language.
- No unsupported "first English translation" or promotional claim.
- No future project status.
- No manuscript link was guessed merely to avoid an unresolved generic link.
- No analytics, advertising, tracker, cookie banner, new external font, or third-party JavaScript.

## 14. Deployment and live-site comparison

Before deployment, production still contained:

- About: "will open"
- Method: "will be made"
- License: "Nothing is published yet"
- Home: "When a book launches"
- GitHub's generic 404 response
- publicly served HOW_TO_VIEW.txt and DNS.md

The user then explicitly authorized publication after independent review. The reviewed commit was pushed to master, GitHub Pages completed successfully, and production was rechecked. The stale wording is gone, the custom 404 is active, key HTML/PDF/CSS/sitemap/robots routes return the expected status, and excluded repository documentation returns 404.

## Confirmations

- Canonical Tudebode source-faithful wording was not rewritten.
- Canonical Tudebode reader's-edition wording was not rewritten.
- No correction record was removed or rewritten.
- No project was falsely marked published.
- Deployment was performed only after the user's follow-up authorization and successful review.
- No unrelated file was discarded.
- Repository documentation remains in Git but is excluded from the website artifact.

## Completion note

Open Chronicles cleanup independently reviewed, corrected, validated, and published.

Stack: static HTML/CSS on GitHub Pages from master. Published work: Peter Tudebode Volume 1 (The Journey to Jerusalem 1.0.0 and The Road to Jerusalem 1.1.1). All other listed works remain In preparation.

Validation: 243 local references pass; W3C HTML validation reports zero messages; axe-core reports zero violations across 20 runs; 35 responsive browser checks, 10 keyboard checks, 6 fragment checks, and 2 print checks pass. Both PDF and canonical-edition safeguards pass. Production and the reviewed repository now agree.
