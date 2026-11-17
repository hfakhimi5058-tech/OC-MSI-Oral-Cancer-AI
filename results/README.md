Results documentation

Primary test summary

`primary_test_summary_rounded.csv` contains a manually transcribed,
four-decimal summary of previously reported aggregate results.

It is provided for repository readability. It is not a byte-preserved
export of the original evidence tables and must not be used to recover
unrounded values, confusion-matrix counts, or statistical uncertainty.

Columns

| Column | Meaning |
|---|---|
| `method` | Model and analysis description |
| `summary_type` | Single historical reference or mean across seed-specific metrics |
| `n_seeds` | Number of seeds represented in this row, not all historical experiments |
| `test_images` | Number of images in the primary test set |
| `roc_auc` | Cancer-positive receiver operating characteristic AUC |
| `average_precision` | Cancer-positive average precision, not necessarily trapezoidal PR-AUC |
| `accuracy` | Classification accuracy under the respective evaluation protocol |
| `decimal_places` | Reporting precision used in this summary |

 Interpretation

The primary test set contains 146 images.

The EfficientNetB0 row represents a historical reference checkpoint.
It does not summarize all EfficientNet experiments conducted during
project development. EfficientNet test performance had previously
been inspected.

The DINOv2 row is the arithmetic mean of seed-specific metrics for
seeds 42, 123, and 2026. It is not an ensemble prediction result.
The DINOv2 test classification threshold was fixed at 0.5.

Do not infer that the two methods used identical training histories,
checkpoint initialization, or threshold-selection procedures.
This is an exploratory image-level comparison, not a controlled
architecture-only experiment.

Averaged and rounded metrics should not be used to reconstruct an
integer confusion matrix.

Supplementary analysis

The candidate-excluded sensitivity analysis contains 141 test images.
It was computed from saved predictions and is separate from the
primary 146-image test analysis.

It is not included in `primary_test_summary_rounded.csv`.
It does not replace the primary analysis or establish a confirmed
leakage correction.

Uncertainty and limitations

- No statistical superiority is established by the numerical differences.
- Seed variation is descriptive, not an independent dataset replication.
- Seed standard deviation is not a confidence interval.
- Patient/sample independence remains unverified.
- No clinical validity or prospective diagnostic performance is established.

Evidence and release status

The original aggregate evidence tables are preserved separately.
Their public inclusion requires file-by-file review and provenance checks.

This manually transcribed summary does not replace those evidence files.
Manuscript values should be checked against the designated original
artifacts before submission.

Raw images, per-image predictions, image identifiers, manifests, and
checkpoints are not authorized for release by this document.
Do not upload the complete private evidence archive.

No training or inference was rerun to prepare this summary.
