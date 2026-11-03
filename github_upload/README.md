# Parking occupancy recognition in snow

Research material for **Adapting Parking-Occupancy Recognition to Snow-Covered Scenes with Hidden Road Markings: A Camera-Held-Out, Error-Constrained Evaluation**.

**Authors:** Togzhan Serik and Amina Kaliyeva, Astana IT University, Kazakhstan.

The project compares inexpensive adaptation strategies for parking occupancy classification using known slot polygons, a frozen ImageNet ResNet-18 encoder and a logistic regression head. Experiments use the public **SPKLv2** resources. **PKLot** and **CNRPark-EXT** are discussed as related datasets; they are not used for training in this experiment.

## Current evidence

- The supplied experiment screenshots report **1,203 frames**, **440 snow-tagged frames**, **19,342 crops** and **9,367 unique winter crops**.
- There are 12 ordered test/validation camera pairs. Each winter crop is tested three times, producing **28,101 fold–crop rows**, not independent additional images.
- `results/reported_metrics_from_screenshots.csv` is a transcription of the displayed main table. It is **not a recomputation from raw predictions**.
- The original result archive, raw predictions, executed notebook and full hardware/provenance records were **not supplied with this package**. They can be added after export from the completed Colab run.
- The included notebook is the source notebook and currently contains **no saved cell outputs**. It has not been rerun while preparing this repository package.
- Heavy falling snow and hidden markings are motivating conditions. A completed, independently reviewed **heavy-snowfall + hidden-marking subset is not available**. The quantitative findings concern snow-tagged scenes with known polygons.

With bounding-box crops, real-winter adaptation W1 has pooled AP(free) **0.605**, compared with **0.641** for the non-snow training baseline selected on winter validation B2. Test false-free rates at the validation-constrained operating point are **0.159** and **0.112**, respectively. The 5% constraint applies to validation and does not guarantee 5% error on a new camera. Polygon masking gives AP(free) **0.709** for W1 and **0.701** for B2; this ablation is exploratory because paired uncertainty for the masking differences has not been supplied.

## Files

| Path | Purpose |
| --- | --- |
| `SnowParking_Research_v2.ipynb` | Complete source notebook for data download, crops, features, training, evaluation and export |
| `paper/Manuscript.docx` | Authors' current editable manuscript supplied for this handoff |
| `paper/Manuscript.pdf` | PDF rendered from the current manuscript |
| `requirements.txt` | Direct notebook dependencies, without invented version pins |
| `results/reported_metrics_from_screenshots.csv` | Main-table values transcribed from the experiment screenshots |
| `results/README.md` | What is included, what is missing and how to add original result files |
| `data/README.md` | Dataset source and local-archive fallback |
| `figures/` | Existing manuscript figures; the learning plot was redrawn from the displayed summary |
| `SOURCES.md` | Dataset attribution and provenance of the files in this package |

## Run in Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Choose **File → Upload notebook**, then select `SnowParking_Research_v2.ipynb` from this repository's downloaded files.
3. Choose **Runtime → Change runtime type**, select a **T4 GPU** if available, and save. CPU execution is also supported but slower for feature extraction.
4. In section **4. Environment, configuration and seeds**, keep `SMOKE_TEST` false for research results. Smoke-test mode uses mock data and must not be reported as an experiment.
5. Run the notebook from the beginning. The initial setup installs any missing direct dependencies. The download stage needs internet access and the public SPKLv2 archive.
6. Section **16** is an optional manual annotation interface. It requires two real, independent reviewers to obtain a verified heavy-snowfall + hidden-marking subset. Running the other cells does not complete those labels automatically.
7. Section **19. Reproducibility: provenance and results archive** writes and downloads **`SnowParking_v2_results.zip`**.
8. Save that archive together with the **executed** notebook using **File → Download → Download .ipynb**. The source notebook in this repository is not a substitute for the executed copy.

Do not start another full run solely to upload an already completed experiment. If the completed Colab runtime is still available, rerun its export cell in section 19 and download its executed notebook first. A disconnected or reset runtime may no longer contain the earlier results.

### If the dataset download fails

Open the original dataset repository linked in `data/README.md` and download the authors' `SPKLv2.zip` archive. Upload it to the current Colab runtime as `/content/SPKLv2.zip`. In the notebook's section 4 configuration, change only the local archive setting:

```python
LOCAL_ZIP = '/content/SPKLv2.zip'
```

Then run the data-loading stage and continue in order. The path must point to the actual uploaded ZIP. A public archive URL that ignores HTTP Range is intentionally rejected by the downloader rather than silently downloading the entire file.

## Local execution

Use a Python environment compatible with PyTorch and torchvision. Install the dependencies and launch Jupyter:

```bash
python -m pip install -r requirements.txt
python -m pip install jupyterlab
jupyter lab SnowParking_Research_v2.ipynb
```

PyTorch and torchvision must be a compatible pair for the chosen CPU/CUDA environment. The notebook records installed package versions during execution; the original run's exact version record is not included here.

## Experiment definitions

- **B0:** always occupied.
- **B1:** non-snow training; source-frame grouped cross-validation selects regularisation; threshold 0.5.
- **B2:** non-snow training; a separate winter validation camera selects regularisation and thresholds. This is not probability calibration or a threshold-only control.
- **S1:** non-snow training plus synthetic-snow copies, with winter validation.
- **W1:** non-snow plus real-winter training, with winter validation.
- **W2:** approximately crop-count matched mixture of non-snow and winter frames; complete-frame sampling changes the data mixture and can slightly exceed the crop budget.

No frames from the test or winter validation view are used in training. Frame-cluster bootstrap intervals keep repeated predictions of the same physical frame together. Nearby frames may still be temporally correlated, and this small four-camera study does not establish transfer to new sites or Astana.

## Submission status

This repository contains a **research draft and supporting material**. Uploading it to GitHub is not journal submission, journal acceptance or instructor approval. The manuscript's author declarations, condition-annotation claims, result provenance and journal formatting should be checked before formal submission.

## Attribution and licensing

Dataset source: [Eighonet/parking-research](https://github.com/Eighonet/parking-research), associated with Martynova et al., *Revising deep learning methods in parking lot occupancy detection*, [arXiv:2306.04288](https://arxiv.org/abs/2306.04288).

The raw SPKLv2 dataset is not redistributed here. Dataset and third-party image rights remain with their respective owners. No software license has been selected for this project in this package; adding one requires the authors' choice and does not change third-party dataset terms.
