# Chest X-Ray Classification using SVM and CNN

## Introduction
Medical image analysis is an important application of machine learning in healthcare, particularly for assisting in disease diagnosis. Chest X-ray classification is widely used for detecting conditions such as pneumonia. In this project, two different approaches are used to classify chest X-ray images into **Normal** and **Pneumonia** categories: Support Vector Machines (SVM) and Convolutional Neural Networks (CNN).

The primary objective of this study is to compare the performance of traditional machine learning methods and deep learning models, and to analyze how model performance varies with different amounts of training data. The evaluation is performed using metrics such as accuracy, precision, recall (sensitivity), specificity, and F1-score.


---

## Dataset Description
The dataset consists of labeled chest X-ray images belonging to two classes: **Normal** and **Pneumonia**. The dataset was divided into training and testing sets, ensuring that the test set remained constant across all experiments to maintain consistency and avoid data leakage.

### Preprocessing Steps
- Resizing images to a fixed dimension  
- Normalization of pixel values  
- Conversion into appropriate formats for SVM and CNN  

For SVM, images were flattened into one-dimensional vectors, whereas for CNN, the spatial structure of the images was preserved.

---

## Methodology

### SVM (Linear and RBF Kernel)

Support Vector Machines are supervised learning models used for classification tasks. In this project, SVM is applied after reducing dimensionality using Principal Component Analysis (PCA), which helps in reducing computational complexity and removing redundant features.

#### Linear Kernel
The linear kernel attempts to find a straight-line decision boundary between classes. It works well when the data is linearly separable but may fail to capture complex relationships in image data.

#### RBF Kernel
The Radial Basis Function (RBF) kernel maps the data into a higher-dimensional space, allowing it to model non-linear relationships. This makes it more suitable for complex datasets such as medical images.

---

### Confusion Matrix (RBF)
[[ 97 137]
[ 5 385]]

- Accuracy: **77.24%**  
- Precision: **73.75%**  
- Recall (Sensitivity): **98.71%**  
- F1-score: **84.43%**  
- Training Accuracy: **99.31%**

The RBF kernel achieves very high recall, indicating that most pneumonia cases are correctly identified. However, the relatively lower precision suggests the presence of false positives.

---

### Confusion Matrix (Linear)
[[ 84 150]
[ 4 386]]

- Accuracy: **75.32%**  
- Precision: **72.01%**  
- Recall (Sensitivity): **98.97%**  
- F1-score: **83.37%**  
- Training Accuracy: **100%**

The linear kernel shows slightly lower performance compared to the RBF kernel. The perfect training accuracy indicates possible overfitting.

<img width="567" height="435" alt="image" src="https://github.com/user-attachments/assets/0f5d97c5-de3c-499f-a9f2-791bee63f5e0" />

---

## CNN Model

Convolutional Neural Networks are specifically designed for image data and are capable of learning hierarchical feature representations. Unlike SVM, CNNs preserve spatial relationships between pixels and automatically extract important features such as edges, textures, and patterns.

### Architecture Overview
- Convolutional layers for feature extraction  
- Pooling layers for dimensionality reduction  
- Fully connected layers for classification  

---

### Confusion Matrix (CNN)
[[250 28]
[ 43 598]]

- Accuracy: **92.27%**  
- Precision: **95.52%**  
- Recall (Sensitivity): **93.29%**  
- F1-score: **94.39%**  
- Training Accuracy: **97.28%**

The CNN model achieves significantly higher performance compared to SVM, with balanced precision and recall.
<img width="547" height="435" alt="image" src="https://github.com/user-attachments/assets/aab1c626-91bf-44e1-99f1-a582f2b1d65f" />

---

## Training with Different Data Sizes

### SVM Accuracy

| Data % | RBF | Linear |
|--------|-----|--------|
| 20% | 0.7628 | 0.7452 |
| 40% | 0.7596 | 0.7548 |
| 60% | 0.7596 | 0.7516 |
| 80% | 0.7564 | 0.7436 |

SVM performance remains relatively stable across different dataset sizes, showing limited improvement with more data.

---

### CNN Performance

| Data % | Accuracy | F1-score | Sensitivity | Specificity |
|--------|----------|----------|-------------|-------------|
| 20% | 0.3125 | 0.2667 | 0.25 | 0.375 |
| 40% | 0.5625 | 0.5882 | 0.625 | 0.5 |
| 60% | 0.5000 | 0.5556 | 0.625 | 0.375 |
| 80% | 0.6250 | 0.6667 | 0.75 | 0.5 |

CNN performance improves with increasing data, although some fluctuations are observed due to limited training epochs.

---

## Results
The results indicate that CNN significantly outperforms SVM in terms of accuracy, precision, recall, and F1-score. While SVM performs reasonably well, it is limited in capturing spatial features in images.

---

## Comparison: SVM vs CNN

- SVM achieves very high recall but lower precision, leading to more false positives  
- CNN provides a better balance between precision and recall  
- CNN achieves a higher F1-score, making it more reliable  
- SVM relies on manual feature extraction, while CNN learns features automatically  

---

## Key Observations

- CNN achieves the highest overall performance  
- RBF kernel performs better than linear kernel  
- SVM performance is stable but does not improve significantly with more data  
- CNN benefits significantly from increased training data  
- Linear SVM shows signs of overfitting  

---

## Conclusion

This study demonstrates that Convolutional Neural Networks are more effective than Support Vector Machines for medical image classification tasks. While SVM provides stable performance, it lacks the ability to capture complex spatial patterns.

CNN achieves higher accuracy and better balance across evaluation metrics. The results also highlight that deep learning models benefit more from larger datasets.

---
