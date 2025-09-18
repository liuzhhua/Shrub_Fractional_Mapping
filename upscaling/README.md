# 🌵 Mapping of Shrub Fractional Abundance in Drylands

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

An end-to-end, scalable framework for mapping shrub cover fractional abundance (SFA) from local to regional scales. This repository combines very high-resolution crown segmentation with Sentinel-2 time-series analysis using state-of-the-art deep learning and machine learning models (DINOv2, CNN, XGBoost).

**Key Features:**
*   **🌿 Fine-Scale Detection:** Accurately segments individual shrub crowns from sub-meter imagery.
*   **🛰 Regional Upscaling:** Leverages Sentinel-2 phenology to predict SFA over large areas.
*   **📊 Explainable AI:** Uses SHAP to identify key seasonal drivers of shrub presence.
*   **⚡ Production-Ready:** Modular code designed for scalability on cloud platforms (GEE, AWS).

---

## 📋 Repository Overview

This project is structured into two sequential, modular steps. You can run each step independently with its own inputs, or chain them together for a complete analysis.

```mermaid
graph LR
    A[VHR Imagery] --> B[Step 1: Crown Segmentation];
    B -- Crown Masks --> C[Step 2: Regional Upscaling];
    D[Sentinel-2 Time Series] --> C;
    C -- Output --> E[Regional SFA Map];
Step	Module	Key Tech	Scale	Output
1	Crown Segmentation	DINOv2, CNN	Local	Binary crown masks
2	Regional Upscaling	XGBoost, SHAP	Regional	Fractional abundance map
🚀 Getting Started
Prerequisites
Python 3.9+ and pip
A GitHub Personal Access Token (for automated downloading of DINOv2 weights)
Geospatial data (See each module's README for specific sources)
Installation & Setup
Clone the Repository


git clone https://github.com/yourusername/shrub-sfa-mapping.git
cd shrub-sfa-mapping
Install Dependencies<br>
Each module has its own environment. Install dependencies for the step you want to run.

For Step 1:

cd crown_segmentation
pip install -r requirements.txt
For Step 2:

cd regional_upscaling
pip install -r requirements.txt
🧪 How to Run
Option 1: Run the Full Pipeline (Recommended)
Process your VHR imagery with Step 1 to generate training labels (crown masks).
Use these masks alongside Sentinel-2 data in Step 2 to train the upscaling model and generate a regional SFA map.
Option 2: Run Modules Independently
Only Step 1: If you only need fine-scale shrub detection.
Only Step 2: If you already have shrub training labels (e.g., from manual delineation or other projects).
Detailed instructions, example commands, and configuration options are provided in each module's README:

🌿 Crown Segmentation Module Documentation
🛰 Regional Upscaling Module Documentation
📊 Performance Highlights
Metric	Step 1: Crown Segmentation	Step 2: Regional Upscaling
R²	0.92 (validation sites)	0.68 (site-scale SFA estimation)
Strength	Detects small, sparse shrubs	Identifies key seasonal phenology predictors
🗃️ Data & Preprocessing
Step 1 Input: Very High-Resolution (VHR) imagery (~0.5 m) from Google Earth Pro, UAVs, or Planet Labs.
Step 2 Input: Sentinel-2 Level-2A (Bottom-of-Atmosphere) imagery and crown masks from Step 1.
Output: GeoTIFF raster files (.tif) for both binary crowns and continuous SFA maps.
For detailed data preparation steps, please refer to the documentation within each module.

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

Fork the Project
Create your Feature Branch (git checkout -b feature/AmazingFeature)
Commit your Changes (git commit -m 'Add some AmazingFeature')
Push to the Branch (git push origin feature/AmazingFeature)
Open a Pull Request
📜 Citation
If you use this software or methodology in your research, please cite the associated paper and this repository:


@article{yourpaper2025,
  title={AI-Driven Mapping of Shrub Fractional Abundance in Drylands},
  author={Your Name, Co-author...},
  journal={Remote Sensing of Environment},
  volume={XXX},
  pages={XXX--XXX},
  year={2025},
  publisher={Elsevier}
}

@software{shrub_sfa_mapping_2025,
  author = {Your Name},
  title = {shrub-sfa-mapping: An end-to-end framework for mapping shrub cover},
  year = {2025},
  publisher = {GitHub},
  journal = {GitHub repository},
  url = {https://github.com/yourusername/shrub-sfa-mapping}
}
📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
