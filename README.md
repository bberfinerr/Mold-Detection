# Mold Detection (final report code)

These three scripts reproduce the code supplied from the final project report. OCR/copy errors in Python syntax and indentation were repaired. The two Mac-specific absolute paths were changed to paths relative to this project folder. Training logic, CNN architecture, threshold, and Streamlit screen were not redesigned. `numpy` is imported by the original `test.py` even though that script does not use it.

## Expected folders

```text
mold-detection-faithful/
  main.py
  test.py
  app.py
  requirements.txt
  dataset/
    train/
      clean/  [training clean photos]
      mold/   [training mold photos]
    val/
      clean/  [validation clean photos]
      mold/   [validation mold photos]
  test_set/
    clean/    [independent clean test photos]
    mold/     [independent mold test photos]
```

The old `data_set/clean` and `data_set/mold` photos must be split manually between `dataset/train` and `dataset/val`. A simple starting division is about 80% for train and 20% for val **within each class**. Copy first and keep the old source intact. Do not place the same image in multiple splits. The old `test_set` has photos directly inside: place each one into `test_set/clean` or `test_set/mold` using its true label, not a model prediction. Do not guess labels; ask the original project team if uncertain. Both class folders should contain test images for the report to work as written.

Run from this project directory in a VS Code PowerShell terminal:

```powershell
py -3 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe main.py
.\.venv\Scripts\python.exe test.py
.\.venv\Scripts\python.exe -m streamlit run app.py
```

`main.py` creates `mold_model_optimized.pt`. The older `mold_model.pth` is a different format and is not used. The scripts have been checked for Python syntax, but training and inference require your actual images and locally installed packages. For GitHub, the `.gitignore` excludes photos, weights, environment files, and prediction logs; check image publication rights before changing it.
