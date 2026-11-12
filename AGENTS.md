# Project agent map

## Purpose and scope

This repository holds Yusef Syed's personal site for GitHub Pages
(https://yusefsyed.github.io/). On November 12 2026, on Yusef's request, the
one-screen card was replaced by a full single-page site: hero, quick facts,
about, work, open source, papers, security research, skills, FAQ and contact,
with search, answer-engine and recruiter-crawler metadata. The site is plain
static HTML and CSS. There is no dependency installation, no build step and no
JavaScript.

Do not add new facts, numbers, employers, dates, posts, research claims, mentor
names or meeting material without a content request from Yusef. Rewording
existing facts is fine; inventing or rounding them is not.

## Authority order

1. Files under `site/` plus a local HTTP preview.
2. `.github/workflows/pages.yml` for deployment behavior and artifact scope.
3. `README.md` for structure, editing and deployment instructions.

Do not infer completed research or authorization to publish from plans.

## Repository map

| Area | First files | Boundary |
|---|---|---|
| Homepage | `site/index.html`, `site/assets/styles.css` | One page, one `<h1>`, sections with stable ids (`quick-facts`, `about`, `work`, `open-source`, `papers`, `security-research`, `skills`, `faq`, `contact`); semantic HTML; light and dark; responsive from 360px |
| Metadata | `<head>` of `site/index.html` | Title, description, canonical, Open Graph, Twitter card, `rel="me"` links, one JSON-LD `@graph` (WebSite, ProfilePage, Person, Organization, ScholarlyArticle x2, SoftwareSourceCode x3, FAQPage) |
| Crawling | `site/robots.txt`, `site/sitemap.xml` | Everything indexable; AI crawlers named and allowed |
| Text for models | `site/llms.txt`, `site/llms-full.txt` | Same facts as the page, in Markdown |
| Other | `site/404.html`, `site/favicon.svg`, `site/humans.txt`, `site/.nojekyll` | Keep `.nojekyll` |
| Deployment | `.github/workflows/pages.yml` | Manual dispatch only; artifact contains only `site/` |
| Setup | `README.md` | Remote is `YusefSyed/yusefsyed.github.io` |

## Content rules

- The same facts live in the visible HTML, the JSON-LD, `llms.txt` and
  `llms-full.txt`. Change all copies together and keep the numbers identical.
- The visible FAQ text and the `FAQPage` JSON-LD answers must match word for word.
- Keep the sentence "I build with AI coding agents that I direct and review."
- Do not name the projects that received security advisories.
- Publish only what is already on the page. Nothing about private career
  activity (hiring processes, programs applied to, funding conversations).
- The two `PLACEHOLDER (ORCID, Google Scholar)` comments in `site/index.html`
  mark where those URLs go once the profiles exist. Never invent an ID.
- When content changes, update the dates: JSON-LD `dateModified`, the footer
  `<time>`, `sitemap.xml` `lastmod`, `llms-full.txt` and `humans.txt`.
- No analytics, trackers, cookie banners, forms, third-party embeds, web fonts
  from a CDN, frameworks or npm. Red (`--mark`) is reserved for the tally marks
  in the hero figure.

## Symptom to evidence map

| Symptom | First inspection | Focused check |
|---|---|---|
| Missing styles | Stylesheet link, `site/assets/styles.css` | HTTP response for `/assets/styles.css` |
| Rich results or validators reject the page | JSON-LD block in `site/index.html` | Extract the block and parse it with `python3 -c "import json,sys; json.load(sys.stdin)"` |
| Numbers disagree between files | `site/index.html`, `site/llms.txt`, `site/llms-full.txt` | `grep -n "19 merged\|5,628\|26 of 44\|19 of 20" site/*` |
| Tally marks miscount | `.ticks` in `site/assets/styles.css`, `--g` and `--r` on each `.ticks` span | Marks = `--g` x 10 + `--r` (97, 13, 10) |
| Horizontal scroll on a phone | `.ticks` width, `.ledger` table | Preview at 360px wide |
| Unexpected published content | Workflow artifact path, `site/` inventory | Confirm only reviewed files are inside `site/` |
| Deployment fails | Workflow run, Pages source setting | Check selected branch and GitHub Actions Pages source |

## Working safely

- Inspect Git status and the diff first; preserve unrelated changes.
- Keep all meeting evidence and private drafts outside this public repository.
- Preserve manual deployment and the `site/` artifact boundary.
- Crawler directives do not make a deployed page private.
- Do not commit, push or deploy unless Yusef or the lead asks.

## Commands

```sh
python3 -m http.server 8000 --directory site
```

Check `/`, `/assets/styles.css`, `/robots.txt`, `/sitemap.xml`, `/llms.txt` and
`/llms-full.txt` in the local preview. Inspect the complete `site/` inventory
before deployment and confirm linked assets exist.

## Definition of done

- The page renders at 360px and at desktop width, in light and dark, without
  horizontal overflow.
- The page and every asset reference resolve through the local HTTP server.
- The HTML has exactly one `<h1>`, unique ids, working `#anchors`, and JSON-LD
  that parses.
- Numbers match across `index.html`, the JSON-LD, `llms.txt` and `llms-full.txt`.
- Deployment is manual and uploads only `site/`.
- The execution receipt names changed files, verification, and unresolved risks.
