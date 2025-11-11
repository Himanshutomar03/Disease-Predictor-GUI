# Disease Predictor GUI

A simple desktop GUI application (Tkinter) that predicts likely diseases from user-selected symptoms. The app:
- Loads a CSV dataset (symptoms, disease, cures, doctor, risk level).
- Normalizes symptom synonyms and encodes multi-label symptom data.
- Balances classes using SMOTE and trains an SVM with GridSearchCV.
- Provides an interactive symptom selector and shows top predictions with confidence and details.

## Features
- Multi-column symptom selection (body systems + common symptoms)
- Synonym mapping for common symptom phrasing
- Class balancing (imbalanced-learn SMOTE)
- Top-3 probability-ranked predictions
- Detailed info pop-up for the top prediction

## Requirements
- Python 3.8+
- Packages:
  - pandas
  - numpy
  - scikit-learn
  - imbalanced-learn
  - tkinter (usually included with Python)

You can install pinned deps:
```bash
python -m pip install -r requirements.txt
```

## Dataset format
Provide a `dataset.csv` with at least these columns:
- `symptoms` — comma-separated symptom strings (e.g. "fever, cough")
- `disease` — target label (string)
- `cures` — brief recommended treatments (string)
- `doctor` — recommended specialist (string)
- `risk level` — risk description (string)

Notes:
- The app filters out diseases with fewer than 2 examples by default.
- Do not commit sensitive patient data. Add dataset filenames to `.gitignore`.

## Run
From the project directory:
```bash
python app.py
```

If you see ModuleNotFoundError for imblearn:
```bash
python -m pip install imbalanced-learn
```

## Troubleshooting
- Ensure the Python interpreter you run with `python` matches where dependencies are installed.
- If the GUI shows "Not enough data" after filtering, add more rows for underrepresented diseases.

## Contributing
- Add issues or pull requests. Keep datasets out of the repo.
- Add unit tests for preprocessing and model training where possible.
