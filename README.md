<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/bench-dark.png">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/bench-light.png">
  <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/banners/bench-light.png" width="100%" alt="theoros-bench">
</picture>

<p><a href="LICENSE"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/license-apache-2-0-dark.png"><img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/license-apache-2-0-light.png" height="31" alt="license: Apache-2.0"></picture></a> <picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/status-protocol-draft-dark.png"><img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/status-protocol-draft-light.png" height="31" alt="status: protocol draft"></picture> <a href="https://github.com/theoros-space"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/part-05-of-06-dark.png"><img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/github/badges/part-05-of-06-light.png" height="31" alt="part: 05 of 06"></picture></a></p>

> [!NOTE]
> **Status:** Protocol draft. Evaluation code lands here from December 2026. Comments on the protocol are welcome in issues.

## Overview

Accuracy alone does not tell you whether a model can fly. theoros-bench scores
onboard models on what a satellite operator actually pays for: accuracy
**and** size, latency and energy on real flight hardware. The benchmark is
open source so any team, including our competitors, can run it and publish
results under the same rules.

## What is measured

| Axis | Metric |
|---|---|
| Cloud, land and water | Mean IoU and per-class F1 on the CloudSEN12+ L1C test split |
| Vessels | F1 at 20 m matching distance |
| Active fire | F1 and IoU on held-out fire events |
| Calibration | Expected calibration error |
| Size | Flight parameters and int8 bytes |
| Speed | Latency per 256 x 256 tile, per target |
| Energy | Joules per tile, per target |

## Rules

1. Test on L1C (top-of-atmosphere) data, because that is what a satellite sees.
2. Report every axis. A result without size and latency is not a result here.
3. Name the hardware, toolchain version and numeric precision.
4. Test splits are never used for training or model selection.

## Submitting a result

Open a pull request that adds one file to [`results/`](results/) following
[`results/TEMPLATE.md`](results/TEMPLATE.md). Every result is reviewed before
it is listed. Dataset sources and licenses are in [`datasets/`](datasets/).

## Where it fits

| | Repository | Role |
|:-:|---|---|
| `01` | [theoros-models](https://github.com/theoros-space/theoros-models) | Multi-task model, training and the ground compiler |
| `02` | [theoros-edge](https://github.com/theoros-space/theoros-edge) | Onboard int8 runtime and flight targets |
| `03` | [theoros-delivery](https://github.com/theoros-space/theoros-delivery) | Signed model packages and over-the-air updates |
| `04` | [theoros-ground](https://github.com/theoros-space/theoros-ground) | Customer API, mission dashboard and result tracking |
| `05` | **theoros-bench** | Open benchmark for onboard Earth observation AI |
| `06` | [theoros-docs](https://github.com/theoros-space/theoros-docs) | Technical documentation and flight documents |

## Contributing

Read the [contributing guide](https://github.com/theoros-space/.github/blob/main/CONTRIBUTING.md).
Outside contributions need a signed [Contributor License Agreement](https://github.com/theoros-space/.github/blob/main/CLA.md).

## License

[Apache License 2.0](LICENSE). Dataset licenses differ; check each dataset card
before commercial use.

---

<p align="center">
  <a href="https://github.com/theoros-space"><picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-signal.svg">
    <img src="https://raw.githubusercontent.com/theoros-space/theoros-brand/main/logo/svg/mark-signal.svg" width="28" alt="Theoros">
  </picture></a>
  <br>
  <sub>Theoros &nbsp;·&nbsp; Onboard AI for Earth observation &nbsp;·&nbsp; Baku and Helsinki &nbsp;·&nbsp; <a href="https://theoros.space">theoros.space</a></sub>
</p>
