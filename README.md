

# **Real-Time Indian Sign Language Gesture Recognition**

This project implements a real-time Indian Sign Language (ISL) gesture recognition system. It detects and interprets static hand gestures from webcam video using computer vision (MediaPipe) and deep learning (LSTM), translating them into English, Hindi, and Gujarati text.

---

## **Project Overview**

Indian Sign Language is a vital communication method for the deaf and hard-of-hearing community. This system captures hand gestures via webcam, extracts hand keypoints using MediaPipe, and classifies gesture sequences using an LSTM model trained on temporal keypoint data. The predicted output is displayed in three languages, making the system inclusive and multilingual.

---

## **Features**

* Real-time hand tracking using **MediaPipe**
* Gesture sequence classification with an **LSTM model**
* Translation support in **English, Hindi, and Gujarati**
* Font rendering for Indian scripts
* Configurable confidence threshold and display parameters

---

## **Directory Structure**

```
.
├── data/                       # Raw collected gesture data
├── fonts/                      # Font files for rendering Hindi and Gujarati
├── preprocessed_data/         # Normalized and labeled landmark data
├── videodata/                 # Video sequences used during data collection
├── buildlstm.py               # LSTM model architecture and training script
├── collect_imgs.py            # Script to record video gesture samples
├── create_dataset.py          # Extracts MediaPipe keypoints and prepares dataset
├── create_mapping.py          # Generates label mappings for multilingual output
├── lstm_model.h5              # Trained LSTM model
├── real_time_inference.py     # Live gesture recognition and translation script
├── README.md                  # Project documentation
```

---

## **Setup and Installation**

Install all required dependencies using:

```bash
pip install opencv-python mediapipe numpy tensorflow keras pillow
```

---

## **Workflow**

### 1. **Collect Gesture Samples**

Capture 30-frame video sequences for each gesture using your webcam:

```bash
python collect_imgs.py
```

Samples are stored in the `videodata/` directory.

---

### 2. **Preprocess Data**

Extract 21 hand landmarks per frame using MediaPipe and convert sequences into structured data:

```bash
python create_dataset.py
```

Preprocessed data is stored in `preprocessed_data/`.

---

### 3. **Create Label Mapping**

Create gesture-to-language mappings for multilingual translation:

```bash
python create_mapping.py
```

This script generates a pickle file containing mappings for English, Hindi, and Gujarati.

---

### 4. **Train the LSTM Model**

Train a sequential LSTM network to classify gesture sequences:

```bash
python buildlstm.py
```

The trained model is saved as `lstm_model.h5`.

---

### 5. **Run Real-Time Inference**

Launch real-time recognition with multilingual output:

```bash
python real_time_inference.py
```

Press `q` to exit the video window.

---

## **How It Works**

1. Captures video frames via webcam
2. Extracts MediaPipe hand landmarks from each frame
3. Feeds the landmark sequence to the LSTM model
4. Predicts gesture label and renders translations in English, Hindi, and Gujarati using font rendering

---

## **Customization**

### Modify Font Settings

In `real_time_inference.py`, you can adjust font and size:

```python
from PIL import ImageFont

hindi_font = ImageFont.truetype("fonts/NotoSansDevanagari.ttf", 42)
gujarati_font = ImageFont.truetype("fonts/NotoSansGujarati.ttf", 42)
```

### Adjust Confidence Threshold

Control prediction sensitivity:

```python
CONFIDENCE_THRESHOLD = 0.85
```

---

## **Planned Improvements**

* Add support for dynamic gestures with higher temporal complexity
* Integrate Text-to-Speech (TTS) for audio output
* Expand gesture dataset for broader ISL vocabulary
* Include support for additional Indian languages

---

## **Contributors**

* **Harshad Nagpure** – Model Development, System Integration
* **Dewansh Gopani** – Data Collection and Preprocessing Support

📧 **Contact:** [h.incworks@gmail.com](mailto:h.incworks@gmail.com)

---

## **References**

* [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker)
* [TensorFlow Sequential API (LSTM)](https://www.tensorflow.org/api_docs/python/tf/keras/Sequential)
* [Indian Sign Language Dictionary (ISLRTC)](https://islrtc.nic.in/)

