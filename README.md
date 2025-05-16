# BirdShazam
A project developed for the BirdCLEF 2024 competition, focusing on accurate bird species classification using audio recordings from the wild.

🔍 Project Overview
This repository presents a complete pipeline for identifying bird species from field recordings using deep learning. It includes:

Audio preprocessing and spectrogram generation

Multi-model classification using EfficientNet and custom CNNs

Inference on 81,000+ unlabeled soundscape samples

Support for rare and nocturnal bird species

Post-inference metrics and interpretability with Grad-CAM

📂 Dataset
Source: BirdCLEF 2024 Competition on Kaggle

Training Data: Field recordings of 181 bird species

Unlabeled Data: 81,000+ soundscape chunks

Preprocessing:

Audio resampled to 32kHz

5s chunks extracted from long recordings

Mel Spectrograms generated (300×300 PNG)

Feature extraction: RMS, spectral flatness for nighttime detection

🧠 Models

🔹 General Classifier
Model: EfficientNet-B3
Trained on 25,000 balanced samples from 181 species


🔹 Nocturnal Species Model
Focus: 7 owl species
Input filtered using a binary night/day classifier
Achieved 91.74% accuracy, F1 = 0.86


🔹 Rare Species Model
Covers 58 underrepresented species
Oversampled training set (~12k samples)
Achieved 90% accuracy, F1 = 0.86


🔹 Multi-Label Model
Trained on synthetic mixed spectrograms
Handles overlapping species in the same audio
Macro F1 Score: 0.75, Precision: 0.85


🌀 Inference Pipeline
Input: 81,000 unlabeled spectrograms
Nighttime detection via binary classifier (RMS + flatness)
Routed through appropriate models: General / Rare / Nocturnal
Combined predictions saved to final_combined_predictions.csv
Output: 181-class probability distribution per 5s chunk


📈 Results
Models evaluated using:
Accuracy (Top-1)
Precision, Recall, Macro F1
Threshold-optimized F1 for multilabel cases
Grad-CAM visualizations included for interpretability


🌱 Real-World Impact
Deployable on university campuses, nature reserves, and urban zones
Supports biodiversity tracking, ecological research, and citizen science
Dashboard-ready output with Song Richness Index (SRI) support

🛠 Technologies Used
Python, PyTorch, Timm
Librosa, PIL, Scikit-learn, Pandas, Matplotlib
Kaggle API, TorchVision


