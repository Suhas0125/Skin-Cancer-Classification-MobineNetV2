# 🩺 Skin Cancer Classification using MobileNetV2

> A deep learning project that classifies dermoscopic skin lesion images into **Benign** and **Malignant** categories using **Transfer Learning** with MobileNetV2.

---

## 📌 Project Overview

Skin cancer is one of the most common forms of cancer worldwide, and **early detection significantly improves treatment outcomes**. Manual diagnosis by dermatologists is accurate but time-consuming and requires expertise.

The goal of this project is to build a **computer-aided diagnosis system** capable of automatically classifying dermoscopic skin lesion images as **Benign** or **Malignant** using a Convolutional Neural Network (CNN).

Instead of training a CNN from scratch, this project uses **MobileNetV2**, a lightweight pretrained model, to leverage transfer learning for improved performance and faster convergence.

---

# 📂 Dataset

**Dataset Used**

- Fanconic Skin Cancer: Malignant vs Benign
- Total Images: **3297**
- Image Size: **224 × 224**
- Classes:
  - Benign
  - Malignant

The images are dermoscopic skin lesion photographs collected from the ISIC archive.

---

# 🚀 Project Pipeline

## 1️⃣ Import Libraries

### What was done

Imported all required libraries:

- TensorFlow / Keras
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- PIL
- OS

### Why?

These libraries provide tools for:

- Image processing
- Data manipulation
- Deep learning
- Visualization
- Model evaluation

---

## 2️⃣ Download Dataset

### What was done

Downloaded the dataset using Kaggle and organized image paths into a DataFrame.

### Why?

Machine learning models require structured input.

Creating a DataFrame makes it easier to:

- store image paths
- assign labels
- preprocess data
- split datasets

---

## 3️⃣ Exploratory Data Analysis (EDA)

### What was done

- Counted total images
- Verified image labels
- Examined class distribution
- Displayed sample images

### Why?

EDA helps understand:

- dataset quality
- possible class imbalance
- image characteristics
- potential preprocessing requirements

Understanding the data before training is an essential step in every machine learning project.

---

## 4️⃣ Binary Label Creation

### What was done

Converted textual labels into numerical values.

Example:

| Original | Encoded |
|----------|---------|
| Benign | 0 |
| Malignant | 1 |

### Why?

Deep learning models work with numerical values rather than text labels.

---

## 5️⃣ Image Preprocessing

### What was done

- Loaded every image
- Resized to **224 × 224**
- Converted images into NumPy arrays
- Applied MobileNetV2 preprocessing

### Why?

MobileNetV2 expects images in a specific format.

Preprocessing ensures:

- consistent image size
- normalized pixel values
- compatibility with pretrained ImageNet weights

---

## 6️⃣ Data Augmentation

### What was done

Applied random transformations:

- Horizontal Flip
- Rotation
- Zoom
- Translation
- Contrast Adjustment

### Why?

Data augmentation creates slightly modified versions of training images.

Benefits:

- reduces overfitting
- improves generalization
- helps the model become robust to variations in image orientation and lighting

---

## 7️⃣ Train / Validation / Test Split

### What was done

Split the dataset into:

- Training Set
- Validation Set
- Test Set

### Why?

Each dataset serves a different purpose.

**Training Set**

Used for learning model parameters.

**Validation Set**

Used during training to monitor performance and tune hyperparameters.

**Test Set**

Used only once after training to evaluate final model performance on unseen data.

This prevents information leakage and provides an unbiased estimate of model performance.

---

## 8️⃣ MobileNetV2 Transfer Learning

### What was done

Loaded MobileNetV2 pretrained on ImageNet.

Removed the original classification layer.

Added:

- Global Average Pooling
- Dropout
- Dense Layer
- Sigmoid Output Layer

### Why?

Training a CNN from scratch requires very large datasets.

Transfer learning allows the model to reuse previously learned visual features such as:

- edges
- textures
- shapes

making it much more effective for relatively smaller medical datasets.

---

## 9️⃣ Model Compilation

### What was done

Configured the model using:

- Adam Optimizer
- Binary Crossentropy Loss
- Accuracy
- Precision
- Recall
- ROC-AUC

