# zsync2

**Pure-Go implementation of the zsync delta-update protocol.**

[github.com/go-deltasync/zsync2](https://github.com/go-deltasync/zsync2)

zsync downloads only the *changed* blocks of a file from an HTTP server,
using a small control file (`.zsync`) that lists weak+strong checksums for
every block. The client compares those against an existing local "seed"
(an older version of the target) and fetches only the bytes it can't
recover locally — typically a small fraction of the whole target.

This repository ships two binaries:

- **`gozsync`** — the client. Reads a `.zsync`, scans a seed for matching
  blocks, fetches missing blocks via HTTP `Range:` requests, writes the
  reconstructed file.
- **`gozsyncmake`** — the server-side tool. Hashes a target file and emits
  the matching `.zsync` control file.

## Status

Phase 1 / MVP. Implements the protocol end-to-end with byte-exact
reconstruction. 100% statement coverage on `internal/zsync`. The compat
test suite verifies bidirectional interoperability with Phipps' C `zsync` —
artifacts our `gozsyncmake` produces can be consumed by the C `zsync` and
vice versa, byte-for-byte.

## What's intentionally not in MVP

- Compressed targets (`Z-Map2` / `Recompress` blocks of the .zsync header)
- Multi-URL failover (the `URL:` header may currently only contain one URL
  in practice; the format supports more)
- Resumable on-disk staging — the whole reconstructed file is held in
  memory before write

These are tracked in [GitHub Issues](https://github.com/go-deltasync/zsync2/issues).

## Next pages

- [Quick start](quickstart.md) — fetch a delta in three commands.
- [CLI reference](cli.md) — full flag listing for both binaries.
- [Wire compatibility](compat.md) — what we tested against and how.
