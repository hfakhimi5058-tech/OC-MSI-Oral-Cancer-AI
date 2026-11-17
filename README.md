# OC-MSI Oral Cancer AI

## Exploratory image-level comparison of EfficientNetB0 and DINOv2

This repository documents an exploratory binary image-classification study
using images from the Oral Cancer Multispectral Imaging (OC-MSI) dataset.
The images used in this work were processed as RGB images.

The comparison includes a historical EfficientNetB0 reference and frozen
DINOv2 features with a trained linear classification head.

**Research use only. This is not a clinically validated diagnostic system.**

## Repository status

This repository is being prepared for manuscript documentation.
Existing notebooks preserve historical development and may contain
superseded experiments, installation commands, file-writing operations,
training calls, and earlier results.

**Do not use “Run all” on the historical notebooks.**
Some historical code can delete and replace an existing dataset-split
directory. Read and review individual cells before any execution.

The notebooks are not yet a clean, independently validated end-to-end
reproduction pipeline. Aggregate result tables and reviewed source
documentation are being prepared for inclusion.

## Dataset and split

| Split | Images |
|---|---:|
| Training | 658 |
| Validation | 146 |
| Test | 146 |
| Total | 950 |

An exact-duplicate audit found no exact cross-split image duplicates in the
audited split. This does not establish patient-level or sample-level
independence and does not rule out other forms of dependence or leakage.

Patient/sample independence remains unverified.

## Models and analysis

### EfficientNetB0: historical reference

The EfficientNetB0 reference uses an existing fine-tuned checkpoint.
Cancer probability is computed as `1 - model output`, reflecting the
class encoding used during training.

EfficientNet test performance had been inspected during project
development. Its results must therefore be interpreted as a historical
reference, not as a fully untouched prospective benchmark.

### DINOv2: frozen-backbone linear probes

- Backbone: `facebook/dinov2-small`
- Model revision: `ed25f3a31f01632728cabb09d1542f84ab7b0056`
- Frozen backbone with a trained linear classification head
- Seeds: `42`, `123`, and `2026`
- Checkpoint selection: validation cancer ROC-AUC
- Cancer probability: `sigmoid(logit)`
- Locked test classification threshold: `0.5`

The supplementary seed plan was established after earlier EfficientNet
test inspection. It should not be described as a study-wide preregistered
comparison.

All three DINOv2 seeds are reported; test results are not used to select
a preferred seed.

## Primary full-test results

The primary test set contains **146 images**.

| Method | ROC-AUC | Average precision | Accuracy |
|---|---:|---:|---:|
| EfficientNetB0 historical reference | 0.9514 | 0.9489 | 0.8767 |
| DINOv2 linear probe — mean across three seeds | 0.9578 | 0.9668 | 0.8813 |

Values are rounded to four decimal places.
The DINOv2 row is the mean of the three seed-specific metrics, not an
ensemble result.

The models have different training histories; this is not a controlled
architecture-only comparison. Numerical differences do not establish
statistical superiority or clinical benefit.

Variation across seeds is descriptive. Seed standard deviations are not
confidence intervals and do not represent independent dataset replications.

## Supplementary sensitivity analysis

A candidate-excluded test analysis uses **141 images** and was calculated
from saved predictions without additional model training or inference.

This is supplementary to the primary 146-image test analysis.
It is not a replacement test set, a confirmed leakage correction, or
evidence of patient independence.

## Provenance and historical records

Original notebooks, checkpoints, split records, and result artifacts are
preserved separately for provenance.

Historical notebook headings, hard-coded result summaries, and earlier
model experiments should not be interpreted as the final study protocol.
Earlier experiments involving other model families are not part of the
primary EfficientNetB0–DINOv2 comparison reported above.

Publication preparation does not require rerunning training, inference,
or split-generation code.

## Data access and redistribution

Raw images are not included in this repository.

Dataset access is subject to the original provider's terms. Dataset
licensing and redistribution permissions must be reviewed before
redistributing any data or derived artifacts.

Per-image identifiers, prediction files, checkpoints, and the complete
private evidence archive are not approved for public release by this README.
Only reviewed artifacts should be added to the public repository.

Any future code license does not automatically apply to the dataset,
pretrained weights, or third-party materials.

## Limitations

- Exploratory image-level study on a limited dataset.
- Patient/sample independence is unverified.
- Absence of exact cross-split duplicates does not establish absence of leakage.
- EfficientNet test performance was inspected during development.
- Model training histories differ.
- No independent external or prospective clinical validation is established.
- Seed variability does not quantify all sources of uncertainty.
- No claim of statistical superiority or clinical diagnostic validity is made.

## Author

Haleh Fakhimi Rezaei
