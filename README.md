Waste Classification Project



Overview
This project implements a machine learning solution for classifying different types of waste materials from images. Using computer vision techniques and a Random Forest classifier, the system can identify six categories of waste: plastic, biological, cardboard, metal, paper, and white-glass. The goal is to assist in automated waste sorting and improve recycling efficiency.

Image Processing Pipeline
Our system transforms raw waste images through a specialized preprocessing pipeline to extract meaningful features:

Input and Output Examples
For each waste category, we transform colorful input images (left) into processed edge- detected grayscale images (right):
•Plastic:
Input: Blue plastic bag with handles
Output: Edge-enhanced grayscale highlighting the bag’s contour and structure
•Biological:
Input: Slice of bread with some mold spots
Output: Processed grayscale emphasizing the rounded shape and texture
•Cardboard:
Input: Brown cardboard with fold line and markings
Output: High-contrast edge detection revealing the cardboard’s lines and texture
•Metal:
Input: Aluminum foil package with “DIAMOND” branding
Output: Enhanced edges showing text and package shape
•Paper:
Input: Crumpled newspaper with print
Output: Complex edge pattern revealing folding structure and wrinkles

•White-glass:
Input: Broken clear glass
Output: Edge-detected fragments highlighting the sharp contours

Preprocessing Steps
•Grayscale conversion to reduce color complexity
•Histogram equalization for improved contrast
•Sobel edge detection to highlight structural features

Feature Extraction
For each processed image, we extract:
•Statistical features (mean, standard deviation)
•Histogram distributions (10 bins)
•Edge density measurements
•Texture analysis features
•Regional grid features (4×4 grid)

Performance Metrics
The current model achieves the following performance:
•Overall Accuracy: 58.78%


Category	Precision	Recall	F1-Score	Support
Plastic	0.54	0.41	0.47	198
Biological	0.68	0.74	0.71	190
Cardboard	0.57	0.69	0.62	173
Metal	0.46	0.45	0.45	132
Paper	0.65	0.71	0.67	211
White-glass	0.56	0.47	0.51	149
Table 1: Classification performance metrics for each waste category

Key Observations
•Biological waste and paper are detected with the highest reliability
•Metal objects present the greatest classification challenge
•Plastic materials show good precision but lower recall

Making Predictions
To classify new waste images, use the following code:
Listing 1: Prediction Script

Future Improvements
•Explore deep learning approaches (CNNs) for potentially higher accuracy
•Implement data augmentation to improve model generalization
•Add more robust feature extraction techniques
•Optimize hyperparameters for the Random Forest classifier
•Explore ensemble methods to combine multiple models
•Include more waste categories for finer-grained classification


Figure 1: Display images before and After using image proccessing
