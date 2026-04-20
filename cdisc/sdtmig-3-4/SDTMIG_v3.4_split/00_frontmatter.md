![Image: page1_img0.jpeg](images/page1_img0.jpeg)

Study Data Tabulation Model Implementation Guide: Human Clinical Trials

Version 3.4 (Final)

Developed by the CDISC Submission Data Standards Team

Notes to Readers

- This is the implementation guide for human clinical trials corresponding to Version 2.0 of the CDISC Study Data Tabulation Model.

Revision History

| Date       | Version     |
| ---------- | ----------- |
| 2021-11-29 | 3.4 Final   |
| 2018-02-20 | 3.3 Final   |
| 2013-11-26 | 3.2 Final   |
| 2012-07-16 | 3.1.3 Final |
| 2008-11-12 | 3.1.2 Final |
| 2005-08-26 | 3.1.1 Final |
| 2004-07-14 | 3.1         |

See Appendix F for representations and warranties, limitations of liability, and disclaimers.

CONTENTS

1 INTRODUCTION

- 1.1 PURPOSE
- 1.2 ORGANIZATION OF THIS DOCUMENT
- 1.3 RELATIONSHIP TO PRIOR CDISC DOCUMENTS
- 1.4 HOW TO READ THIS IMPLEMENTATION GUIDE
  - 1.4.1 How to Read a Domain Specification
- 1.5 KNOWN ISSUES

2 FUNDAMENTALS OF THE SDTM

- 2.1 OBSERVATIONS AND VARIABLES
- 2.2 DATASETS AND DOMAINS
- 2.3 THE GENERAL OBSERVATION CLASSES
- 2.4 DATASETS OTHER THAN GENERAL OBSERVATION CLASS DOMAINS
- 2.5 THE SDTM STANDARD DOMAIN MODELS
- 2.6 CREATING A NEW DOMAIN
- 2.7 SDTM VARIABLES NOT ALLOWED IN THE SDTMIG

3 SUBMITTING DATA IN STANDARD FORMAT

- 3.1 STANDARD METADATA FOR DATASET CONTENTS AND ATTRIBUTES
- 3.2 USING THE CDISC DOMAIN MODELS IN REGULATORY SUBMISSIONS – DATASET METADATA
  - 3.2.1 Dataset-level Metadata
    - 3.2.1.1 Primary Keys
    - 3.2.1.2 CDISC Submission Value-level Metadata
  - 3.2.2 Conformance

4 ASSUMPTIONS FOR DOMAIN MODELS

- 4.1 GENERAL DOMAIN ASSUMPTIONS
  - 4.1.1 Review Study Data Tabulation Model and Implementation Guide
  - 4.1.2 Relationship to Analysis Datasets
  - 4.1.3 Additional Timing Variables
    - 4.1.3.1 EPOCH Variable Guidance
  - 4.1.4 Order of the Variables
  - 4.1.5 SDTM Core Designations
  - 4.1.6 Additional Guidance on Dataset Naming
  - 4.1.7 Splitting Domains
    - 4.1.7.1 Example of Splitting Questionnaires
  - 4.1.8 Origin Metadata
    - 4.1.8.1 Origin Metadata for Variables
    - 4.1.8.2 Origin Metadata for Records
  - 4.1.9 Assigning Natural Keys in the Metadata
- 4.2 GENERAL VARIABLE ASSUMPTIONS
  - 4.2.1 Variable-naming Conventions
  - 4.2.2 Two-character Domain Identifier
  - 4.2.3 Use of "Subject" and USUBJID
  - 4.2.4 Text Case in Submitted Data
  - 4.2.5 Convention for Missing Values
  - 4.2.6 Grouping Variables and Categorization
  - 4.2.7 Submitting Free Text from the CRF
    - 4.2.7.1 "Specify" Values for Non-result Qualifier Variables
    - 4.2.7.2 "Specify" Values for Result Qualifier Variables
    - 4.2.7.3 "Specify" Values for Topic Variables
    - 4.2.7.4 "Specify" Values for --OBJ
  - 4.2.8 Multiple Values for a Variable
    - 4.2.8.1 Multiple Values for an Intervention or Event Topic Variable
    - 4.2.8.2 Multiple Values for a Findings Result Variable
    - 4.2.8.3 Multiple Values for a Non-result Qualifier Variable
    - 4.2.8.4 Multiple Values for a Parameter
  - 4.2.9 Variable Lengths
- 4.3 CODING AND CONTROLLED TERMINOLOGY ASSUMPTIONS
  - 4.3.1 Controlled Terms, Codelist or Format Column
  - 4.3.2 Controlled Terminology Text Case
  - 4.3.3 Controlled Terminology Values
  - 4.3.4 Use of Controlled Terminology and Arbitrary Number Codes
  - 4.3.5 Storing Controlled Terminology for Synonym Qualifier Variables
  - 4.3.6 Storing Topic Variables for General Domain Models
  - 4.3.7 Use of "Yes" and "No" Values
