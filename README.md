# go-deltasync.github.io

Documentation site for the [go-deltasync](https://github.com/go-deltasync)
organization, served at <https://go-deltasync.github.io>.

Built with [Hugo](https://gohugo.io) (extended) and the
[hugo-book](https://github.com/alex-shpak/hugo-book) theme, deployed to GitHub
Pages by `.github/workflows/deploy.yml` on every push to `main`.

## Local preview

```bash
hugo server            # live-reload at http://localhost:1313
hugo --minify --gc     # build into ./public
```

Content lives under `content/docs/<tool>/`; the theme is pulled in as a Hugo
module (see `hugo.toml` / `go.mod`).
