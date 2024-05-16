# Project_1


The dataset was provided by the Mexican government (https://www.kaggle.com/datasets/meirnizri/covid19-dataset). 

From the dataset information:
This dataset contains an enormous number of anonymized patient-related information including pre-conditions. The raw dataset consists of 21 unique features and 1,048,576 unique patients. In the Boolean features, 1 means "yes" and 2 means "no". values as 97, 98, and 99 are missing data.

sex: 1 for female and 2 for male.
age: of the patient.
classification: covid test findings. Values 1-3 mean that the patient was diagnosed with covid in different
degrees. 4 or higher means that the patient is not a carrier of covid or that the test is inconclusive.
patient type: type of care the patient received in the unit. 1 for returned home and 2 for hospitalization.
pneumonia: whether the patient already have air sacs inflammation or not.
pregnancy: whether the patient is pregnant or not.
diabetes: whether the patient has diabetes or not.
copd: Indicates whether the patient has Chronic obstructive pulmonary disease or not.
asthma: whether the patient has asthma or not.
inmsupr: whether the patient is immunosuppressed or not.
hypertension: whether the patient has hypertension or not.
cardiovascular: whether the patient has heart or blood vessels related disease.
renal chronic: whether the patient has chronic renal disease or not.
other disease: whether the patient has other disease or not.
obesity: whether the patient is obese or not.
tobacco: whether the patient is a tobacco user.
usmr: Indicates whether the patient treated medical units of the first, second or third level.
medical unit: type of institution of the National Health System that provided the care.
intubed: whether the patient was connected to the ventilator.
icu: Indicates whether the patient had been admitted to an Intensive Care Unit.
date died: If the patient died indicate the date of death, and 9999-99-99 otherwise.


"Public hospitals are classified according to the level of attention that is given. First Level includes primary care; Second Level hospitals mainly include hospitals with four specialties: Surgery, Internal Medicine, Paediatrics and Gynaecology/Obstetrics and Third Level Hospitals include most other subspecialties and are mainly referred to as "Medical Units of High Care". There is close interaction between first and second levels, as well as second and third levels. Intensive Care Units are placed in second and third level hospitals." https://healthmanagement.org/c/icu/issuearticle/the-mexican-healthcare-system

This data set was analyzed to determine the relationships between total pre-existing conditions and individual conditions and death by calcualting the percentage of patients that died vs total patients for those with and without certain conditions. Plots were generated and saved in this folder. Results of the analysis can be found in the notebook.