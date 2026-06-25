# 🎓 SmartGrad Analytics Engine

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Database](https://img.shields.io/badge/database-SQLite3-green.svg)](https://www.sqlite.org/)
[![Framework](https://img.shields.io/badge/pipeline-Modular-orange.svg)](https://github.com/)
[![License](https://img.shields.io/badge/license-MIT-purple.svg)](LICENSE)

An end-to-end data engineering and predictive machine learning system designed to flag student academic risks on **Day 1 of the semester**, before initial examinations are taken. 

Unlike generic academic projects that suffer from data leakage by utilizing mid-term grades to predict final scores, the **SmartGrad Analytics Engine** isolates structural background and lifestyle indicators to provide schools with early, actionable intervention insights.

---

## 🏗️ System Architecture & Data Flow

The system processes raw institutional data, structuralizes it into a fully normalized relational database, mitigates temporal data leakage, and runs a custom **Two-Stage Predictive Pipeline**:

```mermaid
graph TD
    A[Raw Student CSV] -->|ETL Pipeline| B(Normalized SQLite Database)
    B -->|SQL JOIN Extraction| C[Feature Isolation Engine]
    C -->|Feature Engineering| D{Stage 1: Dropout Classifier}
    D -->|Yes: Flag Risk| E[Emergency Intervention Alert]
    D -->|No: Safe Status| F{Stage 2: Performance Regressor}
    F -->|Continuous Value| G[Predicted Final Score: 0-20]
