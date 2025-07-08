# A Multi-Strategy Approach for AI-Generated Text Detection

This repository provides a summary of our paper, **"A Multi-Strategy Approach for AI-Generated Text Detection,"** which was submitted to the [M-DAIGT (Multi-domain Detection of AI-Generated Text) Shared Task](https://sites.google.com/view/m-daigt-ranlp2025) at RANLP 2025.

**Authors:** [Ali Zain](mailto:vin.alizain@gmail.com), [Sareem Farooqui](mailto:sareemfarooqui10@gmail.com), [Dr. Muhammad Rafi](mailto:muhammad.rafi@nu.edu.pk)  
**Affiliation:** National University of Computer and Emerging Sciences, FAST, Karachi, Pakistan

---

## 📖 Overview

The proliferation of sophisticated Large Language Models (LLMs) has made the detection of AI-generated text a critical area of research. This project addresses this challenge by developing and evaluating three distinct systems for the M-DAIGT shared task, which includes:
*   **Subtask 1:** Detecting AI-generated text in **News Articles**.
*   **Subtask 2:** Detecting AI-generated text in **Academic Abstracts**.

Our primary submission, a fine-tuned RoBERTa-base model, demonstrated exceptional performance, achieving near-perfect scores on both subtasks.

## ⚙️ System Architectures

We developed three systems, each employing a different strategy for text detection.

### 1. RoBERTa-based Classifier (Primary Submission)
A fine-tuned `roberta-base` model. The input text is tokenized, and the final hidden state of the `[CLS]` token is passed through a linear layer for binary classification. This model proved to be the most effective and was our final submission for both subtasks.


*Figure 1: Architecture of the RoBERTa-based Classifier.*

### 2. TF-IDF + SVM Classifier
A traditional machine learning pipeline that serves as a strong baseline. It uses TF-IDF (Term Frequency-Inverse Document Frequency) to vectorize text into n-gram features (n=2, 3), which are then classified by a Linear Support Vector Machine (SVM).


*Figure 2: Architecture of the TF-IDF + SVM Classifier.*

### 3. Candace: Llama-Feature Ensemble
An experimental system that extracts probabilistic features from a suite of Llama-3.2 models (1B & 3B, base & instruct variants). These features (log-probabilities, entropy) are then fed into a custom Transformer Encoder-based classifier for the final prediction.


*Figure 3: Architecture of the Candace System.*

## 📊 Results

Our systems were evaluated on the official M-DAIGT test set. The RoBERTa-based system demonstrated state-of-the-art performance, achieving perfect or near-perfect scores across all metrics.

| System | Subtask (Domain) | Accuracy | F1-Score | Precision | Recall |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **RoBERTa-base (System 1)** | **News (Subtask 1)** | **99.99%** | **99.99%** | **99.80%** | **100.00%** |
| **RoBERTa-base (System 1)** | **Academic (Subtask 2)** | **100.00%** | **100.00%** | **100.00%** | **100.00%** |
| TF-IDF + SVM (System 2) | News (Subtask 1) | 97.90% | 97.91% | 97.52% | 98.30% |
| TF-IDF + SVM (System 2) | Academic (Subtask 2) | 99.85% | 99.85% | 100.00% | 99.70% |
| Candace (System 3) | News (Subtask 1) | 99.75% | 99.75% | 99.60% | 99.90% |
| Candace (System 3) | Academic (Subtask 2) | 99.95% | 99.95% | 100.00% | 99.90% |


## 🙏 Acknowledgments

We thank the organizers of the M-DAIGT shared task for providing the dataset and the evaluation platform. This research is also supported by the provisional award under the National Research Program for Universities (NRPU), Higher Education Commission (HEC) Pakistan (Reference Research Project No. 16153).
