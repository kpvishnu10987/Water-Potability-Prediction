# 💧 Water Potability Prediction System (Random Forest Classifier)

## 🎯 Overview

This project implements a machine learning solution to classify water as **Potable (Safe)** or **Not Potable (Unsafe)** based on 9 physicochemical features (pH, Hardness, Solids, etc.). The core predictive model is a **Tuned Random Forest Classifier**, which was selected for its high performance and stability.

---

## 🏗️ Repository Structure

| File/Folder | Description |
| :--- | :--- |
| `Water_Potability_Prediction_ml.ipynb` | Main Jupyter Notebook containing all steps: EDA, preprocessing, model training, tuning, and evaluation. |
| `water_quality_potability.csv` | The raw dataset used for training the model. |
| `model/` | Directory containing the saved model and necessary preprocessing pipelines for deployment. |
| `model/water_potability_model.joblib` | The final, best-performing **Random Forest model**. |
| `model/scaler.joblib` | The fitted **Standard Scaler** for consistent feature transformation of new data. |
| `model/imputer.joblib` | The fitted **Imputer** for consistent handling of missing values in new data. |
| `requirements.txt` | List of all Python dependencies required to run the project. |

---

## 🛠️ Setup Instructions

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/kpvishnu10987/Water-Potability-Prediction.git
    cd water-potability-prediction
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

---

## 🚀 How to Run

1.  **Jupyter Notebook:** Open and execute all cells in the `Water_Potability_Prediction_ml.ipynb` file to reproduce the entire analysis, training, and saving process.

2.  **Deployment/Prediction (Using Saved Assets):** To use the model for real-time predictions, run a separate script that performs these steps:
    * Load the model, scaler, and imputer using `joblib.load()`.
    * Apply the loaded **imputer** and **scaler** sequentially to any new, raw water data sample.
    * Call `loaded_model.predict(new_scaled_data)`.

---

## 📊 Evaluation Metrics Used

The model's performance was rigorously assessed using multiple metrics, prioritizing ROC-AUC for class discrimination:

| Metric | Result (Random Forest) | Purpose |
| :--- | :--- | :--- |
| **ROC-AUC Score** | **0.9306 (Mean CV)** | Primary metric. Measures the model's ability to distinguish between Potable and Not Potable classes across all probability thresholds. |
| **Accuracy** | 0.842 | Overall percentage of correct predictions. |
| **F1-Score** | 0.837 | Harmonic mean of Precision and Recall; important for balanced performance. |

---

## ⚠️ Important Notes

1.  **Preprocessing is Crucial:** Any new data must be processed using the **saved `scaler.joblib` and `imputer.joblib`** *before* being fed to the model. Failing to do so will result in incorrect predictions.
2.  **Feature Interactions:** EDA showed that no single feature strongly predicts potability; the model's high performance relies on learning the complex, non-linear interactions among all 9 features.
