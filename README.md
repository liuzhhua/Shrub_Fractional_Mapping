🌵 Shrub Fractional Abundance Mapping in Drylands
Shrub Fractional Abundance (SFA) — the proportion of shrubs per unit area — is a vital metric for monitoring aridity and ecosystem health in arid and semi-arid regions.

This project introduces a two-step deep learning & remote sensing framework combining very high-resolution imagery (VHR), Sentinel‑2 time series, and hybrid machine learning models to deliver accurate, scalable SFA maps.

🔍 Overview
Challenges

Small, sparse shrub crowns
Spectral overlap with grasses/herbs
Limited detection with coarse imagery or surveys
Our Solution

Shrub Crown Mapping → VHR from Google Earth + DINOv2 + CNN
Scaling to Sentinel‑2 → Time-series phenology + XGBoost
Explainability → SHAP to identify key seasonal predictors
🚀 Features
🎯 High-accuracy crown detection from VHR imagery
🛰 Regional-scale SFA mapping from Sentinel‑2
🧠 Interpretable machine learning with SHAP
🌍 Ecological insights on SFA–climate relationships
📂 Repository Structure

data/               # Example data & preprocessing
src/
  VHR_processing/    # Crown level segmentation
  sentinel_analysis/# Sentinel‑2 time series & phenology
  modeling/         # DINOv2+CNN & XGBoost models
  shap_analysis/    # Model explainability scripts
requirements.txt    # Dependencies
LICENSE             # License info
🛠 Method Workflow
Step 1 — High-Res Shrub Crown Mapping

Input: 0.5 m VHR imagery
Process: Manual annotation + DINOv2 features + CNN
Output: Binary shrub crown maps
Step 2 — Scaling via Sentinel‑2

Input: 20 m Sentinel‑2 reflectance (multi-temporal)
Features: Time-series spectral metrics
Model: XGBoost regression, trained on Step 1 results
Validation

70 sites (1 km² each)
Accuracy → Crown R² = 0.92, SFA R² = 0.68
📊 Key Results
1.31 million shrub crowns mapped (Inner Mongolia)
High-precision regional SFA maps
Clear unimodal SFA–climate relationships
⚡ Quick Start

# 1. Clone repository
git clone https://github.com/liuzhhua/Shrub_Fractional_Mapping.git
cd Shrub_Fractional_Mapping

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run pipeline
python src/ge_processing/train_shrub_segmentation.py
python src/modeling/train_xgboost.py
python src/modeling/predict_sfa.py
Data required: Download/preprocess high-res imagery + Sentinel‑2 from GEE or Copernicus Hub.

📜 Citation

@article{YourCitation2024,
  title={Integrating Google Earth imagery, Sentinel-2 time-series data, and machine learning to map shrub fractional abundance across arid and semi-arid ecosystems in China},
  author={Liu Zhonghua},
  journal={Remote Sensing of Environment},
  year={2025}
}
📄 License
MIT License — see LICENSE.

🤝 Contributing
PRs and issues welcome!

Keywords: shrub fractional abundance, drylands, remote sensing, Google Earth, Sentinel‑2, phenology, deep learning, DINOv2, XGBoost, SHAP, Inner Mongolia
