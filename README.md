# Local Prediction (Quick Start)

This project includes a Jupyter notebook to run a local prediction using a pre-trained Keras `.h5` model on a sample image.

## Prerequisites
- Python 3.9–3.11 recommended
- macOS ARM users (Apple Silicon): TensorFlow is configured via `tensorflow-macos` and `tensorflow-metal` in `requirements.txt`.
- Model file: `Race Classification Model.h5` present in the repo root.

## Setup
1. Create and activate a virtual environment (recommended):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirements.txt
# If you don't have Jupyter installed:
pip install notebook
```

3. (Optional, macOS ARM) Verify TensorFlow uses Metal acceleration:

```bash
python -c "import tensorflow as tf; print(tf.__version__)"
```

## Run the Notebook
1. Launch Jupyter:

```bash
python -m ipykernel install --user --name=rc-local
jupyter notebook
```

2. Open `run_local_prediction.ipynb`.

3. In the first code cell, set the paths if needed. Defaults expect:
- `MODEL_PATH`: `"/Users/jeron/projects/Race-Classification/Race Classification Model.h5"` (update to this repo path if different)
- `TEST_IMAGE_PATH`: path to your image. To use the sample provided in this repo, set:

```python
MODEL_PATH = "/Users/jeron/projects/Race-Classification-1/Race Classification Model.h5"
TEST_IMAGE_PATH = "/Users/jeron/projects/Race-Classification-1/sample.jpg"
```

4. Run all cells (Kernel → Restart & Run All). You should see:
- TensorFlow version and existence checks
- Model summary
- Predicted class and probabilities
- Visualization of the input image with predicted label

## Optional: YOLOv8 Detection First
If you also want to detect people/faces before classification, ensure `ultralytics` and `opencv-python` are installed (already in `requirements.txt`). The last notebook section runs YOLOv8 and classifies crops.

## Troubleshooting
- If you see `ModuleNotFoundError: No module named 'numpy'`, ensure the virtual environment is activated and `pip install -r requirements.txt` was successful.
- If TensorFlow fails to import on Apple Silicon, ensure you are using Python 3.9–3.11 and the `tensorflow-macos`/`tensorflow-metal` wheels are installed via the provided `requirements.txt`.
- If the model file path is wrong, update `MODEL_PATH` to point to `Race Classification Model.h5` in this repo.
