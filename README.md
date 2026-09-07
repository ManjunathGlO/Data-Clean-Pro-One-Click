# 🧹 DataClean Pro --- One-Click Data Cleaning & Quality Analyzer

> **Turn messy CSV and Excel files into cleaner, validated,
> analysis-ready datasets in one click.**

DataClean Pro is an interactive **Python, Pandas, NumPy, and Streamlit**
application that helps analysts assess dataset quality, apply repeatable
cleaning rules, validate common business conditions, analyze outliers,
compare data quality before and after cleaning, and export or save
cleaning runs for later review.

It is designed as a practical **Data Analyst portfolio project**
demonstrating an end-to-end data preparation workflow rather than a
collection of isolated Pandas operations.

------------------------------------------------------------------------

## 🎯 Why DataClean Pro?

Data analysis is only as reliable as the data behind it.

Real-world datasets frequently contain:

-   Missing values
-   Duplicate records
-   Inconsistent column names
-   Leading/trailing whitespace
-   Inconsistent missing-value indicators
-   Incorrect data types
-   Unstructured date fields
-   Numeric values stored as text
-   Invalid or inconsistent email values
-   Extreme numeric observations
-   Business-rule inconsistencies

Manually repeating these preparation steps for every dataset is
time-consuming and difficult to audit.

**DataClean Pro turns these repetitive tasks into a structured,
configurable, and reviewable workflow.**

### Business Value

**Reduce manual preparation → Improve consistency → Validate data
quality → Produce analysis-ready datasets**

------------------------------------------------------------------------

## 📸 Application Preview

Add your screenshots to an `assets/` folder and use them here:

  ------------------------------------------------------------------------------
  Dashboard                            Cleaning Controls
  ------------------------------------ -----------------------------------------
  ![Dashboard](assets/dashboard.png)   ![Cleaning
                                       Controls](assets/cleaning-controls.png)

  ------------------------------------------------------------------------------

  Outlier Analysis                   Cleaning History
  ---------------------------------- --------------------------------
  ![Outliers](assets/outliers.png)   ![History](assets/history.png)

### Recommended screenshots

For the strongest GitHub presentation, capture:

1.  Main dashboard in your preferred theme
2.  Sidebar with **Cleaning Controls**
3.  Before/after quality results
4.  Cleaning Audit Log
5.  Outlier Analysis
6.  **History** tab showing saved runs

------------------------------------------------------------------------

## 🚀 Key Features

### 📊 1. Data Quality Dashboard

The application provides an immediate overview of dataset health,
including:

-   Row count
-   Column count
-   Missing-cell count
-   Duplicate-row count
-   Missing-data percentage
-   Duplicate percentage
-   Overall data-quality score
-   Quality classification

This gives the analyst a quick baseline before making transformations.

------------------------------------------------------------------------

### 🧹 2. One-Click Data Cleaning

Run the cleaning workflow from a single action:

> **🧹 CLEAN MY DATA**

The pipeline can perform:

-   Blank-row removal
-   Blank-column removal
-   Column-name standardization
-   Text trimming
-   Missing-value-token standardization
-   Numeric-column conversion
-   Date-column conversion
-   Duplicate-row removal
-   Missing-value handling
-   Business-value standardization
-   Customer-name normalization
-   Email normalization and validation
-   Business-rule validation
-   IQR-based outlier detection
-   Optional numeric outlier capping

------------------------------------------------------------------------

### ⚙️ 3. Cleaning Controls

The sidebar lets the analyst configure the cleaning process instead of
forcing one fixed strategy.

#### Missing-value strategy

Available approaches include:

-   Leave missing values unchanged
-   Median imputation for numeric fields + mode for categorical fields
-   Zero for numeric fields + `"Unknown"` for text fields
-   Drop rows containing missing values

#### Outlier treatment

Optional **IQR-based outlier capping** can be enabled for eligible
numeric columns.

Identifier-like columns are protected from inappropriate outlier
treatment.

------------------------------------------------------------------------

### 🔎 4. Data Validation

DataClean Pro includes validation checks for common data-quality and
business conditions, including:

-   Invalid numeric values
-   Quantity validation
-   Unit-price validation
-   Sales validation
-   Email validation
-   Data-type conversion
-   Sales consistency

For datasets containing:

``` text
Quantity
Unit_Price
Sales
```

the application can compare:

``` text
Expected Sales = Quantity × Unit Price
```

A tolerance is used rather than requiring exact equality.

