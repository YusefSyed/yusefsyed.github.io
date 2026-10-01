# Project agent map

## Purpose and scope

This repository prepares Yusef Syed's static research-notes site for GitHub
Pages. The current homepage is a placeholder. Do not add a biography, sample
posts, research claims, mentor names, or meeting material without a later
content request. There is no dependency installation or build step.

## Authority order

1. Files under `site/` plus a local HTTP preview.
2. `.github/workflows/pages.yml` for deployment behavior and artifact scope.
3. `README.md` for setup and content-review instructions.

Do not infer completed research or authorization to publish from plans.

## Repository map

| Area | First files | Boundary |
|---|---|---|
| Homepage | `site/index.html`, `site/assets/styles.css` | Placeholder text only; responsive semantic HTML |
| Crawling | `site/index.html`, `site/robots.txt` | Retain noindex and crawler exclusion until content is ready |
| Deployment | `.github/workflows/pages.yml` | Manual dispatch only; artifact contains only `site/` |
| Setup | `README.md` | Intended remote is `YusefSyed/yusefsyed.github.io` |

## Symptom to evidence map

| Symptom | First inspection | Focused check |
|---|---|---|
| Missing styles | Stylesheet link, `site/assets/styles.css` | HTTP response for `/assets/styles.css` |
| Unexpected published content | Workflow artifact path, `site/` inventory | Confirm only reviewed files are inside `site/` |
| Deployment fails | Workflow run, Pages source setting | Check selected branch and GitHub Actions Pages source |

## Working safely

- Inspect Git status and the diff first when this is a Git checkout; preserve unrelated changes.
- Keep all meeting evidence and private drafts outside this public repository.
- Preserve manual deployment and the `site/` artifact boundary.
- Crawler directives do not make a deployed page private.
- Do not introduce dependencies for this placeholder.

## Commands

```sh
python3 -m http.server 8000 --directory site
```

Check `/`, `/assets/styles.css`, and `/robots.txt` in the local preview. Inspect
the complete `site/` inventory before deployment and confirm linked assets exist.

## Definition of done

- The placeholder renders at narrow and wide viewport widths without overflow.
- The homepage and asset references resolve through the local HTTP server.
- Deployment is manual and uploads only `site/`.
- The execution receipt names changed files, verification, and unresolved risks.
