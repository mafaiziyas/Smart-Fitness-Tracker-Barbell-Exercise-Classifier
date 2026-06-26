# Smart-Fitness-Tracker-Barbell-Exercise-Classifier

> **Status:** Ongoing project (Current phase: Preprocessing completed)

## 🏋️‍♂️ Barbell Exercise Classification ML

An exploration and implementation of context-aware machine learning models designed to automatically track free weight exercises, count repetitions, and detect execution form using wristband sensor data. This repository is inspired by the resources and time-series methodologies provided by [ML4QS (Machine Learning for the Quantified Self)](https://ml4qs.org/data/). 

For ease, the project is currently focusing on differentiating specific barbell exercises - namely **bench press, overhead press (ohp), squat, deadlift, and barbell row** - from resting episodes and free movements.

---

## 📋 Project Overview

While modern fitness wearables easily track aerobic activities (running, cycling, swimming), tracking free weight exercises remains under-explored. This project implements an end-to-end Machine Learning pipeline utilizing wristband accelerometer and gyroscope data to perform three core tasks of a human personal trainer:

* **Exercise Classification:** Automatically identify the current lift being performed and differentiate it from resting periods.
* **Repetition Counting:** Accurately track reps across sets.
* **Form Detection:** Flag structural errors in exercise execution (e.g., improper bar path).

---

## ⚡ Current Focus: Exercise Classification

We are initially focusing on the **Exercise Classification** component. The core objective of this phase is to accurately classify and differentiate each targeted barbell movement (`bench`, `ohp`, `squat`, `dead`, `row`) against resting periods and un-tracked free movements. 

The data preprocessing for this stage is complete, laying the groundwork for model training and evaluation.

---

## 💾 Data Source

The sensor data utilized in this pipeline maps closely to time-series exercise datasets and benchmarks hosted by the Quantified Self research community. You can find the corresponding datasets and sensory reference streams directly via the [ML4QS Data Repository](https://ml4qs.org/data/).

---

## ⚙️ Data Preprocessing & Resampling

The preprocessing pipeline condenses raw streams into a model-ready dataset:

1. **Metadata Extraction:** Parsed 187 CSV file names via `glob` to extract `participant`, `label` (exercise), and `category` (set type) attributes before merging.
2. **Stream Separation & Indexing:** Categorized files into independent **Accelerometer** and **Gyroscope** streams, converted raw `epoch (ms)` timestamps to standard `datetime`, and applied chronological indexing.
3. **Resampling & Alignment:** Since sensors sample at different rates, both streams were resampled using a **100ms** window (`rule="100ms"`) applying `mean` for numerical vectors and `last` for categorical labels. This optimal window preserves macro-movement features without losing fidelity.
4. **Final Cleaned Dataset:** Dropped missing values due to alignment mismatches, leaving a final dataset of **17,912 rows**.

---

## 📊 Data Split Strategy

To prevent data leakage and evaluate real-world generalization, the dataset is strictly partitioned by individual participants:

* **Training Set (~79% | 14,145 rows):** Participants **A, E, and C** - used for core model learning.
* **Validation Set (~12% | 2,092 rows):** Participant **D** - used for hyperparameter tuning.
* **Test Set (~9% | 1,675 rows):** Participant **B** - held out entirely for ultimate evaluation.
