# Air Quality Data Transformation & Statistical Modeling

## 📌 Project Overview
This project analyzes **NO₂ (Nitrogen Dioxide)** concentration data from an Indian air quality dataset. The objective is to:

1. Preprocess real-world air quality data  
2. Apply a **non-linear mathematical transformation**  
3. Estimate **statistical parameters** assuming a Gaussian (normal) distribution  
4. Present results using tables and visual interpretation  

The entire workflow is implemented in **Python** using `pandas` and `numpy`.

---

## 🧠 Methodology

### 1️⃣ Parameter Generation (Roll Number Based)
To ensure uniqueness and reproducibility, transformation parameters are derived from a roll number:

- **α (alpha)** – controls transformation amplitude  
- **β (beta)** – controls sinusoidal frequency  

This ensures personalization while preserving consistency.

---

### 2️⃣ Data Loading & Preprocessing
- Dataset: *India Air Quality Data*
- Encoding handled using `latin1`
- Corrupted rows skipped safely
- Column names normalized

The **NO₂ column** is detected in a case-insensitive manner and converted to numeric values. Invalid or missing entries are removed.

**Output:** Clean NO₂ dataset ready for analysis.

---

### 3️⃣ Non-Linear Transformation
Each valid NO₂ value `x` is transformed as:

\[
z = x + \alpha \cdot \sin(\beta x)
\]

#### Why this transformation?
- Introduces controlled non-linearity  
- Simulates environmental fluctuations  
- Preserves original data scale  

**Output:** New column `z` containing transformed values.

---

### 4️⃣ Statistical Modeling
The transformed variable `z` is modeled as a **Gaussian distribution**.

Estimated parameters:

| Parameter | Description |
|---------|------------|
| μ (Mean) | Central value |
| σ² (Variance) | Data spread |
| σ (Std. Dev.) | √Variance |
| λ (Lambda) | 1 / (2σ²) |
| c | 1 / (σ√2π) |

These are used in probability density estimation.

---

## 📊 Result Table (Sample)

| Index | x (NO₂) | z (Transformed) |
|------|--------|-----------------|
| 0 | 18.0 | 18.42 |
| 1 | 22.0 | 22.31 |
| 2 | 25.0 | 25.11 |
| 3 | 30.0 | 30.47 |
| 4 | 35.0 | 35.08 |

*Values shown are representative.*

---

## 📈 Result Graphs

### Histogram of `z`
- Shows frequency distribution
- Helps visually inspect normality

### Gaussian Curve Overlay
- Uses estimated μ and σ
- Evaluates goodness of fit

---

## 🧪 Observations
- Transformation adds smooth variability
- Mean shifts slightly with α and β
- Distribution remains approximately bell-shaped
- Gaussian modeling is reasonable

---

## 🛠️ Technologies Used
- Python 3  
- NumPy  
- Pandas  
- Matplotlib (for visualization)

---

## 🚀 How to Run
1. Clone the repository  
2. Install dependencies:
   ```bash
   pip install pandas numpy
