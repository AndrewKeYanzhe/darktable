# iPhone 14 Pro Max ProRAW experiment

This fork starts from darktable 5.6.2 and uses the existing decoder changes from
[RawSpeed PR #963](https://github.com/darktable-org/rawspeed/pull/963).
The aim is to test lossless-JPEG Apple ProRAW from an iPhone 14 Pro Max.

## Pinned source

| Component | Commit |
| --- | --- |
| darktable 5.6.2 baseline | `20891f6c6fa7be995e5bf9dff9d1ee5062051773` |
| Original RawSpeed submodule | `c835b05aecfacb7343f7c424abd620aa12116c3f` |
| RawSpeed #963 snapshot | `5fb229779726aa45d76277f7b9c5c84f5d4183d4` |

The RawSpeed snapshot preserves da-phil's nine original commits without edits.
Its base matches the original submodule pin. The submodule URL points to
`AndrewKeYanzhe/rawspeed`, where the snapshot is retained on
`proraw-iphone14pm-pr963`. Normal submodule checkout uses the exact pinned commit;
do not use `git submodule update --remote` to reproduce this experiment.
RawSpeed #971 and JPEG XL DNG support are outside this first milestone.

## Get the same source on either computer

```sh
git clone --branch proraw-iphone14pm-pr963 --recurse-submodules https://github.com/AndrewKeYanzhe/darktable.git
cd darktable
```

For an existing clone after switching branches:

```sh
git submodule sync --recursive
git submodule update --init --recursive
```

## Build later

The same source can target Windows and macOS, with separate native builds.
Use the instructions bundled with this pinned release:

- Windows: [MSYS2 / UCRT64 / MinGW-w64](packaging/windows/README.md).
- macOS: [Homebrew](packaging/macosx/BUILD_hb.txt) or
  [MacPorts](packaging/macosx/BUILD.txt), with Xcode command-line tools.

The baseline documents Windows 10+, Apple Silicon macOS 14+, and Intel macOS 15+.
The predictor patch is shared C++ decoder code; successful compilation on either
platform and correct ProRAW rendering still require verification.

## Status and next milestone

- [x] Fork darktable and RawSpeed.
- [x] Retain the original #963 commits and pin darktable to their exact snapshot.
- [x] Preserve the release baseline for a draft PR inside this fork.
- [ ] Build on Windows and macOS.
- [ ] Test actual iPhone 14 Pro Max ProRAW files: full-resolution decoding,
  darkroom rendering, color/exposure, and export.
- [ ] Check conventional RAW files for regressions.

No compiler or runtime tests have been run. GitHub Actions are disabled in both
forks for this setup phase. Later image testing should use copies and a separate
darktable configuration/library, following the upstream README's test-version
instructions.

Setup and documentation were prepared with OpenAI Codex at the repository
owner's request. Decoder changes are the existing upstream PR author's work;
that PR discloses its own AI assistance. No contribution is being submitted to
the upstream maintainers by this setup.
