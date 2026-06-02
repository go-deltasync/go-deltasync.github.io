---
title: "Quick start"
weight: 1
---

# bita quick start

## Compress

```bash
bita compress -i disk.img disk.cba
# options: --hash-chunking rollsum|buzhash|fixed, --compression brotli|zstd|none, ...
```

## Clone (differential download)

Reconstruct a target from an archive, reusing a local seed and fetching only the
changed chunks — from a local path or an `http(s)://` URL:

```bash
bita clone --seed v1.img https://example.com/v2.cba v2.img --verify-output
# cloned 4194304 bytes (4142202 from seeds, 52102 from archive)
```

`bita info ARCHIVE` prints the chunker/compression metadata.

## Library

```go
import "github.com/go-deltasync/bita"

var arc bytes.Buffer
_ = bita.Compress(input, &arc, bita.CompressConfig{})
a, _ := bita.OpenArchiveReaderAt(bytes.NewReader(arc.Bytes()))
_, _ = bita.Clone(a, out, bita.CloneOptions{Seeds: []io.Reader{seed}})
```
