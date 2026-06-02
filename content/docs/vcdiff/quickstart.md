---
title: "Quick start"
weight: 1
---

# vcdiff quick start

## CLI

```bash
vcdiff encode -s old.bin new.bin patch.vcdiff   # delta against a dictionary
vcdiff decode -s old.bin patch.vcdiff out.bin
cmp new.bin out.bin                             # identical

vcdiff encode new.bin patch.vcdiff              # no source: pure compression
vcdiff decode patch.vcdiff out.bin
```

A single dash (`-`) means stdin/stdout for the streamable argument.

## Library

```go
import "github.com/go-deltasync/vcdiff"

delta := vcdiff.EncodeBytes(source, target)
var out bytes.Buffer
_, _ = vcdiff.Decode(source, bytes.NewReader(delta), &out) // out == target
```

For batch workloads, reuse a `vcdiff.NewEncoder()` across calls to amortize
buffer allocation (~1.5× faster, far fewer allocations).
