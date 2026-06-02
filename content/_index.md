---
title: go-deltasync
type: docs
---

# go-deltasync

**Pure-Go, cgo-free building blocks for delta synchronization** — move and store
only the bytes that actually change between two versions of a file.

Each tool is a clean-room reimplementation that is **wire-compatible with its
reference implementation** (verified by cross-implementation tests in CI), ships
as a single static binary **and** an importable Go package, and is held to
**100% test coverage** by a CI gate.

## Tools

| Tool | What it is | Interops with |
|------|------------|---------------|
| [zsync2](docs/zsync2/) | download only changed bytes over plain HTTP | zsync |
| [rdiff](docs/rdiff/) | rsync signature / delta / patch | librsync |
| [zchunk](docs/zchunk/) | content-defined chunked container + HTTP-Range delta | zchunk (Fedora/DNF) |
| [vcdiff](docs/vcdiff/) | VCDIFF (RFC 3284) delta encode/decode | xdelta3 |
| [bita](docs/bita/) | differential file sync over HTTP (`.cba` archives) | oll3/bita |

Head to the [documentation](docs/) to get started, or browse the source at
[github.com/go-deltasync](https://github.com/go-deltasync).
