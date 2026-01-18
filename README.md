# Air Quality & Health Risk Analysis of Karnataka (CPCB Data)

This project analyzes Government of India CPCB air quality data to understand pollution patterns, seasonal impact, and public health risk across Karnataka cities.
The goal is to transform raw government data into actionable insights using Python and Power BI.

---

## 📊 Dashboard Preview


![Dashboard](Dashboard/Screenshots/Screenshot%202026-01-18%20151245.png)



---

##  Problem Statement

Air pollution is a growing public health concern in India.
This project aims to answer:

* Which cities are most polluted in Karnataka?
* How severe is the overall health risk?
* What were the worst pollution days?
* Does winter worsen air quality?
* Is traffic or industry the bigger polluter?

---

## 🗂️ Dataset

**Source:** Central Pollution Control Board (CPCB), Government of India
**Raw Data:** India Air Quality Dataset (Kaggle)

**Original Columns:**

```
stn_code, sampling_date, state, location, agency, type, so2, no2, rspm, spm,
location_monitoring_station, pm2_5, date
```

---

##  Data Cleaning & Preparation (Python)

### Step 1 – Feature Selection

Removed unnecessary columns to focus on analytical relevance:

**Dropped Columns & Why**

| Column                      | Reason                                        |
| --------------------------- | --------------------------------------------- |
| stn_code                    | Station ID not needed for city-level analysis |
| agency                      | Does not affect pollution trends              |
| type                        | Not required for health analysis              |
| spm                         | Inconsistent & outdated                       |
| location_monitoring_station | Too granular                                  |
| sampling_date               | Duplicate of date                             |

**Final Columns Used**

```
state, location, so2, no2, rspm, date
```

---

### Step 2 – Karnataka Filtering

Filtered only Karnataka records to make the analysis local and meaningful.

---

### Step 3 – Date Engineering

* Converted `date` to datetime
* Extracted:

  * year
  * month
  * season (Winter, Summer, Monsoon)

---

### Step 4 – Health Risk Classification

Created Health Risk categories based on RSPM:

| RSPM    | Health Risk |
| ------- | ----------- |
| < 50    | Safe        |
| 50–100  | Mild        |
| 100–200 | Moderate    |
| 200–300 | High        |
| > 300   | Severe      |

---

### Step 5 – Export Clean Dataset

Saved final cleaned file:

```
karnataka_air_quality_cleaned.csv
```

---

## 📈 Dashboard Development (Power BI)

### KPI Cards

* Average Air Pollution (RSPM)
* Average Traffic Pollution (NO₂)
* Average Industrial Pollution (SO₂)
* Worst Pollution Day
* Unhealthy Air Days

---

### Key Visuals

| Question                        | Visual                                 |
| ------------------------------- | -------------------------------------- |
| Which cities are most polluted? | Bar chart (Avg RSPM by City)           |
| How severe is the health risk?  | Stacked bar (Health Risk distribution) |
| Worst pollution days            | Bar chart (Top 10 days by Max RSPM)    |
| Seasonal impact                 | Column chart (Avg RSPM by Season)      |
| Long-term trend                 | Area chart (Yearly Avg RSPM)           |
| Traffic vs Industry             | Scatter plot (NO₂ vs SO₂, size = RSPM) |

---

## 🧠 Key Insights

* **Tumkur, Davangere and Bengaluru** are the most polluted cities in Karnataka.
* **Winter shows the highest pollution levels**, confirming strong seasonal impact.
* **Traffic pollution (NO₂) is the main contributor**, especially in Bengaluru.
* **Industrial cities show higher SO₂**, proving industry impact.
* Karnataka generally has **safe to moderate air quality**, but long-term exposure poses health risks.

---

## 🛠️ Tools Used

* Python (Pandas) – Data cleaning & preparation
* Power BI – Dashboard & visualization
* CPCB Government Dataset

---

## 📁 Repository Structure

```
Karnataka_AQI_Analysis/
├── Dashboard/
│ ├── Screenshots/
│ │ ├── Screenshot 2026-01-18 1512.png
│ │ ├── Screenshot 2026-01-18 15134.png
│ │ └── ...
│ └── Karnataka_Air_Quality_Analysis.pbix
│
├── Karnataka_AQI.ipynb
├── Karnataka_Air_Quality_Cleaned.csv
├── Karnataka_Air_Quality_Uncleaned.csv
└── README.md
```
