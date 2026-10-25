# Portfolio code corrections and validation

Source: submitted code/assignment2 code.ipynb. Team authorship and the user's model optimisation/report contribution are recorded separately.

Portfolio corrections:
- Removed from PIL.Image import Image, which shadowed the PIL.Image module used by Image.open.
- Added Python/NumPy/PyTorch seeds and paths supporting root or notebooks/ kernel directories.
- Missing images now raise a clear error instead of silently substituting grey placeholders.
- The summary table now uses the observed Task 2 error-analysis holdout score, not a weighted average of constituent CV means. It explicitly labels that holdout as selection-dependent; it is not a clean independent test.

The original report and saved comparison plot are unchanged historical artefacts. They mix CV and validation results, and the report's random-forest fold description differs from the three-fold code. The source code is authoritative for its actual procedure. Original metrics were not retrained and should not be attributed to these modified cells without rerunning.

All Python cells pass syntax checks. Targeted helper checks verify missing-image handling and path configuration without downloading pretrained models. The full notebook, image feature extraction and model fitting were not rerun. Class labels and probability-column ordering should be checked if the dataset is replaced; this project assumes the original class mapping.

Executed helper checks: both EfficientNet image-extraction helpers raise RuntimeError on a missing image before invoking any pretrained backbone. Imports no longer shadow PIL.Image, and the misleading weighted-CV summary expression is absent. Full training was not run.