- 4.4 ACTUAL AND RELATIVE TIME ASSUMPTIONS
  - 4.4.1 Formats for Date/Time Variables
  - 4.4.2 Date/Time Precision
  - 4.4.3 Intervals of Time and Use of Duration for --DUR Variables
    - 4.4.3.1 Intervals of Time and Use of Duration
    - 4.4.3.2 Interval with Uncertainty
  - 4.4.4 Use of the Study Day Variables
  - 4.4.5 Clinical Encounters and Visits
  - 4.4.6 Representing Additional Study Days
  - 4.4.7 Use of Relative Timing Variables
  - 4.4.8 Date and Time Reported in a Domain Based on Findings
  - 4.4.9 Use of Dates as Result Variables
  - 4.4.10 Representing Time Points
  - 4.4.11 Disease Milestones and Disease Milestone Timing Variables
- 4.5 OTHER ASSUMPTIONS
  - 4.5.1 Original and Standardized Results of Findings and Tests Not Done
    - 4.5.1.1 Original and Standardized Results
    - 4.5.1.2 Tests Not Done
    - 4.5.1.3 Examples of Original and Standard Units and Test Not Done
  - 4.5.2 Linking Multiple Observations
  - 4.5.3 Text Strings that Exceed the Maximum Length for General Observation-class Domain Variables
    - 4.5.3.1 Test Name (--TEST) Greater than 40 Characters
    - 4.5.3.2 Text Strings Greater than 200 Characters in Other Variables
  - 4.5.4 Evaluators in the Interventions and Events Observation Classes
  - 4.5.5 Clinical Significance for Findings Observation Class Data
  - 4.5.6 Supplemental Reason Variables
  - 4.5.7 Presence or Absence of Prespecified Interventions and Events
  - 4.5.8 Accounting for Long-term Follow-up
  - 4.5.9 Baseline Values

5 MODELS FOR SPECIAL-PURPOSE DOMAINS

- 5.1 COMMENTS (CO)
- 5.2 DEMOGRAPHICS (DM)
- 5.3 SUBJECT ELEMENTS (SE)
- 5.4 SUBJECT DISEASE MILESTONES (SM)
- 5.5 SUBJECT VISITS (SV)

6 DOMAIN MODELS BASED ON THE GENERAL OBSERVATION CLASSES

- 6.1 MODELS FOR INTERVENTIONS DOMAINS
  - 6.1.1 Procedure Agents (AG)
  - 6.1.2 Concomitant/Prior Medications (CM)
  - 6.1.3 Exposure Domains
    - 6.1.3.1 Exposure (EX)
    - 6.1.3.2 Exposure as Collected (EC)
    - 6.1.3.3 Exposure/Exposure as Collected Examples
  - 6.1.4 Meal Data (ML)
  - 6.1.5 Procedures (PR)
  - 6.1.6 Substance Use (SU)
- 6.2 MODELS FOR EVENTS DOMAINS
  - 6.2.1 Adverse Events (AE)
  - 6.2.2 Biospecimen Events (BE)
  - 6.2.3 Clinical Events (CE)
  - 6.2.4 Disposition (DS)
  - 6.2.5 Healthcare Encounters (HO)
  - 6.2.6 Medical History (MH)
  - 6.2.7 Protocol Deviations (DV)
- 6.3 MODELS FOR FINDINGS DOMAINS
  - 6.3.1 Product Accountability (DA)
  - 6.3.2 Death Details (DD)
  - 6.3.3 ECG Test Results (EG)
  - 6.3.4 Inclusion/Exclusion Criteria Not Met (IE)
  - 6.3.5 Specimen-based Findings Domains
    - 6.3.5.1 Generic Specimen-based Lab Findings Domain Specification
    - 6.3.5.2 Biospecimen Findings (BS)
    - 6.3.5.3 Cell Phenotype Findings (CP)
    - 6.3.5.4 Genomics Findings (GF)
    - 6.3.5.5 Immunogenicity Specimen Assessments (IS)
    - 6.3.5.6 Laboratory Test Results (LB)
    - 6.3.5.7 Microbiology Domains
    - 6.3.5.8 Microscopic Findings (MI)
    - 6.3.5.9 Pharmacokinetics Domains
  - 6.3.6 Morphology (MO)
  - 6.3.7 Morphology/Physiology Domains
    - 6.3.7.1 Generic Morphology/Physiology Specification
    - 6.3.7.2 Cardiovascular System Findings (CV)
    - 6.3.7.3 Musculoskeletal System Findings (MK)
    - 6.3.7.4 Nervous System Findings (NV)
    - 6.3.7.5 Ophthalmic Examinations (OE)
    - 6.3.7.6 Reproductive System Findings (RP)
    - 6.3.7.7 Respiratory System Findings (RE)
    - 6.3.7.8 Urinary System Findings (UR)
  - 6.3.8 Physical Examination (PE)
  - 6.3.9 Questionnaires, Ratings, and Scales (QRS) Domains (FT, QS, RS)
    - 6.3.9.1 Functional Tests (FT)
    - 6.3.9.2 Questionnaires (QS)
    - 6.3.9.3 Disease Response and Clin Classification (RS)
  - 6.3.10 Subject Characteristics (SC)
  - 6.3.11 Subject Status (SS)
  - 6.3.12 Tumor/Lesion Domains
    - 6.3.12.1 Tumor/Lesion Identification (TU)
    - 6.3.12.2 Tumor/Lesion Results (TR)
    - 6.3.12.3 Tumor Identification/Tumor Results Examples
  - 6.3.13 Vital Signs (VS)
