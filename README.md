
# 🌵 Mapping of Shrub Fractional Abundance in Drylands

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/yourusername/shrub-sfa-mapping/graphs/commit-activity)

A modular machine learning & remote sensing framework for mapping shrub cover in arid and semi‑arid ecosystems.

---

## 📖 Overview

Shrub cover is a critical component of arid and semi‑arid ecosystems, significantly influencing **biodiversity**, **soil stability**, and **carbon storage**. However, accurately mapping **Shrub Fractional Abundance (SFA)** over large areas remains a major challenge.

This project presents a novel, two‑stage workflow to address this:
1.  **Fine‑scale shrub crown segmentation** from very high-resolution (VHR) imagery.
2.  **Regional upscaling of SFA** using Sentinel‑2 satellite time series and machine learning.

The repository is designed to be **modular**—each stage resides in its own subfolder with dedicated scripts and documentation, allowing you to run them independently or as an integrated pipeline.

---

## 🗂 Repository Structure

```
.
├── crown_segmentation/          # Step 1 — Detect shrub crowns from VHR imagery
│   ├── README.md                # Detailed instructions for segmentation
│   ├── src/                     # Model training & prediction scripts
│   └── data/                    # Example imagery & annotations
│
├── upscaling/                   # Step 2 — Upscale SFA using Sentinel‑2 & ML
│   ├── README.md                # Detailed instructions for upscaling
│   ├── src/                     # Feature extraction & XGBoost modeling
│   └── data/                    # Example remote sensing inputs
│
├── LICENSE
└── README.md                    # You are here
```

### Subfolder Summaries

*   **`crown_segmentation/`**: High‑Resolution Shrub Crown Segmentation using **DINOv2 & CNN**. Processes VHR imagery (~0.5 m) to generate binary shrub crown masks.
*   **`upscaling/`**: Regional Upscaling of Shrub Fractional Abundance. Leverages crown segmentation results and **Sentinel‑2 phenology variables** to predict continuous SFA at 20 m resolution using **XGBoost**.

---

## 🔄 Workflow

### Step 1 — Crown Segmentation
*   **Input**: VHR imagery (from Google Earth Pro, UAVs, or commercial providers)
*   **Process**: Feature extraction (DINOv2), CNN model training, semantic segmentation of shrub crowns.
*   **Output**: Binary raster maps of shrub crowns.

### Step 2 — Upscaling
*   **Input**: Sentinel‑2 imagery time series + crown segmentation maps from Step 1.
*   **Process**: Sentinel-2 data Processing, XGBoost regression modeling, and model interpretability with SHAP.
*   **Output**: Large‑scale, continuous maps of Shrub Fractional Abundance (SFA).

---

## 🚀 Quick Start

Get up and running with the pipeline in a few steps.

1.  **Clone the repository**
    ```bash
    git clone https://github.com/liuzhhua/Shrub_Fractional_Mapping.git
    cd Shrub_Fractional_Mapping
    ```

2.  **Install dependencies**
    *   **Option A (Modular)**: python environment for crown_segmentation.
    *   **Option B (Modular)**: python environment for upscaling
    ```bash
    cd crown_segmentation
    pip install -r requirements.txt
    ```
    # Run Upscaling
   
    cd upscaling
    pip install -r requirements.txt
    ```

4.  **Run the pipeline**
    *   **Option A (Modular)**: Run only Step 1 or Step 2. See the detailed `README.md` in each subfolder.
    *   **Option B (Full Pipeline)**:
    ```bash
    # Run Crown Segmentation
    cd crown_segmentation
    python src/train_segmentation.py
    python src/predict_crowns.py

    # Run Upscaling
    cd ../upscaling
    python src/download_Sentinel2_data.py
    python src/train_upscaling.py
    python src/predict_sfa.py
    ```

---

## 📊 Example Results

| Stage | R² Score | Resolution | Region Example |
| :--- | :--- | :--- | :--- |
| **Crown Segmentation** | 0.92 | 0.5 m | Site Scale |
| **Upscaling SFA** | 0.68 | 20 m | Inner Mongolia |

> **Note**: Visualizations, charts, and example output maps are available in each subfolder's `outputs/` directory.

---

## 🧩 Dependencies

Core dependencies include:
*   **Python 3.8+**
*   **PyTorch** ≥ 1.13
*   **Geospatial Libraries**: `rasterio`, `geopandas`, `earthengine-api`
*   **Machine Learning**: `xgboost`, `scikit-learn`, `shap`

A full list is available in `requirements.txt`.

---

## 📜 Citation

If this software or method contributes to your research, please cite it as:

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

This project is open source and available under the **[MIT License](LICENSE)**.

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.
Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to modify.
