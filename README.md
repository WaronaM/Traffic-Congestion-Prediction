# Traffic Congestion Prediction — ITRMA4 Research Project

**Student:** Warona Maphala  
**Institution:** Eduvos Midrand  
**Year:** 2026  
**Supervisor:** [Dr. Shumba. S.]

---

## Project Title

**A Comparative Evaluation of Supervised Machine Learning Models for Urban Traffic Congestion Prediction**

---

## What This Project Does

This project uses machine learning to predict traffic congestion levels on urban roads.
Instead of just saying "there is congestion", the models predict **how likely** each congestion
level is — for example:

```
Smooth              →  4%
Slightly Congested  →  3%
Congested           →  4%
Highly Congested    → 89%  ← Predicted class
Blockage            →  0%
```

Five machine learning classifiers are compared:
- Random Forest
- Decision Tree
- Logistic Regression
- K-Nearest Neighbours (KNN)
- Support Vector Machine (SVM)

---

## Dataset

**Source:** Zafar, N. & Ul Haq, I. (2020). *Traffic congestion prediction based on Estimated Time of Arrival.* PLoS ONE, 15(12), e0238200.  
**DOI:** https://doi.org/10.1371/journal.pone.0238200

| Detail | Value |
|--------|-------|
| File | `data/traffic_dataset.csv` |
| Records | 317,112 |
| Columns | 12 |
| Target | 5-class traffic state (Smooth → Blockage) |
| Collection | Google Maps API, Islamabad, Pakistan |
| Period | February 2020 |

> **Note:** The dataset file is in Excel format despite the `.csv` extension.  
> Always load it with `pd.read_excel('traffic_dataset.csv')` — NOT `pd.read_csv()`.

---

## Repository File Structure

```
traffic_congestion_prediction/
│
├── data/
│   └── traffic_dataset.csv          ← The raw dataset (317,112 records)
│
├── src/
│   ├── preprocessing.ipynb          ← Step 1: Data cleaning & feature engineering
│   ├── random_forest.py             ← Random Forest classifier
│   ├── gradient_boost.py            ← Gradient Boost classifier
│   ├── logistic_regression.py       ← Logistic Regression classifier
│   └── xgboost_model.py             ← XGBoost classifier
│
├── EDA/
│   ├── 01_class_distribution.png    ← Bar chart of traffic state counts
│   ├── 02_ci_by_hour.png            ← Average congestion index per hour
│   ├── 03_weekday_vs_weekend.png    ← Traffic states across day types
│   ├── 04_ci_boxplot_by_state.png   ← CI spread per congestion class
│   ├── 05_weather_distribution.png  ← Weather category counts
│   └── 06_correlation_heatmap.png   ← Feature correlation matrix
│
├── results/
│   ├── model_accuracy_summary.csv   ← Final accuracy table for all 5 models
│   └── RESULTS_README.md            ← Guide to all result files
│
└── README.md                        ← You are here
```

---

## How to Run This Project

### Step 1 — Clone the Repository

Open a terminal or command prompt and type:

```bash
git clone https://github.com/YOUR-USERNAME/traffic-congestion-prediction.git
cd traffic-congestion-prediction
```

Replace `YOUR-USERNAME` with your actual GitHub username.

---

### Step 2 — Install Required Libraries

Make sure you have Python installed (Python 3.8 or higher recommended).  
Then install the required packages by running:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

---

### Step 3 — Run Preprocessing First

Open Jupyter Notebook:

```bash
jupyter notebook
```

Then open `src/preprocessing.ipynb` and run all cells from top to bottom.  
This will clean the data and save a file called `traffic_preprocessed.csv`.

---

### Step 4 — Run the Machine Learning Models

After preprocessing is complete, run any of the model scripts:

```bash
python src/random_forest.py
python src/logistic_regression.py
python src/gradient_boost.py
python src/xgboost_model.py
```

> **Important:** Update the file path inside each `.py` file before running.  
> Look for a line like `pd.read_csv('C:/Users/Noreen/...')` and change it to:
> ```python
> pd.read_excel('data/traffic_dataset.csv')
> ```

---

### Step 5 — View EDA Graphs

All exploratory analysis graphs are already saved in the `EDA/` folder.  
You can open them directly — no code needs to run.

---

### Step 6 — Check Results

After running the models, output files (confusion matrices, accuracy reports, AUC-ROC
curves) will be saved to the `results/` folder.

---

## Traffic State Labels

| Class Number | Traffic State     | Congestion Index (CI) |
|:---:|---|---|
| 0 | Smooth            | CI < 0.15             |
| 1 | Slightly Congested | 0.15 – 0.35          |
| 2 | Congested         | 0.35 – 0.65           |
| 3 | Highly Congested  | 0.65 – 2.0            |
| 4 | Blockage          | CI > 2.0              |

---

## Key Features Used

| Feature | Description |
|---------|-------------|
| `Day_Numeric` | Day of week (0 = Monday, 6 = Sunday) |
| `Weather_Enc` | Encoded weather category |
| `Time_Enc` | Peak hour (1) or non-peak hour (0) |
| `Holiday_Enc` | Holiday flag (1 = yes, 0 = no) |
| `SpecialCondition_Enc` | Special event flag (1 = yes, 0 = no) |
| `CI` | Derived Congestion Index per road segment |
| `Hour` | Hour of day (0–23) |
| `Fastest_Route_Distance` | Road segment distance in metres |

---

## Reference

Zafar, N. & Ul Haq, I. (2020). Traffic congestion prediction based on Estimated Time of Arrival. *PLoS ONE*, 15(12), e0238200.  
https://doi.org/10.1371/journal.pone.0238200

---

## Contact

For questions about this project, contact:  
**warona.maphala@icloud.com**  
**LinkedIn:** https://www.linkedin.com/in/warona-maphala
