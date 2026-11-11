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

The original models, one entry each:

- **segmentation-3.0** by pyannote (https://huggingface.co/pyannote/segmentation-3.0),
  licensed under the MIT licence, "Copyright (c) 2023 CNRS". Full text:
  [LICENSE-MIT.txt](LICENSE-MIT.txt).
  - Changes: Converted to safetensors and CoreML formats by avencera
    (https://huggingface.co/avencera/speakrs-models, revision
    `67f963b6a1d94fcd4678948237b3cc8bd69bf1d8`). Not otherwise modified. Arcahi makes no
    changes.
- **wespeaker-voxceleb-resnet34-LM** by pyannote
  (https://huggingface.co/pyannote/wespeaker-voxceleb-resnet34-LM), licensed under CC BY 4.0
  (https://creativecommons.org/licenses/by/4.0/). Original model from the WeSpeaker project
  (Wang et al., ICASSP 2023).
  - Changes: Converted to safetensors and CoreML formats by avencera
    (https://huggingface.co/avencera/speakrs-models, revision
    `67f963b6a1d94fcd4678948237b3cc8bd69bf1d8`). Not otherwise modified. Arcahi makes no
    changes.
  - Provided as is, without warranties, as stated in the licence.
- **speaker-diarization-community-1** by pyannote
  (https://huggingface.co/pyannote/speaker-diarization-community-1), licensed under CC BY 4.0
  (https://creativecommons.org/licenses/by/4.0/). The PLDA and clustering files come from it.
  - Changes: Converted to safetensors and CoreML formats by avencera
    (https://huggingface.co/avencera/speakrs-models, revision
    `67f963b6a1d94fcd4678948237b3cc8bd69bf1d8`). Not otherwise modified. Arcahi makes no
    changes.
  - Provided as is, without warranties, as stated in the licence.

The full CC BY 4.0 text: [LICENSE-CC-BY-4.0.txt](LICENSE-CC-BY-4.0.txt).

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

## Citations

The entries from the speaker-diarization-community-1 model card:

1. Speaker segmentation model

```bibtex
@inproceedings{Plaquet23,
  author={Alexis Plaquet and Hervé Bredin},
  title={{Powerset multi-class cross entropy loss for neural speaker diarization}},
  year=2023,
  booktitle={Proc. INTERSPEECH 2023},
}
```

2. Speaker embedding model

```bibtex
@inproceedings{Wang2023,
  title={Wespeaker: A research and production oriented speaker embedding learning toolkit},
  author={Wang, Hongji and Liang, Chengdong and Wang, Shuai and Chen, Zhengyang and Zhang, Binbin and Xiang, Xu and Deng, Yanlei and Qian, Yanmin},
  booktitle={ICASSP 2023, IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)},
  pages={1--5},
  year={2023},
  organization={IEEE}
}
```

3. Speaker clustering

```bibtex
@article{Landini2022,
  author={Landini, Federico and Profant, J{\'a}n and Diez, Mireia and Burget, Luk{\'a}{\v{s}}},
  title={{Bayesian HMM clustering of x-vector sequences (VBx) in speaker diarization: theory, implementation and analysis on standard tasks}},
  year={2022},
  journal={Computer Speech \& Language},
}
```

Training and tuning made possible thanks to GENCI on the Jean Zay supercomputer.
