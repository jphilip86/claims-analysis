# Healthcare Claims Data Analysis Assignment Overview
You will analyze three interconnected claims files to answer key questions about provider billing patterns, common diagnoses, procedures, and payer relationships. This assignment focuses on relational data analysis using Python and pandas.

# Instructions

## Part 1: Data Loading and Exploration
Complete the following tasks in a Google Colab or Jupyter notebook:

## Data File Access

The dataset files required for this analysis (`STONYBRK_20240531_HEADER.csv`, `STONYBRK_20240531_LINE.csv`, `STONYBRK_20240531_CODE.csv`) are **not included in this repository** due to file size or privacy/data policy constraints.

To access and use these files:

 **My SB Google Drive Folder:**  
   - The data files are stored in a shared Google Drive folder:  
     `/My Drive/Claims/`
   

## Explore each file by displaying:

### Shape (number of rows and columns) 

The exploration results of the three CSV files are as follows:

### df_header:

Shape: 388 rows, 43 columns

There are many missing values in some provider fields.
Basic descriptive statistics indicate the claims span a range of IDs and payer codes.

### df_line:
Shape: 520 rows, 28 columns

Missing values mainly in modifiers and NDC-related fields.

Numeric stats show on average 1 unit per service line and varying charges.

### df_code:
Shape: 1536 rows, 9 columns

No missing values in claim or code identifiers, but other columns contain missing values.

Diagnosis codes data with position info and qualifiers.

First 5 rows
Column names and data types
Missing value counts
Basic descriptive statistics for numeric columns

The above is shown in colab.

## Document your observations about:

**A. How many unique claims are in the dataset?**
There are 388 unique claims in the dataset.

**B. What is the date range of the claims?**
The date range of claims is from September 25, 2023, to May 29, 2024.

**C. How many service lines are there on average per claim?**
On average, there are approximately 1.34 service lines per claim.

**D. How many diagnosis codes are there on average per claim?**
On average, there are approximately 3.96 diagnosis codes per claim.


## Part 2: Relational Data Analysis
Answer the following questions using pandas operations (merge, groupby, value_counts, etc.)

*Question 1: Provider Analysis*
**Who are the top 5 billing providers by number of claims?**

The top 5 billing providers by number of claims are:

SB INTERNISTS (152 claims)

SB SURGICAL ASSOCIATES (81 claims)

NEW YORK SPINE AND BRAIN SURGERY (69 claims)

UNIV.ASSOC.IN OBSTETRICS&GYNECOLOGY (40 claims)

SB PSYCHIATRIC ASSOCIATES (36 claims)

*Question 2: Payer Mix Analysis*
**What are the top 5 primary payers by claim volume?**

Top 5 primary payers by claim volume with percentages:

MEDICARE: 62.37%

HEALTHFIRST FFS: 11.86%

FIDELIS/BETTER HEALTH PLAN: 6.70%

HIP MEDICAID: 4.38%

HEALTHFIRST CAPITATED: 2.58%


*Question 3: Common Diagnoses*
**What are the 10 most frequently appearing diagnosis codes (CodeValue)?**


The 10 most frequent ICD-10 codes with frequencies:

J96.01 (62)  Acute respiratory failure with hypoxia

I10 (49)  Essential (Primary) Hypertension

E78.5 (49)  Hyperlipidemia, unspecified

G93.5 (34)  Compression of brain

D64.9 (29)  Anemia, unspecified

I25.10 (27)  Atherosclerotic heart disease of native coronary artery without angina pectoris

I61.9 (26)  Nontraumatic intracerebral hemorrhage, unspecified

I60.8 (24)  Other subarachnoid hemorrhage

I48.91 (24)  Unspecified atrial fibrillation

I50.9 (22)  Heart failure, unspecified


*Question 4: Common Procedures*
**What are the 10 most frequently billed procedure codes (HCPCS)?**


The 10 most frequently billed HCPCS procedure codes with descriptions and frequencies:

99291: CRITICAL CARE, INITIAL FIRST HOUR (68)

99233: SUBSEQUENT HOSP. CARE, PER DAY (48)

99213: OFFICE/OUTPATIENT VISIT, ESTABLISHED PATIENT (39)

99223: INITIAL HOSPITAL CARE (33)

99222: INITIAL HOSPITAL CARE (32)

99232: SUBSEQUENT HOSPITAL CARE (21)

90833: PSYCHOTHERAPY WITH E&M SERVICE, 30 MINS (16)

99214: OFFICE/OUTPATIENT VISIT, ESTABLISHED PATIENT (14)

92557: COMPREHENSIVE AUDIOMETRY THRESHOLD EVALUATION (14)

99204: OFFICE/OUTPATIENT VISIT FOR NEW PATIENT (14)

*Question 5: Service Location Analysis*
**How many claims were submitted for each PlaceOfService?**

Claims submitted by PlaceOfService code:

21 (INPATIENT): 231 claims

