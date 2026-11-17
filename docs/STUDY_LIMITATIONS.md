# Study limitations and interpretation

## Scope

This study is an exploratory image-level comparison of a historical
EfficientNetB0 reference and frozen DINOv2 features with trained linear
classification heads.

It is not a controlled architecture-only experiment or a clinically
validated diagnostic study.

## Dataset dependence and generalizability

The audited dataset contains 950 images: 658 training, 146 validation,
and 146 primary test images.

No exact cross-split image duplicates were found in the audited split.
This finding does not establish patient-level or sample-level
independence and does not exclude other forms of dependence or leakage.

Patient/sample independence remains unverified. Image-level results
must not be interpreted as patient-level diagnostic performance.

No independent external or prospective clinical validation is
established by this analysis.

## Historical test access and study planning

EfficientNetB0 test performance had been inspected during project
development. Its checkpoint is therefore treated as a historical
reference, not a fully untouched prospective benchmark.

The supplementary DINOv2 seed plan was established after earlier
EfficientNet test inspection. The comparison must not be described
as study-wide preregistered.

Validation-based checkpoint selection does not erase earlier test access.

## Differences between model protocols

The methods have different training histories and model initialization
procedures. Their results do not isolate the effect of architecture alone.

DINOv2 uses a frozen backbone with a trained linear classification head.
The reported seeds are 42, 123, and 2026, and the test classification
threshold was fixed at 0.5.

Do not infer that both methods used identical threshold-selection
procedures or equivalent development budgets.

## Seed variability and numerical comparisons

All three specified DINOv2 seeds are reported. Their aggregate row is
the arithmetic mean of seed-specific metrics, not an ensemble result.

The seeds share the same dataset split. They are not independent
dataset replications.

Seed variability is descriptive and does not quantify all sources of
uncertainty. Seed standard deviations are not confidence intervals.

Numerical differences between methods do not establish statistical
superiority or clinical benefit.

## Supplementary sensitivity analysis

The full 146-image test set remains the primary analysis.

The candidate-excluded sensitivity analysis contains 141 images and
was computed from saved predictions without additional training
or inference.

It is supplementary, does not replace the primary analysis, and
does not establish a confirmed leakage correction or patient
independence.

## Reporting precision and provenance

The public rounded summary is manually transcribed and reports
four decimal places. It does not replace the original evidence tables.

Rounded or averaged metrics must not be used to reconstruct integer
confusion matrices, unrounded values, or statistical uncertainty.

Manuscript values should be checked against the designated original
artifacts before submission.

## Intended use

This repository is for research documentation only.
It does not establish clinical validity, suitability for screening,
or prospective diagnostic performance.

This document does not authorize redistribution of raw images,
per-image identifiers or predictions, checkpoints, or the complete
private evidence archive.
