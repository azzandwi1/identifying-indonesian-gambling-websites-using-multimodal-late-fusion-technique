# Identifying Indonesian Gambling Websites Using Multimodal Late Fusion Technique

This repository contains the implementation of my undergraduate thesis: **"Penerapan Multimodal Late Fusion untuk Identifikasi Situs Web Judi Online di Indonesia"**.
The research focuses on experimenting with multimodal deep learning models to detect online gambling websites in Indonesia by combining **visual (screenshot)** and **textual (OCR-extracted content)** features using a late fusion strategy.

---

## 📖 Abstract

Online gambling in Indonesia has grown rapidly, posing significant legal, economic, and social risks. While the government has blocked millions of domains, new sites continue to emerge, making manual blacklisting ineffective.
This project proposes a **multimodal detection system** using:

* **EfficientNet-B3** for website screenshot classification
* **IndoBERT** for text classification (OCR-based content)
* **Late Fusion strategy** via a lightweight MLP to combine predictions

Experiments show that:

* The **image-based model** achieved up to **97.29% accuracy**.
* The **text-based model** achieved up to **98.57% accuracy**.
* The **fusion model** achieved the best performance with **99.71% accuracy, precision, recall, and F1-score**, albeit with higher inference time.

---

## 📂 Dataset

The dataset consists of website screenshots and extracted text:

* **Screenshots**:

  * 1,950 gambling sites (from [Trust+™ Positif](https://github.com/alsyundawy/TrustPositif))
  * 2,095 non-gambling sites (from [SimilarWeb](https://www.similarweb.com))
* **Text**: Obtained from OCR extraction using EasyOCR and then preprocessed for IndoBERT input.

> Note: The dataset (images) is published on Kaggle as **[gamblingdet-id](https://www.kaggle.com/datasets/azzandwiriski/gamblingdet-id)**.

---

## 🏗️ Methodology

1. **Data Collection**

   * Domains from Trust+™ Positif and SimilarWeb
   * Screenshots captured using Playwright + Cloudflare WARP
   * OCR-based text extraction with EasyOCR

2. **Preprocessing**

   * **Images**: Resize, padding (300×300), normalization, augmentation (flip, color jitter)
   * **Texts**: Cleaning (remove URLs, noise, symbols), tokenization with IndoBERT tokenizer

3. **Model Training**

   * **Image Classifier**: EfficientNet-B3
   * **Text Classifier**: IndoBERT-base-p1 (IndoBenchmark)
   * **Fusion Model**: Late fusion using MLP with logit concatenation

    <img width="2022" height="984" alt="Screenshot 2025-07-30 074210" src="https://github.com/user-attachments/assets/cc70e45e-7001-4c1a-b998-f54c674c0ac8" />

4. **Evaluation Metrics**

   * Accuracy, Precision, Recall, F1-score

---

## 📌 Limitations

* Dataset size limited (\~4k images).
* OCR introduces noise in text extraction.
* Higher inference time for multimodal fusion compared to single models.
