# Year 3 Project – Intelligent Compound Fault Diagnosis using Decoupling CNN

This repository contains the implementation of my **Year 3 first semester project**, titled  
**“Implementation of Decoupling Convolutional Neural Network for Intelligent Compound Fault Diagnosis”**.  
The goal of this project is to design and evaluate a **multi-label CNN model** for diagnosing **compound faults** in industrial machinery, particularly involving **gears** and **bearings** in a motor system.

## 🧠 Model Design

The base model is a **1D CNN** architecture designed for time-series vibration data.  
To enable multi-label prediction, the **Decoupling Classifier** is integrated as a replacement for the standard softmax layer.

### 🔹 Key Features
- Input: 1D vibration signal sampled at 10 kHz  
- Network: CNN + classifying layers
- Classifier: Decoupling classifier with iteration-based weight updates  
- Loss Function: Modified **margin loss** (with parameters m⁺=0.9, m⁻=0.1, λ=0.25)
- Adam optimizer with initial parameter
- Training Epochs = 20 or 30(Case of more data) 
- Batch Size = 32 

## ⚙️ Dataset

The vibration data is collected from a **motor testbed** equipped with a **gear–bearing system**.

| Condition |     Gear     |    Bearing    | Samples |
|-----------|--------------|---------------|---------|
| Normal    | Normal       | Normal        | 171     |
| Fault 1   | Wear         | Normal        | 181     |
| Fault 2   | Misalignment | Normal        | 178     |
| Fault 3   | Normal       | Inner crack   | 176     |
| Fault 4   | Misalignment | Inner crack   | 174     |
| Fault 5   | Wear         | Inner crack   | 169     |

Each record consists of **12,288 points (6 × 2048 samples)** captured at **10 kHz** sampling rate.

## 🧩 Experiments and Results

### 1️⃣ Single-Label Classification
- Trained using four independent labels (normal + 3 fault types).
- Achieved high accuracy and clear signal separation.

### 2️⃣ Multi-Label Testing
- When tested with unseen compound faults, model performance decreased slightly but still showed clear recognition ability.

### 3️⃣ Joint Training (Single + Multi-Label)
- Combined training improved robustness.
- Accuracy slightly reduced due to limited dataset size, but qualitative predictions improved.

## 🧾 References

1. Huang, R., Liao, Y., Zhang, S., & Li, W. (2019).  
   *Deep Decoupling Convolutional Neural Network for Intelligent Compound Fault Diagnosis.*  
   **IEEE Access, 7, 1848–1858.**
