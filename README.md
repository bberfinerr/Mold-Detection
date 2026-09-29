# Mold Detection Using Deep Learning

## About the Project

This graduation project explores automated mold detection in images. Its goal is to distinguish **clean samples** from **samples with mold** and provide a simple interface for reviewing predictions. The application is a prototype for image-based screening and is not a substitute for laboratory analysis.

The project uses a convolutional neural network (CNN) built with PyTorch. The model processes images at 64 × 64 pixels and predicts whether mold is present. A Streamlit web panel allows users to upload images, view predictions and confidence scores, and explore charts and daily or weekly summaries.

## How It Works

- **main.py** trains the model using the training images, checks its performance with validation images, and saves it as `mold_model_optimized.pt`.
- **test.py** tests the saved model with labeled images and displays predictions, a confusion matrix, and a classification report.
- **app.py** provides the web interface and records predictions in `prediction_log.csv`.

## Project Recovery

The original project folder was lost. This repository was recreated using the code preserved in the final graduation report. Errors introduced while copying the code and file paths specific to the original computer were corrected. The model architecture, training process, prediction threshold, and main interface flow were kept consistent with the report.

The final version's trained model file and complete working environment were not recovered, so the model must be trained again using the appropriate images. Its performance should be assessed with a larger independent test set. Predictions may vary depending on lighting, background, image source, and how visible the mold is.
