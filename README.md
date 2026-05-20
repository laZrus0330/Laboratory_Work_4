# Laboratory Work 4 – Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

*Here is my Google Colab Folder:* [**Click Here!**](https://colab.research.google.com/drive/1GzYM7-RWkxZhMNuJko9EoGUqKMd6V5_X?usp=sharing)

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
