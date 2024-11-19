# VaxRisk - Analysis of VAERS Reports for Vaccine Safety Assessment
## Team - Chandrikarani Vaidya, Sai Ganesh Donka and Terala Bhuvana Chandrika.

![image](https://github.com/user-attachments/assets/998493df-d465-4fa7-bef5-c8c7e188f618)

## ABSTRACT
VaxRisk is a data science project that analyzes Vaccine Adverse Event Reporting System (VAERS) data to assess and predict the risk of adverse events (AEs) associated with vaccines. The project focuses on four key vaccines: COVID-19, Varicella-Zoster (VARZOS), Influenza (FLU), and Pneumococcal vaccine polyvalent (PPV). Using machine learning techniques, VaxRisk aims to develop a predictive model for serious AEs based on patient demographics, symptoms, and health history. The project's ultimate goal is to create a tool that helps users and healthcare professionals assess vaccine safety and make informed decisions.

## INTRODUCTION
In recent years, vaccine safety has become a focal point in both the public domain and within the scientific community. The urgency of vaccine development and deployment during the COVID-19 pandemic has heightened awareness around the potential risks and benefits of immunization. While vaccines are universally recognized as one of the most effective public health interventions, concerns over rare but serious adverse events (AEs) persist. As a result, vaccine safety surveillance systems like VAERS play an essential role in identifying patterns of vaccine-related incidents and informing public health policy.

VaxRisk was conceived to provide an in-depth analysis of vaccine safety data, focusing on the adverse events associated with some of the most widely administered vaccines in the U.S. The project aims to bridge the gap between general vaccine safety signal detection and personalized risk assessment. 

The driving motivations for VaxRisk include:
1. Public Concern Over Vaccine Safety: The sheer number of vaccine doses administered worldwide, especially during the COVID-19 pandemic, has led to increased attention on vaccine-related injuries.
2. Scientific Scrutiny of Rare Adverse Events: Although serious AEs are rare, the consequences of these events can be life-threatening.
3. Potential for Predictive Analytics: VaxRisk takes this a step further by applying machine learning algorithms to predict individual risks for serious AEs, enabling more precise interventions and counseling.
4. Need for Personalized Risk Assessment: Current vaccine safety assessments are often based on population-wide data. VaxRisk aims to provide a personalized risk profile for individuals.

## BACKGROUND
The Vaccine Adverse Event Reporting System (VAERS), established in 1990, is a critical tool in monitoring vaccine safety in the United States. Managed by the CDC and FDA, VAERS collects and analyzes reports of adverse events (AEs) that occur after vaccination. The system serves as an early warning tool, helping to detect potential safety concerns for licensed vaccines.
Key Features of VAERS
1. Data Collection: VAERS collects reports of adverse events from healthcare providers, manufacturers, and the public, regardless of suspected causal links to vaccines.
2. Purpose: The system detects unusual patterns of adverse events (safety signals), monitors known reactions, and identifies potential risk factors.
3. Limitations: As a passive reporting system, VAERS is prone to underreporting and overreporting, cannot establish causality, and often contains incomplete or unverified data.
4. Data Access: VAERS data is accessible through the CDC WONDER tool or as raw CSV files, providing de-identified, regularly updated datasets for research.
5. Complementary Systems: VAERS is part of a larger vaccine safety monitoring network, including the Vaccine Safety Datalink (VSD) and Clinical Immunization Safety Assessment (CISA) Project, which use comprehensive data to validate findings and assess safety signals.

## DATA DESCRIPTION
DATA SOURCE: The project uses data from the Vaccine Adverse Event Reporting System (VAERS), which is co-administered by the FDA and CDC to collect reports of adverse events following vaccination.
Dataset link: https://vaers.hhs.gov/data/datasets.html

The VAERS public data set consists of three separate CSV files:
1. VAERSDATA.CSV: Contains demographic and adverse event information
2. VAERSVAX.CSV: Contains vaccine-specific data
3. VAERSSYMPTOMS.CSV: Contains detailed symptom information

Data Fields:
1. VAERSDATA.CSV has 35 fields including VAERS_ID, age, sex, symptom text, patient outcomes, etc.
2. VAERSVAX.CSV has 8 fields including vaccine type, manufacturer, lot number, dose, etc.
3. VAERSSYMPTOMS.CSV has 11 fields with MedDRA coded symptom terms.

Key Variables:
1. Demographic information (age, gender)
2. Vaccine details (type, manufacturer, lot number)
3. Adverse event symptoms
4. Patient outcomes (hospitalization, disability, death, etc.)

## EXPLORATORY DATA ANALYSIS
Data from 2015 to 2024 was merged, resulting in a dataset of 2,106,687 rows and 47 columns, with a total size of 1.3 GB.

Vaccine Type Analysis: Covid dominates the adverse event reports followed by VARZOS, FLU and PPV. So we will be working further with these 4 vaccines.

Demographic Analysis: Age distribution showed a peak in the 50-60 year age group, indicating a higher frequency of reports among older adults.
Gender distribution revealed that females accounted for 61% of reports, males for 31.9%, and 7.1% were unspecified.

Temporal Trends: A significant spike in adverse event reports was observed starting in late 2020, coinciding with the COVID-19 pandemic. The peak occurred in 2021, followed by a gradual decline, though numbers remained higher than pre-pandemic levels through 2024.

Symptom Analysis: The top reported symptoms were pyrexia (fever) and headache, followed by fatigue, pain, and chills.

Manufacturer Analysis: Pfizer/BioNTech and Moderna had the highest number of reports, likely due to their major role in COVID-19 vaccinations.

# Phase 2
In Phase 2 of our project, we have conducted a thorough analysis of the data and eliminated redundancies identified during Phase 1. As a result, we have produced an updated data cleaning file, titled "Basic_cleaning&EDA.ipynb." Additionally, we have developed separate EDA (_EDA) and machine learning (ML_) notebooks for each vaccine, complemented by a dedicated file for the target variable, named "Top4Vaccine(Target variable).ipynb." 
Here is the link for cleaned csv files
https://umbc.box.com/s/sl7mthzhw97dvg8hnjpsf4r3sr7xk0vb

Phase 2 involved comprehensive data preparation to enable precise predictive analysis of adverse events(AEs). Key processes included: Categorical Encoding, Text Cleaning and data filtering focusing in four vaccines.

## Feature Engineering and Selection
Feature engineering was pivotal for constructing an informative dataset for predictive modeling.

Target Variable Creation: A binary “SERIOUS” variable was defined based on outcomes such as death, life-threatening conditions, hospitalization, disability, and birth defects. The MedDRA Important Medical Event (IME) List was used to match symptoms and classify them as serious or non-serious.

Key Features: Age, gender, hospitalization status, symptom text, vaccine manufacturer, and other demographic factors were selected as primary predictors.

## Data Modeling and Challenges
Data Modeling and Challenges

Machine learning models were developed to predict serious AEs:

Modeling Pipeline: A comprehensive pipeline was constructed, integrating TF-IDF vectorization for text data and StandardScaler for numeric data normalization.

Split Strategy: The dataset was divided into training (70%) and testing (30%) sets.

Algorithms Implemented: Logistic Regression
Algorithms to be implemented: AdaBoost Classifier, Random Forest Classifier and K-Nearest Neighbors (KNN).

Challenge we faced was Mixed Data Types: Addressed this by employing vectorization for text features and scaling for numerical attributes.

## Pipeline Description
TF-IDF Vectorization: Applied to textual columns such as symptom descriptions.
StandardScaler: Utilized to standardize numerical columns for model consistency.
Stopword Removal: Custom stopwords were defined to enhance the relevance of text features.

## Model Evaluation Metrics
Evaluation was conducted using standard metrics like accuracy, F1-score, precision and recall.

Logistic Regression and ensemble models showed strong initial predictive performance but highlighted the need for handling data imbalances.

## Future Directions

Model Enhancement: Additional machine learning algorithms and SMOTE will be applied to improve model reliability.

User Interface Development: Plans include building a user-friendly interface for healthcare professionals and the public to input vaccination data and assess potential AE severity.

Algorithm Benchmarking: Further comparisons will be conducted to determine the most effective predictive model.
