
# 🌿 Crown Segmentation Module

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX) *(Optional: add if you have a DOI)*

**High‑Resolution Shrub Crown Segmentation using DINOv2 & CNN**

This module detects and segments individual shrub crowns from very high‑resolution (VHR) imagery (~0.5 m). It leverages **DINOv2** for powerful self-supervised feature extraction and a **Convolutional Neural Network (CNN)** for precise semantic segmentation, providing the foundational data for large-scale SFA upscaling.

---

## 📍 Objective

To generate accurate, fine-scale binary masks of shrub crowns in arid and semi-arid regions. These masks serve as the critical training labels for the regional upscaling of Shrub Fractional Abundance (SFA) in **Step 2**.

---

## 🛠️ Workflow

The segmentation process follows a clear, multi-stage pipeline:

1.  **Preprocessing**: Prepare VHR imagery and corresponding annotation data.
2.  **Feature Extraction**: Utilize a pre-trained DINOv2 model to generate rich, contextual image features.
3.  **Model Training**: Train a CNN segmentation model (U-Net, DeepLab, etc.) using the extracted features.
4.  **Prediction & Output**: Generate binary crown segmentation maps for input scenes.
---

## ⚡ Quick Start

*1. Install Dependencies

*  Ensure you are in the crown_segmentation directory.

* ```bash
  pip install -r requirements.txt
  ```

*2. Train the Segmentation Model

      Configure paths in config.yaml (if applicable) and run:
      
```bash
     python src/train_segmentation.py
```

*3. Generate Predictions

      Run the prediction script on your target imagery:
      
```bash
  python src/predict_crowns.py
```
    
  **Inputs**
  
  VHR Imagery: GeoTIFFs from sources like Google Earth Pro exports, Google Earth Engine, or UAV/drone surveys.
  
  Annotation Data: Georeferenced shapefiles or raster masks for model training.
  
    
  **Outputs**
  Binary Crown Masks: GeoTIFF files (*.tif) with shrub pixels classified.
  
  Model Weights: Saved model checkpoints for future inference.
  
  Training Logs: Performance metrics and loss curves.
  

*  4. Performance & Validation
  **Metric**

  Score	Notes
  R² (Validation)	0.92	Tested on 70 field sites in Inner Mongolia.



---

## 📁 File Structure

```
.
crown_segmentation/
├── data/                    # Example data and annotations
│   ├── raw/                 # Raw input imagery
│   ├── processed/           # Processed training chips
│   └── predictions/         # Output prediction maps
├── src/                     # Source code
│   ├── train_segmentation.py # Model training script
│   ├── predict_crowns.py    # Inference script
│   ├── utils/               # Helper functions (preprocessing, metrics)
│   └── models/              # CNN model architectures
├── outputs/                 # Training logs, model weights, visuals
├── config.yaml              # Configuration parameters (optional)
└── README.md               # This file
```
---

## 📜 Citation
If you use this specific module in your work, please cite the main repository and any relevant publications:


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
📄 License
This module is licensed under the MIT License — see the main project LICENSE file for details.

