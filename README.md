# <img src="https://cdn.freebiesupply.com/logos/large/2x/the-university-of-melbourne-logo-svg-vector.svg" width=15% align=left> COMP90089: Machine Learning Applications for Health Group Project (2024S2-Final-Group-24)
# Acute Hypotension Prediction Using MIMIC-IV Data

This project focuses on identifying and predicting acute hypotensive episodes in patients using data derived from the MIMIC-IV database. The primary data processing and feature extraction steps are carried out through SQL queries on Google BigQuery, with the results saved locally as .csv files for further analysis in Python. If needed, adjustments can be made to directly access the MIMIC-IV database and execute SQL queries in Google Colab.

## Project Structure

- **SQL Queries**: All SQL queries used in this project are stored in `sql.txt`. These queries extract various clinical and demographic data, focusing on patient records with mean arterial pressure (MAP) measurements and other key indicators.

- **Data Files**:
  - **age.csv**: Contains patient age data, used as a demographic feature.
  - **gender.csv**: Contains patient gender data, also used as a demographic feature.
  - **all_map_for_patient_having_less_than_60.csv**: Contains all MAP measurement records for patients with at least one instance of MAP < 60 mmHg. This dataset is used to select positive and negative samples for modeling.
  - **item3.csv**: Contains records of key laboratory tests, including:
    - Diastolic Blood Pressure (item ID: 220051)
    - Systolic Blood Pressure (item ID: 220050)
    - Heart Rate (item ID: 220045)
    - SpO2 (item ID: 220277)
    - MAP (item ID: 220052)
    - Respiratory Rate (item ID: 220210)  
    These measurements are core features for the model.
  - **sofa.csv**: Contains patients' Sequential Organ Failure Assessment (SOFA) scores, used as a feature.
  - **apsiii.csv**: Contains patients' Acute Physiology Score III (APS III) scores, used as a feature.
  - **vasopressin.csv**: Displays the usage of vasopressin by patients, included as a feature.
  - **ventilation.csv**: Displays the usage of ventilation by patients, also included as a feature.

## Data Processing Pipeline

1. **Feature Extraction**: Relevant SQL queries retrieve demographic and clinical data for each patient. These features include age, gender, MAP, and various lab test results that are important for assessing hypotension risk.

2. **Sample Selection**:
   - **Positive Samples**: Acute hypotensive episodes where MAP is < 60 mmHg.
   - **Negative Samples**: Normal periods where MAP consistently remains above 60 mmHg.

3. **Data Cleaning**: The dataset undergoes outlier detection and handling, including:
   - Replacing outliers with NaN values, which are subsequently dropped.

4. **Modeling**: Predictive modeling is carried out to differentiate between normal and acute hypotensive episodes based on extracted features.

## Future Adjustments

If direct database access becomes preferable, the current pipeline can be adjusted to allow SQL query execution directly within Google Colab, bypassing the need for intermediary .csv files.

---

This README provides a high-level overview of the project structure, data sources, and processing steps. For more details, please refer to individual notebooks and the `sql.txt` file.
