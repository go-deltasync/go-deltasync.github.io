# go-deltasync.github.io

The website for the [go-deltasync](https://github.com/go-deltasync) organization,
served at <https://go-deltasync.github.io>.

Two static generators, one Pages site:

- **Landing page** (`/`) — built with [Hugo](https://gohugo.io); source in
  `content/` + `layouts/index.html`, tool cards driven by `[[params.tools]]` in
  `hugo.toml`.
- **Documentation** (`/docs/`) — built with [MkDocs](https://www.mkdocs.org)
  (readthedocs theme); source in `docs/` + `mkdocs.yml`.

`.github/workflows/deploy.yml` builds both on every push to `main` (Hugo into
`./public`, mkdocs into `./public/docs`) and deploys the combined site to GitHub
Pages.

## Local preview

```bash
# landing
hugo server                       # http://localhost:1313

# docs
python -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
mkdocs serve                      # http://localhost:8000
```
