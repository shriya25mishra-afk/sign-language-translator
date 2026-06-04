# SignLingo — Real-Time Sign Language Translator

> **Published Research:** Mishra, S. & Siddavatam, S. (2026). *SignLingo: Real Time Sign Language Translator.* International Journal for Multidisciplinary Research (IJFMR), Volume 8, Issue 2, March-April 2026. E-ISSN: 2582-2160. Paper ID: IJFMR260275299

---

##  Problem

Over 63 million people in India have significant hearing disabilities. Communication between Deaf and Hard-of-Hearing (DHH) individuals and non-signers is severely limited — resulting in reduced access to education, healthcare, and public services.

Existing sign language recognition systems are either:
- Too computationally heavy for real-time use
- Sensitive to lighting and background conditions
- Not designed for Indian Sign Language (ISL)

**SignLingo solves this** by providing a lightweight, real-time, web-based sign language translator that runs on a standard webcam — no specialized hardware needed.

---

##  What I Built

A full-stack, real-time sign language recognition web application using deep learning and computer vision.

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, JavaScript |
| Backend | Python (Flask / FastAPI) |
| Database | MongoDB |
| Gesture Detection | MediaPipe, OpenCV |
| Deep Learning Model | TensorFlow, Keras, CNN |
| Input | Standard Webcam |

---

## ⚙️ How It Works

```
Webcam Input
    ↓
MediaPipe extracts hand landmarks (21 keypoints per hand)
    ↓
CNN classifies gesture from landmark features
    ↓
Predicted sign displayed as text in real time
    ↓
Stored in user profile history (MongoDB)
```

1. User logs in via web interface and activates webcam
2. System captures live video frames of hand gestures
3. MediaPipe + OpenCV detect and track hand landmarks, filtering background noise
4. CNN model classifies the gesture from spatial and temporal landmark data
5. Recognized text displayed instantly on screen with confidence score
6. Session history saved to user profile dashboard

---

##  Results

| Metric | Result |
|---|---|
| Real-time classification accuracy | **92%** |
| Inference speed | Real-time at **24fps** |
| Dataset | Custom-built hand gesture dataset |
| Model type | Lightweight CNN (runs on standard laptop) |
| Recognition delay | Near-zero — results displayed instantly |

The system was evaluated under different user and environmental conditions. Within the scope of trained gestures, it demonstrated **reliable and consistent performance** without requiring GPU hardware.

---

##  System Architecture

```
┌─────────────────┐       REST API      ┌──────────────────────┐
│   FRONTEND      │ ─────────────────→  │   BACKEND SERVICES   │
│                 │                     │                      │
│ • Registration  │                     │ MediaPipe / OpenCV   │
│ • Login         │                     │   (Hand Detection)   │
│ • Live Webcam   │                     │         ↓            │
│ • Text Output   │                     │   CNN Deep Learning  │
│ • Dashboard     │                     │   (Classification)   │
│                 │ ←───────────────── │         ↓            │
└─────────────────┘    Real-time Sync   │   Text Output        │
                                        └──────────────────────┘
                                                  ↓
                                         ┌────────────────┐
                                         │   MongoDB DB   │
                                         │ • User Data    │
                                         │ • History      │
                                         └────────────────┘
```

---

##  How to Run

### Prerequisites
```bash
pip install mediapipe opencv-python tensorflow keras flask pymongo numpy
```

### Clone and Run
```bash
git clone https://github.com/shriya25mishra-afk/sign-language-translator
cd sign-language-translator
python app.py
```

Open `http://localhost:5000` in your browser, register, and start translating.

---

##  Project Structure

```
sign-language-translator/
│
├── app.py                  # Flask backend entry point
├── model/
│   ├── train_model.py      # CNN training script
│   ├── model.h5            # Trained model weights
│   └── gesture_labels.json # Gesture class labels
├── dataset/
│   └── gestures/           # Custom captured gesture images
├── static/
│   ├── css/
│   └── js/
├── templates/
│   ├── index.html          # Home / Login
│   ├── register.html
│   ├── dashboard.html
│   └── predict.html        # Live recognition interface
└── README.md
```

---

##  Key Design Decisions

**Why MediaPipe instead of raw image input?**
MediaPipe extracts 21 precise hand landmark coordinates per frame, making the model robust to lighting changes, background noise, and signer appearance variation — issues that plague traditional appearance-based approaches.

**Why CNN over Transformer?**
Transformer models (like those in Camgoz et al., 2020) achieve higher accuracy but require large datasets and GPU hardware. This system is designed for low-resource environments — a lightweight CNN achieves 92% accuracy while running in real time on a standard laptop.

**Why custom dataset?**
Publicly available datasets are built for American or European sign languages. A custom dataset was captured to include Indian Sign Language gestures, improving recognition relevance for the target user group.

---

##  Known Limitations

- Currently supports a predefined vocabulary of gestures — not full conversational ISL
- Performance may reduce under poor lighting or cluttered backgrounds
- Facial expressions and body posture (important in full sign language) not yet included
- Text output currently in English only

---

##  Future Scope

- Expand gesture vocabulary and dataset diversity
- Add multi-language text output support
- Integrate speech output (text-to-speech)
- Explore transformer-based architectures for continuous sign recognition
- Mobile deployment optimization

---

##  Research Paper

This project was published as a peer-reviewed research paper:

**Title:** SignLingo: Real Time Sign Language Translator  
**Authors:** Shriya Mishra, Shakila Siddavatam  
**Journal:** International Journal for Multidisciplinary Research (IJFMR)  
**Volume:** 8, Issue 2 | **Date:** March-April 2026  
**E-ISSN:** 2582-2160  
**Paper ID:** IJFMR260275299  
**Website:** www.ijfmr.com  

---

##  Author

**Shriya Mishra**  
M.Sc. Computer Science — Abeda Inamdar Senior College, Pune  
shriya25mishra@gmail.com | [LinkedIn](https://linkedin.com/in/shriya-mishra25)