- 6.4 FINDINGS ABOUT EVENTS OR INTERVENTIONS
  - 6.4.1 When to Use Findings About Events or Interventions
  - 6.4.2 Naming Findings About Domains
  - 6.4.3 Variables Unique to Findings About
  - 6.4.4 Findings About Events or Interventions (FA)
  - 6.4.5 Skin Response (SR)

7 TRIAL DESIGN MODEL DATASETS

- 7.1 INTRODUCTION TO TRIAL DESIGN MODEL DATASETS
  - 7.1.1 Purpose of the Trial Design Model
  - 7.1.2 Definitions of Trial Design Concepts
  - 7.1.3 Current and Future Contents of the Trial Design Model
- 7.2 EXPERIMENTAL DESIGN (TA AND TE)
  - 7.2.1 Trial Arms (TA)
    - 7.2.1.1 Trial Arms Issues
  - 7.2.2 Trial Elements (TE)
    - 7.2.2.1 Trial Elements Issues
- 7.3 SCHEDULE FOR ASSESSMENTS (TV, TD, AND TM)
  - 7.3.1 Trial Visits (TV)
    - 7.3.1.1 Trial Visits Issues
  - 7.3.2 Trial Disease Assessments (TD)
  - 7.3.3 Trial Disease Milestones (TM)
- 7.4 TRIAL ELIGIBILITY AND SUMMARY (TI AND TS)
  - 7.4.1 Trial Inclusion/Exclusion Criteria (TI)
  - 7.4.2 Trial Summary (TS)
    - 7.4.2.1 Use of Null Flavor
- 7.5 HOW TO MODEL THE DESIGN OF A CLINICAL TRIAL

8 REPRESENTING RELATIONSHIPS AND DATA

- 8.1 RELATING GROUPS OF RECORDS WITHIN A DOMAIN USING THE --GRPID VARIABLE
  - 8.1.1 --GRPID Example
- 8.2 RELATING PEER RECORDS
  - 8.2.1 Related Records (RELREC)
  - 8.2.2 RELREC Dataset Examples
- 8.3 RELATING DATASETS
  - 8.3.1 RELREC Dataset Relationship Example
- 8.4 RELATING NON-STANDARD VARIABLE VALUES TO A PARENT DOMAIN
  - 8.4.1 Supplemental Qualifiers (SUPP--)
  - 8.4.2 Submitting Supplemental Qualifiers in Separate Datasets
  - 8.4.3 SUPP-- Examples
  - 8.4.4 When Not to Use Supplemental Qualifiers
- 8.5 RELATING COMMENTS TO A PARENT DOMAIN
- 8.6 HOW TO DETERMINE WHERE DATA BELONG IN SDTM-COMPLIANT DATA TABULATIONS
  - 8.6.1 Guidelines for Determining the General Observation Class
  - 8.6.2 Guidelines for Forming New Domains
  - 8.6.3 Guidelines for Differentiating Between Interventions, Events, Findings, and Findings About Events or Interventions
- 8.7 RELATED SUBJECTS (RELSUB)
- 8.8 RELATED SPECIMENS (RELSPEC)

9 STUDY REFERENCES

- 9.1 DEVICE IDENTIFIERS
- 9.2 NON-HOST ORGANISM IDENTIFIERS (OI)

10 APPENDICES

- Appendix A: CDISC SDS TEAM
- Appendix B: GLOSSARY AND ABBREVIATIONS
- Appendix C: CONTROLLED TEARMINOLOGY
- Appendix D: CDISC VARIABLE-NAMING FRAGMENTS
- Appendix E: REVISON HISTORY
- Appendix F: REPRSENTATIONS AND WARRANTIES,LIMITATIONS OF LIABILITY,AND DISCLAIMERS
