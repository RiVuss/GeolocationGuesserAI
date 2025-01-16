# 🌎 Geolocation Guesser AI

## 🔄 Overview
This project develops a convolutional neural network (CNN)-based deep learning model to predict the subregion of the world where a given image was captured. The model, inspired by the game GeoGuessr, aims to identify unique patterns in images to provide interpretable predictions of geographic locations.

### 🔍 Features
- **Dataset**: 25,000 images sourced from [Google Street View](https://www.kaggle.com/datasets/paulchambaz/google-street-view) and [Geotagged Streetview Images](https://www.kaggle.com/datasets/rohanmyer/geotagged-streetview-images-15k), covering 126 unique countries.
- **Preprocessing**: Dataset includes geographic coordinates, converted to countries and subregions using [ISO-3166 Codes](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/tree/master/all).
- **Augmentation**: Techniques like flipping and rotation to address class imbalances.
- **Model**: Pre-trained ResNet variants (ResNet18, ResNet50, ResNet101) fine-tuned for the task.
- **Explainability**: Grad-CAM heatmaps highlight visual features driving predictions. Gemini 1.5 Flash to identify objects in the regions of interest.

### 📊 Results Summary
- Best-performing model: **ResNet50**
  - Test Accuracy: 47.56%
  - Top-3 Prediction Accuracy: 73.01%
- Interpretability analysis revealed key visual features (e.g., vegetation, road signs, buildings).



## 🔢 Methodology
1. **Data Augmentation**
The classes in the dataset are imbalanced. To adress this, we also tried running the models with augmented data, flipping, skewing and changing the brightness of the images.
  <p float="left">
  <img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/sample_augmented_images/11403.png" width="30%" />
  <img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/sample_augmented_images/augmented_0a4cf2e5_11403.png" width="30%" /> 
  </p>
  
2. **Model Training**
   - ResNet18, ResNet50, and ResNet101 models
   - For each model:
       - original dataset
       - original dataset + augmented data
       - original dataset + augmented data + no frozen parameters
  
3. **Explainability** 
   - First, [Grad-CAM](https://arxiv.org/abs/1610.02391) was used to create heatmaps of influential regions in the test set predictions.
   - Then a cut out portion of the region of interest was sent over to Gemini 1.5 Flash to return a list of objects identified in the dataset.
   - The Gemini output for the example below: ["Sky", "Powerline", "Tree", "Building", "Pole", "Vegetation"]
  
<p float="left">
  <img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/sample_images/345.png" width="30%" />
  <img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/sample_images/gradcam_345.jpeg" width="30%" /> 
  <img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/sample_images/roi_345_0.jpeg" width="18%" />
</p>

## 📊 Modelling Results
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/modelAccuracies.png" width=70%>
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/PredictionCorrectness.png" width=70%>
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/results_table.png" width=70%>

## 🔎 Explainable AI Results
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/objects_detected.png" width=70%>
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/top5bottom5.png" width=70%>


## 📈 Dataset Details
- **Images**: 640x640 pixels with geographic metadata.
- 20k training set 5k test set
- coordinated translated to sub-regions
<img src="https://github.com/RiVuss/GeolocationGuesserAI/blob/main/visualizations/data_distribution.png" width=50%>

## ⚙️ Future Work
- Using larger datasets and models
- Integrate text recognition for regional clues (e.g., road signs, advertisements).
- Latitude and longitude predicting.

## 🔗 References
- [Kaggle Streeview Image Dataset](https://www.kaggle.com/datasets/ayuseless/streetview-image-dataset)
- [Deep Residual Learning for Image Recognition (2016)](https://arxiv.org/abs/1512.03385)
- [Grad-CAM: Visual Explanations from Deep Networks (2017)](https://arxiv.org/abs/1610.02391)
- [ISO-3166 Country Codes](https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/tree/master/all)



