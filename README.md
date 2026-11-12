# Yusef Syed — personal site

Static GitHub Pages site for `YusefSyed/yusefsyed.github.io`, served at
https://yusefsyed.github.io/. One page of plain HTML and CSS: no build step,
no packages, no JavaScript, no analytics, no third-party requests.

## What is on the page

`site/index.html` has, in order: a hero (name, role, one line, a summary
paragraph, primary links, and a tally figure from one ToolEffectBench task),
then sections with stable anchors:

| Anchor | Section |
|---|---|
| `#quick-facts` | Role, focus, location, work authorization, availability, education, contact |
| `#about` | Short first-person description |
| `#work` | ToolEffectBench, Scopehaven, effect-tracer, Agent Eval Mutation Lab, Providence |
| `#open-source` | Merged pull requests by repository, with a total |
| `#papers` | The two Zenodo papers, linked by DOI |
| `#security-research` | Advisory and report counts (projects are not named) |
| `#skills` | Languages and tools, focus areas |
| `#faq` | Seven questions and answers |
| `#contact` | Email, GitHub, LinkedIn, X, résumé |

## Files under `site/`

| File | Purpose |
|---|---|
| `index.html` | The page, its metadata (title, description, canonical, Open Graph, Twitter card, `rel="me"`) and one JSON-LD `@graph` |
| `assets/styles.css` | All styling: light and dark via `prefers-color-scheme`, responsive from 360px, print styles |
| `favicon.svg` | Icon |
| `robots.txt` | Allows all crawlers, names the main AI crawlers, points to the sitemap |
| `sitemap.xml` | The home page and its `lastmod` date |
| `llms.txt` | Short Markdown summary with links, for language models |
| `llms-full.txt` | The full page text in Markdown |
| `humans.txt` | Author and build note |
| `404.html` | Not-found page that links home |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

The JSON-LD graph holds `WebSite`, `ProfilePage`, `Person`, `Organization`
(Scopehaven), two `ScholarlyArticle`, three `SoftwareSourceCode` and `FAQPage`.

## Editing content

The same facts appear in several places. When a fact changes, change every copy:

1. Visible text in `site/index.html`.
2. The JSON-LD block in the `<head>` of `site/index.html`. The `FAQPage`
   answers must match the visible FAQ text word for word.
3. `site/llms.txt` and `site/llms-full.txt`.
4. The dates: `dateModified` in the JSON-LD, the `<time>` in the footer,
   `lastmod` in `site/sitemap.xml`, and the date in `site/llms-full.txt` and
   `site/humans.txt`.

The open-source table has a total row; keep it equal to the sum of the rows and
to the count in the sentence above the table.

ORCID and Google Scholar: `site/index.html` has two HTML comments marked
`PLACEHOLDER (ORCID, Google Scholar)`. When the profiles exist, add their URLs
to the Contact list and to `sameAs` in the JSON-LD. Do not add made-up IDs.

Add only material approved for public release. Everything under `site/` is
published, and the repository root is public too.

## Preview locally

From this repository's root:

```sh
python3 -m http.server 8000 --directory site
```

Open `http://localhost:8000`. Stop the server with Ctrl-C. Check `/`,
`/assets/styles.css`, `/robots.txt`, `/sitemap.xml` and `/llms.txt`.

## Deploy

Pages uses **GitHub Actions** as its publishing source (**Settings → Pages →
Build and deployment → Source**). Deployment is manual: open **Actions → Deploy
GitHub Pages → Run workflow** and select the branch to publish. Pushes do not
trigger deployment. A successful run reports its URL in the `github-pages`
environment. The workflow uploads **only `site/`**.

After a deploy, the page can be checked with Google's Rich Results Test and the
Schema.org validator, and the sitemap can be submitted in Google Search Console
and Bing Webmaster Tools.