> **Note:** Validation findings are reported separately from the
> simplified overall quality score.

------------------------------------------------------------------------

### 📉 5. Outlier Analysis

Numeric columns can be analyzed using the **Interquartile Range (IQR)**
method.

The application identifies:

-   Q1
-   Q3
-   IQR
-   Lower bound
-   Upper bound
-   Outlier count
-   Outlier percentage

When enabled, eligible extreme values can be capped at IQR-based
boundaries.

Outliers are treated as **potentially unusual observations**, not
automatically as incorrect data.

------------------------------------------------------------------------

### 📈 6. Before vs. After Quality Assessment

One of the core principles of the application is to make the impact of
cleaning visible.

Example:

``` text
                    BEFORE        AFTER
Rows                  10,000        9,845
Missing Cells            820          120
Duplicates               155            0
Quality Score            84.2         97.6
```

This makes the transformation easier to review and communicate.

------------------------------------------------------------------------

### 📝 7. Cleaning Audit Log

Major transformations are summarized in a cleaning log.

Example:

``` text
Blank rows removed
Blank columns removed
Text cells trimmed
Missing-value tokens standardized
Columns converted to numeric
Columns converted to dates
Duplicate rows removed
Outliers detected
Outliers capped
Validation checks completed
```

The audit log provides transparency into what happened during the
cleaning process.

------------------------------------------------------------------------

### 📋 8. Column-Level Profiling

The **Column Profile** view provides information such as:

  Metric      Description
  ----------- ---------------------------
  Column      Dataset field
  Data Type   Detected Pandas data type
  Non-Null    Populated records
  Missing     Missing records
  Missing %   Percentage missing
  Unique      Distinct values

This helps identify problematic fields before and after transformation.

------------------------------------------------------------------------

### 📥 9. Export

After cleaning, users can export the resulting dataset as:

-   **CSV**
-   **Excel**

The Excel output can include supporting quality information such as
cleaning logs, profiling information, and outlier analysis.

------------------------------------------------------------------------

### 🕘 10. Persistent Cleaning History

DataClean Pro can save completed cleaning runs locally so they can be
reviewed later.

Use:

> **💾 SAVE THIS RUN TO HISTORY**

Saved runs can contain:

-   Dataset name
-   Timestamp
-   Cleaning run ID
-   Original dataset
-   Cleaned dataset
-   Rows before/after
-   Quality before/after
-   Missing values before/after
-   Duplicate rows before/after

The **🕘 History** tab allows users to:

-   Review previous runs
-   Inspect saved cleaned datasets
-   Download saved cleaned data
-   Download original data
-   Delete a saved history record

History metadata is stored locally using **SQLite**, with the associated
datasets stored under the project's history directory.

------------------------------------------------------------------------

# 🏗️ Application Workflow

``` text
┌──────────────────────┐
│   Upload CSV / Excel │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Profile Dataset    │
│   Assess Quality     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Configure Controls   │
│ Missing Values       │
│ Outlier Treatment    │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   One-Click Clean    │
│ Standardize / Convert │
│ Deduplicate / Impute │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│      Validate        │
│ Business Rules       │
│ Emails / Numeric     │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Analyze Outliers   │
│   Review Audit Log   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Compare Before/After │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Export / Save History│
└──────────────────────┘
```

------------------------------------------------------------------------

# 🧠 Data Quality Score

The current application uses a **simplified diagnostic quality score**
based primarily on missing-data and duplicate-record rates.

Conceptually:

``` text
Quality Score
= 100
− Missing Data Impact
− Duplicate Data Impact
```

The score is bounded between:

``` text
0 ───────────────────────────── 100
Poor                         Excellent
```

### Quality classification

       Score Status
  ---------- --------------------
     90--100 🟢 Excellent
    75--89.9 🟡 Good
    50--74.9 🟠 Needs Attention
       \< 50 🔴 Poor

> **Important:** The score is a quick diagnostic indicator. Validation
> findings, email issues, business-rule issues, and outliers are
> surfaced separately and are not fully represented by this simplified
> formula.

A production implementation could expand the score to include
completeness, validity, consistency, uniqueness, timeliness, and
business-rule compliance.

------------------------------------------------------------------------

# 💼 Business Use Cases

DataClean Pro can support data preparation for:

### Sales Analytics

Prepare transaction data for:

-   Revenue analysis
-   Sales performance reporting
-   Customer analysis
-   Forecasting

