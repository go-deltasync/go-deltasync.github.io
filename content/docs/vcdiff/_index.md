---
title: "vcdiff"
weight: 40
bookCollapseSection: true
---

# vcdiff

A pure-Go, **xdelta3-interoperable** implementation of the VCDIFF
([RFC 3284](https://www.rfc-editor.org/rfc/rfc3284)) delta format. Encode a delta
from a source ("dictionary") to a target and decode it back, using the standard
wire layout so deltas interoperate with `xdelta3 -S` in both directions.

- [Quick start](quickstart.md)
- Repository: [github.com/go-deltasync/vcdiff](https://github.com/go-deltasync/vcdiff)

```bash
go install github.com/go-deltasync/vcdiff/cmd/vcdiff@latest
```

Encode throughput is at parity with the C reference, decode is a touch faster,
and the delta is slightly smaller — close on every axis for a pure-Go build.
