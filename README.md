# Alignment-Tuned-Zero-Shot-Stance-Detection-with-Contrastive-Learning

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)]
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

This repository contains the official implementation for the paper:  
**"Zero-Shot Stance Detection using Reinforcement Learning and Contrastive Learning"**  

The entire project—from data loading and preprocessing to model training and evaluation—is implemented in a single Google Colab notebook for easy reproducibility.

---

## 📄 Project Documentation

For a detailed explanation of the methodology, theory, and in-depth analysis, refer to the [full project documentation PDF](https://drive.google.com/file/d/1OGq3qJbUjxRQiQxEKdr6COB0RPv_96Nr/view?usp=drive_link).

---

## 📖 Table of Contents

- [ Problem Statement](#-problem-statement)  
- [ Our Approach](#-our-approach)  
- [ How to Run](#-how-to-run)  
- [ Dependencies](#-dependencies)  
- [ Results](#-results)  

---

## Problem Statement

Traditional stance detection models perform well on known topics but fail to generalize to unseen ones due to their dependence on topic-specific labeled data.

This project addresses the challenge of **zero-shot stance detection**, where the model must determine the stance (`FAVOR`, `AGAINST`, `NONE`) for previously unseen topics—without retraining.

---

##  Our Approach

To enable generalization in zero-shot settings, we integrate:

### 1. Reinforcement Learning for Evidence Selection  
- The RL agent reads a document sentence by sentence.  
- It decides whether each sentence contributes meaningful evidence for stance classification.  
- Rewards are based on how much the selected evidence improves classification accuracy.  
- This mimics human reasoning and encourages focused selection.

### 2. Contrastive Learning for Generalizable Representations  
- Pulls representations of (topic, text) pairs with the same stance closer.  
- Pushes apart those with different stances.  
- Forces the model to capture stance-related cues (e.g., sentiment, argument structure) rather than memorize topic keywords.

---

## How to Run

This project is built to run entirely in **Google Colab**.

###  Enable GPU Acceleration:
1. Go to `Runtime` → `Change runtime type`  
2. Set hardware accelerator to `GPU` (T4 preferred)  
3. Click `Save`

### Run the Notebook:
Execute the cells in order:

-  **Install Dependencies**: Automatically handled in the first cell  
-  **Data Loading**: Uses preloaded datasets or allows custom uploads  
-  **Train & Evaluate**: Train the model and view zero-shot evaluation metrics directly in the notebook

---

## Dependencies

The notebook auto-installs everything needed using `!pip install`.

Key libraries used:

- `PyTorch`
- `transformers`
- `datasets`
- `scikit-learn`
- `numpy`

No manual setup required.

---

## Results

Our model outperforms traditional baselines in zero-shot stance detection tasks.  
The integration of RL and CL enables it to **generalize to unseen topics** while maintaining high accuracy and robustness.

Highlights:
- Learns to select key evidence dynamically
- Captures stance semantics independent of topic
- Significantly reduces overfitting to training topics
