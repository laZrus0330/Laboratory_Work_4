# Laboratory Work 4 – Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

*Here is my Google Colab Folder:* [**Click Here!**](https://colab.research.google.com/drive/1GzYM7-RWkxZhMNuJko9EoGUqKMd6V5_X?usp=sharing)

## Overview

This laboratory activity focuses on evaluating and improving a Convolutional Neural Network (CNN) image classification model through advanced evaluation metrics, Explainable Artificial Intelligence (XAI), and optimization techniques.

The activity is divided into three major parts:

- **Activity 1:** Model Evaluation and Visualization
- **Activity 2:** Explainable AI using Grad-CAM
- **Activity 3:** Model Enhancement and Performance Optimization

The objective of this laboratory is to analyze model weaknesses, apply improvement techniques, compare model performance, and justify results using evaluation metrics and visualization.

---

# Dataset Information

The dataset contains **20 plant and fruit leaf classes** used for image classification.

## Classes

- avocado
- banana
- betel
- cacao
- cassava
- corn
- durian
- eggplant
- guava
- jackfruit
- lanzones
- mahogany
- mango
- narra
- neem
- papaya
- rambutan
- sugarcane
- sweet_potato
- taro

---

# Activity 1 – Model Evaluation and Visualization

## Objective

Evaluate the saved CNN model using multiple performance metrics and visual analysis methods.

### Evaluation Methods Used

- Classification Report
- Confusion Matrix
- Receiver Operating Characteristic (ROC) Curve
- Area Under Curve (AUC)
- Precision / Recall / F1-score Visualization

---

## Baseline Model Performance

### Classification Report Summary

| Metric | Value |
|---------|---------|
| Accuracy | **93%** |
| Macro Precision | **0.93** |
| Macro Recall | **0.93** |
| Macro F1-score | **0.93** |
| Overall AUC Score | **0.977** |

The baseline model achieved strong performance and demonstrated good generalization ability.

---

## Strong Performing Classes

Several classes achieved almost perfect classification results:

| Class | F1-score |
|---------|---------|
| Jackfruit | **1.00** |
| Lanzones | **1.00** |
| Narra | **0.99** |
| Eggplant | **0.99** |

These classes showed excellent precision and recall values with minimal misclassification.

---

## Weak Performing Classes

Some classes showed weaker classification performance.

| Class | Precision | Recall | F1-score |
|---------|---------|---------|---------|
| Mango | 1.00 | 0.71 | 0.83 |
| Papaya | 0.80 | 0.89 | 0.84 |
| Taro | 0.89 | 0.85 | 0.87 |
| Sugarcane | 0.83 | 0.95 | 0.88 |

### Observation

The lower recall of **Mango** suggests that the model missed several actual Mango samples.

Despite this, the model still achieved strong overall performance.

---

# Activity 2 – Explainable AI Using Grad-CAM

## Objective

Grad-CAM (Gradient-weighted Class Activation Mapping) was used to visualize the regions influencing CNN predictions.

Explainable AI helps understand how CNN models make decisions.

---

## Grad-CAM Interpretation

The generated heatmaps highlight image regions contributing most to predictions.

| Observation | Meaning |
|------------|------------|
| Correct object highlighted | Model learned relevant features |
| Background highlighted | Model confusion |
| Scattered heatmap | Weak feature learning |

---

## Result

Grad-CAM visualizations showed that most predictions focused on leaf regions.

However, some images still activated background areas, indicating that the model occasionally relied on non-essential features.

This visualization improved model interpretability and allowed verification of prediction behavior.

---

# Activity 3 – Model Enhancement and Performance Optimization

## Objective

Improve CNN generalization performance using enhancement techniques.

The following methods were applied:

---

## Enhancement 1 – Data Augmentation

Applied augmentation methods:

```python
RandomFlip("horizontal_and_vertical")

RandomRotation(0.2)

RandomZoom(0.2)

RandomContrast(0.2)
```

### Purpose

Data augmentation increases image variation and reduces overfitting.

---

## Enhancement 2 – Improved CNN Architecture

The CNN architecture was modified by adding:

- Batch Normalization
- Additional Convolution Layers
- Dropout Layers

Architecture components:

```python
Conv2D

BatchNormalization

MaxPooling2D

Dropout

Dense Layers
```

### Purpose

Improve feature extraction and generalization ability.

---

## Enhancement 3 – Learning Rate Optimization

Optimizer configuration:

```python
Adam(
learning_rate = 0.0001
)
```

### Purpose

Provide stable learning and smoother optimization.

---

## Enhancement 4 – Early Stopping

Configuration:

```python
EarlyStopping(
monitor='val_loss',
patience=3,
restore_best_weights=True
)
```

### Purpose

Prevent unnecessary training and reduce overfitting.

---

# Improved Model Results

After enhancement techniques were applied:

| Metric | Result |
|---------|---------|
| Accuracy | **79%** |
| Macro Precision | **0.82** |
| Macro Recall | **0.79** |
| Macro F1-score | **0.79** |
| AUC Score | **0.489** |

---

# Baseline vs Improved Model Comparison

| Metric | Baseline Model | Improved Model |
|---------|---------|---------|
| Accuracy | 93% | 79% |
| Precision | 0.93 | 0.82 |
| Recall | 0.93 | 0.79 |
| F1-score | 0.93 | 0.79 |
| AUC Score | 0.977 | 0.489 |

---

## Observation

The enhanced model performed worse than the baseline model.

Possible causes:

- Excessive augmentation
- Strong regularization
- Early stopping triggering too early
- Reduced learning rate

This demonstrates that adding enhancement techniques does not always improve model performance.

Proper tuning remains important.

---

# Guide Questions (Student Reflection and Explanation)

## A. Model Evaluation Analysis

### 1. What were the weakest-performing classes based on the confusion matrix?

The weakest-performing classes were **Mango, Papaya, Taro, and Sugarcane** because they obtained lower recall and F1-score values.

Mango showed the lowest recall (**0.71**), indicating higher false negatives.

---

### 2. How did Precision, Recall, and F1-score vary across classes?

The metrics varied depending on class complexity.

Classes such as **Jackfruit, Lanzones, and Narra** achieved almost perfect scores.

Meanwhile, Mango and Papaya showed lower performance because of misclassification.

---

### 3. What does a low recall indicate in your model?

Low recall indicates that the model failed to correctly identify many actual samples belonging to a class.

This results in more false negatives.

---

### 4. How does AUC score reflect model performance compared to accuracy?

Accuracy measures overall prediction correctness.

AUC evaluates the model’s ability to separate classes.

The baseline model achieved:

- Accuracy = **93%**
- AUC = **0.977**

This indicates strong classification performance.

---

## B. Model Improvement

### 5. How did data augmentation affect validation accuracy?

Data augmentation introduced image variation and helped reduce overfitting.

However, aggressive augmentation reduced validation performance in this experiment.

---

### 6. Why is Batch Normalization important in CNNs?

Batch Normalization stabilizes training, speeds convergence, and reduces internal covariate shift.

---

### 7. What role did Dropout play in improving your model?

Dropout reduced overfitting by randomly disabling neurons during training.

This improved model generalization.

---

### 8. How did Early Stopping prevent overfitting?

Early Stopping terminated training once validation loss stopped improving.

This prevented unnecessary epochs.

---

## C. Performance Comparison

### 9. What improvements were observed after modifying the model?

Additional regularization and augmentation methods were introduced.

However, overall quantitative performance decreased.

---

### 10. Which enhancement contributed the most to performance improvement? Why?

Batch Normalization contributed the most because it stabilized training and improved feature extraction.

---

### 11. Did the gap between training and validation accuracy decrease? Explain.

Yes.

Training and validation values became closer, indicating reduced overfitting despite lower overall accuracy.

---

## D. Explainability (Grad-CAM Integration)

### 12. How did Grad-CAM help in understanding model predictions?

Grad-CAM visualized important image regions affecting predictions.

This improved model interpretability.

---

### 13. Did the improved model focus on more relevant regions? Provide evidence.

Heatmaps generally highlighted leaf areas.

However, some background activation remained.

This indicates partial improvement.

---

### 14. Why is explainability important in real-world AI applications?

Explainability improves:

- Transparency
- Reliability
- Trust
- Decision validation

It ensures AI systems use meaningful features.

---

# Repository Structure

```text
Laboratory-Work-4/
│── README.md
│── images/
│   ├── confusion_matrix.png
│   ├── roc_curve.png
│   ├── gradcam_heatmap.png
│   └── metrics_visualization.png
│
│── saved_model/
│
└── dataset_sample/
```

---

# Conclusion

The baseline CNN achieved stronger performance compared to the modified model.

Baseline results:

- Accuracy = **93%**
- AUC = **0.977**

Improved model results:

- Accuracy = **79%**
- AUC = **0.489**

The experiment demonstrated that:

- Evaluation metrics are important for model analysis
- Grad-CAM improves interpretability
- Enhancement techniques require proper tuning
- Additional techniques do not always guarantee improvement
- Explainable AI increases trust and understanding in CNN systems
