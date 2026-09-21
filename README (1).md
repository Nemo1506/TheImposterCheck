# 🛡️ The Imposter Check

### Multi-Modal AI Identity Verification & Forensic Deepfake Detection Platform

[![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115%2B-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?logo=opencv&logoColor=white)](https://opencv.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.18-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.1-189FDD)](https://xgboost.readthedocs.io/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> 🔎 A research-oriented forensic AI platform for analyzing identity documents and media using computer vision, OCR, signal-level forensics, deep learning, and ensemble-based risk classification.

**Developed by Nemaan**  
GitHub: [Nemo1506](https://github.com/Nemo1506)

---

## 📌 Project Overview

**The Imposter Check** is a multi-modal identity verification and digital-forensics system designed to analyze potentially manipulated identity documents and media.

The platform combines deterministic forensic signals with optional machine-learning inference to evaluate:

- 📄 Identity documents and scanned credentials
- 🖼️ Image manipulation and digital tampering
- 📸 Camera/liveness and presentation attacks
- 🎙️ Synthetic or AI-generated voice characteristics
- 🪪 Multiple identity cards in a single image
- 🔗 Cross-document identity consistency
- 🌐 Remote URL-based media inspection
- 📊 Risk scoring and forensic decision reporting

The system exposes a **FastAPI REST API** and a browser-based forensic dashboard.

---

## 🧠 Technical Architecture

```text
                ┌─────────────────────────────────────┐
                │        INPUT / INGESTION LAYER      │
                │ Image • Video • Audio • PDF • DOCX │
                │ Camera • URL • Multi-file upload    │
                └──────────────────┬──────────────────┘
                                   │
                                   ▼
                ┌─────────────────────────────────────┐
                │       PREPROCESSING & PARSING       │
                │ OpenCV • OCR • PDF/DOCX extraction │
                │ Quality • Blur • Glare • Contrast   │
                └──────────────────┬──────────────────┘
                                   │
                                   ▼
                ┌─────────────────────────────────────┐
                │      FORENSIC FEATURE EXTRACTION   │
                │ ELA • Noise Residuals • FFT/Moire │
                │ ORB/Keypoints • Pitch/Jitter       │
                └──────────────────┬──────────────────┘
                                   │
                                   ▼
                ┌─────────────────────────────────────┐
                │       ML / ENSEMBLE INFERENCE      │
                │ EfficientNetB0 • XGBoost • Rules   │
                │ Cost-sensitive risk classification │
                └──────────────────┬──────────────────┘
                                   │
                                   ▼
                ┌─────────────────────────────────────┐
                │       DECISION & REPORTING          │
                │ PASS • REVIEW • REJECT • Risk Score│
                │ Signals • Provenance • Audit Data │
                └─────────────────────────────────────┘
```

### 🔬 Core forensic techniques

| Technique | Purpose |
|---|---|
| **Error Level Analysis (ELA)** | Detects inconsistent JPEG compression patterns associated with image manipulation |
| **Noise Residual Analysis** | Examines sensor/noise inconsistencies across regions |
| **2D FFT / Moiré Analysis** | Identifies periodic frequency patterns associated with screen-replay presentation attacks |
| **ORB / Keypoint Matching** | Helps identify duplicated or copy-move regions |
| **OCR** | Extracts document text for semantic/reference comparison |
| **Image Quality Metrics** | Measures brightness, contrast, blur, and glare |
| **Pitch/Jitter Analysis** | Extracts acoustic characteristics useful for synthetic-voice screening |
| **EfficientNetB0** | Optional deep visual inference for document classification |
| **XGBoost** | Combines engineered forensic features into a risk classification |
| **Deterministic Guardrails** | Provides a fallback decision path when optional trained artifacts are unavailable |

---

## 🚀 Key Features

### 📄 1. Multi-Format Identity Inspection
Supports:

- PNG / JPG / WEBP / TIFF
- MP4 / WEBM / MOV
- WAV / MP3 / OGG
- PDF
- DOCX

### 🪪 2. Multi-Card Detection
Automatically detects multiple card-like regions in a single image and processes them independently.

### 📸 3. Camera & Liveness Workflow
Uses browser camera APIs for snapshot and short video capture to support presentation-attack analysis.

### 🎙️ 4. Audio Forensics
Analyzes acoustic characteristics and pitch variation for research-oriented synthetic/TTS voice detection.

### 🔗 5. Cross-Identity Comparison
Processes multiple files and generates a comparison result using extracted textual and forensic signals.

### 🌐 6. URL Inspection
Accepts public HTTP/HTTPS targets for remote media inspection.

### 🔐 7. Authentication & Session Management
Includes local authentication, password hashing, JWT-based session tokens, profile management, and scan history.

### 📊 8. Forensic Dashboard
Provides risk scores, extracted signals, analysis metadata, and decision provenance through a browser UI.

### 🐳 9. Docker Support
Includes a Dockerfile and `docker-compose.yml` for containerized deployment.

---

## 🧪 Machine Learning Pipeline

The repository contains scripts for an experimental ML workflow:

```text
Dataset Generation
       ↓
Preprocessing
       ↓
Feature Extraction
       ↓
EfficientNetB0 Visual Model
       ↓
10-Dimensional Forensic Feature Vector
       ↓
Cost-Sensitive XGBoost
       ↓
Risk / Decision Inference
```

### Example workflow

```bash
python data/generate_samples.py

python training/train_efficientnet.py

python ml/generate_features.py

python ml/train_xgboost.py

python ml/verify_models.py
```

> ⚠️ Model artifacts are intentionally excluded from Git via `.gitignore`. Trained models should be generated locally or supplied through an appropriate model-storage workflow.

---

## 🧰 Technology Stack

### Backend
- 🐍 Python 3.12
- ⚡ FastAPI
- 🚀 Uvicorn
- 📦 Pydantic
- 🖼️ OpenCV
- 🧮 NumPy
- 🧾 Pillow

### AI / ML
- 🧠 TensorFlow / Keras
- 🌲 XGBoost
- 📈 Scikit-learn
- 🔍 PaddleOCR
- 🤗 Sentence Transformers
- 🧰 Joblib

### Frontend
- 🌐 HTML5
- 🎨 CSS3
- ⚙️ JavaScript
- 📷 Web Media APIs

### DevOps
- 🐳 Docker
- 🧩 Docker Compose
- 🐚 Shell automation
- 🧪 Pytest

---

## 📁 Project Structure

```text
TheImposterCheck/
├── backend/
│   ├── app/
│   │   ├── auth.py
│   │   ├── comparator.py
│   │   ├── detector.py
│   │   ├── main.py
│   │   ├── parsers.py
│   │   ├── schemas.py
│   │   └── services.py
│   ├── web/
│   ├── Dockerfile
│   ├── requirements.txt
│   └── requirements-ml.txt
├── data/
│   ├── raw/
│   ├── processed/
│   ├── sample_inputs/
│   └── generate_samples.py
├── docs/
│   └── architecture.md
├── ml/
│   ├── dataset_generator.py
│   ├── generate_features.py
│   ├── train_xgboost.py
│   └── verify_models.py
├── training/
│   └── train_efficientnet.py
├── tests/
│   └── test_services.py
├── models/
├── docker-compose.yml
├── app.sh
├── start.sh
├── stop.sh
├── .env.example
├── .gitignore
└── LICENSE
```

---

## ⚙️ Local Setup

### 1️⃣ Clone the repository

```bash
git clone https://github.com/Nemo1506/TheImposterCheck.git
cd TheImposterCheck
```

### 2️⃣ Create a virtual environment

#### Windows PowerShell

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

#### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3️⃣ Install backend dependencies

```bash
pip install -r backend/requirements.txt
```

### 4️⃣ Install optional ML dependencies

```bash
pip install -r backend/requirements-ml.txt
```

> 💡 Some ML/OCR dependencies can require platform-specific packages and additional system libraries.

### 5️⃣ Start the API

```bash
python -m uvicorn backend.app.main:app --reload --host 127.0.0.1 --port 8000
```

Open:

```text
http://127.0.0.1:8000
```

FastAPI documentation:

```text
http://127.0.0.1:8000/docs
```

---

## 🐳 Docker

Build and start the service:

```bash
docker compose up --build
```

The API will be available on port `8000`.

---

## 🧪 Testing

Run the automated test suite from the repository root:

```bash
PYTHONPATH=. pytest -v
```

The test suite covers areas such as:

- Image-quality feature extraction
- Reference-text similarity
- Multi-card detection
- ELA heatmap generation
- Authentication lifecycle
- Multi-file comparison
- Tampering guardrails
- Screen-replay / moiré analysis

> 📌 Test outcomes can vary with optional model artifacts and installed OCR/ML dependencies. Validate datasets and thresholds independently before using the system for real-world identity decisions.

---

## 🔐 Security & Responsible Use

This project is intended for **education, research, prototyping, and controlled demonstrations**.

It should **not** be treated as a production KYC, biometric, law-enforcement, or identity-verification system without independent validation.

Before production deployment, additional controls are required, including:

- 🔒 Secure secret management
- 🧱 Strict CORS configuration
- 🛡️ SSRF protection for URL inspection
- 🔐 Strong production authentication and authorization
- 🗄️ Secure persistent storage
- 📋 Privacy and data-retention controls
- 🧪 Independent model validation
- 📏 Threshold calibration
- ⚖️ Bias and fairness evaluation
- 🔍 Adversarial robustness testing
- 📝 Comprehensive audit logging

---

## 📈 Research & Evaluation Notes

Model metrics such as AUC, precision, recall, or false-negative rates are **dataset-dependent** and should not be interpreted as universal real-world performance.

The included implementation combines learned models with deterministic forensic heuristics. When trained model artifacts are unavailable, the application can fall back to deterministic analysis.

---

## 👨‍💻 Author

**Nemaan**

🎓 B.Tech — Artificial Intelligence & Machine Learning  
🐙 GitHub: [@Nemo1506](https://github.com/Nemo1506)

---

## 📄 License

This project is licensed under the **MIT License**.

See [LICENSE](LICENSE) for details.

---

⭐ If you find this project useful for learning or research, consider starring the repository.
