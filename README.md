
---

##  Dataset

The dataset contains anonymized student records with the following features:

- **Input Features**: `quiz1`, `quiz2`, `midterm`, `assignments`, `project`, `final`
- **Target**: `status` — `pass` or `fail`

Additional fields like `grade` and `total` were removed from the features to prevent data leakage.

---

##  Model Pipeline

###  Preprocessing
- Filled missing values (mean for numeric, mode for categorical)
- Encoded categorical features:
  - `grade`: Ordinal encoding (F → A)
  - `status`: Label encoding (pass = 1, fail = 0)
- Removed high-leakage features: `grade`, `total`

###  Splitting & Resampling
- Performed `train_test_split` **before** oversampling
- Applied **SMOTE** to handle class imbalance on the training set only
- Scaled features using `StandardScaler` (fit on train, transform on both)

###  Model Training
- Trained `LogisticRegression` using `liblinear` solver with `max_iter=1000`
- Evaluated on untouched test data using accuracy, precision, recall, F1-score, and confusion matrix

---

##  Model Evaluation

 **Test Accuracy**: ~95%

### Confusion Matrix

<img width="515" height="432" alt="image" src="https://github.com/user-attachments/assets/c6b7a409-073f-496f-af9f-96fb371dbc7b" />
