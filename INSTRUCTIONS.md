# Reproduction & Environment Setup Guide

This guide provides step-by-step instructions for setting up the environment, installing the required packages, and running the `alzheimers_two_models.ipynb` notebook.

---

## 1. Prerequisites
* **Operating System**: Linux, macOS, or Windows (WSL2 recommended for Windows).
* **Python Version**: Python `3.10` or higher (tested on `3.10.20`).
* **Hardware**: CPU (multi-core recommended; tested on 12 cores) or NVIDIA GPU with CUDA drivers.

---

## 2. Environment Setup Options

Choose **Method A** (if using Conda/Miniconda) or **Method B** (if using standard Python `venv`).

### Method A: Setup Using Conda (Recommended)

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/bam841/Brain_demented-NonDementedIdentifier.git
   cd Brain_demented-NonDementedIdentifier
   ```

2. **Create the Conda Environment**:
   ```bash
   conda env create -f environment.yml
   ```

3. **Activate the Environment**:
   ```bash
   conda activate brain_mri_env
   ```

4. **Register the Jupyter Kernel**:
   ```bash
   python -m ipykernel install --user --name brain_mri_env --display-name "Python (Brain MRI Env)"
   ```

---

### Method B: Setup Using Python `venv` and `pip`

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/bam841/Brain_demented-NonDementedIdentifier.git
   cd Brain_demented-NonDementedIdentifier
   ```

2. **Create and Activate a Virtual Environment**:
   * **On Linux / macOS**:
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```
   * **On Windows (Command Prompt / PowerShell)**:
     ```bash
     python -m venv venv
     .\venv\Scripts\activate
     ```

3. **Upgrade Pip and Install Dependencies**:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Register the Jupyter Kernel**:
   ```bash
   python -m ipykernel install --user --name venv_brain_mri --display-name "Python (Brain MRI venv)"
   ```

---

## 3. Package Version Reference

The pipeline was developed and verified using the following package specifications:

| Package | Minimum Version | Tested Version | Purpose |
| :--- | :---: | :---: | :--- |
| **Python** | `>= 3.10` | `3.10.20` | Runtime environment |
| **TensorFlow** | `>= 2.15.0` | `2.21.0` | Deep learning models (CNN & MobileNetV2) |
| **Scikit-Learn** | `>= 1.3.0` | `1.7.2` | Clinical evaluation metrics & cross-validation |
| **NumPy** | `>= 1.24.0` | `2.2.6` | Numerical tensor operations |
| **Pandas** | `>= 2.0.0` | `2.3.3` | Dataset indexing & experiment tracking |
| **Pillow (PIL)** | `>= 10.0.0` | `12.3.0` | Image loading, integrity audits & flipping |
| **OpenCV** | `>= 4.8.0` | `4.11.0` | Canny edge detection & morphological filters |
| **Matplotlib** | `>= 3.8.0` | `3.10.9` | Visual EDA, confusion matrices & ROC plots |
| **Seaborn** | `>= 0.13.0` | `0.13.2` | Statistical data visualizations |
| **Jupyter / ipykernel**| `>= 1.0.0` | `8.37.0` | Interactive notebook execution |

---

## 4. Running the Notebook

1. **Launch Jupyter Notebook / Lab**:
   ```bash
   jupyter notebook alzheimers_two_models.ipynb
   ```
   *Or open the folder directly in **VS Code** with the Python / Jupyter extension enabled.*

2. **Select the Kernel**:
   * In the top-right corner of Jupyter / VS Code, ensure the kernel is set to **`Python (Brain MRI Env)`** or your active virtual environment.

3. **Execute the Cells**:
   * All figures, metrics, and models are **already pre-executed and visible** upon opening.
   * To re-run from scratch, click **Kernel $\to$ Restart & Run All**.

---

## 5. Dataset Structure

The repository includes the organized binary MRI dataset under `Alzheimer_Binary/`:
```
Alzheimer_Binary/
├── train/              # Expanded training dataset (8,870 images)
│   ├── Non_Demented/   # 4,480 images (2,240 original + 2,240 flipped)
│   └── Demented/       # 4,390 images (2,195 original + 2,195 flipped)
├── val/                # Untouched validation set (950 images - Zero Leakage)
│   ├── Non_Demented/   # 480 images
│   └── Demented/       # 470 images
└── test/               # Untouched test set (951 images - Zero Leakage)
    ├── Non_Demented/   # 480 images
    └── Demented/       # 471 images
```

---

## 6. Troubleshooting & FAQs

* **TensorFlow oneDNN / CPU notices**:
  * If you see messages such as `oneDNN custom operations are on`, these are standard informational optimizations indicating TensorFlow is utilizing multi-threaded CPU SIMD instructions (AVX2/FMA).
* **Missing CUDA Drivers**:
  * The entire notebook is designed to run efficiently on standard CPUs (average training time: ~3–4 minutes). A dedicated GPU is not required.
* **ModuleNotFoundError**:
  * If an import error occurs, verify that Jupyter is using the newly created kernel (`Python (Brain MRI Env)`), not the default system Python.
