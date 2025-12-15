# Air Traffic Anomaly Detection ✈️

## Overview
This project implements an **unsupervised anomaly detection system** to identify abnormal aircraft behavior from real-world flight movement data.  
The system models *normal flight behavior* and flags statistically rare events that may indicate irregular or potentially unsafe conditions.

The workflow follows principles from **Andrew Ng’s Machine Learning Specialization**, emphasizing simplicity, interpretability, and probabilistic modeling.

---

## Problem Statement
Air traffic datasets are typically **unlabeled**, making supervised learning approaches impractical.  
The objective of this project is to detect anomalous flight behavior using **unsupervised learning**, without relying on predefined anomaly labels.

---

## Dataset
The dataset contains aircraft movement records from **November–December 2022**, including:
- Latitude and longitude
- Speed (mph)
- Altitude
- Timestamp information

**Note:**  
The dataset is sourced from Kaggle and is not included in this repository due to size constraints.

---

## Exploratory Data Analysis (EDA)

EDA was conducted to understand the structure, quality, and statistical behavior of the data before applying any machine learning model.

### Data Inspection
- Examined dataset shape, columns, and data types
- Ensured time-based ordering using timestamps
- Checked for missing or invalid values in key numerical features

This step verified that the dataset is suitable for sequential and statistical analysis.

---

### Univariate Analysis
The distributions of core numerical features were analyzed:
- **Speed (mph)**
- **Altitude**

Most values fall within stable operating ranges, with a small number of extreme values.  
This behavior aligns well with the assumptions required for anomaly detection.

---

### Feature Engineering
To better capture flight dynamics, the following features were derived:

- **Vertical Rate**  
  Change in altitude between consecutive timestamps, representing climb or descent behavior.

- **Trajectory Change**  
  A simple proxy for flight path deviation, computed as the absolute change in latitude and longitude between consecutive data points.

These features help expose sudden or irregular changes in aircraft behavior.

---

### Spatial Visualization
A longitude–latitude scatter plot was used to visualize overall flight paths.  
This confirmed that:
- Most aircraft follow consistent spatial patterns
- A small number of points deviate noticeably from typical routes

---

### EDA Summary
EDA results indicate that:
- Normal flight behavior is consistent and structured
- Rare deviations exist in speed, altitude change, and trajectory
- The data is well-suited for **unsupervised anomaly detection**

Based on these observations, a **Multivariate Gaussian model** was selected.

---

## Methodology
1. Perform basic EDA to understand data behavior  
2. Engineer simple, interpretable flight features  
3. Model normal behavior using a **Multivariate Gaussian distribution**  
4. Compute probability scores for each flight state  
5. Flag low-probability events as anomalies using a threshold (ε)

This approach prioritizes explainability over complexity.

---

## Results
- The model identifies statistically rare flight states as anomalies
- Anomalies appear as low-probability points in the learned distribution
- Spatial plots show anomalies occurring at unusual positions or movements

---

## Technologies Used
- Python
- Pandas, NumPy
- TensorFlow
- TensorFlow Probability
- Matplotlib

---

## Key Takeaway
This project demonstrates how **unsupervised probabilistic modeling** can be applied to real-world, unlabeled aviation data to support safety-oriented analysis.

---

## Future Improvements
- Per-aircraft (tail number) anomaly modeling
- Threshold tuning for recall-focused safety systems
- Integration with real-time flight data streams

---

## Author
Built as a practical application of concepts learned from **Andrew Ng’s Machine Learning Specialization**.


