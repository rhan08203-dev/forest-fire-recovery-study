# Forest Fire Recovery Study

**森林火灾后植被绿度与树冠覆盖的变化差异及数学预测**

*Post-Fire Differences Between Vegetation Greenness and Tree Canopy Cover*

This research examines the relative states of remotely estimated vegetation greenness (LG) and tree canopy cover (ZP_TCC) during post-fire years 1–8. It includes observations from 81 fires in the United States, quadratic prediction functions, first-year observation corrections, and retrospective validation.

## Report and supporting documents

- [Complete research report — PDF, Chinese](forest_v5_full_report.pdf)
- [Editable report — Word](forest_v5_full_report.docx)
- [Curves for all 81 fires](forest_v5_all_case_curves.pdf)
- [Model and index technical manual](model_and_index_manual.md)
- [Full code and reproducibility evidence — PDF](forest_v5_code_and_evidence.pdf)

## Full data and executable code

Download **forest_v5_reproducible_research.zip** from the repository's **Releases** section. This is the complete research archive, with the original internal directory structure preserved. Downloading only the repository's automatically generated source-code ZIP does not include the release attachment.

The research archive contains:

- `analysis/forest_recovery/data/satellite_pixel_years.csv`: 103,764 satellite location-year records.
- `analysis/forest_recovery/data/fixed_positions.geojson`: 9,564 fixed sampling locations.
- `analysis/forest_recovery/data/events.csv`: 81 events and their data-use groups.
- LG calibration references, field and airborne measurement references, and recent-fire observations.
- `analysis/forest_recovery/model.json`: fixed measurement and prediction parameters.
- All analysis CSV outputs, including `all_case_predictions.csv`, `test_predictions.csv`, and `model_metrics.csv`.
- Executable Python code and Google Earth Engine JavaScript source.
- README, data dictionary, requirements, and SHA-256 manifests.

The original archive's SHA-256 is recorded in [SHA256SUMS.txt](SHA256SUMS.txt):

```text
3b1ccb53f3ad7bf03d637f6f042adceb6b05f05ad85c8f14da8e5b2dcb026c62
```

## Reproduction

Extract the release attachment and keep its internal directory structure. From the extracted archive's root directory, use Python 3.12:

```bash
python -m pip install -r analysis/forest_recovery/requirements.txt
python analysis/forest_recovery/rebuild_measurements.py
python analysis/forest_recovery/check_green_calibration.py
python analysis/forest_recovery/analyze.py
python analysis/forest_recovery/make_figures.py
python analysis/forest_recovery/build_report.py
python analysis/forest_recovery/build_manual.py
python analysis/forest_recovery/verify.py
```

See the archive's README and data dictionary for the complete workflow, missing-value rules, satellite product versions, and measurement limitations. Saved-data reproduction does not require a GEE login; acquiring new satellite exports requires an authorized GEE account.

## Interpretation and limitations

LG estimates green vegetation cover; ZP_TCC is a satellite tree canopy cover proxy, not measured live-tree basal area or complete ecosystem recovery. Each indicator is normalized by its own pre-fire, impact-to-control reference. `DE = R_ZP_TCC − R_LG`.

The dataset comprises 36 fitting and cross-validation fires, 37 retrospective test fires, and eight supplementary fires. Predictions are limited to years 1–8; correction errors are evaluated only for years 2–8. The evaluation is retrospective and does not establish prospective accuracy for every individual fire. The report retains measurement limitations and results without demonstrated improvement.

## Contributions and AI assistance

The author defined the research questions, objectives, indicators and model forms; proposed the first-year correction and amplitude-cap approach; selected the adopted method; and reviewed the interpretation and conclusions.

ChatGPT assisted with collecting public data and literature, processing and checking data, and writing data-acquisition, analysis, plotting and reproduction programs. The author is responsible for reviewing the final report and conclusions.

## 中文说明

本仓库提供正式报告、全部火灾曲线、模型说明与代码证据。全部原始观测CSV、固定坐标、事件分组、模型参数和可执行程序，保存在 **Releases中的完整复现压缩包** 中；其内部目录和文件内容未因上传GitHub而改变。请下载该附件后按包内README复现。SHA-256用于核对文件完整性，不单独证明观测的生态真实性。
