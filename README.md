# EEG_EDF_analyzer
Jfernandez_Capstone_Project_DS4BME
# EEG Analysis Streamlit App

## Overview
This project is a Streamlit-based app designed for analyzing EEG (Electroencephalogram) recordings. It processes EEG data in EDF format, extracts key features like bandpower and Patient State Index (PSI), visualizes raw data and spectrograms, and predicts the patient's state (awake or anesthetized). The app is built for interactive exploration and clinical insights.

## Video
https://youtu.be/nZbnIAgeDas?si=QIceh7zB_eUSAFE7 

## Features
1. **File Upload**: Users can upload EEG data in EDF format for analysis.
2. **Channel Selection**: Choose specific EEG channels to focus on, mapped to common electrode placements in anesthesia (L1, L2, R1, R2).
3. **Data Visualization**:
   - Plot raw EEG data for selected epochs.
   - Generate spectrograms to explore frequency power over time.
4. **Feature Extraction**:
   - Compute bandpower for Delta, Theta, Alpha, Beta, and Gamma frequency bands.
   - Calculate PSI, an index representing sedation levels (0-100 scale).
   - Extract Spectral Edge Frequency (SEF).
5. **Binary Classification**: Predict whether the patient is awake or anesthetized using a Random Forest classifier.
6. **Long Period Analysis**:
   - Generate multitaper spectrograms for extended EEG segments.
   - Analyze power trends over time for different frequency bands.

## Key Functions
- **`bandpower(data, sf, band, window_sec=None, relative=False)`**: Calculates average power in specific frequency bands ("Delta (0.5-4 Hz)": (0.5, 4), "Theta (4-8 Hz)": (4, 8),"Alpha (8-12 Hz)": (8, 12), "Beta (12-30 Hz)": (12, 30), "Gamma (30-50 Hz)": (30, 50),).
- **`calculate_psi(eeg_data, fs)`**: Computes the aproximate PSI based z-scores, should be replaced by the manufacturer's actual PSI when available.
- **`extract_features(data, sf)`**: Extracts bandpower and PSI for classification and testing.
- **`classify_awake_vs_anesthetized(features_df)`**: Performs binary classification using bandpower as features and PSI as testing.

## Usage
1. **Run the App**: Launch the app by running the Streamlit script.
      streamlit run app.py
2. **Upload Data**: Upload an EEG recording in EDF format.
3. **Select Options**: Choose the channel, epoch duration, and start time for analysis.
4. **View Results**:
   - Analyze raw EEG signals and spectrograms.
   - Extract metrics like bandpower, SEF, and PSI.
   - Predict the patient's state (awake or anesthetized).
5. **Long Period Trends**: Perform analysis over extended EEG segments to identify specific epochs of interest.

## Requirements
- Python 3.8
- Required Libraries:
  - `streamlit`
  - `mne`
  - `numpy`
  - `pandas`
  - `matplotlib`
  - `scipy`
  - `sklearn`

## Notes
- The app is for educational and exploratory purposes only. It is not a substitute for clinical-grade tools.
- Ensure that uploaded EDF files contain channels matching the expected electrode names for accurate analysis.
- Tested on Masimo Sedline exported files

## Author
Juan Fernandez  
Data Science for BME - Capstone Project  
2024
