Shrub Fractional Abundance Mapping in Drylands
Shrub Fractional Abundance (SFA) — the proportion of shrubs per unit area — is a key indicator of aridity and ecosystem health in arid and semi-arid regions.
This project presents a two-step deep learning + remote sensing framework combining high-resolution Google Earth imagery, Sentinel-2 time series, and hybrid AI models to map SFA at regional scales.

📌 Overview
Challenges in Large-Scale SFA Mapping

Small shrub crowns, sparse distributions
Spectral similarity with grasses and herbs
Limitations of coarse imagery & field surveys
Our Approach

High-Res Shrub Crown Mapping → Google Earth (0.5 m) imagery + Hybrid DINOv2 + CNN
Scaling to Sentinel-2 (20 m, multi-temporal) → Phenology metrics + XGBoost regression
Explainability → SHAP to identify key phenological periods
🚀 Key Features
High-Accuracy Shrub Mapping — Manual segmentation + DINOv2 feature extraction
Regional SFA Prediction — Sentinel-2 time series + XGBoost
Model Transparency — SHAP-based interpretation
Ecological Insights — Relationships between SFA and climate variables
📂 Repository Structure

data/               # Example data & preprocessing
src/
  ge_processing/    # Google Earth segmentation
  sentinel_analysis/# Sentinel-2 time series & phenology
  modeling/         # DINOv2+CNN & XGBoost models
  shap_analysis/    # Explainability scripts
results/            # Maps & validation metrics
notebooks/          # Reproducible notebooks
requirements.txt    # Dependencies
LICENSE             # License info
🛠 Methods
Step 1 — Shrub Crown Mapping

Input: 0.5 m Google Earth imagery
Output: Binary shrub crown maps
Model: DINOv2 + CNN
Step 2 — Scaling Up with Sentinel-2

Input: 20 m Sentinel-2 surface reflectance (multi-temporal)
Features: NDVI + multi-band phenology metrics
Model: XGBoost regression with Step 1 labels
Validation

70 sites (1 km² each); R² = 0.92 (crowns), R² = 0.68 (SFA)
📊 Results
1.31 million shrub crowns mapped in Inner Mongolia
Accurate regional SFA maps
Unimodal SFA–climate relationships identified
🔧 Getting Started

# 1. Clone
git clone https://github.com/liuzhhua/Shrub_Fractional_Mapping.git
cd Shrub_Fractional_Mapping

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run pipeline
python src/ge_processing/train_shrub_segmentation.py
python src/modeling/train_xgboost.py
python src/modeling/predict_sfa.py
Data: Download and preprocess high-resolution imagery + Sentinel-2 from GEE or Copernicus Hub.

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
We welcome contributions! Please open an issue or pull request.
