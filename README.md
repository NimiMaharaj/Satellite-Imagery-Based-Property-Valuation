Satellite Imagery–Based Property Valuation
Overview

This project builds a multimodal property price prediction system by combining traditional tabular real-estate data with satellite imagery.
The motivation is to capture neighborhood and environmental context (green cover, road density, urban structure) that is not present in standard datasets but strongly influences property value.

The pipeline integrates:
Latitude/Longitude based satellite images
Convolutional Neural Network (CNN) feature extraction
Feature fusion with structured data
Regression-based valuation models

Problem Statement
Conventional property valuation models rely heavily on tabular features such as area, number of rooms, and location coordinates. These models fail to capture visual and spatial context, such as:

Quality of surrounding infrastructure
Greenery and open spaces
Proximity to roads and water bodies
Urban density patterns


This project addresses that gap by incorporating satellite imagery into the valuation process.
Data Sources
1. Tabular Data

Contains structured attributes such as:
Property ID
Latitude, Longitude
Area, number of rooms
Property age
Target variable: Property price

2. Satellite Imagery
High-resolution satellite images are downloaded using coordinates via the Google Static Maps API.
Zoom level: 18
Image size: 224×224
Map type: Satellite (no labels)
Each image represents the surrounding context of a property.


Project Pipeline

Step 1: Satellite Image Acquisition
Satellite images are fetched programmatically using latitude and longitude for each property and stored locally with a unique identifier.

Step 2: Image Preprocessin
Images are resized and normalized to be compatible with CNN models.

Step 3: Feature Extraction
A pretrained CNN (ResNet50) is used as a feature extractor.

Final output: 2048-dimensional feature vector per image
The CNN is used without the classification head

Step 4: Feature Fusion
Image embeddings are concatenated with tabular features to form a unified feature space.

Step 5: Model Training
Regression models are trained on:
Tabular features only
Image features only
Combined (multimodal) features

Performance is evaluated using RMSE, MAE, and R².
Multimodal XGBoost
RMSE: 0.1647
MAE : 0.1162
R2 : 0.9014

Key Results
Tabular + image features outperform tabular-only models
Satellite imagery improves spatial understanding
Visual context adds measurable predictive power