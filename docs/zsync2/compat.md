# Wire compatibility with upstream zsync

The whole point of `go-deltasync/zsync2` is that the `.zsync` it reads and
writes is **byte-for-byte identical** to what the upstream C/C++
implementations produce. This page is the receipt.

## What we test against

Two reference implementations exist in the wild:

| Implementation | Repo | Language | Status |
| --- | --- | --- | --- |
| `zsync` (Phipps) | <https://github.com/cph6/zsync> | C | the original, ships in Debian/Ubuntu as `zsync` |
| `zsync2` (AppImageCommunity) | <https://github.com/AppImageCommunity/zsync2> | C++17 | the rewrite, ships standalone |

The two share the on-the-wire format byte-for-byte, so it's enough to test
against one of them. We test against the Debian `zsync` package because:

- it's the most widely deployed
- it's the upstream that defines the format
- it installs in CI with `apt-get install -y zsync` — no five-minute
  AppImageCommunity build

If the compat test passes against `zsync`, it passes against `zsync2`.

## The compat test

`internal/zsync/compat_test.go` runs with the `compat` build tag:

```bash
go test -tags=compat ./internal/zsync
```

It does four round trips:

1. **`gozsyncmake` → `zsync`** — we produce a `.zsync`, the C client
   reconstructs the target using only the seed + HTTP server, output
   must be byte-identical
2. **`zsyncmake` → `gozsync`** — same in reverse: upstream produces the
   `.zsync`, we reconstruct
3. **Parse stability** — read a C-produced `.zsync` into our `ControlFile`,
   re-serialize it, diff against the original bytes
4. **Bit-flip detection** — flip one byte in the seed, verify both
   implementations notice the mismatch and re-fetch the affected block

All four pass at every commit; CI gates merges on this. If `zsync` /
`zsyncmake` are not on `$PATH` (local development on macOS, say) the suite
skips cleanly rather than failing.

## CI

The [`compat` workflow](https://github.com/go-deltasync/zsync2/blob/main/.github/workflows/compat.yml)
runs on every push and PR to `main`. It:

1. Installs `zsync` from Ubuntu's apt repo
2. Runs `go test -tags=compat -race ./...`
3. Fails the PR if any of the four round trips diverge by a byte

## What's *not* covered

- **Compressed targets** (`Z-Map2` block of the `.zsync` header): we don't
  produce or consume them in MVP. Reading a C-produced compressed `.zsync`
  returns a clear error rather than silently producing garbage.
- **Multi-URL failover**: the format permits multiple `URL:` headers; we
  read all of them but only try the first.
