# Ensemble CNN for Fashion-MNIST Classification

This project compares a single CNN model with a 5-model ensemble CNN trained on the Fashion-MNIST dataset. The ensemble is created using bootstrap sampling and probability averaging to improve prediction stability.

---

## Project Structure

```
fmnist-cnn-ensemble/
│
├── ensemble_cnn_fmnist.ipynb
├── README.md
└── requirements.txt
```

---

## Objectives

### 1. Load and Prepare the Data
- Load Fashion-MNIST dataset (Keras)
- Use the first **50 images**
- Normalize pixel values to **[0, 1]**
- Reshape to **(28, 28, 1)**
- Split into training and validation sets


### 2. Define the CNN Model

| Layer | Configuration |
|-------|--------------|
| Conv2D | 32 filters, 3×3, ReLU |
| MaxPooling2D | 2×2 |
| Flatten | — |
| Dense | 10 units, softmax |

Compiled using:

  ```text
  optimizer: Adam
  loss: sparse_categorical_crossentropy
  metrics: accuracy
  ```


### 3. Build the Ensemble
- Train **5** identical CNN models
- Each receives a **bootstrapped dataset**
- Train each for **3 epochs**


### 4. Evaluate the Ensemble
- Predict using all 5 models
- Average their probability outputs
- Choose final class with `argmax`
- Evaluate accuracy on validation and test sets


### 5. Compare With a Single CNN
- Train one standalone CNN
- Evaluate on validation and test sets
- Compare with ensemble accuracy

---

## Expected Outputs

| Model | Validation Accuracy | Test Accuracy |
|-------|----------------------|----------------|
| Single CNN | ✔ | ✔ |
| Ensemble CNN | ✔ | ✔ |

---

## How to Run

1. Clone the repo:

  ```bash
  git clone <repo-link>
  ```

2. Install dependencies:

  ```bash
  pip install -r requirements.txt
  ```

3. Launch notebook:

  ```bash
  jupyter notebook ensemble_cnn_fmnist.ipynb
  ```

---

## Notes
- Only **50 samples** are used, per assignment requirements
- Accuracy will be limited due to small dataset
- Main goal is to demonstrate **ensemble learning**

---

## License
MIT License — free for academic and personal use.

---

By Jairaj R
