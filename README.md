# 🧪 Ozone Pollution in California — 2024 Analysis Report

---

## 📌 Overview  
This report presents a comprehensive exploratory data analysis (EDA) of ozone pollution levels across California in 2024. Using air quality data from the U.S. Environmental Protection Agency (EPA), the study investigates temporal and spatial trends in ozone concentration, detects outliers, handles missing data, and generates visual insights for decision-makers concerned with environmental health and air quality policy.

---

## 📉 Missing Data Analysis

### 🔍 Missing Fields:
- `CBSA Code`, `CBSA Name`: Missing due to lack of associated statistical region for some sensors.
- `Method Code`: Some records lacked data collection method identifiers.
- `Daily Max 8-hour Ozone Concentration`: Missing for certain sensors on certain dates (likely due to hardware failure or transmission gaps).

### 🛠 Handling Strategy:
- Rows with missing values in key numerical columns were either dropped or imputed using:
  - Forward fill (`ffill`) for continuous readings.
  - Group-based imputation (by `Site ID` or `County`) when applicable.
- Categorical nulls (e.g., `CBSA Name`) were left as-is if they didn’t affect core analysis.

---

## 🌍 Geospatial & Temporal Patterns

### 1️⃣ How does daily maximum 8-hour ozone concentration vary over time and regions?

- **Time Trends**:
  - Ozone levels peak during summer (July–August), matching expected high temperatures and photochemical activity.
  - Concentration is relatively lower during winter months.

- **Regional Trends**:
  - Inland areas like **San Bernardino**, **Riverside**, and **Fresno** showed consistently high ozone levels.
  - Coastal regions such as **San Francisco** and **San Diego** experienced lower average ozone concentrations due to maritime airflow.

---

### 2️⃣ Are there areas that consistently show high ozone concentrations?

Yes. Based on spatial plots and regional aggregation:

- **Top Hotspots**:
  - San Bernardino County
  - Riverside County
  - Kern County

These regions exhibit sustained high ozone levels, likely due to industrial activity and geographical entrapment of pollutants (valley effect).

---

### 3️⃣ Do different methods report different ozone levels?

- The dataset includes multiple `Method Code` entries per site.
- Boxplots grouped by `Method Code` revealed minor differences in reported values — some methods tend to slightly underreport.
- However, most discrepancies fall within acceptable environmental monitoring ranges.

---

## 📆 Urban Activity Effect (Weekday vs Weekend)

- Analysis of `Day of Week` revealed a **noticeable drop** in ozone concentrations during weekends, particularly **Sundays**.
- Hypothesis: Reduced traffic and industrial activity lower precursor emissions (NOx and VOCs).
- This confirms that human activity strongly influences local air quality.

---

## 🌡️ Outlier Detection & Removal

- Z-score and IQR methods were used to detect outliers in:
  - `Daily Max 8-hour Ozone Concentration`
  - `Daily AQI Value`

- Outliers were primarily extreme spikes (often above 0.120 ppm), likely caused by:
  - Wildfires
  - Faulty sensors
  - Temperature inversions

Outliers were flagged for contextual review but kept in the dataset to preserve true extreme pollution events.

---

## 🗺️ Interactive Mapping

- Using `Plotly` and `Folium`, maps were generated to:
  - Show ozone concentration variation across locations
  - Animate changes over time with a date-slider
  - Zoom into California, with colored markers representing AQI

**Map Enhancements**:
- Color gradient reflects concentration (green = safe, red = hazardous)
- Hover tooltips display `Local Site Name` and `Date`
- Starting zoom centered on California coordinates

---

## ✅ Key Takeaways

- **Seasonal spikes** in ozone are consistent and significant in warm months.
- Inland counties show chronic ozone problems and may require more aggressive intervention.
- Weekend reductions imply that policy actions (e.g., traffic reduction) can lower pollution effectively.
- Outlier spikes should be monitored closely for correlation with wildfires or equipment failure.

---

## 📌 Recommendations

- **Targeted Monitoring**: Focus on hotspots like San Bernardino and Kern for stricter emissions policies.
- **Public Awareness**: Issue health alerts during summer months, especially for vulnerable groups.
- **Further Research**: Study correlation between ozone and meteorological data (temperature, humidity).
- **Sensor Calibration**: Investigate method discrepancies and unify reporting across sites.

---
