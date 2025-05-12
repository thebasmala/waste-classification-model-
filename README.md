# ♻️ Waste Classification Project

## Overview
This project implements a machine learning solution for classifying different types of waste materials from images. Using computer vision techniques and a Random Forest classifier, the system can identify six categories of waste:

- Plastic  
- Biological  
- Cardboard  
- Metal  
- Paper  
- White-glass  

🎯 The goal is to assist in automated waste sorting and improve recycling efficiency.

---
## Installation

1. Clone the repo

```shell
git clone https://github.com/Basmla/PyOCR pyocr
cd pyocr
```
2. Create a virtual environment.

```shell
python -m venv .venv
source ./.venv/bin/activate
```

3. Install the requirements

```shell
pip install -r requirements.txt
```

## 🖼️ Image Processing Pipeline

Our system transforms raw waste images through a specialized preprocessing pipeline to extract meaningful features.

### Input and Output Examples

| Category      | Input Description                                   | Output Description                                              |
|---------------|-----------------------------------------------------|-----------------------------------------------------------------|
| **Plastic**   | Blue plastic bag with handles                       | Edge-enhanced grayscale highlighting the bag’s structure        |
| **Biological**| Slice of bread with mold spots                      | Grayscale emphasizing the rounded shape and texture             |
| **Cardboard** | Brown cardboard with fold line and markings         | Edge detection revealing fold lines and texture                 |
| **Metal**     | Aluminum foil package with "DIAMOND" branding       | Enhanced edges showing text and shape                           |
| **Paper**     | Crumpled newspaper with print                       | Edge pattern showing folds and wrinkles                         |
| **White-glass**| Broken clear glass                                 | Edge-detected fragments showing sharp contours                  |

---

## 🧪 Preprocessing Steps
1. Grayscale conversion to reduce color complexity  
2. Histogram equalization for improved contrast  
3. Sobel edge detection to highlight structural features  

---

## 🧠 Feature Extraction

From each processed image, the system extracts:
- Statistical features (mean, standard deviation)
- Histogram distributions (10 bins)
- Edge density measurements
- Texture analysis features
- Regional grid features (4×4 grid)

---

## 📊 Performance Metrics

**Overall Accuracy:** 58.78%

| Category      | Precision | Recall | F1-Score | Support |
|---------------|-----------|--------|----------|---------|
| Plastic       | 0.54      | 0.41   | 0.47     | 198     |
| Biological    | 0.68      | 0.74   | 0.71     | 190     |
| Cardboard     | 0.57      | 0.69   | 0.62     | 173     |
| Metal         | 0.46      | 0.45   | 0.45     | 132     |
| Paper         | 0.65      | 0.71   | 0.67     | 211     |
| White-glass   | 0.56      | 0.47   | 0.51     | 149     |

> 📝 **Key Observations:**
> - Biological waste and paper are detected with high reliability  
> - Metal is the most difficult category  
> - Plastic has good precision but low recall  

---

## 🔍 Making Predictions

You can classify new waste images using the following Python function:

```python
def process_and_predict(img_path):
    img = cv2.imread(img_path)
    processed = preprocess_image(img, img_size=(128, 128))
    features = extract_features(processed)
    prediction = clf.predict([features])[0]
    return img, processed, categories[prediction]

# Example usage
img_path = "path/to/your/waste/image.jpg"
original, processed, predicted_category = process_and_predict(img_path)
print(f"Predicted waste category: {predicted_category}")
```

---

## 🚀 Future Improvements
- Explore deep learning approaches (CNNs) for better accuracy  
- Apply data augmentation for better generalization  
- Improve feature extraction techniques  
- Tune hyperparameters of the Random Forest model  
- Use ensemble methods  
- Add more waste categories for finer classification

- ## 🖼️ T - Images Appendix
 The image before and After using the image proccessing.
![d40d6e4c-971b-4cc6-8da9-39f34b638aee](https://github.com/user-attachments/assets/8f23bec3-0c5b-423b-b6e0-0e4f640f4351)
> 📌 Add your input/output images here:

