# Smart-Fitness-Tracker-Barbell-Exercise-Classifier

> **Status:** Ongoing project (Current phase: Preprocessing completed)

## 🏋️‍♂️ Barbell Exercise Classification ML

An exploration and implementation of context-aware machine learning models designed to automatically track free weight exercises, count repetitions, and detect execution form using wristband sensor data. This repository is inspired by the research paper: *"Exploring the Possibilities of Context-Aware Applications for Strength Training"*. 

For ease, the project is currently focusing on differentiating specific barbell exercises—namely **bench press, overhead press (ohp), squat, deadlift, and barbell row**—from resting episodes and free movements.

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
