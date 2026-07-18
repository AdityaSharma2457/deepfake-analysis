# 🛡️ TruthLens AI

### Detecting AI-Generated Images Through Deep Learning & Digital Forensics

> **TruthLens AI** is an advanced deep learning platform designed to distinguish authentic photographs from AI-generated images using state-of-the-art computer vision techniques. By combining transfer learning with frequency-domain analysis, the system aims to generalize across multiple image generation models instead of relying on generator-specific artifacts.

---

## 📖 Overview

The rapid advancement of generative AI models such as **Stable Diffusion, FLUX, DALL·E, Midjourney, Kandinsky, and PixArt** has made synthetic images increasingly difficult to distinguish from real photographs.

This project addresses that challenge by developing an AI-powered forensic system capable of analyzing uploaded images and predicting whether they are **Real** or **AI-Generated**.

Unlike conventional binary classifiers, the objective is to build a detector that **generalizes to unseen image generators**, making it suitable for real-world deployment where new generative models continue to emerge.

---

# 🚀 Vision

Create a scalable AI forensic platform capable of:

* Detecting AI-generated images with high confidence
* Generalizing to unseen image generation models
* Providing interpretable predictions through explainability techniques
* Supporting millions of training samples
* Serving as a deployable web platform for researchers, journalists, educators, and digital investigators

---

# 🎯 Objectives

* Build a large-scale curated dataset containing real and AI-generated images.
* Fine-tune an EfficientNet-B4 architecture for binary image classification.
* Explore frequency-domain representations (FFT/DCT) to improve robustness.
* Evaluate generalization against unseen AI generators.
* Deploy the trained model through a modern web application.
* Provide confidence scores and visual explanations for every prediction.

---

# 🧠 Proposed Architecture

```text
                      Input Image
                           │
                   Image Preprocessing
                           │
          ┌────────────────┴────────────────┐
          │                                 │
      RGB Image                     Frequency Transform
                                     (FFT / DCT)
          │                                 │
          └──────────────┬──────────────────┘
                         │
                  EfficientNet-B4
                         │
               Global Average Pooling
                         │
                      Dropout
                         │
                  Fully Connected
                         │
               Real / AI Generated
```

---

# 📂 Dataset Strategy

## Real Images

* MS COCO
* Open Images Dataset
* ImageNet
* Additional licensed real-world image datasets

## AI-Generated Images

Generated and collected from multiple image generation models including:

* Stable Diffusion
* Stable Diffusion XL
* FLUX
* DALL·E
* Midjourney
* Kandinsky
* PixArt
* Future diffusion models

The dataset is designed to maximize diversity in:

* Scene categories
* Lighting conditions
* Compression levels
* Image resolutions
* Camera viewpoints
* Generator architectures

---

# ⚙️ Technology Stack

| Component           | Technology      |
| ------------------- | --------------- |
| Language            | Python          |
| Deep Learning       | PyTorch         |
| Backbone            | EfficientNet-B4 |
| Image Processing    | OpenCV, Pillow  |
| Numerical Computing | NumPy           |
| Frequency Analysis  | FFT / DCT       |
| Explainability      | Grad-CAM        |
| Backend             | FastAPI         |
| Frontend            | React           |
| Database            | PostgreSQL      |
| Deployment          | Docker          |

---

# 🔬 Machine Learning Pipeline

```text
Dataset Collection
        │
        ▼
Cleaning & Verification
        │
        ▼
Image Preprocessing
        │
        ▼
Frequency Transformation
        │
        ▼
Transfer Learning
(EfficientNet-B4)
        │
        ▼
Training
        │
        ▼
Validation
        │
        ▼
Testing
        │
        ▼
Model Export
        │
        ▼
FastAPI Backend
        │
        ▼
React Frontend
        │
        ▼
Deployment
```

---

# 📊 Evaluation Metrics

The model will be evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Confusion Matrix
* Precision–Recall Curve

Special emphasis will be placed on **cross-generator evaluation**, where the model is tested on generators not seen during training.

---

# 🌍 Real-World Applications

* Digital Media Verification
* Journalism
* Social Media Moderation
* Academic Integrity
* Deepfake Detection Pipelines
* Content Authenticity Verification
* Cyber Forensics
* AI Content Compliance

---

# 🔍 Explainability

To improve trust in predictions, the platform will incorporate explainable AI techniques such as **Grad-CAM**, allowing users to visualize the image regions that most influenced the model's decision.

---

# 📈 Future Roadmap

* [ ] Large-scale dataset collection
* [ ] EfficientNet-B4 baseline
* [ ] Frequency-domain feature integration
* [ ] Cross-generator benchmarking
* [ ] Grad-CAM visualization
* [ ] Video deepfake detection
* [ ] REST API
* [ ] React dashboard
* [ ] Batch image analysis
* [ ] Public cloud deployment
* [ ] Continuous model retraining pipeline
* [ ] Research publication

---

# 📁 Proposed Project Structure

```text
truthlens-ai/

├── backend/
│   ├── api/
│   ├── models/
│   ├── inference/
│   ├── preprocessing/
│   ├── frequency/
│   └── training/
│
├── frontend/
│
├── datasets/
│
├── notebooks/
│
├── checkpoints/
│
├── experiments/
│
├── docker/
│
├── docs/
│
└── README.md
```

---

# 💡 Key Challenges

* Generalization to unseen AI generators
* Dataset quality and diversity
* Robustness against compression and resizing
* False-positive reduction
* Efficient inference
* Large-scale model retraining
* Explainable predictions

---

# 📌 Project Status

> 🚧 **Under Active Development**

This project is currently focused on building a robust large-scale dataset and training pipeline. Initial milestones include establishing a strong EfficientNet-B4 baseline before extending the system with frequency-domain analysis, explainability, and scalable deployment.

---

# 🤝 Contributing

Contributions are welcome. If you are interested in computer vision, digital forensics, or AI-generated content detection, feel free to open an issue or submit a pull request.

---

# 📜 License

This project will be released under the **MIT License**.

---

# ⭐ Acknowledgements

Special thanks to the open-source computer vision and machine learning community for providing datasets, pretrained models, and research that make projects like this possible.
