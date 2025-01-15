# 🌎 Geolocation Guesser AI

## 🔄 Overview
This project develops a convolutional neural network (CNN)-based deep learning model to predict the subregion of the world where a given image was captured. The model, inspired by the game GeoGuessr, aims to identify unique patterns in images to provide interpretable predictions of geographic locations.

### 🔍 Features
- **Dataset**: 25,000 images sourced from [Google Street View](https://www.kaggle.com/datasets/paulchambaz/google-street-view) and [Geotagged Streetview Images](https://www.kaggle.com/datasets/rohanmyer/geotagged-streetview-images-15k), covering 126 unique countries.
- **Preprocessing**: Dataset includes geographic coordinates, converted to countries and subregions using [ISO-3166 Codes](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/tree/master/all).
- **Augmentation**: Techniques like flipping and rotation to address class imbalances.
- **Model**: Pre-trained ResNet variants (ResNet18, ResNet50, ResNet101) fine-tuned for the task.
- **Explainability**: Grad-CAM heatmaps highlight visual features driving predictions. Gemini 1.5 Flash to identify objects in the regions of interest.

## 📊 Results
- Best-performing model: **ResNet50**
  - Train Accuracy: 50.25%
  - Test Accuracy: 47.56%
  - Top-3 Prediction Accuracy: 73.01%
- Interpretability analysis revealed key visual features (e.g., vegetation, road signs, buildings).

## 📈 Dataset Details
1. **Images**: 640x640 pixels with geographic metadata.
2. **Subregions Analyzed**:
   - Southern Asia
   - Western Asia
   - Eastern Asia
   - South-eastern Asia
   - Australia and New Zealand
   - Southern Europe
   - Sub-Saharan Africa
   - Western Europe
   - Northern Europe
   - Eastern Europe
   - Northern America
   - Latin America and the Caribbean

## 🔢 Methodology
1. **Model Training**:
   - ResNet18, ResNet50, and ResNet101 trained on original and augmented datasets.
   - Experimented with frozen and unfrozen parameters.
2. **Explainability**:
   - Grad-CAM for heatmaps of influential regions.
   - Analysis of specific objects using Gemini 1.5 Flash for ROI detection.

## 🤓 Challenges
1. **Dataset Imbalance**: Limited representation of certain regions.
2. **Augmentation Impact**: Augmented data did not consistently improve performance.
3. **Object Detection**: Reliance on general model (Gemini 1.5 Flash) could introduce bias.

## ⚙️ Future Work
- Using larger datasets and models
- Integrate text recognition for regional clues (e.g., road signs, advertisements).
- Latitude and longitude predicting.

## 🔗 References
- [Kaggle Streeview Image Dataset](https://www.kaggle.com/datasets/ayuseless/streetview-image-dataset)
- [Deep Residual Learning for Image Recognition (2016)](https://arxiv.org/abs/1512.03385)
- [Grad-CAM: Visual Explanations from Deep Networks (2017)](https://arxiv.org/abs/1610.02391)
- [ISO-3166 Country Codes](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/tree/master/all)



