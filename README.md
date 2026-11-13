<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-paper.svg">
  <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-ink.svg" width="44" align="right" alt="Theoros">
</picture>

# theoros-bench

**05  Open benchmark for onboard Earth observation AI.** Part of the [Theoros](https://github.com/theoros-space) onboard AI product.

[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-2FD39A)](LICENSE)

> **Status: protocol draft.** Evaluation code lands here from December 2026.

Accuracy alone does not tell you whether a model can fly. theoros-bench
scores onboard models on what a satellite operator actually pays for:
accuracy **and** size, latency and energy on real flight hardware.

## What is measured

| Axis | Metric |
|---|---|
| Cloud and land/water | mean IoU, per-class F1 on CloudSEN12+ L1C test split |
| Vessels | F1 at 20 m matching distance |
| Active fire | F1 and IoU on held-out fire events |
| Calibration | expected calibration error |
| Size | flight parameters and int8 bytes |
| Speed | latency per 256 x 256 tile, per target |
| Energy | joules per tile, per target |

## Rules

1. Test on L1C (top-of-atmosphere) data, because that is what a satellite sees.
2. Report every axis. A result without size and latency is not a result here.
3. Name the hardware, toolchain version and precision.
4. Test splits are never used for training or model selection.

## Submitting a result

Open a pull request that adds one file to `results/` following
`results/TEMPLATE.md`. Results are reviewed before they are listed.

## License

Apache License 2.0. Dataset licenses differ; check each dataset card before
commercial use.
