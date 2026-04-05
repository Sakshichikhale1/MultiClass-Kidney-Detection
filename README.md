# Kidney CT Scan Classification – Multiple Models

## Overview

This project classifies **kidney CT scans** into four categories: **Normal, Cyst, Tumor, and Stone**.
It contains **four separate models**, each with a different architecture and evaluation metrics:

1. **Baseline CNN** – simple convolutional network.
2. **Kidney_CNN** – improved CNN with more layers/filters.
3. **DenseNet + Grad-CAM** – DenseNet121-based model with explainability using Grad-CAM.
4. **LightNet** – custom lightweight CNN optimized for this dataset.

---

## Dataset

* **Source:** [Kaggle CT Kidney Dataset](https://www.kaggle.com/datasets/nazmul0087/ct-kidney-dataset-normal-cyst-tumor-and-stone)
* **Total Images:** 12,446 JPG
* **Classes:** Normal, Cyst, Tumor, Stone
* **Folder Structure:**

```text
ct_kidney/
├── Normal/
├── Cyst/
├── Tumor/
└── Stone/
```

---

## Project Structure

```text
project/
├── notebooks/
│   ├── Baseline_CNN.ipynb
│   ├── KIDNEY_CNN.ipynb
│   ├── DENSENET+GRADCAM.ipynb
│   └── LightNet.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

---

## Dependencies

* Python 3.x
* TensorFlow / Keras
* NumPy, Pandas
* Scikit-learn
* Matplotlib

Install all dependencies with:

```bash
pip install -r requirements.txt
```

---

## Workflow

### 1. Data Preparation

* Images loaded using `glob`.
* Labels extracted from folder names.
* Labels encoded with `LabelEncoder`.
* Split dataset: **Train / Validation / Test** (approx. 72% / 8% / 20%), stratified by class.

### 2. Data Augmentation

* Rotation, zoom, width/height shift, horizontal flip
* Rescaling to [0,1]

### 3. Models & Architectures

| Model File            | Architecture / Notes                                 | Test Accuracy |
| --------------------- | ---------------------------------------------------- | ------------- |
| `baseline_cnn.py`     | Simple CNN (3 conv blocks + dense layers)            | 99.96%        |
| `kidney_cnn.py`       | Improved CNN (more filters, batch norm, dropout)     | 89.44%        |
| `densenet_gradcam.py` | DenseNet121 + Grad-CAM explainability                | 93.13%        |
| `lightnet.py`         | Lightweight custom CNN (4 conv blocks + GAP + dense) | 94.94%        |


---

## Training

* **Optimizer:** Adam (lr=0.001)
* **Loss:** Categorical Crossentropy
* **Batch size:** 16
* **Epochs:** 10 (or as per file)
* **Callbacks:** EarlyStopping, ReduceLROnPlateau

---

## Evaluation

For each model:

1. **Test Accuracy**
2. **Confusion Matrix** – correct vs misclassified samples
3. **ROC Curves** – one per class
4. **Sample Predictions** – visualization of True vs Predicted labels
5. **Training Curves** – Accuracy & Loss over epochs

---

## Comparison of Models

| Model               | Accuracy     | Observations                                                      |
| ------------------- | ------------ | ----------------------------------------------------------------- |
| Baseline CNN        | 99.96 %      | Simple architecture, may overfit or underperform on complex cases |
| Kidney_CNN          | 89.44 %      | Improved accuracy due to deeper network and augmentation          |
| DenseNet + Grad-CAM |93.13 %       | High accuracy + explainability using Grad-CAM heatmaps            |
| LightNet            | 94.94%       | Lightweight, fast training, good generalization                   |

---

## Improvements & Next Steps

* Use Grad-CAM on all CNNs for interpretability.
* Try pre-trained models with fine-tuning.
* Expand dataset via augmentation or synthetic images.
* Evaluate on external CT scans for better generalization.
* Experiment with hyperparameters (learning rate, batch size, epochs).

---

## Usage

1. Clone the repository.
2. Place the dataset in `ct_kidney/`.
3. Run any model file to train or evaluate:

```bash
python baseline_cnn.py
```


## References

* [CT Kidney Dataset – Kaggle](https://www.kaggle.com/datasets/nazmul0087/ct-kidney-dataset-normal-cyst-tumor-and-stone)
* TensorFlow/Keras Documentation: [https://www.tensorflow.org/](https://www.tensorflow.org/)

---
## 👩‍💻 Author

**Sakshi Chikhale**

⭐ If you like this project, give it a star on GitHub!

---


