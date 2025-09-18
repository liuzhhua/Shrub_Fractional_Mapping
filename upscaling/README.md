
# 🌍 Regional Upscaling of Shrub Fractional Abundance

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://zenodo.org/badge/DOI/xxxx.xxxx/zenodo.XXXXXXX.svg)](https://doi.org/xxxx.xxxx/zenodo.XXXXXXX)

**Regional Upscaling using Sentinel-2 Time Series & XGBoost**

This module builds on high-resolution shrub crown maps (Step 1) to train and scale prediction of Shrub Fractional Abundance (SFA) across large regions using Sentinel-2 time series data and machine learning.

---

## 🎯 Objective

Predict SFA at consistent 20 m resolution over large extents by leveraging XGBoost model and temporal and phenology information of vegetation.

---

## 🛠️ Workflow

The pipeline consists of:

1. **Data Preparation**  
   Align and resample Step 1 outputs to Sentinel-2 grid; normalize season dates.

2. **Data Download**  
   Compute and download Sentinel-2 time series in Google Earth Engine.

3. **Model Training**  
   Train XGBoost model with k-fold cross-validation and hyperparameter tuning.

4. **Prediction & Mapping**  
   Apply model to produce SFA raster outputs

5. **Model Interpretation**  
   Use SHAP values to quantify variable importance


---

## ⚡ Quick Start

**Install Dependencies:**

```bash
pip install -r requirements.txt
```

**Extract Features from Sentinel-2 Archive:**

```bash
Javascript run download_S2_data.jason
```

**Train the Upscaling Model:**

```bash
python src/train_upscaling.py
```

**Generate Predictions:**

```bash
python src/predict_sfa.py
```

---

## 🗂️ Inputs & Outputs

**Inputs:**
- Shrub Fractional Abundance labels: Derived from crown segmentation maps (Step 1), aggregated to 20 m resolution
- Sentinel-2 imagery: Level-2A surface reflectance, annual or multi-year, cloud-masked

**Outputs:**
- SFA Raster Map: GeoTIFF (*.tif) with continuous fractional abundance (0-1)
- Variable Importance Table: CSV with predictor importance
- SHAP Summary Plots: Visual interpretation of model decisions
- Model Metadata: JSON with config and performance metrics

---

## 📊 Performance & Validation

- **Model R² (Validation):** 0.68 at site scale
- Captures key phenological patterns across seasons
- Identifies optimal seasonal predictors via SHAP

<p align="center">
  <img src="https://via.placeholder.com/600x300/6AA84F/FFFFFF?text=SHAP+Feature+Importance" alt="SHAP analysis" width="60%">
  <br>
  <em>Example SHAP plot showing key seasonal predictors</em>
</p>

---

## 📁 File Structure

```
regional_upscaling/
├── data/                    # Training data and features
│   ├── shrub_labels/        # SFA labels from Step 1 (20m aggregated)
│   ├── sentinel2/           # Processed Sentinel-2 time series
├── src/                     # Source code
│   ├── download_S2_data.py  # Feature extraction from Sentinel-2
│   ├── train_upscaling.py   # Model training script
│   ├── predict_sfa.py       # Inference script
│   ├── utils/               # Helper functions (preprocessing, metrics)
│   └── models/              # XGBoost model configuration
├── outputs/                 # Prediction maps, model weights, results
├── config.yaml              # Configuration parameters (optional)
└── README.md                # This file
```

---

## 💡 Best Practices

- **Temporal Coverage:** Use at least 1 full growing season of Sentinel-2 data
- **Label Quality:** Ensure Step 1 training labels are accurate and enough
- **Model Interpretation:** Balance accuracy with ecological interpretability
- **Validation:** Incorporate field validation data if available

---

## 🔍 Example Applications

- **Dryland monitoring:** Track shrub encroachment in grazing lands
- **Carbon accounting:** Estimate above-ground biomass in shrub ecosystems
- **Habitat mapping:** Identify critical wildlife habitats
- **Climate change studies:** Monitor vegetation response to changing conditions

---

## 🛠️ Troubleshooting

- **Cloud contamination:** Use robust cloud masking algorithms
- **Temporal gaps:** Consider data fusion from multiple satellites
- **Computational limits:** Use chunked processing for large areas

---

## 📚 Citation

If you use this module in your research, please cite:

```bibtex
@misc{shrub_sfa_mapping_2025,
  author    = {Zhonghua Liu},
  title     = {Integrating very high‑resolution imagery, Sentinel-2 time-series data, and machine learning to map shrub fractional abundance across arid and semi-arid ecosystems in China},
  year      = {2025},
  journal   = {Remote Sensing of Environment},
  publisher = {GitHub},
  url       = {https://github.com/liuzhhua/Shrub_Fractional_Mapping}
}
```

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

*For questions or contributions, please open an issue or pull request on [GitHub](https://github.com/liuzhhua/Shrub_Fractional_Mapping).*
