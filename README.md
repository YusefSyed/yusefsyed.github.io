# Yusef Syed — personal page

Minimal static GitHub Pages scaffold intended for `YusefSyed/yusefsyed.github.io`.
The homepage is a one-screen card: name, one line on what I work on, and links
to Scopehaven, effect-tracer, ToolEffectBench, GitHub, the résumé PDF and
LinkedIn. No posts or research results yet; those can be added later after review.

## Preview locally

From this repository's root:

```sh
python3 -m http.server 8000 --directory site
```

Open `http://localhost:8000`. Stop the server with Ctrl-C.
There are no packages to install and no build step.

## Prepare GitHub Pages

The repository is created at https://github.com/YusefSyed/yusefsyed.github.io.
Pages is configured to use **GitHub Actions** as its publishing source.
To check this, open **Settings → Pages → Build and deployment → Source**.
Deployment is manual: open **Actions → Deploy GitHub Pages → Run workflow**
and select the branch containing the reviewed scaffold. Pushes do not trigger
deployment. A successful deployment reports its URL in the `github-pages`
environment.

The workflow uploads **only `site/`**. Keep drafts, plans, meeting notes,
recordings, and other private material outside that directory and outside this
public repository. A public repository exposes its root documentation too,
even though those files are not in the Pages artifact.

## Before adding research content

- Review every file under `site/`; all of it will be published on deployment.
- Add only material approved for public release.
- When the site is ready to be indexed, remove the `robots` meta tag from
  `site/index.html` and replace `Disallow: /` in `site/robots.txt` with an
  appropriate crawl policy.
- Preview the final content and manually run the deployment workflow.

The placeholder requests no indexing. These crawler directives are not access
controls; any deployed page is publicly accessible.
