# NHS-GP-Analysis
 A data analysis project exploring NHS GP workloads by region
# NHS GP Distribution Analysis (April 2024)

This project analyzes the regional distribution of General Practitioners (GPs) across NHS regions in England and evaluates service pressure based on the average number of registered patients per GP.

---

## 📌 Project Goals

- Visualize the number of GP practices in each NHS region
- Calculate and compare the average number of patients each GP serves per region
- Identify potential regional disparities in healthcare resource allocation

---

## 🗂️ Dataset

**Source**: [NHS Digital – April 2024 GP Practice data](#)  
**File Used**: `april_2024_attendances.csv`  

| Column Name          | Description                                 |
|----------------------|---------------------------------------------|
| `region`             | NHS administrative region                  |
| `practice_code`      | Unique code per GP practice                |
| `registered_patients`| Number of patients registered at the practice |

---

## 🔧 Data Processing

- Removed missing values from `region`, `practice_code`, and `registered_patients`
- Aggregated:
  - GP count per region using `DISTINCTCOUNT(practice_code)`
  - Total registered patients using `SUM(registered_patients)`
- Created a calculated measure:

```dax
Patients_per_GP = 
DIVIDE(
    SUM(registered_patients),
    DISTINCTCOUNT(practice_code)
)
