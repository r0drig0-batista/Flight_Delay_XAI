# Flight Delay Prediction Using Explainable AI

## Project Overview

This project investigates how **Explainable Artificial Intelligence (XAI)** techniques can be used to interpret machine learning models for **flight delay prediction**. Rather than focusing solely on predictive performance, the work emphasises *understanding*, *trust*, and *interpretability* of model decisions in a realistic, operational setting.

The study adopts a **structured explainability workflow** that spans the full modelling pipeline:

* **Pre-modelling explanations** (data understanding and exploratory analysis),
* **In-modelling explanations** (interpretable glass-box models), and
* **Post-modelling explanations** (post-hoc analysis of black-box models).

The project was developed in the context of an academic study and is documented in detail in the accompanying paper fileciteturn0file0.

---

## Problem Setting

Flight delays remain a major challenge in the aviation industry, affecting passengers, airlines, and airport operations. While machine learning models can achieve reasonable predictive accuracy, their adoption in real-world contexts is often limited by a lack of transparency.

This project formulates **flight delay prediction as a binary classification task**, where each flight is labelled as either *on-time* or *delayed*. The goal is not only to predict delays, but to **explain why** a model makes a particular prediction.

The dataset combines heterogeneous information sources:

* Operational flight data (airline, aircraft, departure time, route),
* Temporal features (day, month, time of day),
* Weather conditions (rain, wind, temperature), and
* Geographical information (encoded as flight distance).

---

## Explainability-Centred Methodology

A key contribution of this project is the **comparison of multiple XAI techniques across different stages of the modelling pipeline**, highlighting their strengths and limitations.

### 1. Pre-Modelling Explanations

Before training any predictive model, extensive exploratory analysis was conducted to understand the structure and limitations of the data. This stage focuses on *why the data looks the way it does*, rather than on prediction.

Key aspects include:

* Dataset reduction to two major US airports to improve feasibility and class balance,
* Feature engineering to improve interpretability (e.g. Haversine distance, binary rain indicator),
* Correlation analysis and categorical frequency analysis,
* Dimensionality reduction (PCA and t-SNE) to study global structure and class separability.

These analyses reveal that flight delays are driven by **complex, non-linear interactions**, with no clear low-dimensional separation between delayed and on-time flights.

---

### 2. In-Modelling Explanations (Glass-Box Model)

To study interpretability during training, an inherently interpretable **Decision Tree** classifier is used as a glass-box model.

This model:

* Provides explicit decision rules and transparent feature usage,
* Highlights dominant operational patterns (e.g. airline, departure time, seasonality),
* Serves as a baseline for understanding how simple, human-readable rules explain delays.

Although predictive performance is limited, the decision tree offers valuable insights into *how* delay risk is structured.

---

### 3. Post-Modelling Explanations (Black-Box Model)

To better capture complex patterns, a **Random Forest** classifier is trained as a black-box model. Since its internal logic is opaque, multiple **post-hoc XAI techniques** are applied.

These techniques are grouped into three complementary families:

* **Simplification-based explanations**
  A surrogate decision tree is trained to approximate the Random Forest, illustrating the trade-off between fidelity and interpretability.

* **Feature-based explanations**
  SHAP and LIME are used to analyse both global and local feature contributions, showing that operational and temporal variables dominate predictions, while weather plays a secondary but non-negligible role.

* **Example-based explanations**
  Counterfactual explanations and nearest-neighbour analysis provide instance-level insights and highlight actionability limitations in real-world settings.

---

## Explanation Quality Evaluation

Beyond qualitative inspection, the project evaluates explanation quality using **functionally grounded metrics**:

* **Comprehensiveness**, measuring how predictions change when important features are removed,
* **Sufficiency**, measuring whether key features alone can reproduce the original prediction.

Results show that:

* Important features are *necessary but not sufficient*,
* The model distributes information across multiple variables,
* Explanations based on single feature groups are inherently incomplete.

---

## Key Findings

* No single XAI technique provides a complete explanation of model behaviour.
* Glass-box models are transparent but limited in expressive power.
* Post-hoc methods offer complementary perspectives but vary in faithfulness and stability.
* Combining **multiple XAI approaches** is essential for reliable interpretation of complex models.

Overall, the project demonstrates that explainability should be treated as a **multi-stage, multi-method process**, rather than as a single tool applied after training.

---

## Project Scope and Intent

This repository is intended as a **research-oriented project**, focused on:

* Understanding model behaviour,
* Comparing explainability techniques,
* Highlighting practical limitations of XAI in real-world data.

It is **not** designed as a production-ready delay prediction system, but as a structured exploration of explainability in tabular machine learning.

For full methodological details, experimental results, and visual analyses, please refer to the accompanying paper fileciteturn0file0.
