# 🩺 Skin Disease Classification System
<img width="1536" height="1024" alt="ChatGPT Image Jun 30, 2026, 12_28_46 AM" src="https://github.com/user-attachments/assets/3c826bef-ccf6-4034-ac11-5db729c73c08" />

> **Python 3.12 • TensorFlow 2.x • Flask 3.x • MIT License**

---
# 📸 Application Preview

### Home Page
<img width="1600" height="734" alt="WhatsApp Image 2026-06-29 at 11 28 43 PM" src="https://github.com/user-attachments/assets/3536491e-75c6-4318-9381-e25bc2aa0854" />

### Upload Screen
<img width="535" height="319" alt="WhatsApp Image 2026-06-29 at 11 30 14 PM" src="https://github.com/user-attachments/assets/53b9ab27-99a3-40ee-89e2-db1b13642ca4" />

### Prediction Result
<img width="1121" height="708" alt="WhatsApp Image 2026-06-29 at 11 30 48 PM" src="https://github.com/user-attachments/assets/5c2144aa-dfc0-4ead-b6dd-9939ae7f16d5" />

## ⚠️ Important Disclaimer

This project is for **educational and portfolio purposes only**. It is **not a certified medical device** and must never be used as a substitute for professional diagnosis. Always consult a licensed dermatologist for any skin concern.

---

# 📖 Overview

An AI-assisted web application that classifies photographs of skin lesions into **nine common dermatological conditions** using a **MobileNetV2 transfer-learning model**, served through a **Flask API** and a responsive **vanilla JavaScript frontend**.

Upload a photo of a skin lesion and receive instantly:

- ✅ The predicted condition with a confidence score
- ✅ A full probability breakdown across all supported classes
- ✅ A plain-language description of the predicted condition
- ✅ A general next-step recommendation

---

# ✨ Features

- MobileNetV2 transfer-learning classifier (9 classes)
- Real-time inference via a Flask REST API
- Confidence-ranked probability breakdown
- Light/Dark mode with persisted user preference
- Accessible, semantic, ARIA-labeled frontend
- Server-side and client-side upload validation

---

# 🩹 Supported Conditions

| Condition | Category |
|-----------|----------|
| Actinic keratosis | Pre-cancerous |
| Atopic Dermatitis | Inflammatory |
| Benign keratosis | Benign |
| Dermatofibroma | Benign |
| Melanocytic nevus | Benign |
| Melanoma | Malignant |
| Squamous cell carcinoma | Malignant |
| Tinea Ringworm Candidiasis | Fungal/Infection |
| Vascular lesion | Vascular |

---

# 🧠 Model Architecture

The model uses a frozen **MobileNetV2 backbone** (ImageNet-pretrained) with a custom classification head.

```text
Input (224×224×3)
        │
MobileNetV2 (ImageNet weights, frozen)
        │
GlobalAveragePooling2D
        │
Dropout(0.3)
        │
Dense(128, relu)
        │
Dense(9, softmax)
```

Training configuration:

- Optimizer: Adam
- Loss: Sparse Categorical Cross-Entropy
- Transfer Learning: MobileNetV2
- Framework: TensorFlow/Keras

---

# 📂 Project Structure

```bash
skin-disease-classification/
│
├── app.py
├── requirements.txt
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
│
├── model/
│   ├── config.json
│   ├── metadata.json
│   ├── model.weights.h5
│   └── class_names.json
│
├── static/
│   ├── index.html
│   ├── script.js
│   └── style.css
│
├── docs/
│   └── AUDIT_REPORT.md
│
└── screenshots/
```

---

# ⚙️ Installation & Setup

## Prerequisites

- Python 3.12
- pip

## Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/skin-disease-classification.git

cd skin-disease-classification
```

## Create Virtual Environment

### Linux/Mac

```bash
python -m venv venv
source venv/bin/activate
```

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

## Environment Variables

```bash
cp .env.example .env
```

Edit the `.env` file as needed.

---

# 📦 Core Dependencies

- Flask
- Flask-CORS
- TensorFlow
- NumPy
- Pillow
- python-dotenv

---

# 🚀 Usage

Start the server:

```bash
python app.py
```

Open:

```text
http://localhost:5000
```

Upload a skin image and view the prediction.

---

# 🔌 API Example

```bash
curl -X POST http://localhost:5000/predict \
-F "image=@sample.jpg"
```

Example response:

```json
{
  "predicted_class": "Melanocytic nevus",
  "confidence": 91.42,
  "probabilities": {
    "Melanocytic nevus": 91.42,
    "Benign keratosis": 4.11
  },
  "description": "A standard benign skin mole.",
  "recommendation": "Perform regular skin checks."
}
```

---

# 📚 API Reference

| Endpoint | Method | Description |
|----------|---------|-------------|
| `/` | GET | Serves frontend application |
| `/predict` | POST | Accepts image upload and returns prediction |

---

# 🏋️ Training Instructions

1. Mount your dataset.
2. Open `train_skin_disease_model.ipynb`.
3. Run all training cells.
4. Evaluate on a test split.
5. Export `class_names.json`.
6. Save the model:

```text
config.json
metadata.json
model.weights.h5
```

---

# 🔮 Future Improvements

- Fine-tune MobileNetV2 backbone
- Add automated tests using pytest
- Add API authentication
- Host model weights via Git LFS or Hugging Face
- Add Grad-CAM visualizations
- Deploy to cloud platforms

---

reenshots of your application here:

```text
screenshots/
├── home.png
├── upload.png
└── prediction.png
```

---

# 📜 License

This project is distributed under the **MIT License**.

See the `LICENSE` file for details.

---

# 🙏 Acknowledgements

- MobileNetV2 — Sandler et al.
- TensorFlow/Keras Team
- Dataset Contributors
- Flask Community
