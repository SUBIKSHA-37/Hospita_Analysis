📌 Project Overview

Hospitals generate large volumes of patient data every day, but this data is rarely turned into decisions. This project takes a raw hospital patient dataset and turns it into actionable insight — cleaning it, exploring it statistically, and packaging the findings into an interactive Power BI dashboard that a hospital administrator could actually use.

Business problem it addresses:


Which patient conditions drive the highest treatment costs?
Which conditions have the highest readmission risk?
Does cost or age affect patient satisfaction?
Are there demographic cost or outcome disparities worth investigating?



🧩 Business Problem

A hospital's leadership team wants to understand where its money is going, which patients are most at risk of returning, and whether patients are satisfied with care — without manually digging through spreadsheets. This project builds the analytics layer that answers those questions in one dashboard.


🔄 Project Workflow

Raw CSV Data
     │
     ▼
Data Quality Assessment (nulls, duplicates, dtypes)
     │
     ▼
Statistical Analysis (mean, median, std, skew, kurtosis)
     │
     ▼
Outlier Detection (IQR method, boxplots)
     │
     ▼
Univariate & Bivariate EDA (matplotlib / seaborn)
     │
     ▼
Correlation Analysis
     │
     ▼
GroupBy Business Analysis (cost by gender, condition, outcome)
     │
     ▼
Feature Engineering (Age_Group bucketing)
     │
     ▼
Cleaned Dataset Export (cleaned_data.csv)
     │
     ▼
Power BI Interactive Dashboard

🏗️ Architecture Diagram

┌──────────────┐     ┌───────────────────┐     ┌──────────────────┐     ┌────────────────┐
│  Raw Dataset  │ ──▶ │  Python / Pandas   │ ──▶ │  Cleaned Dataset  │ ──▶ │   Power BI      │
│  (.csv)       │     │  (Colab Notebook)  │     │  (.csv)           │     │   Dashboard     │
└──────────────┘     └───────────────────┘     └──────────────────┘     └────────────────┘
      │                       │                          │                       │
      ▼                       ▼                          ▼                       ▼
  Patient records      EDA, stats, outliers      Age_Group added,        Interactive filters,
  (984 rows)            correlation analysis      ready for BI            KPI cards, trends


📁 Folder Structure

Hospital-Patient-Data-Analysis/
│
├── data/
│   ├── raw/                  # Original unprocessed dataset
│   │   └── hospital_patient_data_raw.csv
│   └── processed/            # Cleaned, feature-engineered dataset
│       └── cleaned_data.csv
│
├── notebook/
│   └── Hospital_Patient_Data_Analysis.ipynb
│
├── dashboard/
│   └── Hospital_Dashboard.pbix
│
├── images/                   # Dashboard & chart screenshots
│
├── report/                   # Internship report (PDF/DOCX)
│
├── README.md
├── LICENSE
├── requirements.txt
└── .gitignore


📊 Dataset Information

AttributeDetailRecords984 patientsColumns11 (10 original + 1 engineered)Missing values0Duplicate rows0FormatCSV

Columns:

ColumnDescriptionPatient_IDUnique patient identifierAgePatient age in yearsGenderMale / FemaleConditionDiagnosed medical condition (15 categories)ProcedureTreatment/procedure administeredCostTreatment cost (₹)Length_of_StayDays admittedReadmissionWhether the patient was readmitted (Yes/No)OutcomeRecovered / StableSatisfactionPatient satisfaction score (1–5)Age_GroupEngineered bucket: Child, Young, Adult, Senior, Old


🛠️ Technology Stack

LayerToolsData Cleaning & AnalysisPython, Pandas, NumPyVisualization (EDA)Matplotlib, SeabornEnvironmentGoogle Colab / Jupyter NotebookBI DashboardMicrosoft Power BIVersion ControlGit & GitHub


⚙️ Installation Guide

Requirements


Python 3.9+
Power BI Desktop (Windows) to open the .pbix file


Setup

bash# Clone the repository
git clone https://github.com/SUBIKSHA-37/Hospital-Patient-Data-Analysis.git
cd Hospital-Patient-Data-Analysis

# Create a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

How to Run

Python workflow:

bashjupyter notebook notebook/Hospital_Patient_Data_Analysis.ipynb

Run all cells top to bottom. The notebook reads data/raw/hospital_patient_data_raw.csv, performs cleaning and EDA, and exports cleaned_data.csv.

Power BI workflow:


Open dashboard/Hospital_Dashboard.pbix in Power BI Desktop.
If prompted, point the data source to data/processed/cleaned_data.csv.
Refresh the data model.



📈 Dashboard Features


KPI cards for total patients, total treatment cost, average length of stay, and average satisfaction
Interactive filters by Gender, Condition, and Age Group
Cost breakdown by condition and procedure
Readmission rate analysis by condition
Outcome distribution (Recovered vs Stable)
Satisfaction trends across age groups



💡 Business Insights


Cost concentration: Cancer, Prostate Cancer, and Heart Attack cases are the most expensive conditions to treat, each averaging ₹18,000–₹25,000 per patient.
Readmission risk: Heart Attack and Heart Disease patients have the highest readmission rates by a wide margin compared to other conditions — a strong candidate for a targeted follow-up care program.
Satisfaction drivers: Patient satisfaction trends downward as age and treatment cost increase, suggesting older/high-cost patients may need more attentive post-treatment communication.
Gender cost gap: Average treatment cost for female patients is noticeably higher than for male patients in this dataset, worth investigating against the condition mix by gender.
Outcome vs satisfaction: Patients with a "Recovered" outcome report meaningfully higher satisfaction than those marked "Stable."


(All figures are derived directly from cleaned_data.csv.)


🖼️ Dashboard Screenshots

Add exported screenshots of your Power BI dashboard pages here, e.g.:

images/dashboard_overview.png
images/cost_analysis.png
images/readmission_analysis.png


🚀 Future Improvements


Migrate raw data ingestion into a SQL database (MySQL/PostgreSQL) instead of flat CSV
Build a proper ETL pipeline (Python + SQL) instead of a single notebook
Automate the pipeline with Apache Airflow
Containerize with Docker for reproducible environments
Add CI/CD via GitHub Actions (lint + notebook execution checks)
Deploy the Power BI dataset refresh via Power BI Service / Gateway
Add statistical hypothesis testing (e.g., t-test on cost by gender)
Publish the dashboard as a Power BI web-embedded report



👩‍💻 Author

Subiksha
Final-year B.Tech, Artificial Intelligence & Data Science
GitHub: github.com/SUBIKSHA-37

