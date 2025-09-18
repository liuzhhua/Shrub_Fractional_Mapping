🌵 Mapping of Shrub Fractional Abundance in Drylands
A modular machine learning & remote sensing framework for arid and semi‑arid ecosystems

License: MIT
Python
Remote Sensing

📖 Overview
Shrub cover plays an important ecological role in arid and semi‑arid ecosystems, influencing biodiversity, soil stability, and carbon storage.
However, mapping Shrub Fractional Abundance (SFA) at large scales remains challenging.

This project develops a two‑stage workflow:

Fine‑scale shrub crown segmentation from high‑resolution imagery
Regional upscaling of SFA using Sentinel‑2 time series and machine learning
The repository is modular — each stage has its own subfolder, scripts, and documentation, so you can run them independently or as a complete pipeline.

🗂 Repository Structure

.
├── crown_segmentation/    # Step 1 — Detect shrub crowns from very high-resolution imagery
│   ├── README.md           # Detailed crown segmentation instructions
│   ├── src/                # Model training & prediction scripts
│   └── data/               # Example HRS imagery & annotations
│
├── upscaling/              # Step 2 — Upscale SFA using Sentinel‑2 & machine learning
│   ├── README.md           # Detailed upscaling instructions
│   ├── src/                # Feature extraction & XGBoost modeling
│   └── data/               # Example remote sensing inputs
│
├── LICENSE
└── README.md               # Main repo overview (this file)
Subfolder Summaries
crown_segmentation/
High‑Resolution Shrub Crown Segmentation using DINOv2 & CNN.
Takes very high‑resolution (VHR) imagery (~0.5 m) and produces binary shrub crown masks.

upscaling/
Regional Upscaling of Shrub Fractional Abundance with Sentinel‑2 Time Series.
Uses crown segmentation results from Step 1 plus Sentinel‑2 phenology variables to predict SFA at 20 m resolution.

🔄 Workflow
Step 1 — Crown Segmentation
Input: VHR imagery (Google Earth Pro / UAV / commercial providers)
Process: Feature extraction (DINOv2), training of CNN, segmentation of shrub crowns
Output: Binary shrub crown maps (raster)
Step 2 — Upscaling
Input: Sentinel‑2 imagery + crown segmentation (Step 1)
Process: Feature extraction (seasonal vegetation indices), XGBoost regression, SHAP interpretability
Output: Large‑scale continuous SFA maps
🚀 Quick Start
1️⃣ Clone the repository


git clone https://github.com/yourusername/shrub-sfa-mapping.git
cd shrub-sfa-mapping
2️⃣ Install dependencies


pip install -r requirements.txt
3️⃣ Run the pipeline

Option A: Run only Step 1 or Step 2 (see each subfolder's README)
Option B: Run the full pipeline:

cd crown_segmentation
python src/train_segmentation.py
python src/predict_crowns.py

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
