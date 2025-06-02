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

