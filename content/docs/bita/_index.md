---
title: "bita"
weight: 50
bookCollapseSection: true
---

# bita

A pure-Go, cgo-free reimplementation of [oll3/bita](https://github.com/oll3/bita):
differential file synchronization over HTTP. `bita` chunks a file with a
content-defined rolling-hash chunker, stores the unique chunks in a compressed
`.cba` archive, and reconstructs ("clones") the file elsewhere by reusing chunks
already available locally (the *seeds*) and fetching only the rest.

- [Quick start](quickstart.md)
- Repository: [github.com/go-deltasync/bita](https://github.com/go-deltasync/bita)

```bash
go install github.com/go-deltasync/bita/cmd/bita@latest
```

Wire-compatible with the Rust `bita` CLI (RollSum **and** BuzHash chunkers),
verified in both directions; compress/clone throughput is at parity with the
reference.