11 (DOCTOR'S OFFICE): 132 claims

22: 24 claims

23: 1 claim

**What percentage of claims are for "INPATIENT" vs "DOCTOR'S OFFICE"?**
Percentage of claims for major locations:

INPATIENT: 59.54%

DOCTOR'S OFFICE: 34.02%

## Part 3: Advanced Analysis with Joins

**Question 6: Claims with High Service Line Counts**

Claim 36710175, Provider UNIV.ASSOC.IN OBSTETRICS&GYNECOLOGY, 5 lines, $873 total charges

Claim 36740402, Provider UNIV.ASSOC.IN OBSTETRICS&GYNECOLOGY, 6 lines, $945 total charges

Claim 36668119, Provider UNIV.ASSOC.IN OBSTETRICS&GYNECOLOGY, 6 lines, $1030 total charges

Claim 36757684, Provider UNIV.ASSOC.IN OBSTETRICS&GYNECOLOGY, 5 lines, $873 total charges

Claim 36794825, Provider SB CHILDREN'S SERVICE, 7 lines, $1163 total charges


**Question 7: Diagnosis-Procedure Combinations**

Most common diagnosis code for CPT 99291 is J96.01 with 53 occurrences.


**Question 8: Charges by Payer**

Top 10 payers by total charges:

MEDICARE: $131,008 total, ~$541 average per claim, 242 claims

HEALTHFIRST FFS: $29,794 total, ~$648 average, 46 claims

FIDELIS/BETTER HEALTH PLAN: $10,810 total, ~$416 average, 26 claims

HIP MEDICAID: $10,014 total, ~$589 average, 17 claims

AETNA: $6,930 total, $1155 average, 6 claims

DIRECT SELF PAY: $6,575 total, $1096 average, 6 claims

UNITED COMMUNITY PLAN GOVT PROGRAM: $5,175 total, $1035 average, 5 claims

HEALTHFIRST CAPITATED: $4,905 total, $490 average, 10 claims

EMPIRE BLUE SR: $4,620 total, $1155 average, 4 claims

MAGNACARE: $3,465 total, $1155 average, 3 claims

## Part 4: Creative Analysis
**Question 9: Your Own Analysis Develop and answer your own analytical question using the claims data**. 

### Question:
Which billing providers submit claims with the greatest diversity of diagnosis codes per claim?

### Insight:
Providers who consistently bill claims with a high average number of diagnosis codes (ICD-10) are likely managing the most clinically complex patients.

This could indicate specialists, hospitalists, or providers in acute-care settings, where patients often have multiple concurrent conditions. High complexity might require more staff, longer provider-patient interaction time, or careful coordination between specialties.

### Operational Implications:
Identifying these providers can help healthcare administrators allocate resources more efficiently, such as clinical support staff or care management teams.

It can also inform training or provider profiling—for example, new providers could be paired with experienced clinicians who have demonstrated expertise in managing complex cases.
This metric can serve as an early flag for potential over-coding or fraud, especially if a provider’s average diagnosis code per claim is abnormally high compared to their peers.

### Clinical/Quality Implications:
These metrics enable quality improvement studies: are the patients of “complex billing” providers receiving better care coordination?
It can help in risk adjustment when comparing outcome measures across providers in population health analysis.

### Financial/Strategic Implications:
Payers may focus audits or documentation review on providers with unusually complex billing profiles to ensure claims are properly supported.

High complexity typically equates to increased charges, which is important in contract negotiations with payers, bundled payments, and managing patient care costs.

### Visualization Strength:
The horizontal bar chart makes it immediately clear which providers have the most complex case mixes, supporting rapid decision-making and deeper drill-downs if needed.

### Summary:
By merging these datasets and aggregating diagnosis code counts by provider, you uncover who in the system handles the most challenging cases. This enables both operational, financial, and clinical teams to understand, support, and optimize care around the true complexity in the patient population, driving actionable improvements in resource allocation and patient outcomes.

### Key References

1. Centers for Medicare and Medicaid Services (CMS): “ICD-10 Implementation Guide for Large Practices.”  
   [ICD-10 Implementation Guide](https://www.perplexity.ai/search/explain-each-line-df-header-pd-w7b2NoLHSb2XO7kI2yBE3Q#:~:text=Key%20References%3A), decision-making.

2. Peer-reviewed quality studies of claims case-mix analysis: “Coding Response to a Case-Mix Measurement System Based ... - NIH.”  
   [Coding Response to a Case-Mix Measurement System](https://www.perplexity.ai/search/explain-each-line-df-header-pd-w7b2NoLHSb2XO7kI2yBE3Q#:~:text=Key%20References%3A), decision-making.

3. AHIMA Journal: “Data Reporting Limitations Need to Be Addressed When Including ...”  
   [AHIMA Article on Reporting Limitations](https://journal.ahima.org/page/data-reporting-limitations-need-to-be-addressed-when-including-sdoh-z-codes-on-medical-claims)

4. ScienceDirect: “A physician-led initiative to improve clinical documentation results in enhanced diagnosis reporting and CMI.”  
   [ScienceDirect Study](https://www.perplexity.ai/search/explain-each-line-df-header-pd-w7b2NoLHSb2XO7kI2yBE3Q#:~:text=Key%20References%3A), decision-making.

5. Perplexity (LLM)  
   Used for synthesizing and summarizing results and troubleshooting errors in the code.

---
These sources document how ICD-10 code counts per claim/provider are used in healthcare data science and administration to quantify case complexity and drive decision-making.
