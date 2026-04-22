# Facial Emotion Recognition using OpenCV and Deep Learning

This project implements and compares multiple approaches for facial emotion recognition using the FER2013 dataset. The work includes traditional feature-based methods, deep learning models, transfer learning, and a real-time webcam-based demo.

## Project Overview

The main goal of this project is to classify facial expressions into emotion categories and compare how different computer vision approaches perform on the same task.

The following models are implemented and evaluated:

- LBP + SVM
- HOG + SVM
- Custom CNN
- Fine-tuned MobileNetV2
- Real-time emotion detection using OpenCV and the trained CNN

## Dataset

The project uses the **FER2013** dataset.

FER2013 contains:
- grayscale facial images
- image size: 48 × 48
- seven emotion classes:
  - angry
  - disgust
  - fear
  - happy
  - neutral
  - sad
  - surprise

## Methods Used

### Traditional methods
- **LBP + SVM**
  - Uses Local Binary Pattern features with a Support Vector Machine classifier.
- **HOG + SVM**
  - Uses Histogram of Oriented Gradients with a Support Vector Machine classifier.

### Deep learning methods
- **Custom CNN**
  - A convolutional neural network built from scratch for emotion classification.
- **Custom CNN + Data Augmentation**
  - Improved version of the CNN using augmentation for better generalisation.
- **MobileNetV2 (Fine-tuned)**
  - Transfer learning model using a pretrained MobileNetV2 with deeper layers unfrozen for adaptation.

### Real-time deployment
- **OpenCV Haar Cascade**
  - Used for face detection in webcam input.
- **CNN-based realtime classification**
  - Uses the trained CNN model with smoothing and confidence-based filtering.

## Results Summary

| Model                       | Accuracy | Key Behaviour |
|----------------------------|----------|---------------|
| LBP + SVM                  | ~25%     | Strong bias, poor separation |
| HOG + SVM                  | ~43%     | Improved but limited |
| Custom CNN + Augmentation  | ~58%     | Best overall performance |
| MobileNetV2 (Fine-Tuned)   | ~56%     | Strong improvement after adaptation |

## Key Findings

- Traditional handcrafted features provide useful baselines but show limited performance.
- CNN-based models significantly improve emotion classification accuracy.
- Data augmentation improves generalisation and helps real-time stability.
- Fine-tuning is necessary when applying transfer learning to grayscale facial emotion data.
- Real-time emotion recognition is feasible, but performance is more reliable for strong expressions such as happy and surprise than for subtle emotions such as fear and disgust.

## Real-Time Demo

A real-time emotion detection system is included using:
- OpenCV face detection
- trained CNN model
- confidence filtering
- temporal smoothing

This improves stability during live webcam predictions, although weaker expressions remain more difficult to classify consistently.

## Project Structure

```text
facial-emotion-recognition-cv/
│
├── notebooks/
│   └── emotion_recognition.ipynb
│
├── src/
│   ├── deep_learning/
│   │   └── custom_cnn.py
│   ├── traditional_cv/
│   ├── realtime/
│   └── utils/
│
├── requirements.txt
├── README.md
└── .gitignore