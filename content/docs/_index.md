---
title: Documentation
type: docs
bookFlatSection: false
weight: 1
---

# go-deltasync documentation

Pure-Go, cgo-free building blocks for **delta synchronization** — move and store
only the bytes that change between two versions of a file. Every tool is
wire-compatible with its reference implementation, ships as a single static
binary **and** an importable Go package, and is held to 100% test coverage.

Pick a tool to get started:

- [**zsync2**](zsync2/) — download only changed bytes over plain HTTP (zsync)
- [**rdiff**](rdiff/) — rsync signature / delta / patch (librsync)
- [**zchunk**](zchunk/) — content-defined chunked container + HTTP-Range delta
- [**vcdiff**](vcdiff/) — VCDIFF (RFC 3284) delta encode/decode (xdelta3)
- [**bita**](bita/) — differential file sync over HTTP, `.cba` archives (oll3/bita)
