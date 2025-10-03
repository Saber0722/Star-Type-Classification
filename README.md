# Star Type Classification: Integrating AI/ML with Astrophysics

## Overview

This repository contains a beginner-friendly project that combines machine learning (ML) with astrophysics to classify stars into six types based on physical properties. The project uses a small, clean dataset to demonstrate exploratory data analysis (EDA), data preprocessing, and model training/evaluation. It serves as an introduction to astronomical datasets and how features like temperature and luminosity align with stellar physics concepts, such as the Hertzsprung-Russell (HR) diagram.

Key features:
- **EDA**: Visualizations including histograms, pairplots, correlation heatmaps, and the HR diagram to understand data distributions and relationships.
- **Preprocessing**: Handling skewness with log-transforms, encoding categorical features (e.g., spectral class), and scaling.
- **Models**: Four classifiers—Decision Tree (DT), Random Forest (RF), Support Vector Machine (SVM), and Multi-Layer Perceptron (MLP)—evaluated with test accuracy and 5-fold cross-validation (CV).
- **Results**: High accuracies due to the dataset's separability, with RF achieving perfect scores.

## Dataset Description

The dataset is sourced from [Kaggle: Star Dataset](https://www.kaggle.com/datasets/deepu1109/star-dataset) and contains 240 rows (one per star) with 7 columns. It's a tabular CSV file (`6 class csv.csv`) representing synthetic or observed stellar properties, balanced with 40 samples per class.

### Key Columns and Meanings:
- **Temperature (K)**: Surface temperature in Kelvin (ranges ~3,000–40,000 K; hotter stars are bluer and often more massive).
- **Luminosity (L/Lo)**: Brightness relative to the Sun (ranges 0.0001–800,000; skewed toward extremes for giants).
- **Radius (R/Ro)**: Size relative to the Sun (ranges 0.01–2,000; giants and hypergiants dominate high values).
- **Absolute Magnitude (Mv)**: Intrinsic brightness (ranges -10 to +20; lower values = brighter; negative for giants).
- **Star Color**: Categorical (e.g., "Red", "Blue", "Blue White"; derived from temperature; cleaned for inconsistencies like "Blue-white").
- **Spectral Class**: Categorical (O, B, A, F, G, K, M; ordinal from hottest/O to coolest/M; key for classification).
- **Star Type**: Target label (0: Brown Dwarf, 1: Red Dwarf, 2: White Dwarf, 3: Main Sequence, 4: Supergiant, 5: Hypergiant).

### Insights from Dataset:
- **Size and Quality**: Small (240 rows), no missing values, balanced classes—ideal for beginners.
- **Physics Ties**: Features reflect stellar evolution; e.g., hot, luminous stars cluster as supergiants, cool dim ones as dwarfs.
- **Download**: The EDA notebook automatically downloads it via `kagglehub` into a subfolder (`star-dataset`).

## Directory Structure

The repository follows a simple structure with all files in the root directory. After running EDA.ipynb, a new folder (`star-dataset`) is created for the downloaded data.

```
Star_Classification/
├── .gitignore          # Ignores venv, __pycache__, etc.
├── EDA.ipynb           # Exploratory Data Analysis and dataset download
├── data_prep.ipynb     # Data preprocessing (transforms, encoding, scaling)
├── train.ipynb         # Model training, evaluation, and CV
├── requirements.txt    # Python dependencies
├── LICENSE             # MIT License
└── README.md           # This file

# After running EDA.ipynb:
└── star-dataset/       # Downloaded folder containing 6 class csv.csv
```

## Installation

To run this project, use a Python virtual environment (venv) to isolate dependencies. Python 3.8+ is recommended.

### Step 1: Clone the Repository
```bash
git clone https://github.com/Saber0722/Star_Classification.git
cd Star_Classification
```

### Step 2: Set Up Virtual Environment
Create and activate a venv:
```bash
# On Windows:
python -m venv venv
venv\Scripts\activate

# On macOS/Linux:
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies
Install required packages from `requirements.txt`:
```bash
pip install -r requirements.txt
```
Dependencies include: pandas, numpy, matplotlib, seaborn, scikit-learn, kagglehub.

## Usage

Run the notebooks in sequence using Jupyter (install if needed: `pip install jupyter`). Each builds on the previous.

1. **EDA.ipynb**: Run this first. The initial cell downloads the dataset via `kagglehub` to `./star-dataset/`. It performs data inspection, visualizations (e.g., HR diagram, pairplots), and basic cleaning. Outputs: Understanding of dataset structure and physics insights.
   ```bash
   jupyter notebook EDA.ipynb
   ```

2. **data_prep.ipynb**: Loads the downloaded data, encodes categoricals (star color, spectral class), and scales numericals. Outputs: Prepared train/test splits.
   ```bash
   jupyter notebook data_prep.ipynb
   ```

3. **train.ipynb**: Trains and evaluates models on prepared data. Includes test accuracies, confusion matrices, and 5-fold CV. Outputs: Model performance metrics.
   ```bash
   jupyter notebook train.ipynb
   ```
   
For an interactive version with embedded visualizations and detailed write-ups, check out the [Kaggle Notebook](https://www.kaggle.com/code/aakashchilakamarri/star-type-classification).

Run all cells in each notebook sequentially. Total runtime: <1 minute on a standard machine.

## Results

Models were evaluated on an 80/20 train-test split (192/48 samples) and 5-fold CV for robustness.

- **Decision Tree (DT)**:
  - Test Accuracy: 1.00
  - CV Accuracy: 0.99 (±0.02)

- **Random Forest (RF)**:
  - Test Accuracy: 1.00
  - CV Accuracy: 0.99 (±0.02)

- **Support Vector Machine (SVM)**:
  - Test Accuracy: 0.98
  - CV Accuracy: 0.96 (±0.05)

- **Multi-Layer Perceptron (MLP)**:
  - Test Accuracy: 0.98
  - CV Accuracy: 0.99 (±0.02) (with convergence warnings addressed via increased iterations)

RF performed best overall, achieving perfect classification due to ensemble handling of feature interactions. Minor errors (e.g., Main Sequence misclassified as Red Dwarf) reflect physical overlaps in cool stars.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Dataset: Deepu1109 on Kaggle.
- Inspired by astrophysics resources like the Hertzsprung-Russell diagram.
- Built with scikit-learn and seaborn for ML and visualizations.

For questions or collaborations, open an issue or contact via GitHub. Last updated: September 14, 2025.
