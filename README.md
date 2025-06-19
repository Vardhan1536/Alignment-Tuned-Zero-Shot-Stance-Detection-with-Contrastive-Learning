# Alignment-Tuned-Zero-Shot-Stance-Detection-with-Contrastive-Learning
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python: 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)

This repository contains the implementation of the paper:  
**"Zero-Shot Stance Detection using Reinforcement Learning and Contrastive Learning"**

Our project introduces a novel framework that enables stance detection models to generalize to unseen topics without requiring topic-specific labeled data.

---

## Table of Contents

- [ Problem Statement](#-problem-statement)  
- [ Our Approach](#-our-approach)  
- [ Model Architecture](#-model-architecture)  
- [ Getting Started](#-getting-started)  
- [ Usage](#-usage)  
- [ Results](#-results)   
- [ Citation](#-citation)  
- [ License](#-license)

---

## Problem Statement

Traditional stance detection models are highly effective but suffer from a major limitation: they require large, topic-specific labeled datasets for training.  
When faced with a new topic not seen during training (a *zero-shot* scenario), their performance drops significantly.

This project tackles the challenge of building a stance detection model that can accurately determine stance (`FAVOR`, `AGAINST`, `NONE`) towards **unseen topics**.

---

## Our Approach

To achieve true zero-shot generalization, we combine two powerful techniques:

### 1. Reinforcement Learning for Evidence Selection
Instead of treating the entire document as a single input, we model the process of finding relevant evidence as a sequential decision-making task.

- **Agent**: A policy network that reads a document sentence by sentence  
- **Action**: Decides whether to select the current sentence as key evidence  
- **State**: The target topic and selected evidence so far  
- **Reward**: Based on how selected evidence improves stance classification accuracy  

This mimics human-like reasoning and evidence gathering.

---

### 2. Contrastive Learning for Generalizable Representations

To ensure the model generalizes beyond known topics, we apply a contrastive learning objective:

- Pulls together representations of `(topic, text)` pairs with the **same stance**
- Pushes apart representations with **different stances**

This teaches the model to learn universal stance cues like sentiment and argumentative structure, instead of topic-specific keywords.

---

## Model Architecture

Our model is composed of:

- **Text Encoder**: Transformer-based (e.g., BERT, RoBERTa) for contextual embeddings
- **RL Agent (Policy Network)**: Selects key sentences sequentially
- **Stance Classifier**: Predicts stance based on aggregated evidence
- **Contrastive Head**: Used to compute contrastive loss during training

![image](https://github.com/user-attachments/assets/6eb46c82-abfc-4e65-b559-7706ff3df694)

---

## Getting Started

### Prerequisites

- Python 3.8+
- Pip & Virtualenv
- CUDA-enabled GPU (for training)

---

### Installation

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