### E-commerce Analytics

Prepare:

-   Order data
-   Customer data
-   Product data
-   Transaction data

### Marketing Analytics

Prepare datasets for:

-   Campaign analysis
-   Conversion analysis
-   Customer segmentation
-   ROI reporting

### Operations Analytics

Prepare data for:

-   KPI reporting
-   Trend analysis
-   Performance monitoring
-   Operational dashboards

### Business Intelligence

Prepare source data before loading it into:

-   Power BI
-   Tableau
-   Excel
-   SQL workflows
-   Python analytics pipelines

------------------------------------------------------------------------

# 🧪 Example Dataset

A useful portfolio demonstration dataset contains fields such as:

``` text
Customer_Name
Email
Gender
City
Category
Product
Quantity
Unit_Price
Sales
Order_Date
```

Example data-quality issues:

``` text
" male "
"MALE"
"Male"

" bangalore "
"BANGALORE"
"Bengaluru"

Missing email
Invalid email
Duplicate record
Numeric value stored as text
Inconsistent date format
Extreme sales value
Sales calculation mismatch
```

This deliberately messy dataset demonstrates why automated profiling and
cleaning are useful.

------------------------------------------------------------------------

# 🛠️ Technology Stack

  Technology                Purpose
  ------------------------- --------------------------------------------
  **Python**                Application and data-processing logic
  **Pandas**                Data manipulation and transformation
  **NumPy**                 Numerical processing
  **Streamlit**             Interactive application UI
  **OpenPyXL**              Excel generation
  **SQLite**                Persistent local cleaning-history metadata
  **Regular Expressions**   Text and email normalization/validation

------------------------------------------------------------------------

# 📁 Recommended Repository Structure

``` text
Data-Clean-Pro-One-Click/
│
├── app.py
├── README.md
├── requirements.txt
├── .gitignore
│
├── assets/
│   ├── dashboard.png
│   ├── cleaning-controls.png
│   ├── outliers.png
│   └── history.png
│
├── sample_data/
│   └── messy_ecommerce.csv
│
└── data/
    └── history/
        └── .gitkeep
```

### `.gitignore`

Do not commit uploaded datasets or local cleaning history.

Recommended:

``` gitignore
__pycache__/
*.py[cod]

.venv/
venv/
.env

.streamlit/secrets.toml

data/history/*
!data/history/.gitkeep
```

For a public portfolio repository, use synthetic or anonymized sample
data.

------------------------------------------------------------------------

# 🚀 Installation

## 1. Clone the repository

``` bash
git clone https://github.com/YOUR-USERNAME/Data-Clean-Pro-One-Click.git
cd Data-Clean-Pro-One-Click
```

Replace `YOUR-USERNAME` with your GitHub username.

## 2. Create a virtual environment

### Windows

``` bash
python -m venv .venv
.venv\Scripts\activate
```

### macOS / Linux

``` bash
python3 -m venv .venv
source .venv/bin/activate
```

## 3. Install dependencies

``` bash
python -m pip install -r requirements.txt
```

Example `requirements.txt`:

``` text
numpy
openpyxl
pandas
streamlit
```

## 4. Run the application

``` bash
python -m streamlit run app.py
```

Then open the local Streamlit address shown in your terminal, normally:

``` text
http://localhost:8501
```

------------------------------------------------------------------------

# 🖥️ How to Use

### Step 1 --- Upload

Upload a:

``` text
.csv
.xlsx
.xls
```

file.

### Step 2 --- Analyze

Review:

-   Dataset size
-   Missing values
-   Duplicate records
-   Quality score
-   Column profile
-   Data types

### Step 3 --- Configure

Use **Cleaning Controls** in the sidebar.

Select the missing-value strategy and decide whether to enable outlier
capping.

### Step 4 --- Clean

Open:

> **🧹 Clean & Validate**

Then select:

> **🧹 CLEAN MY DATA**

### Step 5 --- Review

Inspect:

-   Before/after metrics
-   Quality score
-   Cleaning audit log
-   Cleaned dataset
-   Validation findings

Then review:

> **🔎 Outliers**

and:

> **📋 Column Profile**

### Step 6 --- Export

Open:

> **📥 Export**

Download the cleaned CSV or Excel report.

### Step 7 --- Save

If you want to preserve the cleaning run:

> **💾 SAVE THIS RUN TO HISTORY**

### Step 8 --- Revisit

Open:

> **🕘 History**

