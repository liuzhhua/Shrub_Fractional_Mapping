🌵 Mapping of Shrub Fractional Abundance in Drylands
License: MIT
Python
Remote Sensing

A modular machine learning & remote sensing framework for arid and semi-arid ecosystems

📖 Overview
Shrub cover plays a crucial role in arid and semi-arid ecosystems, influencing biodiversity, soil stability, and carbon storage.
However, mapping Shrub Fractional Abundance (SFA) at large scales remains challenging.

This project presents a two-stage workflow:

Fine-scale shrub crown segmentation from high-resolution imagery
Regional upscaling of SFA using Sentinel-2 time series and machine learning
The repository is modular: each stage is in its own subfolder with scripts and documentation.
Run them independently or as a complete pipeline!

🗂 Repository Structure

.
├── crown_segmentation/    # Step 1 — Detect shrub crowns from VHR imagery
│   ├── README.md
│   ├── src/
│   └── data/
│
├── upscaling/             # Step 2 — Upscale SFA with Sentinel-2 & ML
│   ├── README.md
│   ├── src/
│   └── data/
│
├── LICENSE
└── README.md              # Main repo overview (this file)
Subfolder Summaries
crown_segmentation/
High‑resolution shrub crown segmentation using DINOv2 & CNN.
Input: VHR imagery (~0.5 m). Output: Binary shrub crown masks.

upscaling/
Regional upscaling of SFA with Sentinel‑2 Time Series.
Uses outputs from crown segmentation and Sentinel-2 to predict SFA at 20 m resolution.

🔄 Workflow
Step 1 — Crown Segmentation

Input: VHR imagery (Google Earth Pro / UAV / commercial)
Process: Feature extraction (DINOv2), CNN training, crown segmentation
Output: Binary shrub crown maps (raster)
Step 2 — Upscaling

Input: Sentinel-2 imagery + crown segmentation results
Process: Feature extraction (vegetation indices), XGBoost regression, SHAP interpretation
Output: Large-scale continuous SFA maps
🚀 Quick Start
1️⃣ Clone the repository


git clone https://github.com/yourusername/shrub-sfa-mapping.git
cd shrub-sfa-mapping
2️⃣ Install dependencies


pip install -r requirements.txt
3️⃣ Run the pipeline

Option A: Run only Step 1 or Step 2 (see each subfolder's README)
Option B: Run the full pipeline:

# Step 1: Crown Segmentation
cd crown_segmentation
python src/train_segmentation.py
python src/predict_crowns.py

# Step 2: Upscaling
cd ../upscaling
python src/extract_features.py
python src/train_upscaling.py
python src/predict_sfa.py
📊 Example Results
Stage	R² Score	Resolution	Region Example
Crown Segmentation	0.92	0.5 m	Inner Mongolia
Upscaling SFA	0.68	20 m	Site Scale
Visualizations and example outputs are included in each subfolder's outputs/ directory.

🧩 Dependencies
Python 3.9+
PyTorch ≥ 1.13
Geospatial: rasterio, geopandas, earthengine-api
ML: xgboost, scikit-learn, shap
📜 Citation
If you use this workflow in your research, please cite:


@misc{shrub_sfa_mapping_2025,
  author    = {Your Name and Co-authors},
  title     = {AI-Driven Mapping of Shrub Fractional Abundance in Drylands},
  year      = {2025},
  publisher = {GitHub},
  url       = {https://github.com/yourusername/shrub-sfa-mapping}
}
📄 License
This project is licensed under the MIT License — see LICENSE for details.

🤝 Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to modify.

⭐️ If you find this project useful, please star the repo and share your feedback!
