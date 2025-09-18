
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
*   **Process**: Extraction of seasonal vegetation indices, XGBoost regression modeling, and model interpretability with SHAP.
*   **Output**: Large‑scale, continuous maps of Shrub Fractional Abundance (SFA).

---

## 🚀 Quick Start

Get up and running with the pipeline in a few steps.

1.  **Clone the repository**
    ```bash
    git clone https://github.com/yourusername/shrub-sfa-mapping.git
    cd shrub-sfa-mapping
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the pipeline**
    *   **Option A (Modular)**: Run only Step 1 or Step 2. See the detailed `README.md` in each subfolder.
    *   **Option B (Full Pipeline)**:
    ```bash
    # Run Crown Segmentation
    cd crown_segmentation
    python src/train_segmentation.py
    python src/predict_crowns.py

    # Run Upscaling
    cd ../upscaling
    python src/extract_features.py
    python src/train_upscaling.py
    python src/predict_sfa.py
    ```

---

## 📊 Example Results

| Stage | R² Score | Resolution | Region Example |
| :--- | :--- | :--- | :--- |
| **Crown Segmentation** | 0.92 | 0.5 m | Inner Mongolia |
| **Upscaling SFA** | 0.68 | 20 m | Site Scale |

> **Note**: Visualizations, charts, and example output maps are available in each subfolder's `outputs/` directory.

---

## 🧩 Dependencies

Core dependencies include:
*   **Python 3.9+**
*   **PyTorch** ≥ 1.13
*   **Geospatial Libraries**: `rasterio`, `geopandas`, `earthengine-api`
*   **Machine Learning**: `xgboost`, `scikit-learn`, `shap`

A full list is available in `requirements.txt`.

---

## 📜 Citation

If this software or method contributes to your research, please cite it as:

```bibtex
@misc{shrub_sfa_mapping_2025,
  author    = {Your Name and Co-authors},
  title     = {AI-Driven Mapping of Shrub Fractional Abundance in Drylands},
  year      = {2025},
  publisher = {GitHub},
  url       = {https://github.com/yourusername/shrub-sfa-mapping}
}
```

---

## 📄 License

This project is open source and available under the **[MIT License](LICENSE)**.

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.
1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

For major changes, please open an issue first to discuss what you would like to change.
```

### Key Improvements Made:

1.  **Visual Badges**: Added shields.io badges at the top for license, Python version, and maintenance status. This provides instant, at-a-glance information. You can customize these further.
2.  **Clear Structure**: Used headers and emojis to break the text into easily scannable sections.
3.  **Improved Formatting**:
    *   The repository structure is in a code block for clarity.
    *   The workflow is presented as a clear, two-step process.
    *   The results table is neatly formatted.
4.  **Action-Oriented Language**: The "Quick Start" section uses clear, copy-pastable commands.
5.  **Professional Tone**: The text is polished to be both informative and engaging for a scientific/technical audience.
6.  **Contributing Guidelines**: Added a standard template for contributing, which encourages community involvement.

Simply copy and paste this into your `README.md` file, and remember to replace `yourusername` with your actual GitHub username!
