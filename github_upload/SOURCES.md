# Sources and provenance

## Original data

SPKLv2 resources: https://github.com/Eighonet/parking-research

Associated paper: A. Martynova, M. Kuznetsov, V. Porvatov, V. Tishin, A. Kuznetsov, N. Semenova, and K. Kuznetsova. *Revising deep learning methods in parking lot occupancy detection*. arXiv:2306.04288, 2023. https://arxiv.org/abs/2306.04288

## Supplied files

- `SnowParking_Research_v2.ipynb` is copied from the supplied source notebook without changing its code. It has 38 cells and no saved outputs in this package. Some opening markdown retains the original planned-work wording and author placeholders. The current manuscript and evidence-status statements in this README qualify what has actually been supplied.
- `paper/Manuscript.docx` is derived from the authors' latest uploaded Word file with technical conversion defects repaired; authors' revised prose retained. `paper/Manuscript.pdf` is rendered from that document for this handoff.
- `results/reported_metrics_from_screenshots.csv` is transcribed from the supplied main-results screenshot `image(20261102-180508).png`. No raw predictions were available for independent recalculation during packaging.
- `figures/views.png`, `figures/synthetic.png` and `figures/errors.png` were extracted from the supplied notebook screenshots. They contain dataset-derived illustrations.
- `figures/operating.png` was extracted from the supplied operating-curve screenshot.
- `figures/learning.pdf` was redrawn from the learning-curve summary displayed in the supplied screenshot. Its bars are standard deviations across subsampling seeds, not confidence intervals.

## Scope of verification

Packaging checks can confirm valid notebook JSON, Python syntax and copied-file hashes. They do not establish that the original image experiments were rerun, that the recorded metrics were independently reproduced, that manuscript author declarations are complete, or that a heavy-snowfall + hidden-marking subset was reviewed by two people.

The README and upload packaging were prepared with AI assistance. The authors should verify their content together with all scientific and author-contribution statements before journal submission.
