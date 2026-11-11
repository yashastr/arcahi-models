# Attribution

Every model file in this repository's releases, where it comes from, who made it, its
licence, and what was changed. Arcahi changes nothing: each file is the byte-for-byte copy
of its source below, published under a flat asset name (see [README.md](README.md)).

## `speakrs-models-0.7.0`

**Taken from:** [avencera/speakrs-models](https://huggingface.co/avencera/speakrs-models)
on Hugging Face, at revision `67f963b6a1d94fcd4678948237b3cc8bd69bf1d8` (the revision
speakrs 0.7.0 pins, `MODEL_REVISION` in its `src/models.rs`), by **avencera (Praveen
Perera)**, the author of [speakrs](https://github.com/avencera/speakrs). That repository is
licensed **CC BY 4.0** (https://creativecommons.org/licenses/by/4.0/). Its provenance
statement: the artifacts are exported or converted for speakrs from the pyannote
community-1 pipeline and its segmentation and WeSpeaker components; the PLDA and VBx
parameters are extracted from the pipeline cache; the CoreML bundles are converted from the
exported model artifacts for Apple-platform execution.

**Changes made by avencera (upstream):** the weights were exported to safetensors (CPU
set), converted and compiled to CoreML `.mlmodelc` bundles (CoreML set), and the PLDA
parameters were extracted to NumPy files. **Changes made by Arcahi:** none; names only, as
in the README.

The original models:

| Original model | By | Licence |
|---|---|---|
| [pyannote/segmentation-3.0](https://huggingface.co/pyannote/segmentation-3.0) | pyannote | MIT |
| [pyannote/wespeaker-voxceleb-resnet34-LM](https://huggingface.co/pyannote/wespeaker-voxceleb-resnet34-LM), pyannote's packaging of the [WeSpeaker](https://github.com/wenet-e2e/wespeaker) VoxCeleb ResNet34-LM speaker embedding | pyannote, from WeSpeaker | CC BY 4.0 |
| [pyannote/speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1) (the pipeline, its PLDA parameters) | pyannote | CC BY 4.0 |

### Files

| File (path in the bundle) | Set | From |
|---|---|---|
| `segmentation-3.0.safetensors` | CPU | segmentation-3.0 (MIT), exported by avencera |
| `wespeaker-multimask-tail.safetensors` | CPU | wespeaker-voxceleb-resnet34-LM (CC BY 4.0), exported by avencera |
| `plda_lda.npy`, `plda_tr.npy`, `plda_mu.npy`, `plda_psi.npy`, `plda_mean1.npy`, `plda_mean2.npy` | CPU and CoreML | speaker-diarization-community-1 (CC BY 4.0), extracted by avencera |
| `wespeaker-voxceleb-resnet34.min_num_samples.txt` | CPU and CoreML | wespeaker-voxceleb-resnet34-LM (CC BY 4.0): the shortest input it takes |
| `segmentation-3.0.mlmodelc`, `segmentation-3.0-b32.mlmodelc`, `segmentation-3.0-b64.mlmodelc` | CoreML | segmentation-3.0 (MIT), converted by avencera |
| `wespeaker-fbank.mlmodelc`, `wespeaker-fbank-b32.mlmodelc`, `wespeaker-fbank-30s.mlmodelc` | CoreML | the filterbank front end of wespeaker-voxceleb-resnet34-LM (CC BY 4.0), converted by avencera |
| `wespeaker-multimask-tail-b32.mlmodelc` | CoreML | wespeaker-voxceleb-resnet34-LM (CC BY 4.0), converted by avencera |
| `wespeaker-voxceleb-resnet34-tail.mlmodelc`, `-tail-b3.mlmodelc`, `-tail-b32.mlmodelc` | CoreML | wespeaker-voxceleb-resnet34-LM (CC BY 4.0), converted by avencera |
| `wespeaker-chunk-emb-p1s-w21.mlmodelc`, `-w36`, `-w51`, `-w81`, `-w111` | CoreML | wespeaker-voxceleb-resnet34-LM (CC BY 4.0), converted by avencera |

Each `.mlmodelc` bundle is four files: `model.mil`, `coremldata.bin`,
`weights/weight.bin` and `analytics/coremldata.bin`. Each file's size and SHA-256 are in the
release's `SHA256SUMS` and pinned in the app.

### Notice for CC BY 4.0 files

These files are shared under the Creative Commons Attribution 4.0 International licence,
https://creativecommons.org/licenses/by/4.0/. Credit: pyannote (pyannote.audio, the
community-1 pipeline and its WeSpeaker embedding packaging), the WeSpeaker project, and
avencera (speakrs-models, the exports and conversions). No warranties are given.

### Notice for MIT files

`pyannote/segmentation-3.0` is licensed under the MIT licence, as its Hugging Face model
card states. Its model card is behind Hugging Face's access form, so its copyright line and
the full MIT text are not copied here yet; they will be added by pull request, and the app's
About screen carries them. The MIT licence: https://opensource.org/license/mit.
