<div align="center">

# 🛡️ TruthLens AI

### *Seeing Through the Synthetic*

**A deep learning forensics platform for distinguishing real photographs from AI-generated images — built to generalize across generators, not just memorize them.**

[![Status](https://img.shields.io/badge/status-active--development-orange?style=for-the-badge)](#-project-status)
[![License](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)](#-license)
[![PyTorch](https://img.shields.io/badge/PyTorch-EfficientNet--B4-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](#%EF%B8%8F-technology-stack)
[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](#%EF%B8%8F-technology-stack)
[![FastAPI](https://img.shields.io/badge/API-FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](#%EF%B8%8F-technology-stack)

</div>

---

## 🌌 Why TruthLens?

Generative models like **Stable Diffusion, FLUX, DALL·E, Midjourney, Kandinsky,** and **PixArt** have made synthetic imagery nearly indistinguishable from reality. Most detectors today learn to recognize the fingerprint of *one* generator and collapse the moment a new model appears.

**TruthLens AI is built differently.** By fusing spatial features from a fine-tuned **EfficientNet-B4** backbone with **frequency-domain signatures (FFT/DCT)** — the subtle upsampling artifacts and spectral irregularities that survive across architectures — the goal is a detector that doesn't just memorize *known fakes*, but recognizes the *signature of synthesis itself*.

> 🧭 **The core bet:** generalization beats memorization. A model trained only on Stable Diffusion outputs will fail on tomorrow's generator. A model trained on *how synthesis behaves in frequency space* has a fighting chance.

---

## 🎯 Objectives

| # | Goal |
|---|------|
| 1️⃣ | Build a large-scale, diverse dataset of real and AI-generated images |
| 2️⃣ | Fine-tune EfficientNet-B4 for binary real-vs-synthetic classification |
| 3️⃣ | Fuse in FFT/DCT frequency representations for cross-generator robustness |
| 4️⃣ | Rigorously benchmark generalization to **unseen** generators |
| 5️⃣ | Ship an explainable, deployable web platform with confidence scoring |

---

## 🧠 Model Architecture

```
                              ┌─────────────────┐
                              │   Input Image    │
                              └────────┬─────────┘
                                       │
                              ┌────────▼─────────┐
                              │  Preprocessing    │
                              │  (resize · norm)  │
                              └────────┬─────────┘
                       ┌───────────────┴───────────────┐
                       │                                │
              ┌────────▼────────┐            ┌──────────▼──────────┐
              │     RGB Path      │            │   Frequency Path    │
              │  (spatial pixels) │            │     (FFT / DCT)     │
              └────────┬────────┘            └──────────┬──────────┘
                       │                                │
                       └───────────────┬────────────────┘
                                       │
                              ┌────────▼─────────┐
                              │  EfficientNet-B4   │
                              │   (fused features)  │
                              └────────┬─────────┘
                                       │
                              ┌────────▼─────────┐
                              │ Global Avg Pooling │
                              └────────┬─────────┘
                                       │
                              ┌────────▼─────────┐
                              │      Dropout        │
                              └────────┬─────────┘
                                       │
                              ┌────────▼─────────┐
                              │  Fully Connected    │
                              └────────┬─────────┘
                                       │
                         ┌─────────────▼─────────────┐
                         │   🟢 REAL   │   🔴 AI-GENERATED  │
                         └─────────────────────────────┘
```

---

## 📂 Dataset Strategy

<table>
<tr>
<td width="50%" valign="top">

### 📸 Real Images
- MS COCO
- Open Images Dataset
- ImageNet
- Additional licensed real-world sources

</td>
<td width="50%" valign="top">

### 🤖 AI-Generated Images
- Stable Diffusion & SDXL
- FLUX
- DALL·E
- Midjourney
- Kandinsky
- PixArt
- *(extensible to future generators)*

</td>
</tr>
</table>

**Diversity axes engineered into the dataset:**

`Scene categories` · `Lighting conditions` · `Compression levels` · `Resolutions` · `Camera viewpoints` · `Generator architectures`

---

## 🔬 End-to-End Pipeline

```
 📥 Collect  →  🧹 Clean & Verify  →  🖼️ Preprocess  →  🌊 Frequency Transform
      │
      ▼
 🔁 Transfer Learning (EfficientNet-B4)  →  🏋️ Train  →  ✅ Validate  →  🧪 Test
      │
      ▼
 📦 Export Model  →  ⚡ FastAPI Backend  →  💻 React Frontend  →  🚀 Deploy
```

---

## ⚙️ Technology Stack

| Layer | Technology |
|---|---|
| 🧮 Language | Python |
| 🔥 Deep Learning | PyTorch |
| 🏗️ Backbone | EfficientNet-B4 |
| 🖼️ Image Processing | OpenCV · Pillow |
| 🔢 Numerical Computing | NumPy |
| 🌊 Frequency Analysis | FFT / DCT |
| 🔍 Explainability | Grad-CAM |
| ⚡ Backend | FastAPI |
| 💻 Frontend | React |
| 🗄️ Database | PostgreSQL |
| 🐳 Deployment | Docker |

---

## 📊 Evaluation Metrics

`Accuracy` · `Precision` · `Recall` · `F1 Score` · `ROC-AUC` · `Confusion Matrix` · `Precision–Recall Curve`

> ⚡ **The metric that matters most:** cross-generator accuracy — performance on generative models **excluded from training**. This is the true test of generalization, and the north star for every architectural decision in this project.

---

## 🔍 Explainability

Every prediction ships with a **Grad-CAM heatmap**, highlighting exactly which regions of an image pushed the model toward "real" or "synthetic." No black-box verdicts — just transparent, inspectable reasoning suitable for journalists, researchers, and investigators who need to justify their conclusions.

---

## 🌍 Real-World Applications

<table>
<tr>
<td>🗞️ Journalism & Fact-Checking</td>
<td>📱 Social Media Moderation</td>
<td>🎓 Academic Integrity</td>
</tr>
<tr>
<td>🕵️ Deepfake Detection Pipelines</td>
<td>🔐 Cyber Forensics</td>
<td>✅ AI Content Compliance</td>
</tr>
<tr>
<td>📰 Digital Media Verification</td>
<td colspan="2">🏛️ Content Authenticity for Institutions</td>
</tr>
</table>

---

## 📈 Roadmap

- [ ] Large-scale dataset collection
- [ ] EfficientNet-B4 baseline
- [ ] Frequency-domain feature integration
- [ ] Cross-generator benchmarking
- [ ] Grad-CAM visualization
- [ ] REST API
- [ ] React dashboard
- [ ] Batch image analysis
- [ ] Video deepfake detection
- [ ] Public cloud deployment
- [ ] Continuous model retraining pipeline
- [ ] Research publication

---

## 📁 Project Structure

```
truthlens-ai/
├── backend/
│   ├── api/            # FastAPI routes & endpoints
│   ├── models/          # Model architecture definitions
│   ├── inference/        # Prediction & scoring logic
│   ├── preprocessing/    # Image cleaning & normalization
│   ├── frequency/        # FFT / DCT transforms
│   └── training/         # Training loops & configs
├── frontend/            # React application
├── datasets/            # Curated real + synthetic image sets
├── notebooks/           # Experimentation & analysis
├── checkpoints/         # Saved model weights
├── experiments/         # Ablations & benchmark logs
├── docker/              # Containerization configs
├── docs/                # Documentation
└── README.md
```

---

## 💡 Key Challenges

| Challenge | Why It's Hard |
|---|---|
| 🎯 Generalization | Detectors overfit to generator-specific artifacts |
| 📚 Dataset Quality | Diversity and label integrity at scale are costly |
| 🗜️ Robustness | Compression & resizing erase forensic signals |
| ⚖️ False Positives | Misclassifying real photos erodes trust |
| ⚡ Efficient Inference | Real-time verification needs low latency |
| 🔄 Continuous Retraining | New generators emerge faster than benchmarks update |
| 🔍 Explainability | Predictions must be defensible, not just accurate |

---

## 📌 Project Status

> 🚧 **Under Active Development**

Currently focused on building a robust, large-scale dataset and training pipeline. Initial milestones center on establishing a strong EfficientNet-B4 baseline before layering in frequency-domain analysis, explainability, and scalable deployment.

---

## 🤝 Contributing

Contributions are welcome and genuinely appreciated — whether that's dataset curation, model experimentation, frontend polish, or documentation.

1. 🍴 Fork the repository
2. 🌿 Create a feature branch
3. 💻 Make your changes
4. ✅ Open a pull request

Interested in computer vision, digital forensics, or AI-generated content detection? Open an issue and let's talk.

---

## 📜 License

Released under the **MIT License**.

---

## ⭐ Acknowledgements

Deep gratitude to the open-source computer vision and machine learning community — for the datasets, pretrained models, and published research that make projects like this possible.

<div align="center">

---

*If TruthLens AI is useful to you, consider ⭐ starring the repo.*

</div>
