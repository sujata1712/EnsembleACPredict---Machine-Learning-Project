# **EnsembleACPredict: An Ensemble Machine Learning Framework for Anticancer Peptide (ACP) Classification with LGBM‑Based Feature Importance**
---

## Project Summary:
Anticancer peptides (ACPs) are short amino acid sequences with selective cytotoxicity toward cancer cells and comparatively low toxicity to normal cells.
This project presents **EnsembleACPredict**, a supervised **machine learning framework** for ACP classification that integrates multiple classifiers with ensemble learning.

Key contributions:

* Extraction of **sequence-level features** using [Pfeature](https://webs.iiitd.edu.in/raghava/pfeature/).
* Application of **feature selection & scaling** for preprocessing.
* Training of **SVM, Decision Tree, Random Forest, LightGBM, XGBoost, and Bagging Classifier**.
* Integration using **VotingClassifier ensemble** (soft voting).
* **LightGBM feature importance** analysis for biological interpretability.

---

## Objective:
- Build a robust ML framework to classify ACPs vs non-ACPs  
- Analyze key features using **LightGBM importance**    
- Provide a reproducible model for **drug candidate prioritization**  

---

## Dataset

* **Source**: ENNAACT Anticancer and Non-Anticancer Peptide dataset
* **Classes**:

  * `1` → Anticancer Peptides (ACPs)
  * `0` → Non-ACPs
* **Format**: Plain-text sequences (single-letter amino acid codes).
* Preprocessing: Deduplication, removal of non-standard tokens, uppercase standardization.

---

## Feature Extraction (via Pfeature)

We computed **sequence-level descriptors**:

* **AAC**: Amino Acid Composition
* **AAB**: Amino Acid Binary
* **PCB**: Physicochemical Binary
* **PCP**: Physicochemical Properties
* **DPC**: Dipeptide Composition
* **PAAC**: Pseudo Amino Acid Composition

---

##  Methods

1. **Data Preprocessing**

   * `VarianceThreshold` to remove low-variance features
   * `StandardScaler` (for SVM and distance-based models)

2. **Base Models**

   * Support Vector Machine (SVM)
   * Decision Tree
   * Random Forest
   * LightGBM
   * XGBoost
   * Bagging Classifier (SVC-based)

3. **Ensemble Strategy**

   * **VotingClassifier** (Soft Voting over SVM, LightGBM, XGBoost, Bagging SVC)

---

## Results

| Model              | Accuracy (%) | Precision (%) | Recall (%) | Specificity (%) | F1 Score (%) | ROC AUC (%) | MCC  |
| ------------------ | ------------ | ------------- | ---------- | --------------- | ------------ | ----------- | ---- |
| **Ensemble Model** | **97.48**    | 93.97         | 82.58      | 99.34           | 87.90        | 97.87       | 0.87 |
| Bagging Classifier | 97.40        | 94.69         | 81.06      | 99.43           | 87.35        | 97.49       | 0.86 |
| SVM                | 97.32        | 95.45         | 79.55      | 99.53           | 86.78        | 97.50       | 0.86 |
| XGBoost            | 97.23        | 92.31         | 81.82      | 99.15           | 86.75        | 97.70       | 0.85 |
| LightGBM           | 97.23        | 88.37         | 86.36      | 98.58           | 87.36        | 97.81       | 0.86 |
| Random Forest      | 95.39        | 100.00        | 58.33      | 100.00          | 73.68        | 97.29       | 0.74 |
| Decision Tree      | 93.37        | 70.23         | 69.70      | 96.32           | 69.96        | 83.01       | 0.66 |

- **Best Accuracy**: 97.48% (Ensemble Model)
- **Best Biological Interpretability**: LightGBM feature importance

---

## Feature Importance

* **Top features** identified by LightGBM:

  * **PCP\_Z4** (Hydrophobicity index)
  * **AAC\_K** (Lysine composition)
  * **AAC\_C** (Cysteine composition)

These features are biologically significant, consistent with ACPs’ membrane-targeting activity.

---

## Future Scope

* Integration with **deep learning models** (CNNs, BiLSTMs, Transformers).
* Deployment as a **web tool** for biologists & drug discovery researchers.
* Application to **other bioactive peptides** (AMPs, AVPs, antifungal).
* Hybrid approaches with **molecular docking & dynamics simulations**.

---

## References

1. Garai, S., Thomas, J., Dey, P., Das, D. (2023). *LGBM-ACp: An ensemble model for anticancer peptide prediction*. **Molecular Diversity**.
2. Pfeature Manual. (n.d.). *Documentation for Pfeature library*.

---

## 👩‍💻 Author

**Sujata Sinhababu**
B.Tech CSE, 4th Year 
Summer Internship, NIT Agartala (2025)
