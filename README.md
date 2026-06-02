# go-deltasync.github.io

The organization's institutional landing page, served at
<https://go-deltasync.github.io> and built with [Hugo](https://gohugo.io).
It is a single page (custom `layouts/index.html`, tool cards driven by
`[[params.tools]]` in `hugo.toml`).

Documentation lives in a separate repository,
[go-deltasync/docs](https://github.com/go-deltasync/docs) — MkDocs Material
versioned with [mike](https://github.com/jimporter/mike), served at
<https://go-deltasync.github.io/docs/>. This page links there.

`.github/workflows/deploy.yml` builds the landing with Hugo and deploys it to
GitHub Pages on every push to `main`.

## Local preview

```bash
hugo server      # http://localhost:1313
```
