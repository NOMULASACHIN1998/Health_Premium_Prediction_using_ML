# Health_Premium_Prediction_using_ML
Health Insurance Cost Prediction — Fixing Hidden Model Failures with Smart Segmentation

A Real-World ML Case Study on Error Analysis, Model Segmentation & Production Deployment

📌 Project Overview

This project started with a surprising discovery:
My health-insurance cost prediction model showed 95%+ overall accuracy, but when I drilled deeper, one specific group was completely failing — young adults (18–25).

This sparked a deep investigation into model behavior, subgroup performance, and the importance of system-level thinking in machine learning.

The final solution:
✔ Two specialized ML models
✔ Intelligent age-based model routing
✔ A fully deployable Streamlit application

This repository documents the full journey: data analysis → diagnosis → solution → deployment.

🔍 1. Problem: Hidden Failure Beneath High Accuracy

During validation, I broke down predictions by age group and found:

Age Group	Model Performance
25+	Excellent — stable, high R²
18–25	🔥 Completely chaotic — ~40% error

High overall accuracy was hiding catastrophic performance on a specific subgroup.

Why the failure?

After error analysis, the root causes were clear:

Sparse medical history in young adults

High variance in risk profiles

Different cost drivers: genetics > lifestyle

One global model couldn't generalize across two fundamentally different populations

This is a classic real-world ML pitfall:

A single model is rarely optimal for heterogeneous data distributions.

🧪 2. Deep Error Analysis (The Turning Point)

Taking inspiration from Codebasics’ advanced ML workflow, I applied subgroup-level error analysis:

Key steps:

Segmented predictions by age brackets

Plotted age vs. residuals

Analyzed feature influence differences

Investigated distributional drift within subgroups

Findings:

Young adults had:

Very wide cost distribution

Lower feature stability

Higher impact from hereditary features

Poor representation in training data

This subgroup essentially had an entirely different target distribution.

🧩 3. Solution: Model Segmentation Strategy

Instead of pushing the global model harder, I re-designed the system:

🧠 Model 1 — Young Adults (18–25)

Tailored for high-variance profiles

Strong emphasis on Genetical_Risk (hereditary indicators)

Achieved 98.64% R²

Much higher stability in sparse-data conditions

📈 Model 2 — General Population (25+)

Optimized for age-correlated medical cost drivers

Captured lifestyle + chronic risk patterns

Achieved 99.68% R²

Why segmentation works

Real-world ML often requires multiple specialized models rather than one monolithic “perfect” model.

Model segmentation helped each subset learn patterns specific to its distribution.
