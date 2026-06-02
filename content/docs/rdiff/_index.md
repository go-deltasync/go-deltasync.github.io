---
title: "rdiff"
weight: 20
bookCollapseSection: true
---

# rdiff

A pure-Go, **librsync-interoperable** implementation of the classic rsync
**signature → delta → patch** workflow. Summarise a basis file as a signature,
compute a delta from that signature to a new file, then patch the basis to
reconstruct the new file — interoperable with `rdiff`/librsync.

- [Quick start](quickstart.md) · [CLI reference](cli.md) · [Wire compatibility](compat.md)
- Repository: [github.com/go-deltasync/rdiff](https://github.com/go-deltasync/rdiff)

```bash
go install github.com/go-deltasync/rdiff/cmd/rdiff@latest
```
