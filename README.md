# Land Use / Land Cover Classification using CNN
## Landsat 8/9 Imagery — Greater Sydney Region, Australia

---

## Overview
This project implements a Convolutional Neural Network (CNN) to classify
Land Use and Land Cover (LULC) for the Greater Sydney region using
Landsat 8/9 satellite imagery. The model is trained on Landsat spectral
bands combined with NDVI, using the ESRI 10m LULC map as ground truth.
The Area of Interest (AOI) covers approximately 50 km² around Sydney, Australia.

---

## Project Pipeline

### 1. Landsat Data Acquisition
- Downloads the latest Landsat 8/9 scene directly via the USGS M2M API
- Filters for cloud cover under 20%
- Displays True Color Composite (RGB) of the AOI

### 2. ESRI LULC Map
- Downloads the ESRI Land Use Land Cover map at 10m spatial resolution
- Clips the map to match the exact extent of the downloaded Landsat scene
- Displays the LULC map with a full class legend

### 3. NDVI Computation
- Calculates Normalized Difference Vegetation Index from Landsat bands
- Formula: (NIR - Red) / (NIR + Red) using Bands 5 and 4
- Displays NDVI map with colour legend

### 4. CNN Model Training
- Combines all Landsat spectral bands + NDVI as input features
- Uses ESRI LULC classes as ground truth labels
- Applies data augmentation and balanced class sampling
- Performs hyperparameter tuning across multiple configurations
- Visualises train / validation / test pixel splits overlaid on the image

### 5. Accuracy Evaluation
- Confusion Matrix (raw counts + normalised)
- Per-class F1 Score and IoU (Intersection over Union)
- ROC Curves with AUC for each LULC class
- Full spatial LULC prediction map vs Landsat RGB

---

## Team
| Name |
|------|
| Sahil Kaler |
| Suryansh Rathore |
| Manhar |
| Diptanshu |
| Arya Talera |

---

## Setup & Installation

### Prerequisites
- Python 3.11
- USGS EarthExplorer account with M2M API access approved

### Install dependencies
```bash
pip install -r requirements.txt
```

### Run the notebook
Open `notebooks/maincode.ipynb` in VS Code or Jupyter and run cells top to bottom.

---

## Tech Stack
- Python 3.11
- TensorFlow / Keras — CNN model
- Rasterio — satellite image handling
- Scikit-learn — metrics and data splitting
- USGS M2M API — Landsat data download
- ESRI Living Atlas — LULC ground truth