### Why?

Binary Crossentropy is the standard loss function for binary classification.

Additional metrics provide better insight than accuracy alone, especially in medical applications.

---

## 🔟 Model Training

### What was done

Trained the model using:

- EarlyStopping
- ModelCheckpoint
- ReduceLROnPlateau

### Why?

These callbacks help:

**EarlyStopping**

Stops training when validation performance stops improving.

**ModelCheckpoint**

Saves the best-performing model.

**ReduceLROnPlateau**

Automatically reduces the learning rate when improvement slows.

Together they improve training stability and reduce overfitting.

---

## 1️⃣1️⃣ Model Evaluation

The trained model was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- Confusion Matrix
- ROC Curve
- Precision-Recall Curve

### Why multiple metrics?

Medical diagnosis should not rely on accuracy alone.

Different metrics evaluate different aspects of model performance.

**Accuracy**

Overall correctness.

**Precision**

Among predicted malignant lesions, how many were actually malignant.

**Recall**

Among actual malignant lesions, how many were correctly detected.

High recall is especially important because missing a malignant case can have serious consequences.

**F1 Score**

Balances Precision and Recall.

**ROC-AUC**

Measures how well the classifier separates benign and malignant images across all decision thresholds.

---

## 1️⃣2️⃣ Prediction

The trained model was tested on:

- Random test images
- Multiple test images
- New images uploaded by the user

### Why?

Testing on completely unseen images helps verify whether the model has learned meaningful visual patterns instead of memorizing the training data.

---

# 📊 Results

| Metric | Score |
|---------|-------|
| Accuracy | 83.94% |
| Precision | 84.89% |
| Recall | 78.67% |
| F1 Score | 0.8166 |
| ROC-AUC | 0.9056 |


---

# 📈 Visualizations

The project also includes:

- Training Accuracy Curve
- Training Loss Curve
- Precision Curve
- Recall Curve
- ROC Curve
- Precision–Recall Curve
- Confusion Matrix

These visualizations provide a deeper understanding of model learning and performance.

---

# 💡 Strengths

- Transfer Learning with MobileNetV2
- Data Augmentation
- Multiple Evaluation Metrics
- ROC Analysis
- Confusion Matrix
- Prediction on unseen images
- Clean end-to-end deep learning pipeline

---

# ⚠️ Limitations

- Binary classification only
- Performance depends on dataset quality
- Smaller than datasets used in clinical research
- Not intended for real-world medical diagnosis without extensive clinical validation

---

# 🔮 Future Improvements

- Fine-tune MobileNetV2
- Train on larger datasets such as HAM10000
- Compare with EfficientNetB0 and ResNet50
- Add Grad-CAM for explainability
- Deploy as a Streamlit web application
- Extend to multi-class skin lesion classification

---

# 🛠️ Technologies Used

- Python
- TensorFlow
- Keras
- MobileNetV2
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

---

# 📂 Repository Structure

```
Skin-Cancer-Classification/
│
├── notebooks/
│   └── Skin_Cancer_Classification.ipynb
│
├── model/
│   └── skin_cancer_mobilenetv2.keras
│
├── results/
│   ├── accuracy_curve.png
│   ├── loss_curve.png
│   ├── confusion_matrix.png
│   ├── roc_curve.png
│   └── precision_recall_curve.png
│
├── sample_images/
│
├── README.md
├── requirements.txt
└── LICENSE
```

---

# 📜 Conclusion

This project demonstrates how **transfer learning** can be effectively applied to medical image classification. MobileNetV2 successfully learned discriminative features from dermoscopic images and achieved strong performance on the test dataset. The project follows a complete machine learning workflow—from data preprocessing and augmentation to evaluation and prediction—making it a solid demonstration of practical deep learning skills.

Although the model shows promising results, it should be considered an educational and research prototype rather than a clinical diagnostic tool. Future improvements such as larger datasets, fine-tuning, explainability techniques, and deployment can further enhance its performance and real-world applicability.

---

## 👨‍💻 Author

**Suhas Gundla**

B.Tech Student, Indian Institute of Technology Hyderabad (IITH)

Interested in Machine Learning, Deep Learning, and Computer Vision.
