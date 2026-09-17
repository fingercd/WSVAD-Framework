# WSVADBench

VADBench is a pluggable research framework for weakly supervised video anomaly detection (WSVAD). It provides shared contracts for video identity, sampling, encoder features, cache policies, training, prediction, and evaluation.

## Scope

- Registers 25 encoder research candidates and 21 runtime catalog entries, with explicit planned, integrated, and blocked states. Registration does not mean every model has passed a real-weight validation.
- Covers fixed-clip encoders and long-video or streaming state paths, while keeping vision tokens, visual memory, and decoder KV cache distinct.
- Includes UCF-Crime weak-supervision baseline configurations and tools for data audits, feature extraction, MIL training, prediction, and frame-level evaluation.
- The complete UCF-Crime dataset is not included, and this repository does not claim a completed full-dataset benchmark. Videos, model weights, and run artifacts are not published here.

## Install and test

Python 3.10–3.12 is required:

```bash
uv sync --extra dev --extra train --extra video
uv run python -m pytest
```

Real encoders require their own environments and weights, prepared under the applicable upstream licenses and pinned revisions.

## License

First-party code in this repository is licensed under the MIT License. Upstream code, model weights, and datasets retain their own terms.
Cluster paths in the server helpers and environment registry are examples; replace them with your own paths before deployment.

The repository includes the official UCF-Crime split and temporal-annotation text files with pinned sources and SHA-256 entries; it does not include video files.
