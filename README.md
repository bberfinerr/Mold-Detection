# Mold Detection Using Deep Learning

## About the project

This graduation project explores automated mold detection in images. Its goal is to distinguish **clean** samples from samples with **mold** and provide a simple interface for reviewing predictions. The application is intended as a prototype for image-based screening, not a substitute for laboratory analysis.

We trained a convolutional neural network (CNN) with PyTorch on labeled images. The model takes an RGB image resized to 64 × 64 pixels and returns a mold probability. A Streamlit web panel lets users upload one or more images, view the predicted class and score, and explore charts and daily or weekly summaries of saved predictions.

## How it works

- `main.py` trains the CNN using `dataset/train`, evaluates each epoch using `dataset/val`, and saves the trained TorchScript model as `mold_model_optimized.pt`.
- `test.py` runs the saved model on labeled images in `test_set` and prints predictions, a confusion matrix, and a classification report.
- `app.py` provides the Streamlit interface and records predictions in `prediction_log.csv`.

## Project structure

```text
mold-detection-faithful/
  main.py
  test.py
  app.py
  requirements.txt
  dataset/
    train/
      clean/
      mold/
    val/
      clean/
      mold/
  test_set/
    clean/
    mold/
```

The dataset, test images, trained model, virtual environment, and prediction log are excluded from this repository. To retrain, place your own labeled images in the folders above. Each image should appear in only one of the training, validation, or test splits. `ImageFolder` uses alphabetical folder names, so `clean` maps to class 0 and `mold` maps to class 1.

## Run locally (Windows)

Open a PowerShell terminal in the folder containing `main.py`:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe main.py
.\.venv\Scripts\python.exe test.py
.\.venv\Scripts\python.exe -m streamlit run app.py
```

Training saves `mold_model_optimized.pt` in the current folder. Run `main.py` before `test.py` or `app.py`. The older `mold_model.pth` belongs to a different model version and is not used here.

## Project recovery and limitations

The original project folder was lost, so this repository was recreated from the final graduation report that remained available. The report contained the code for `main.py`, `test.py`, and `app.py`. Copying errors in the extracted text and machine-specific file paths were corrected to make the scripts usable on another computer. The reported model architecture, training loop, prediction threshold, and interface flow were retained.

The final version's trained TorchScript model and complete working environment were not recovered. The model must be trained again with the appropriate images, and its performance should be evaluated on a sufficiently large, independent test set. Predictions may vary with image source, lighting, background, and how much mold is visible.
