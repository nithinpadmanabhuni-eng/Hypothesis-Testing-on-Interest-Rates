# Hypothesis-Testing-on-Interest-Rates

📊 Statistical Tests on US Interest Rates

This project performs statistical hypothesis testing on US interest rate data.
The dataset contains weekly observations of interest rates, and analysis is performed using:

Two-sample Z-Test (approximation)

Two-sample t-Test (Welch’s Test)

F-Test for Variance Comparison

The goal is to identify whether the mean and variance of the Federal Funds Rate have changed significantly between two different time periods.

📂 Dataset Description

The dataset used is an Excel file containing:

Column	Description
Date	Date of the observation
Value	Recorded interest rate

During preprocessing, the columns were renamed to:

DATE

FEDFUNDS

This dataset was uploaded manually into Google Colab and processed there.

🧹 Data Preprocessing

All cleaning steps were performed inside the Colab notebook, not manually.

✔ Steps performed:

Uploaded Excel file to Colab.

Loaded using pd.read_excel().

Removed automatically generated index columns (Unnamed: 0).

Renamed:

df = df.rename(columns={"Date": "DATE", "Value": "FEDFUNDS"})


Converted DATE to datetime:

df["DATE"] = pd.to_datetime(df["DATE"], errors="coerce")


Dropped rows where DATE or FEDFUNDS was missing.

Created a new YEAR column using:

df["YEAR"] = df["DATE"].dt.year


After cleaning, the dataset contained valid weekly interest rate observations suitable for statistical analysis.

🕒 Time Period Selection

To compare interest rate behavior over time, the data was divided into two periods:

Period 1: 2010–2014

Period 2: 2015–2019

Both periods contain sufficient observations for valid hypothesis testing.

🧪 Statistical Tests Conducted

All tests were implemented using Python (Pandas, NumPy, SciPy) inside Colab.

1️⃣ Two-Sample Z-Test (Approximation)

Since population standard deviation is unknown, the Z statistic was approximated using the two-sample t statistic (valid for moderate sample sizes).

Hypotheses

H₀: μ₁ = μ₂
(Mean FEDFUNDS does not differ between 2010–2014 and 2015–2019)

H₁: μ₁ ≠ μ₂
(Means are different)

2️⃣ Two-Sample t-Test (Welch’s Test)

Welch’s t-test was used because it does not assume equal variances.

Hypotheses

H₀: μ₁ = μ₂

H₁: μ₁ ≠ μ₂

3️⃣ F-Test for Equality of Variances

This test compares whether the volatility of the interest rate changed between the two periods.

Hypotheses

H₀: σ₁² = σ₂²
(Variances are equal)

H₁: σ₁² ≠ σ₂²
(Variances differ)

Formula
F = larger_variance / smaller_variance

🧮 Methodology Summary
✔ Load dataset
✔ Clean and rename columns
✔ Convert DATE column
✔ Extract two time-based samples
✔ Perform:

Z-Test

Welch t-Test

F-Test

✔ Print interpretation for all tests
✔ Optional graphs (line plot, boxplot)
📝 Conclusion (Template)

Based on the p-values:

Z-Test conclusion:
State whether we reject or fail to reject H₀ based on your p-value.

t-Test conclusion:
State whether the means differ significantly.

F-Test conclusion:
State whether the variance of interest rates changed between periods.

(Fill these in using your actual outputs from Colab.)

📁 Repository Structure
Hypothesis-Testing-on-Interest-Rates/
│
├── analysis.ipynb          # Colab notebook with full analysis
├── Us-Interest-Rate-Weekly.xlsx
└── README.md               # Project documentation

▶ How to Run (Colab)

Open Google Colab

Upload dataset (.xlsx)

Run cells step-by-step (loading → cleaning → splitting → tests → summary)

All code is included in the notebook.
