# Bagging-on-heart-dataset
This repository demonstrates a data preprocessing and machine learning pipeline for predicting heart disease using a dataset with the following columns:

## Dataset Columns
- **Age**: Age of the patient (numeric)
- **Sex**: Gender of the patient (0 = Female, 1 = Male)
- **ChestPainType**: Type of chest pain experienced by the patient (categorical: `TA`, `ATA`, `NAP`, `ASY`)
- **RestingBP**: Resting blood pressure (numeric, in mm Hg)
- **Cholesterol**: Serum cholesterol (numeric, in mg/dl)
- **FastingBS**: Fasting blood sugar (categorical: 0 = No, 1 = Yes)
- **RestingECG**: Resting electrocardiographic results (categorical: `Normal`, `ST`, `LVH`)
- **MaxHR**: Maximum heart rate achieved (numeric)
- **ExerciseAngina**: Exercise-induced angina (categorical: 0 = No, 1 = Yes)
- **Oldpeak**: ST depression induced by exercise relative to rest (numeric)
- **ST_Slope**: Slope of the peak exercise ST segment (categorical: `Up`, `Flat`, `Down`)
- **HeartDisease**: Target variable (binary: 0 = No, 1 = Yes)

---

## Preprocessing Steps

### 1. **Handling Outliers**
- Outliers in numeric columns were detected and treated using the **Z-score method**.
- Any data point with a Z-score greater than 3 or less than -3 was considered an outlier and handled accordingly.

### 2. **One-Hot Encoding**
- The `ChestPainType` column, which is categorical, was encoded using **one-hot encoding**.
- Each unique value in `ChestPainType` was converted into a separate binary column.

### 3. **Converting Categorical Data into Numeric**
- Other categorical columns (e.g., `Sex`, `FastingBS`, `RestingECG`, `ExerciseAngina`, `ST_Slope`) were converted into numeric values using the **`apply` function**.

### 4. **Scaling the Data**
- After preprocessing, all numeric features were **scaled** to bring them into a standard range (e.g., using StandardScaler or MinMaxScaler).
- This ensures that no single feature dominates the training of the machine learning model due to differences in scale.

---
## 5. **Result**
1. *For High-Variance Models (e.g., DecisionTreeClassifier)**:
   - Use bagging to significantly improve performance and reduce overfitting.
   - Consider ensemble methods like Random Forests for even better results.

2. **For Low-Variance Models (e.g., SVM)**:
   - Bagging may not provide substantial benefits and can add unnecessary computational cost.
   - Instead, focus on optimizing hyperparameters (e.g., kernel, C, gamma) for better performance.

3. **Model Selection**:
   - If computational resources are limited, `SVM` without bagging might be more efficient for achieving comparable performance.
   - If variance reduction is critical (e.g., small datasets or noisy data), bagging with `DecisionTreeClassifier` is a better choice.
