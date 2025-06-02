# NHS-GP-Analysis
 A data analysis project exploring NHS GP workloads by region
# NHS GP Distribution Analysis (April 2024)

This project analyzes the regional distribution of General Practitioners (GPs) across NHS regions in England using April 2024 data. The goal is to understand service pressure based on the average number of patients served by each GP practice.

---

## 📌 Project Goals

- Visualize the number of GP practices in each NHS region
- Calculate the average number of registered patients per GP
- Identify regional disparities in GP service capacity

---

## 📁 Dataset

- **Source**: NHS GP Practice Data, April 2024
- **File Used**: `april_2024_attendances.csv`

| Column Name          | Description                                  |
|----------------------|----------------------------------------------|
| `region`             | NHS region name                              |
| `practice_code`      | Unique GP practice code                      |
| `registered_patients`| Number of patients registered at each practice |

---

## 🧪 Data Processing (Power BI)

- Removed rows with missing `region`, `practice_code`, or `registered_patients`
- Aggregated data per region:
  - Total GP practices: `DISTINCTCOUNT(practice_code)`
  - Total patients: `SUM(registered_patients)`
- Created a measure to calculate patient load per GP:

```dax
Patients_per_GP = 
DIVIDE(
    SUM('april_2024_attendances'[registered_patients]),
    DISTINCTCOUNT('april_2024_attendances'[practice_code])
)
📊 Visualizations
1. GP Count by Region
Bar chart showing the number of GP practices in each region.


2. Patients per GP by Region
Bar chart showing the average number of registered patients per GP.


3. Regional Comparison Table (Colored)
Table with conditional formatting to highlight regions with the highest patient load per GP.


📈 Key Findings
North East and Yorkshire has the highest GP workload (~10,182 patients per GP), indicating possible strain.

Midlands follows closely with ~10,084 patients per GP.

North West has relatively lower GP load (~7,243 patients per GP), suggesting more balanced care capacity.

💡 Future Improvements
Add time series analysis (multi-month data)

Compare with A&E wait times and other NHS KPIs

Build interactive dashboards with slicers and filters

📎 Files
april_2024_attendances.csv: NHS data file

NHS_GP_Distribution_Report.pbix: Power BI project file

/images/: Screenshots of visualizations

🙋‍♀️ Author
Made by Xin Wang – aspiring NHS data analyst
