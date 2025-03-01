# **Indian Sign Language Gesture Recognition To Multilingual Text**  

A **real-time gesture recognition system** that converts **hand movements into text translations** in **English, Hindi, and Gujarati**. This project bridges communication gaps by allowing users to express words through simple hand gestures, which are recognized using **deep learning and computer vision**.  

---

## **📌 Project Overview**  

Sign languages and gesture-based communication are often underutilized due to a lack of widespread tools for recognition. This project uses a **long short-term memory (LSTM) model** trained on hand gesture sequences to recognize gestures and display **real-time translations**. The system is designed to be lightweight and efficient for real-world applications, with potential uses in accessibility tools, education, and human-computer interaction.  

### **Key Features**  

✅ **Real-time hand tracking** using **MediaPipe Hands**  
✅ **Sequential gesture recognition** powered by an **LSTM model**  
✅ **Multi-language support** (English, Hindi, Gujarati)  
✅ **Optimized prediction smoothing** to improve recognition stability  
✅ **Custom font rendering** for better visibility in different languages  
✅ **Supports one-hand and two-hand gestures**  

---

## **📁 Folder Structure**  

```
/gesture-translator
│── /fonts                           # Font files for Hindi & Gujarati
│── /data_preprocessing               # Preprocessing scripts & label mappings
│── dataset_collection.py             # Collects and processes gesture data
│── preprocess_data.py                 # Extracts hand keypoints for training
│── train_model.py                     # Trains LSTM model for gesture recognition
│── real_time_translation.py           # Real-time inference with translations
│── lstm_model.h5                      # Trained LSTM model
│── label_mapping.pickle               # Stores class labels & translations
│── README.md                          # Project documentation
```

---

## **🛠️ Setup & Installation**  

Before running the project, install the required dependencies:  

```bash
pip install opencv-python mediapipe numpy tensorflow keras pillow
```

---

## **📊 Data Collection & Processing**  

### **1️⃣ Collect Gesture Data**  
This script captures **video sequences** of hand gestures and extracts **MediaPipe hand keypoints**.  

```bash
python dataset_collection.py
```

- The system captures **30 frames per gesture** to ensure smooth recognition.  
- Extracted keypoints are **normalized and stored** for training.  

### **2️⃣ Preprocess the Data**  
Convert raw keypoints into a structured dataset for training:  

```bash
python preprocess_data.py
```

- Ensures **consistent data format**.  
- Saves extracted features for training the LSTM model.  

---

## **📈 Training the Model**  

### **3️⃣ Train the LSTM Model**  
```bash
python train_model.py
```
- Uses a **sequential LSTM network** to learn gesture patterns.  
- The trained model is saved as **`lstm_model.h5`**.  

---

## **🎥 Running Real-Time Gesture Translation**  

### **4️⃣ Start Gesture Recognition**  
```bash
python real_time_translation.py
```
- Uses the webcam to detect **hand movements**.  
- Displays **live translations** in **English, Hindi, and Gujarati**.  

**Exit by pressing `q`.**  

---

## **🖥️ How It Works?**  

1️⃣ **Detects hand movements** using MediaPipe.  
2️⃣ **Extracts keypoints** and converts them into a time-sequenced dataset.  
3️⃣ **Feeds the data into an LSTM model** for classification.  
4️⃣ **Predicts the gesture and displays translations** in **three languages**.  

💡 **To improve accuracy, predictions are smoothed using history tracking.**  

---

## **🎨 Customization**  

### **Modify Font Colors or Sizes**  
Edit `real_time_translation.py`:  

```python
hindi_font = ImageFont.truetype("fonts/NotoSansDevanagari-VariableFont_wdth,wght.ttf", 42)
gujarati_font = ImageFont.truetype("fonts/NotoSansGujarati-VariableFont_wdth,wght.ttf", 42)
text_colors = {"english": (255, 255, 255), "hindi": (255, 255, 0), "gujarati": (0, 255, 255)}
```

### **Adjust Prediction Confidence**  
Change the minimum confidence required for displaying a prediction:  

```python
CONFIDENCE_THRESHOLD = 0.85
```

---

## **🔹 Future Enhancements**  

🔸 Expand the dataset for more **gestures and words**.  
🔸 Improve detection for **partial hand visibility**.  
🔸 Add **voice output** for translations.  
🔸 Support additional **Indian languages** (e.g., Tamil, Bengali, Marathi).  

---

## **👨‍💻 Contributors**  

- **Harshad Nagpure** – Developed & Trained the Model  
- **Dewansh Gopani** – Assisted with Data Collection & Fine Tuning   

📧 **Contact:** h.incworks@gmail.com  

---

## **🔗 References**  

- **MediaPipe Hands**: [https://developers.google.com/mediapipe](https://developers.google.com/mediapipe)  
- **LSTM for Gesture Recognition**: [https://www.tensorflow.org/tutorials](https://www.tensorflow.org/tutorials)  
- **ISL Gestures & Dictionary** : [https://islrtc.nic.in/]

---
