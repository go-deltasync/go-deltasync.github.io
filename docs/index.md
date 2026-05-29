# go-deltasync

Cross-platform, pure-Go implementations of file-level delta synchronization
protocols. No cgo. Single binary. Same `.zsync` on the wire as Phipps' C
reference and AppImageCommunity's C++ rewrite, just portable to macOS and
Windows without porting effort.

## Projects

| Project | Status | Description |
| --- | --- | --- |
| [zsync2](zsync2/index.md) | Phase 1 / MVP | Pure-Go zsync client + `.zsync` maker |

More to come — rsync wire-format, casync chunker, etc. are likely
candidates if the demand justifies them.

## Why

The C/C++ implementations work, but they assume glibc-isms (`fopencookie`,
`st_mtim`, `off_t`). Porting them to macOS or Windows is a real effort. A
single-binary Go reimplementation that ships the same on-the-wire format
fills the gap without forking the upstream world.

## Compatibility goal

Every project in this org passes a cross-implementation compatibility test
in CI: artifacts produced by the canonical reference implementation must be
consumable by the Go version, and vice versa. We don't ship until that test
is green.
