Here’s a cleaned, professional, and technically accurate version of your README that reflects your actual implementation with precise terminology and structure:

---

# **Real-Time Indian Sign Language (ISL) Recognition System**

This project is a real-time recognition system for Indian Sign Language (ISL) that translates hand gestures into English text. It uses computer vision and machine learning techniques to identify static gestures from webcam input, making communication more accessible for individuals using sign language.

---

## **Project Overview**

The goal of this project is to develop an efficient ISL gesture recognition system that operates in real time. It captures hand gestures using a webcam, detects key landmarks using MediaPipe, and classifies the gesture using a trained machine learning model. The predicted gesture is then displayed as text on screen.

---

## **Key Features**

* Real-time gesture detection using **MediaPipe Hands**
* Static gesture classification using a **Random Forest Classifier**
* Efficient preprocessing and landmark extraction for high accuracy
* Lightweight, fast, and suitable for local deployment
* Modular codebase for data collection, training, and inference

---

## **Folder Structure**

```
/isl-recognition
│── /data_collection/                # Scripts for collecting gesture images and landmarks
│── /models/                         # Trained ML model and label mappings
│── /utils/                          # Utility functions for preprocessing and display
│── collect_data.py                 # Capture and save gesture images
│── extract_keypoints.py            # Extract MediaPipe landmarks from images
│── train_model.py                  # Train Random Forest Classifier
│── inference.py                    # Real-time prediction using webcam
│── model.pkl                       # Trained gesture recognition model
│── labels.pickle                   # Label encoder for class names
│── README.md                       # Project documentation
```

---

## **Setup and Installation**

### Prerequisites

Install the required packages using pip:

```bash
pip install opencv-python mediapipe numpy scikit-learn joblib
```

---

## **Workflow**

### 1. Data Collection

Use the `collect_data.py` script to capture images for each gesture. The script uses a webcam to save frames associated with specific gesture labels.

```bash
python collect_data.py
```

Each gesture class should have a separate folder with consistent frame counts for training.

---

### 2. Keypoint Extraction

Extract MediaPipe hand landmarks from the collected images and store them for training:

```bash
python extract_keypoints.py
```

This script will generate a dataset of normalized keypoint features per gesture sample.

---

### 3. Model Training

Train a Random Forest classifier using the extracted landmark data:

```bash
python train_model.py
```

The model will be saved as `model.pkl` and the label encoder as `labels.pickle`.

---

### 4. Real-Time Inference

Launch the real-time gesture recognition interface:

```bash
python inference.py
```

* The webcam feed is processed in real-time.
* Detected hand gestures are classified and displayed as text.
* Press `q` to quit.

---

## **How It Works**

1. **Hand Detection**: MediaPipe detects hand landmarks from video frames.
2. **Feature Extraction**: Normalized x, y, z coordinates of 21 keypoints are extracted.
3. **Classification**: A Random Forest model classifies the landmarks into gesture classes.
4. **Display**: The predicted label is rendered on the video stream.

---

## **Customization Options**

* **Model Selection**: You can experiment with other classifiers (SVM, KNN, etc.) by modifying `train_model.py`.
* **Landmark Features**: Add velocity or angle-based features for dynamic gestures.
* **Display Settings**: Modify `inference.py` to change font, text color, or add GUI features.

---

## **Future Work**

* Add support for dynamic gesture recognition using LSTM-based models.
* Extend the system to output speech via text-to-speech (TTS) modules.
* Incorporate multi-language text output (Hindi, Gujarati, etc.).
* Build a web-based or mobile interface for broader accessibility.

---

## **Authors**

* **Harshad Nagpure** – System Design, Model Development, Inference Pipeline
* **Dewansh Gopani** – Data Collection and Preprocessing Support

For inquiries: **[h.incworks@gmail.com](mailto:h.incworks@gmail.com)**

---

## **References**

* [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker)
* [Scikit-learn Random Forest Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
* [Indian Sign Language Dictionary – ISLRTC](https://islrtc.nic.in/)

