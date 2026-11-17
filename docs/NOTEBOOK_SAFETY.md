# Notebook safety and historical-source status

## Read before running any notebook

The notebooks in this repository are historical development records.
They are not approved as a sequential, end-to-end reproduction pipeline.

Do not select “Run all”.

Publication preparation does not require additional training, inference,
test evaluation, or dataset-split generation.

## Known hazards in the reviewed archival source

A separate private archival review copy was inspected during publication
preparation. Its saved outputs and execution counts were removed while
preserving code and Markdown sources.

The following observations apply to that reviewed copy. Cell numbers are
one-based positions across all cells and may not match other notebooks
or later revisions.

| Cell(s) | Observed behavior | Required handling |
|---|---|---|
| 10 | Can delete the existing split directory with `shutil.rmtree` and replace it by copying another directory; can also overwrite model copies | Do not execute during publication preparation |
| 2, 3 | Install dependencies; cell 2 also contains dataset-download code | Historical setup, not an approved installation procedure |
| 17, 18 | Install different major-version ranges of Transformers | Do not treat these cells as a single reproducible environment specification |
| 43 | Trains EfficientNetB0 and writes training artifacts | Preserve as historical source; do not rerun |
| 69, 72, 74 | Train DINOv2 linear heads and write checkpoints and prediction tables | Preserve as historical source; do not rerun |

This table is not an exhaustive inventory of side effects. Other cells
may load models, evaluate data, write results, or package artifacts.

Automated scans are heuristic. An absence of flagged credentials or
identifiers is not a security clearance.

## Interpretation of historical content

Historical notebook titles, comments, and result summaries may describe
earlier experiments rather than the final manuscript analysis.

In particular:

- “Leakage-safe” in an old comment is not evidence of patient independence.
- No exact cross-split duplicates were found in the audited split, but
  patient/sample independence remains unverified.
- Earlier test inspection must remain disclosed.
- Validation-based checkpoint selection does not erase earlier test access.
- Historical references to other model families are not evidence that
  those models are part of the final EfficientNetB0–DINOv2 comparison.
- Hard-coded summaries should be checked against the designated evidence
  artifacts before use in a manuscript.

Do not silently rewrite the original historical files to make them appear
prospectively planned. Document corrections and derived publication copies
separately.

## Public-release boundaries

Only explicitly reviewed files should be added to the public repository.

Do not upload the following without a separate release review:

- Raw images or dataset directories
- Patient/sample identifiers or unreviewed image filenames
- Per-image predictions, manifests, or image-hash tables
- Checkpoints or third-party weights with unreviewed redistribution rights
- Credentials, access tokens, or private configuration
- Unreviewed notebook outputs or embedded attachments
- The complete private evidence archive

Removing notebook outputs does not remove sensitive information that may
be embedded in source code or Markdown.

A branch in a public repository is also public.
A `.gitignore` file is not a privacy or access-control mechanism and does
not remove files already tracked in Git.

## Preservation and release procedure

1. Preserve original notebooks and evidence separately.
2. Create publication copies without modifying the originals.
3. Review source, Markdown, metadata, outputs, and attachments.
4. Record changes and provenance for derived copies.
5. Review the final Git diff and the exact files being published.
6. Merge or create a versioned release only after completing the review.

No clinical validity, patient independence, absence of all leakage, or
statistical superiority is established by this repository.
