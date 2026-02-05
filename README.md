# Multimodal Machine Learning for Automated Sleep Stage Classification and Sleep Duration Estimation


## 📌 Project Overview
This project implements a **multimodal deep learning system** for automatic sleep stage classification and sleep estimation using **EEG, EOG, and EMG** signals.  
The system supports both **3-class** and **5-class** sleep staging and estimates clinically relevant sleep parameters.

---

## 🎯 Aim
To design and implement an automated system for sleep stage classification and sleep estimation using multimodal physiological signals.

---

## 🎯 Objectives
- Perform **3-class sleep classification** (Wake, NREM, REM)
- Perform **5-class sleep classification** (Wake, N1, N2, N3, REM)
- Prevent subject-level data leakage using subject-wise splitting
- Improve REM and transition-stage classification accuracy
- Estimate sleep metrics such as:
  - Total sleep time
  - Sleep efficiency
  - Sleep latency
  - REM latency

---

## 🧠 Problem Statement
Manual sleep scoring is time-consuming, subjective, and requires expert clinicians.  
Single-modality automatic sleep staging suffers from low accuracy, especially for REM sleep.  
This project addresses these issues using **multimodal signals and hierarchical classification**.

---

## 📊 Dataset
**Sleep-EDF / Sleep-EDF Expanded Dataset**

- EEG (Electroencephalogram)
- EOG (Electrooculogram)
- EMG (Electromyogram)
- Epoch length: **30 seconds**
- Subject-wise train/validation/test split

---

## 🏗️ System Architecture

### 🔹 Approach 1: Hierarchical 3-Class Classification
**Stage 1:** Wake vs Sleep  
**Stage 2:** REM vs NREM (applied only on sleep epochs)  
**Final Output:** Wake / NREM / REM  

### 🔹 Approach 2: Direct 5-Class Classification
Single multimodal model predicts:
- Wake
- N1
- N2
- N3
- REM

---

## ⚙️ Methodology

### Step 1: Data Preprocessing
- Load EEG, EOG, EMG signals
- Normalize signals
- Segment data into fixed-length sequences
- Ensure subject-wise separation

### Step 2: Sequence Formation
- Temporal sequences of epochs (`SEQ_LEN`)
- Each sequence predicts the last epoch label

### Step 3: Model Design
- 1D CNN for feature extraction
- Temporal Convolution Network (TCN)
- Attention mechanism
- Fully connected classifier

### Step 4: Training
- Loss: Cross Entropy Loss
- Optimizer: AdamW
- Metric: Accuracy
- Best model saved using validation accuracy

### Step 5: Evaluation
- Accuracy
- Confusion matrix
- Classification report
- Sleep estimation metrics

---

## 🧮 Algorithms

### 3-Class Classification Algorithm
1. Load multimodal sleep data
2. Convert labels to Wake/Sleep
3. Train Stage-1 classifier
4. Convert Sleep labels to REM/NREM
5. Train Stage-2 classifier
6. Merge Stage-1 and Stage-2 predictions
7. Evaluate performance
8. Estimate sleep metrics

### 5-Class Classification Algorithm
1. Load multimodal signals
2. Create temporal sequences
3. Train SSNet-based model
4. Predict sleep stages
5. Evaluate using accuracy and confusion matrix

---

## 📈 Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

---

## 🛌 Sleep Estimation Metrics
- Total Recording Time
- Total Sleep Time
- Wake Time
- NREM Time
- REM Time
- Sleep Efficiency (%)
- Sleep Latency
- REM Latency

---

##  Results
### 3-Class Classification
<img width="1800" height="1500" alt="confusion_matrix" src="https://github.com/user-attachments/assets/90520f50-6e65-4f88-9d13-b0fe78215268" />


### 5-Class Classification
<img width="2100" height="1800" alt="confusion_matrix" src="https://github.com/user-attachments/assets/ad63b5d2-a861-4b39-a013-c5d5a6ebc066" />


---

## Advantages
- Uses multimodal physiological signals
- Improves REM sleep detection
- Prevents subject-level data leakage
- Suitable for real-time sleep monitoring
- Scalable and clinically relevant

---

## Applications
- Clinical sleep disorder diagnosis
- Home sleep monitoring systems
- Wearable health devices
- Sleep research and analysis

---

## 🔮 Future Work
- Extend to 6-class sleep staging
- Real-time streaming inference
- Edge-device deployment
- Integration with wearable sensors

---

## 📌 Conclusion
A robust multimodal and hierarchical sleep classification system was successfully implemented.  
The system achieves high accuracy for both 3-class and 5-class sleep staging and provides reliable sleep estimation metrics, demonstrating strong potential for real-world clinical applications.

---


## 📄 License
This project is intended for academic and research purposes.
