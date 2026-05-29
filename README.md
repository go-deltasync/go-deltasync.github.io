# go-deltasync.github.io

Source for <https://go-deltasync.github.io>, the org-wide documentation site.

Built with [mkdocs](https://www.mkdocs.org/) using the `readthedocs` theme.
Deploys to GitHub Pages on every push to `main` via the
[`deploy-pages`](.github/workflows/deploy.yml) workflow.

## Local preview

```bash
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

Site comes up at <http://localhost:8000>.

## Adding a new project

1. Add a folder under `docs/<project-name>/` with an `index.md`.
2. Add the new pages to the `nav:` section of `mkdocs.yml`.
3. PR.
