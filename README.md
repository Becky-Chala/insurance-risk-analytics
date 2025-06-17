# insurance-risk-analytics
## Week 3 Project Documentation

This project focuses on data exploration, preparation, and reproducibility using DVC in a financial and insurance data context.

---

### ✅ Task 1: Exploratory Data Analysis (EDA)

**Objective**  
To understand the structure and quality of the raw dataset, identify and handle missing values, and create a clean version of the dataset ready for further processing.

**Steps Completed**
- **Loaded Data:** Imported the `.txt` dataset and examined column names and data types.
- **Inspected Missing Values:** Checked for missing values using:
  ```python
  df.isnull().sum().sort_values(ascending=False)
  ```
- **Dropped High-Missing Columns:** Removed columns like `NumberOfVehiclesInFleet`, `CrossBorder`, `CustomValueEstimate`, `Rebuilt`, `Converted`, `WrittenOff`, and `NewVehicle` due to excessive missing values.
- **Dropped Incomplete Rows:** Cleaned rows missing critical fields such as `Gender`, `MaritalStatus`, `VehicleType`, `make`, `Model`, `CapitalOutstanding`, etc.
- **Saved Cleaned Data:** Stored the result in:
  ```
  data/cleaned_rating_dataset.csv
  ```

---

### ✅ Task 2: Feature Preparation & Data Version Control (DVC)

**Objective**  
Prepare the dataset for machine learning by encoding categorical variables and scaling numerical features. Then version-control the cleaned dataset using DVC to ensure auditability and reproducibility.

#### 🛠 Feature Preparation
- **Encoding:** Applied `LabelEncoder` to transform categorical variables such as `Gender`, `MaritalStatus`, and `VehicleType` into numeric form.
- **Scaling:** Used `StandardScaler` to normalize continuous variables like `CapitalOutstanding`, `cubiccapacity`, and others.
- **Saved Prepared Data:**
  ```
  data/prepared_ML_rating.csv
  ```

#### 💾 DVC Setup & Tracking

**Steps Taken:**
1. **Initialize DVC**
   ```bash
   dvc init
   ```

2. **Configure Local Remote Storage**
   ```bash
   mkdir dvc-storage
   dvc remote add -d localstorage ./dvc-storage
   ```

3. **Add the Data to DVC Tracking**
   ```bash
   dvc add data/prepared_ML_rating.csv
   ```

4. **Commit DVC Files to Git**
   ```bash
   git add data/prepared_ML_rating.csv.dvc .gitignore .dvc/config
   git commit -m "Track prepared dataset with DVC"
   ```

5. **Push Data to Local Remote**
   ```bash
   dvc push
   ```

---

### 📂 Project Structure

```
fintech-insurance/
├── data/
│   ├── cleaned_rating_dataset.csv
│   └── prepared_ML_rating.csv
├── eda.ipynb
├── .dvc/
├── dvc-storage/
├── .gitignore
├── README.md
└── requirements.txt
```

---

### ✅ Status Summary

| Task | Description                      | Status   |
|------|----------------------------------|----------|
| 1    | Exploratory Data Analysis (EDA)  | ✅ Done   |
| 2    | ML Prep + DVC Versioning         | ✅ Done   |
