---
title: "Quick start"
weight: 1
---

# zchunk quick start

## Create a `.zck` archive

```bash
zchunk create -i disk.img disk.img.zck
# train + embed a zstd dictionary for better small-chunk ratios:
zchunk create --dict -i disk.img disk.img.zck
```

## Delta-download an update

`download` fetches only the chunks missing from a local copy, using HTTP Range
requests against a detached header:

```bash
zchunk download --header https://example.com/disk.img.zck.header \
  --local old.img.zck https://example.com/disk.img.zck -o new.img.zck
```

## Library

```go
import "github.com/go-deltasync/zchunk"

comp, _ := zchunk.CompressChunk(zchunk.CompressionZstd, nil, data)
// Builder writes .zck files; ReadLead/ReadPreface/ReadIndex parse them;
// PlanDelta + DownloadDelta over a RangeReader perform delta downloads.
```

See the [repository README](https://github.com/go-deltasync/zchunk) for the full
command and API surface.
