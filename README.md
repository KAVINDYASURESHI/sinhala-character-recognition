# Sinhala Character Recognition

## Overview
An OCR system that recognizes handwritten Sinhala script characters.
Features an interactive drawing GUI built with Tkinter where users 
draw a character with their mouse and the model predicts it in real-time.

## Pipeline

### Stage 1 — dataset creation.ipynb
- Loads handwritten character images from dataset/ folder
- 4 character classes: අ (a), එ (ae), ඉ (e), උ (u)
- Reads images in grayscale using OpenCV
- Resizes each image to 8x8 pixels → flattens to 64 features
- Total dataset: 270 images (across 4 classes)
- Saves processed data as data.npy and labels as target.npy

### Stage 2 — train_KNN.ipynb
- Loads data.npy and target.npy
- Splits data 80/20 train/test
- Trains K-Nearest Neighbors (KNN) classifier
- Evaluates model performance:
  - Accuracy: 85.2% on test set (54 samples)
  - Class 'ae' (එ): 100% precision and recall
  - Generates full classification report
- Saves trained model as sinhala_character_KNN.sav

### Stage 3 — creat_window.ipynb
- Loads trained KNN model
- Launches interactive Tkinter GUI (500x500 canvas)
- User draws a Sinhala character using mouse
- Click PREDICT → model classifies the drawn character
- Click CLEAR → reset canvas for new drawing
- Click SAVE → saves drawn image to data/ folder
- Displays predicted character in Sinhala script

## Characters Recognized
| Label | Sinhala | Romanized |
|-------|---------|-----------|
| 0     | අ       | a         |
| 1     | එ       | ae        |
| 2     | ඉ       | e         |
| 3     | උ       | u         |

## Model Details
- Algorithm: K-Nearest Neighbors (KNN)
- Library: scikit-learn (KNeighborsClassifier, default k=5)
- Image size: 8x8 pixels (64 features)
- Train/Test Split: 80/20
- Test Accuracy: 85.2%
- Best performing class: එ (ae) — 100% precision & recall

## Why KNN?
Similar handwritten characters produce similar pixel feature 
vectors. KNN finds the closest matching training samples,
making it a natural and effective choice for character 
recognition with a small dataset.

## Tech Stack
- Python 3.9
- scikit-learn (KNeighborsClassifier, accuracy_score)
- OpenCV (image reading, grayscale conversion, resizing)
- NumPy (array processing)
- Tkinter (interactive drawing GUI)
- PIL / Pillow (image capture from canvas)
- joblib (model saving/loading)
- Jupyter Notebook

## How to Run
1. Clone this repository
2. Install requirements:
   pip install scikit-learn opencv-python numpy pillow joblib
3. Add your own dataset/ folder with subfolders per character
4. Run dataset creation.ipynb to process images
5. Run train_KNN.ipynb to train and save the model
6. Run creat_window.ipynb to launch the drawing GUI
7. Draw a Sinhala character and click PREDICT!

## Note on Dataset
The dataset/ folder is not included in this repository.
The model was trained on handwritten samples collected manually.

## Author
Kavindya Hewage | Abu Dhabi, UAE
LinkedIn: linkedin.com/in/kavindya-sureshi-8b39681b8/
GitHub: github.com/KAVINDYASURESHI
Portfolio: https://KAVINDYASURESHI.github.io
