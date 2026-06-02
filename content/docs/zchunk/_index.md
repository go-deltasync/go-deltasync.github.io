---
title: "zchunk"
weight: 30
bookCollapseSection: true
---

# zchunk

A pure-Go, cross-platform toolkit for the [zchunk](https://github.com/zchunk/zchunk)
file format — a content-defined-chunked container with per-chunk checksums that
enables **HTTP-Range delta updates** (as used by Fedora/DNF). Interoperable with
the reference `zck` / `unzck` tools.

- [Quick start](quickstart.md)
- Repository: [github.com/go-deltasync/zchunk](https://github.com/go-deltasync/zchunk)

```bash
go install github.com/go-deltasync/zchunk/cmd/zchunk@latest
```
