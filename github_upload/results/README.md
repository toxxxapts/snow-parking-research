# Results and evidence status

## Included now

`reported_metrics_from_screenshots.csv` contains the displayed main-table metrics from the supplied experiment screenshots. Values have been transcribed to three decimal places. This CSV is a readable report of those screenshots, **not** an independently recalculated result, saved model, raw prediction table or replacement for the original experiment export.

The main source screenshot is `image(20261102-180508).png`, supplied by the authors. Other supplied screenshots show illumination/camera breakdowns, the learning curve and crop-masking ablation. `../SOURCES.md` records provenance.

The CSV's `safe` policy is constrained to FFR ≤ 0.05 on validation only. Test false-free rates can exceed that target. AP is a ranking metric and is unchanged by selecting a different threshold within the same model.

## Add from the actual Colab run

First download `SnowParking_v2_results.zip` from section 19 of the completed notebook and save the executed `.ipynb` copy. The export contains the notebook's `results/` directory. The source writes files including:

- `crops_manifest.csv`
- `eda_view_condition.csv`
- `table_v1_replication.csv`
- `predictions_all_folds.csv.gz`
- `table_main_results.csv`
- `table_paired_deltas.csv`
- `table_per_camera.csv`
- `table_per_illumination.csv`
- `table_h3_illumination.csv`
- `table_learning_curve.csv`
- `table_ablation_mask.csv` when its ablation is enabled
- `table_errors_by_view_illum.csv`
- `table_errors_by_spot.csv`
- `cost.json`
- `provenance.json`
- `figures/`

`condition_review.csv` and `table_heavy_hidden_subset.csv` require actual human condition labels and sufficient verified examples. Do not create or report them as completed evidence merely because the annotation interface exists.

For normal GitHub web uploads, add the small table CSVs, `cost.json`, `provenance.json` and the executed notebook. Keep the complete results archive and large per-crop prediction file separately if they exceed the web upload limit; they are not included in this handoff. Consult the current GitHub limits before uploading any newly generated large file.

The current package contains no original results ZIP, prediction file, complete condition-review dataset or claim that H1–H4 succeeded.
