# arcahi-models

Model files used by the **Arcahi desktop app** (the meeting-notes app in
`Arcahi/Arcahi_frontend`, `apps/product/desktop`). Nothing else is kept here: no code,
no recordings, no user data.

## How the files are kept

- **One release per model version**, named `<model>-<version>`, for example
  `speakrs-models-0.7.0`. A release is never changed after it is published; a new version is
  a new release.
- **Every file is pinned by SHA-256.** The app's source lists each file's URL and SHA-256
  hash, and the app (and its build) refuses a file whose hash does not match. A file
  changed here would be refused, not used.
- **Release asset names are flat.** GitHub release assets cannot hold folders, so a path
  inside a model bundle is written with `--` in place of `/`: for example
  `segmentation-3.0.mlmodelc/weights/weight.bin` is the asset
  `segmentation-3.0.mlmodelc--weights--weight.bin`. The app puts each file back at its path.
- **Files are copied unchanged** from their source, byte for byte. Where each comes from, who
  made it, its licence and what was changed upstream: [ATTRIBUTION.md](ATTRIBUTION.md).

## How the app uses them

- **Speaker diarization (`speakrs-models-0.7.0`)**, for speakrs 0.7.0, run on the person's
  computer after a recording:
  - the CPU set is bundled inside the signed app at build time (downloaded from the release
    by the build and checked against its pinned hash), so diarization works offline from
    the first launch;
  - on Apple Silicon, the app downloads the CoreML set in the background after the first
    launch, checks each file's hash, and uses it only once every file has passed.
- Beta builds download from this repository's releases. Production builds will use
  Arcahi's own domain, with the same files and the same hashes.

## Changes to this repository

The first commit was made directly to `main`, once, with Yashas's approval. Every change
since goes through a pull request. Nobody force-pushes.