Select a previous run to inspect or download it.

------------------------------------------------------------------------

# 🧠 Analytical Design Decisions

## Missing Values

Different fields may require different treatment.

For example:

``` text
Numeric measure      → Median
Categorical field    → Mode
Unknown category     → "Unknown"
Critical record      → Analyst review
```

The application therefore provides configurable strategies instead of
assuming that one method is correct for every dataset.

## Outliers

An extreme value is not automatically an error.

For example:

``` text
₹10,000
₹12,000
₹15,000
₹18,000
₹500,000
```

The ₹500,000 transaction could represent:

-   A data-entry error
-   A legitimate enterprise transaction
-   A special business event

Therefore, automated outlier capping should be treated as a
**data-preparation technique**, not proof that an observation is
incorrect.

------------------------------------------------------------------------

# 🔐 Data & Privacy

DataClean Pro is designed to operate locally.

Saved History runs are stored under:

``` text
data/history/
```

For a public GitHub repository:

-   Do not commit confidential company data.
-   Do not commit personal datasets.
-   Do not commit credentials or secrets.
-   Use synthetic or anonymized sample data.
-   Keep local history out of Git tracking.

------------------------------------------------------------------------

# 📌 Skills Demonstrated

### Data Analytics

-   Data profiling
-   Data cleaning
-   Missing-value analysis
-   Duplicate detection
-   Outlier analysis
-   Data validation
-   Quality assessment

### Python

-   Pandas
-   NumPy
-   Data transformation
-   File processing
-   Regular expressions
-   SQLite persistence
-   Error handling

### Analytics Engineering

-   Repeatable transformations
-   Validation workflows
-   Auditability
-   Analysis-ready outputs
-   Before/after measurement

### Application Development

-   Streamlit
-   Interactive controls
-   File upload/download
-   Session-state workflows
-   Persistent history
-   CSV/Excel reporting

------------------------------------------------------------------------

# 📈 What This Project Demonstrates

DataClean Pro demonstrates the following analytical workflow:

``` text
PROFILE
   ↓
DIAGNOSE
   ↓
CLEAN
   ↓
VALIDATE
   ↓
MEASURE
   ↓
REVIEW
   ↓
EXPORT
```

The goal is not simply to remove "bad" rows.

The goal is to make data quality **visible, repeatable, reviewable, and
easier to trust** before downstream analysis.

------------------------------------------------------------------------

# ⚠️ Limitations

DataClean Pro is a general-purpose portfolio application.

It does not automatically determine:

-   Whether an outlier is a genuine business event
-   Whether a missing value should logically be imputed
-   Whether a record is factually accurate
-   Complex domain-specific business rules
-   Referential integrity across multiple tables
-   Accuracy against an external source of truth

These decisions still require **business context and analyst judgment**.

------------------------------------------------------------------------

# 🔮 Future Enhancements

Potential production-level improvements include:

-   [ ] Configurable quality-score dimensions and weights
-   [ ] Advanced anomaly detection
-   [ ] Custom business-rule configuration
-   [ ] Data-quality trend analysis across saved runs
-   [ ] Dataset version comparison
-   [ ] SQL database connectors
-   [ ] Power BI integration
-   [ ] Multi-file batch processing
-   [ ] Custom cleaning pipelines
-   [ ] Data lineage tracking
-   [ ] Automated PDF quality reports
-   [ ] Cloud deployment
-   [ ] Authentication and user management

------------------------------------------------------------------------

# 💼 Resume Project Description

**DataClean Pro --- One-Click Data Cleaning & Quality Analyzer**

> Developed a Python/Streamlit application that automates CSV/Excel data
> profiling and preparation, including missing-value handling, duplicate
> detection, data-type conversion, text normalization, email validation,
> business-rule checks, and IQR-based outlier treatment. Implemented
> before/after quality assessment, cleaning audit logs, CSV/Excel
> export, and persistent cleaning-history tracking for repeatable
> data-quality workflows.

------------------------------------------------------------------------

# 👨‍💻 Author

**Manjunath G L**

**Data Analyst**

**Python • SQL • Excel • Power BI • Tableau • Statistics • Data
Visualization • Business Intelligence**

------------------------------------------------------------------------

## ⭐ If You Find This Project Useful

If DataClean Pro helps you understand automated data cleaning and
data-quality workflows, consider giving the repository a ⭐.

------------------------------------------------------------------------

## 📄 License

This project is available for educational and portfolio purposes.
