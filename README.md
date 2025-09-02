---

Integrating Google Earth imagery, Sentinel-2 time-series data, and machine learning to map shrub fractional abundance across arid and semi-arid ecosystems in China
==================================================================

Overview
--------
Shrub fractional abundance (SFA), the proportion of shrubs per unit area, is a key indicator for assessing environmental aridity and ecosystem health in drylands. Large-scale SFA mapping has been challenging because:

- Shrubs have small crown sizes and sparse distributions.
- They show spectral similarity with grasses and herbs.
- Coarser-resolution remote sensing and field surveys are limited for detection.

This project introduces a two-step deep learning and remote sensing framework that integrates:

- High-resolution Google Earth imagery (0.5m)
- Time-series Sentinel-2 observations (20m)
- Hybrid deep learning models (DINOv2 + CNNs)
- Machine learning regression (XGBoost) with Time-series Sentinel-2 data

The approach was developed and validated in Inner Mongolia, China, and is adaptable to other arid and semi-arid ecosystems worldwide.

Key Contributions
-----------------
1. High-accuracy shrub crown mapping from Google Earth imagery:
   - Manual segmentation to create benchmark datasets.
   - Hybrid DINOv2 + CNN deep learning architecture.
2. Scaling up using Sentinel-2 time-series data:
   - Generated Sentinel-2 time-series data.
   - Developed an XGBoost model to predict SFA.
3. Model explainability:
   - SHAP analysis identified key phenological periods.
4. Regional-scale ecological insights:
   - Found unimodal relationships between SFA and climate variables.

Repository Structure
--------------------
data/                 - Example data and preprocessing scripts  
src/                  - Source code for image processing, modeling, evaluation  
  ge_processing/      - Google Earth image segmentation scripts  
  sentinel_analysis/  - Sentinel-2 time series and phenology extraction  
  modeling/           - DINOv2 + CNN and XGBoost models  
  shap_analysis/      - Model explainability scripts  
results/              - Output maps and validation metrics  
notebooks/            - Jupyter notebooks for reproduction  
requirements.txt      - Python dependencies  
README.txt            - Project documentation  
LICENSE               - License information  

Methods Summary
---------------
Step 1 — High-Resolution Shrub Crown Mapping  
- Input: 0.5 m Google Earth imagery.  
- Process: Manual annotation + hybrid DINOv2 feature extractor + CNN classifier.  
- Output: Accurate binary shrub crown maps.  

Step 2 — Scaling to Sentinel-2 Time Series  
- Input: Sentinel-2 surface reflectance (20m, multi-temporal).  
- Extract: Phenological metrics from NDVI and spectral bands.  
- Train: XGBoost regression model using Step 1 maps as labels.  
- Apply: Model to map SFA regionally.  

Validation  
- 70 sites (1 km² each) cross-site validation.  
- Accuracy: R² = 0.92 (shrubs), R² = 0.68 (SFA).  

Interpretability  
- SHAP analysis highlighted the most important phenological stages for prediction.

Results
-------
- Mapped 1.31 million shrub crowns in Inner Mongolia.  
- Produced high-accuracy regional SFA maps.  
- Identified relationships between SFA and climatic variables.

Getting Started
---------------
1. Clone the repository  
   git clone https://github.com/liuzhhua/Shrub_Fractional_Mapping.git  
   cd <Shrub_Fractional_Mapping>

2. Install dependencies  
   pip install -r requirements.txt

3. Prepare data  
   - Download and preprocess high-res imagery.  
   - Acquire Sentinel-2 imagery from GEE or Copernicus Hub.

4. Run the pipeline  
   python src/ge_processing/train_shrub_segmentation.py  
   python src/sentinel_analysis/predict_shrub_segmentation.py  
   python src/modeling/train_xgboost.py  
   python src/modeling/predict_sfa.py  

Citation
--------
If you use this project, cite as:

@article{YourCitation2024,  
  title={Integrating Google Earth imagery, Sentinel-2 time-series data, and machine learning to map shrub fractional abundance across arid and semi-arid ecosystems in China},  
  author={Liu Zhonghua},  
  journal={Remote Sensing of Environment},  
  year={2025}  
}

License
-------
This project is licensed under the MIT License — see the LICENSE file.

Contributing
------------
We welcome contributions! Open an issue or pull request for bug reports, suggestions, or enhancements.

Keywords: shrub fractional abundance, arid ecosystems, remote sensing, Google Earth imagery, Sentinel-2, phenology, deep learning, DINOv2, XGBoost, SHAP, Inner Mongolia

---

If you want, I can also prepare a **`README_fig_workflow.png`** diagram you can include in your repo alongside this text. That way the workflow is visually clear for visitors on GitHub.

Do you want me to generate that **visual workflow diagram** for you as well? It would make this README far more engaging.
