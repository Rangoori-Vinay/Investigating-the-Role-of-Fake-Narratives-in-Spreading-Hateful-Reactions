---

# Fake and Hate Speech Detection in Multilingual Social Media Text

![Model Flow](https://i.imgur.com/a4msRUM.png)

This project focuses on identifying **fake news** and **hate speech** in multilingual social media posts, leveraging transliteration, translation, embedding extraction, and clustering techniques to improve detection accuracy.

---

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Model Architecture](#model-architecture)
- [Screenshots](#screenshots)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributors](#contributors)

---

## Introduction

In today's digital world, social media platforms are often misused to spread **fake news** and **hate speech**, leading to harmful reactions. This project aims to build a **multi-task learning model** that can detect and classify fake and hate content in multilingual text, primarily focusing on Hindi and English code-mixed social media data. We utilize advanced techniques such as **transliteration**, **translation**, and **clustering** to enhance model performance.

---

## Features

- **Transliteration and Translation**: Hinglish (Hindi-English) text is transliterated to Hindi and translated into English using **IndicXlit** and **IndicTrans2** models.
- **Embedding Extraction**: Multiple models such as **BERT**, **XLM-Roberta**, **ALBERT**, **Electra**, and **mBERT** are used to extract text embeddings.
- **Cluster-Based Feature Engineering**: Distances from cluster centers are computed to improve model accuracy.
- **Shared Multi-Task Layers**: The model uses shared layers for simultaneous **fake detection** and **hate detection** tasks.

---

## Model Architecture

### Preprocessing
1. **Text Cleaning**: Removal of symbols, punctuation, and conversion of emojis to text.
2. **Transliteration**: Hinglish text is converted into Hindi using IndicXlit.
3. **Translation**: Hindi text is translated into English using IndicTrans2 for better model compatibility.

### Embedding Extraction
We used the following models to extract text embeddings:
- **BERT**
- **XLM-Roberta**
- **ALBERT**
- **Electra**
- **mBERT**

### Multi-Task Learning
The model architecture includes:
1. **Shared Layers**: Used for both fake and hate detection tasks.
2. **Separate Branches**:
   - **Fake Detection Branch**: Uses specific layers to detect fake content.
   - **Hate Detection Branch**: Identifies hate speech in text.
3. **Clustering**: Clusters are formed based on embeddings, and distances from cluster centers are incorporated as additional features.

![Shared Layers Flow](https://i.imgur.com/706v4QX.png)

---

## Screenshots

### Cluster Formation & Distance Calculation

<table>
  <tr>
    <td align="center">
      <strong>Cluster Formation</strong><br>
      <img src="https://i.imgur.com/693blY8.png" alt="Cluster Formation" width="400"/>
    </td>
    <td align="center">
      <strong>Distance Calculation</strong><br>
      <img src="https://i.imgur.com/9gOQSzM.png" alt="Distance Calculation" width="400"/>
    </td>
  </tr>
</table>

### Results Comparison

<table>
  <tr>
    <td align="center">
      <strong>Fake Detection Results</strong><br>
      <img src="https://i.imgur.com/dCszwHq.png" alt="Fake Detection Results" width="400"/>
    </td>
    <td align="center">
      <strong>Hate Detection Results</strong><br>
      <img src="https://i.imgur.com/S1EkNta.png" alt="Hate Detection Results" width="400"/>
    </td>
  </tr>
</table>

---

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your_username/ml-fake-hate-detection.git
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up the environment**:
   - Add API keys and model paths in the configuration file.

---

## Usage

To run the model:

1. **Preprocess the Data**:
   ```bash
   python preprocess.py --input_path path_to_data
   ```

2. **Train the Model**:
   ```bash
   python train.py --model multi_task_model
   ```

3. **Evaluate the Model**:
   ```bash
   python evaluate.py --test_data path_to_test_data
   ```

---

## Results

| Model             | Task             | F1 Score Without Clusters | F1 Score With Clusters |
|-------------------|------------------|---------------------------|------------------------|
| BERT              | Hate Detection   | 81.97                     | 97.15                  |
| Electra           | Fake Detection   | 70.16                     | 73.11                  |
| XLM-Roberta       | Hate Detection   | 77.99                     | 78.75                  |
| XLM-Roberta       | Fake Detection   | 72.96                     | 76.21                  |

---
