# Optimized Fuzzy-Based Personalized Deep Glucose Level Prediction

This project presents a hybrid, layered modeling approach that integrates **physiological white-box models** with **black-box deep learning architectures** (LSTM, GRU, TCN) for accurate and personalized glucose level prediction in **Type 1 Diabetes (T1D)** patients. The system further incorporates **genetic algorithms** for prediction horizon optimization and **fuzzy logic** for severity estimation.

---

## Key Highlights

- Hybrid modeling using both physiological and deep learning models
- Prediction Horizon optimization via Genetic Algorithm
- Severity level classification using Fuzzy Logic
- Integration of white-box features into deep learning networks
- Personalized insights based on real patient data (OhioT1DM)

---

## Dataset

- **Source**: [OhioT1DM Dataset](http://smarthealth.cs.ohio.edu/bglp/OhioT1DM-dataset-paper.pdf)
- **Patients**: 8 individuals, 8-week continuous monitoring
- **Features**: CGM readings, insulin dosage, carbohydrate intake, etc.
- **Sampling**: Every 5 minutes

---

## Methodology

### 1. White-Box Physiological Modeling
- Inspired by UVA/Padova T1D Simulator
- Three subsystems:
  - **Insulin Uptake Module**
  - **Glucose Absorption Module**
  - **Glucose-Insulin Interaction Module**
- Parameter estimation using **Adaptive Single Component Metropolis-Hastings**

### 2. Black-Box Deep Learning Models
- **LSTM**, **GRU**, and **TCN** models trained with:
  - Raw time-series data
  - Features derived from white-box models
- Metrics used: **MAE**, **RMSE**, **MSE**, **R²**

### 3. Genetic Algorithm for PH Optimization
- Chromosome encoding of model parameters
- Fitness = inverse RMSE + physiological consistency
- Outputs optimal horizons (e.g., 12, 34, 43 min)

### 4. HbA1c Estimation
- Estimated using predicted average glucose:
  \[
  HbA1c = \frac{eAG(mg/dL) + 46.7}{28.7}
  \]

### 5. Fuzzy Logic-Based Severity Classification
- Inputs: **Glucose Level** and **Weight**
- 5 glucose categories × 4 weight categories
- 20 predefined fuzzy rules
- Outputs: severity levels (Very Low to Very High)

---

## 🧾 Project Structure

glucose-prediction/
│
├── data/ # OhioT1DM raw XML files
├── preprocessing/ # Time alignment, missing value handling
├── features/ # Feature extraction scripts (moving avg, lag, etc.)
├── models/
│ ├── whitebox/ # Physiological subsystem modules
│ └── blackbox/ # LSTM, GRU, TCN models
├── optimization/ # Genetic algorithm scripts
├── severity/ # Fuzzy logic implementation
├── evaluation/ # Evaluation metrics, plots
└── README.md

Future Scope
Integration with real-time wearable devices

Reinforcement learning for insulin dosage recommendation

Expansion to Type 2 diabetes management
