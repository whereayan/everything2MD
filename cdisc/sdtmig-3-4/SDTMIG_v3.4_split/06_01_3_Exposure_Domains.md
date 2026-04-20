#### 6.1.3 Exposure Domains

Clinical trial study designs can range from open label (where subjects and investigators know which product each subject is receiving) to blinded (where the subject, investigator, or anyone assessing the outcome is unaware of the treatment assignment(s) to reduce potential for bias). To support standardization of various collection methods and details, as well as process differences between open-label and blinded studies, 2 SDTM domains based on the Interventions General Observation Class are available to represent details of subject exposure to protocol-specified study treatment(s): Exposure (EX) and Exposure as Collected (EC).

##### 6.1.3.1 Exposure (EX)

EX – Description/Overview

An interventions domain that contains the details of a subject's exposure to protocol-specified study treatment. Study treatment may be any intervention that is prospectively defined as a test material within a study, and is typically but not always supplied to the subject.

EX – Specification

ex.xpt, Exposure — Interventions. One record per protocol-specified study treatment, constant-dosing interval, per subject, Tabulation.

| Variable Name | Variable Label                           | Type | Controlled Terms, Codelist or Format1 | Role               | CDISC Notes                                                                                                                                                                                                                                                                                                                 | Core |
| ------------- | ---------------------------------------- | ---- | ------------------------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| STUDYID       | Study Identifier                         | Char |                                       | Identifier         | Unique identifier for a study.                                                                                                                                                                                                                                                                                              | Req  |
| DOMAIN        | Domain Abbreviation                      | Char | EX                                    | Identifier         | Two-character abbreviation for the domain.                                                                                                                                                                                                                                                                                  | Req  |
| USUBJID       | Unique Subject Identifier                | Char |                                       | Identifier         | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                                                                                                                                                                                | Req  |
| EXSEQ         | Sequence Number                          | Num  |                                       | Identifier         | Sequence number given to ensure uniqueness of subject records within a domain. May be any valid number.                                                                                                                                                                                                                     | Req  |
| EXGRPID       | Group ID                                 | Char |                                       | Identifier         | Used to tie together a block of related records in a single domain for a subject.                                                                                                                                                                                                                                           | Perm |
| EXREFID       | Reference ID                             | Char |                                       | Identifier         | Internal or external identifier (e.g., kit number, bottle label, vial identifier).                                                                                                                                                                                                                                          | Perm |
| EXSPID        | Sponsor-Defined Identifier               | Char |                                       | Identifier         | Sponsor-defined reference number. May be preprinted on the CRF as an explicit line identifier or defined in the sponsor's operational database. Example: Line number on a CRF page.                                                                                                                                         | Perm |
| EXLNKID       | Link ID                                  | Char |                                       | Identifier         | Identifier used to link related records across domains.                                                                                                                                                                                                                                                                     | Perm |
| EXLNKGRP      | Link Group ID                            | Char |                                       | Identifier         | Identifier used to link related, grouped records across domains.                                                                                                                                                                                                                                                            | Perm |
| EXTRT         | Name of Treatment                        | Char | *                                     | Topic              | Name of the protocol-specified study treatment given during the dosing period for the observation.                                                                                                                                                                                                                          | Req  |
| EXCAT         | Category of Treatment                    | Char | *                                     | Grouping Qualifier | Used to define a category of EXTRT values.                                                                                                                                                                                                                                                                                  | Perm |
| EXSCAT        | Subcategory of Treatment                 | Char | *                                     | Grouping Qualifier | A further categorization of EXCAT values.                                                                                                                                                                                                                                                                                   | Perm |
| EXDOSE        | Dose                                     | Num  |                                       | Record Qualifier   | Amount of EXTRT when numeric. Not populated when EXDOSTXT is populated.                                                                                                                                                                                                                                                     | Exp  |
| EXDOSTXT      | Dose Description                         | Char |                                       | Record Qualifier   | Amount of EXTRT when non-numeric. Dosing amounts or a range of dosing information collected in text form. Example: "200-400". Not populated when EXDOSE is populated.                                                                                                                                                       | Perm |
| EXDOSU        | Dose Units                               | Char | (UNIT)                                | Variable Qualifier | Units for EXDOSE, EXDOSTOT, or EXDOSTXT representing protocol-specified values. Examples: "ng", "mg", "mg/kg", "mg/m2".                                                                                                                                                                                                     | Exp  |
| EXDOSFRM      | Dose Form                                | Char | (FRM)                                 | Variable Qualifier | Dose form for EXTRT. Examples: "TABLET", "LOTION".                                                                                                                                                                                                                                                                          | Exp  |
| EXDOSFRQ      | Dosing Frequency per Interval            | Char | (FREQ)                                | Record Qualifier   | Usually expressed as the number of repeated administrations of EXDOSE within a specific time period. Examples: "Q2H", "QD", "BID".                                                                                                                                                                                          | Perm |
| EXDOSRGM      | Intended Dose Regimen                    | Char |                                       | Record Qualifier   | Text description of the intended schedule or regimen for the Intervention. Example: "TWO WEEKS ON, TWO WEEKS OFF".                                                                                                                                                                                                          | Perm |
| EXROUTE       | Route of Administration                  | Char | (ROUTE)                               | Variable Qualifier | Route of administration for the intervention. Examples: "ORAL", "INTRAVENOUS".                                                                                                                                                                                                                                              | Perm |
| EXLOT         | Lot Number                               | Char |                                       | Record Qualifier   | Lot number of the intervention product.                                                                                                                                                                                                                                                                                     | Perm |
| EXLOC         | Location of Dose Administration          | Char | (LOC)                                 | Record Qualifier   | Specifies location of administration. Examples: "ARM", "LIP".                                                                                                                                                                                                                                                               | Perm |
| EXLAT         | Laterality                               | Char | (LAT)                                 | Variable Qualifier | Qualifier for anatomical location further detailing laterality of the intervention administration. Examples: "LEFT", "RIGHT".                                                                                                                                                                                               | Perm |
| EXDIR         | Directionality                           | Char | (DIR)                                 | Variable Qualifier | Qualifier for anatomical location further detailing directionality. Examples: "ANTERIOR", "LOWER", "PROXIMAL", "UPPER".                                                                                                                                                                                                     | Perm |
| EXFAST        | Fasting Status                           | Char | (NY)                                  | Record Qualifier   | Indicator used to identify fasting status. Examples: "Y", "N".                                                                                                                                                                                                                                                              | Perm |
| EXADJ         | Reason for Dose Adjustment               | Char | *                                     | Record Qualifier   | Describes reason or explanation of why a dose is adjusted.                                                                                                                                                                                                                                                                  | Perm |
| TAETORD       | Planned Order of Element within Arm      | Num  |                                       | Timing             | Number that gives the planned order of the element within the arm.                                                                                                                                                                                                                                                          | Perm |
| EPOCH         | Epoch                                    | Char | (EPOCH)                               | Timing             | Trial epoch of the exposure record. Examples: "RUN-IN", "TREATMENT".                                                                                                                                                                                                                                                        | Perm |
| EXSTDTC       | Start Date/Time of Treatment             | Char | ISO 8601 datetime or interval         | Timing             | The date/time when administration of the treatment indicated by EXTRT and EXDOSE began.                                                                                                                                                                                                                                     | Exp  |
| EXENDTC       | End Date/Time of Treatment               | Char | ISO 8601 datetime or interval         | Timing             | The date/time when administration of the treatment indicated by EXTRT and EXDOSE ended. For administrations considered given at a point in time (e.g., oral tablet, pre-filled syringe injection), where only an administration date/time is collected, EXSTDTC should be copied to EXENDTC as the standard representation. | Exp  |
| EXSTDY        | Study Day of Start of Treatment          | Num  |                                       | Timing             | Study day of EXSTDTC relative to DM.RFSTDTC.                                                                                                                                                                                                                                                                                | Perm |
| EXENDY        | Study Day of End of Treatment            | Num  |                                       | Timing             | Study day of EXENDTC relative to DM.RFSTDTC.                                                                                                                                                                                                                                                                                | Perm |
| EXDUR         | Duration of Treatment                    | Char | ISO 8601 duration                     | Timing             | Collected duration of administration. Used only if collected on the CRF and not derived from start and end date/times.                                                                                                                                                                                                      | Perm |
| EXTPT         | Planned Time Point Name                  | Char |                                       | Timing             | Text description of time when administration should occur. This may be represented as an elapsed time relative to a fixed reference point, such as time of last dose. See EXTPTNUM and EXTPTREF.                                                                                                                            | Perm |
| EXTPTNUM      | Planned Time Point Number                | Num  |                                       | Timing             | Numerical version of EXTPT to aid in sorting.                                                                                                                                                                                                                                                                               | Perm |
| EXELTM        | Planned Elapsed Time from Time Point Ref | Char | ISO 8601 duration                     | Timing             | Planned elapsed time relative to the planned fixed reference (EXTPTREF). This variable is useful where there are repetitive measures. Not a clock time.                                                                                                                                                                     | Perm |
| EXTPTREF      | Time Point Reference                     | Char |                                       | Timing             | Name of the fixed reference point referred to by EXELTM, EXTPTNUM, and EXTPT. Examples: PREVIOUS DOSE, PREVIOUS MEAL.                                                                                                                                                                                                       | Perm |
| EXRFTDTC      | Date/Time of Reference Time Point        | Char | ISO 8601 datetime or interval         | Timing             | Date/time for a fixed reference time point defined by EXTPTREF.                                                                                                                                                                                                                                                             | Perm |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

EX – Assumptions

1. EX structure and use

   a. Examples of treatments represented in the EX domain include but are not limited to placebo, active comparators, and investigational products. Treatments that are not protocol-specified should be represented in the Concomitant/Prior Medications (CM) or another Interventions domain as appropriate.

   b. The EX domain is recognized in most cases as a derived dataset where EXDOSU reflects the protocol-specified unit per study treatment. Collected data points (e.g., number of tablets, total volume infused) along with additional inputs (e.g., randomization file, concentration, dosage strength, product accountability) are used to derive records in the EX domain.

   c. The EX domain is required for all studies that include protocol-specified study treatment. Exposure records may be directly or indirectly determined; metadata should describe how the records were derived. Common methods for determining exposure (from most direct to least direct) include the following:

   i. Derived from actual observation of the administration of drug by the investigator

   ii. Derived from automated dispensing device that records administrations

   iii. Derived from subject recall

   iv. Derived from product accountability data

   v. Derived from the protocol. When a study is still masked and protocol-specified study treatment doses cannot yet be reflected in the protocol-specified unit due to blinding requirements, then the EX domain is not expected to be populated.

   d. The EX domain should contain 1 record per constant-dosing interval per subject. Sponsors define the constant-dosing interval, which may include any period of time that can be described in terms of a known treatment given at a consistent dose, frequency, infusion rate, and so on. For example, for a study with once-a-week administration of a standard dose for 6 weeks, exposure may be represented as:

   i. a single record per subject, spanning the entire 6-week treatment phase, if information about each dose is not collected; or

   ii. up to 6 records (1 for each weekly administration), if the sponsor monitors each treatment administration.
2. Exposure treatment description

   a. EXTRT captures the name of the protocol-specified study treatment and is the topic variable. It is a required variable and must have a value. EXTRT must include only the treatment name and must not include dosage, formulation, or other qualifying information. For example, "ASPIRIN 100MG TABLET" is not a valid value for EXTRT. This example should be expressed as EXTRT = "ASPIRIN", EXDOSE = "100", EXDOSU = "mg", and EXDOSFRM = "TABLET".

   b. Doses of placebo should be represented by EXTRT = "PLACEBO" and EXDOSE = "0" (indicating 0 mg of active ingredient was taken or administered).
3. Categorization and grouping

   a. EXCAT and EXSCAT may be used when appropriate to categorize treatments into categories and subcategories. For example, if a study contains several active comparator medications, EXCAT may be set to "ACTIVE COMPARATOR". Such categorization may not be useful in all studies, so these variables are permissible.
4. Timing variables

   a. The timing of exposure to study treatment is captured by the start/end date and start/end time of each constant-dosing interval. If the subject is only exposed to study medication within a clinical encounter (e.g., if an injection is administered at the clinic), VISITNUM may be added to the domain as an additional timing variable. VISITDY and VISIT would then also be permissible qualifiers. However, if the beginning and end of a constant- dosing interval is not confined within the time limits of a clinical encounter (e.g., if a subject takes pills at home), then it is not appropriate to include VISITNUM in the EX domain. This is because EX is designed to capture the timing of exposure to treatment, not the timing of dispensing treatment. Further, VISITNUM should not be used to indicate that treatment began at a particular visit and continued for a period of time. The SDTM does not have any provision for recording "start visit" and "end visit" of exposure.

   b. For administrations considered given at a point in time (e.g., oral tablet, pre-filled syringe injection), where only an administration date/time is collected, EXSTDTC should be copied to EXENDTC as the standard representation.
5. Collected exposure data points are to be represented in the Exposure as Collected (EC) domain. When the relationship between EC and EX records can be described in RELREC, then it should be defined. EX derivations must be described in the Define-XML document.Additional interventions qualifiers
6. Additional interventions qualifiers

   a. EX contains medications received; the inclusion of administrations not taken, not given, or missed is under evaluation. Because EX includes only treatments received, --MOOD would generally not be used in EX.

   b. --DOSTOT is under evaluation for potential deprecation and replacement with a mechanism to describe total dose over any interval of time (e.g., day, week, month). Sponsors considering use of EXDOSTOT may want to consider using other dose-amount variables (EXDOSE or EXDOSTXT) in combination with frequency (EXDOSFRQ) and timing variables to represent the data.

   c. When the EC domain is implemented in conjunction with the EX domain, EXVAMT and EXVAMTU would not be used in EX; collected values instead would be represented in ECDOSE and ECDOSU (and ECVAMT and ECVAMTU as needed).

   d. Any identifier variables, timing variables, or findings general observation-class qualifiers may be added to the EX domain, but the following qualifiers would generally not be used: –PRESP, --OCCUR, --STAT, and --REASND.

##### 6.1.3.2 Exposure as Collected (EC)

EC – Description/Overview

An interventions domain that contains information about protocol-specified study treatment administrations, as collected.

EC – Specification

ec.xpt, Exposure as Collected — Interventions. One record per protocol-specified study treatment, collected-dosing interval, per subject, per mood, Tabulation.

| Variable Name | Variable Label                           | Type | Controlled Terms, Codelist or Format1 | Role               | CDISC Notes                                                                                                                                                                                                                                                                                                                 | Core |
| ------------- | ---------------------------------------- | ---- | ------------------------------------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| STUDYID       | Study Identifier                         | Char |                                       | Identifier         | Unique identifier for a study.                                                                                                                                                                                                                                                                                              | Req  |
| DOMAIN        | Domain Abbreviation                      | Char | EC                                    | Identifier         | Two-character abbreviation for the domain.                                                                                                                                                                                                                                                                                  | Req  |
| USUBJID       | Unique Subject Identifier                | Char |                                       | Identifier         | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                                                                                                                                                                                | Req  |
| ECSEQ         | Sequence Number                          | Num  |                                       | Identifier         | Sequence number given to ensure uniqueness of subject records within a domain. May be any valid number.                                                                                                                                                                                                                     | Req  |
| ECGRPID       | Group ID                                 | Char |                                       | Identifier         | Used to tie together a block of related records in a single domain for a subject.                                                                                                                                                                                                                                           | Perm |
| ECREFID       | Reference ID                             | Char |                                       | Identifier         | Internal or external identifier (e.g., kit number, bottle label, vial identifier).                                                                                                                                                                                                                                          | Perm |
| ECSPID        | Sponsor-Defined Identifier               | Char |                                       | Identifier         | Sponsor-defined reference number. May be preprinted on the CRF as an explicit line identifier or defined in the sponsor's operational database. Example: Line number on a CRF page.                                                                                                                                         | Perm |
| ECLNKID       | Link ID                                  | Char |                                       | Identifier         | Identifier used to link related records across domains.                                                                                                                                                                                                                                                                     | Perm |
| ECLNKGRP      | Link Group ID                            | Char |                                       | Identifier         | Identifier used to link related, grouped records across domains.                                                                                                                                                                                                                                                            | Perm |
| ECTRT         | Name of Treatment                        | Char | *                                     | Topic              | Name of the intervention treatment known to the subject and/or administrator.                                                                                                                                                                                                                                               | Req  |
| ECMOOD        | Mood                                     | Char | (BRDGMOOD)                            | Record Qualifier   | Mode or condition of the record specifying whether the intervention (activity) is intended to happen or has happened. Values align with BRIDG pillars (e.g., scheduled context, performed context) and HL7 activity moods (e.g., intent, event). Examples: "SCHEDULED", "PERFORMED".                                        | Perm |
| ECCAT         | Category of Treatment                    | Char | *                                     | Grouping Qualifier | Used to define a category of related ECTRT values.                                                                                                                                                                                                                                                                          | Perm |
| ECSCAT        | Subcategory of Treatment                 | Char | *                                     | Grouping Qualifier | A further categorization of ECCAT values.                                                                                                                                                                                                                                                                                   | Perm |
| ECPRESP       | Pre-Specified                            | Char | (NY)                                  | Variable Qualifier | Used when a specific intervention is prespecified. Values should be "Y" or null.                                                                                                                                                                                                                                            | Perm |
| ECOCCUR       | Occurrence                               | Char | (NY)                                  | Record Qualifier   | Used to indicate whether a treatment occurred when information about the occurrence is solicited. ECOCCUR = "N" when a treatment was not taken, not given, or missed.                                                                                                                                                       | Perm |
| ECREASOC      | Reason for Occur Value                   | Char |                                       | Record Qualifier   | The reason for the value in --OCCUR. If --OCCUR = "N", this is the reason the exposure did not occur.                                                                                                                                                                                                                       | Perm |
| ECDOSE        | Dose                                     | Num  |                                       | Record Qualifier   | Amount of ECTRT when numeric. Not populated when ECDOSTXT is populated.                                                                                                                                                                                                                                                     | Exp  |
| ECDOSTXT      | Dose Description                         | Char |                                       | Record Qualifier   | Amount of ECTRT when non-numeric. Dosing amounts or a range of dosing information collected in text form. Example: "200-400". Not populated when ECDOSE is populated.                                                                                                                                                       | Perm |
| ECDOSU        | Dose Units                               | Char | (UNIT)                                | Variable Qualifier | Units for ECDOSE, ECDOSTOT, or ECDOSTXT.                                                                                                                                                                                                                                                                                    | Exp  |
| ECDOSFRM      | Dose Form                                | Char | (FRM)                                 | Variable Qualifier | Dose form for ECTRT. Examples: "TABLET", "LOTION".                                                                                                                                                                                                                                                                          | Exp  |
| ECDOSFRQ      | Dosing Frequency per Interval            | Char | (FREQ)                                | Record Qualifier   | Usually expressed as the number of repeated administrations of ECDOSE within a specific time period. Examples: "Q2H", "QD", "BID".                                                                                                                                                                                          | Perm |
| ECDOSTOT      | Total Daily Dose                         | Num  |                                       | Record Qualifier   | Total daily dose of ECTRT using the units in ECDOSU. Used when dosing is collected as total daily dose.                                                                                                                                                                                                                     | Perm |
| ECDOSRGM      | Intended Dose Regimen                    | Char |                                       | Record Qualifier   | Text description of the intended schedule or regimen for the Intervention. Example: "TWO WEEKS ON", "TWO WEEKS OFF".                                                                                                                                                                                                        | Perm |
| ECROUTE       | Route of Administration                  | Char | (ROUTE)                               | Variable Qualifier | Route of administration for the intervention. Examples: "ORAL", "INTRAVENOUS".                                                                                                                                                                                                                                              | Perm |
| ECLOT         | Lot Number                               | Char |                                       | Record Qualifier   | Lot number of the ECTRT product.                                                                                                                                                                                                                                                                                            | Perm |
| ECLOC         | Location of Dose Administration          | Char | (LOC)                                 | Record Qualifier   | Specifies location of administration. Example: "ARM", "LIP".                                                                                                                                                                                                                                                                | Perm |
| ECLAT         | Laterality                               | Char | (LAT)                                 | Variable Qualifier | Qualifier for anatomical location further detailing laterality of the intervention administration. Examples: "LEFT", "RIGHT".                                                                                                                                                                                               | Perm |
| ECDIR         | Directionality                           | Char | (DIR)                                 | Variable Qualifier | Qualifier for anatomical location further detailing directionality. Examples: "ANTERIOR", "LOWER", "PROXIMAL", "UPPER".                                                                                                                                                                                                     | Perm |
| ECPORTOT      | Portion or Totality                      | Char | (PORTOT)                              | Variable Qualifier | Qualifier for anatomical location further detailing distribution (i.e., arrangement of, apportioning of). Examples: "ENTIRE", "SINGLE", "SEGMENT".                                                                                                                                                                          | Perm |
| ECFAST        | Fasting Status                           | Char | (NY)                                  | Record Qualifier   | Indicator used to identify fasting status. Examples: "Y", "N".                                                                                                                                                                                                                                                              | Perm |
| ECPSTRG       | Pharmaceutical Strength                  | Num  |                                       | Record Qualifier   | Amount of an active ingredient expressed quantitatively per dosage unit, per unit of volume, or per unit of weight, according to the pharmaceutical dose form.                                                                                                                                                              | Perm |
| ECPSTRGU      | Pharmaceutical Strength Units            | Char | (UNIT)                                | Variable Qualifier | Unit for ECPSTRG. Examples: "mg/TABLET", "mg/mL".                                                                                                                                                                                                                                                                           | Perm |
| ECADJ         | Reason for Dose Adjustment               | Char |                                       | Record Qualifier   | Describes reason or explanation of why a dose is adjusted.                                                                                                                                                                                                                                                                  | Perm |
| TAETORD       | Planned Order of Element within Arm      | Num  |                                       | Timing             | Number that gives the planned order of the element within the arm.                                                                                                                                                                                                                                                          | Perm |
| EPOCH         | Epoch                                    | Char | (EPOCH)                               | Timing             | Trial epoch of the exposure as collected record. Examples: "RUN-IN", "TREATMENT".                                                                                                                                                                                                                                           | Perm |
| ECSTDTC       | Start Date/Time of Treatment             | Char | ISO 8601 datetime or interval         | Timing             | The date/time when administration of the treatment indicated by ECTRT and ECDOSE began.                                                                                                                                                                                                                                     | Exp  |
| ECENDTC       | End Date/Time of Treatment               | Char | ISO 8601 datetime or interval         | Timing             | The date/time when administration of the treatment indicated by ECTRT and ECDOSE ended. For administrations considered given at a point in time (e.g., oral tablet, pre-filled syringe injection), where only an administration date/time is collected, ECSTDTC should be copied to ECENDTC as the standard representation. | Exp  |
| ECSTDY        | Study Day of Start of Treatment          | Num  |                                       | Timing             | Study day of ECSTDTC relative to the sponsor-defined DM.RFSTDTC.                                                                                                                                                                                                                                                            | Perm |
| ECENDY        | Study Day of End of Treatment            | Num  |                                       | Timing             | Study day of ECENDTC relative to the sponsor-defined DM.RFSTDTC.                                                                                                                                                                                                                                                            | Perm |
| ECDUR         | Duration of Treatment                    | Char | ISO 8601 duration                     | Timing             | Collected duration of administration. Used only if collected on the CRF and not derived from start and end date/times.                                                                                                                                                                                                      | Perm |
| ECTPT         | Planned Time Point Name                  | Char |                                       | Timing             | Text description of time when administration should occur. This may be represented as an elapsed time relative to a fixed reference point, such as time of last dose. See ECTPTNUM and ECTPTREF.                                                                                                                            | Perm |
| ECTPTNUM      | Planned Time Point Number                | Num  |                                       | Timing             | Numerical version of ECTPT to aid in sorting.                                                                                                                                                                                                                                                                               | Perm |
| ECELTM        | Planned Elapsed Time from Time Point Ref | Char | ISO 8601 duration                     | Timing             | Planned elapsed time relative to the planned fixed reference (ECTPTREF). This variable is useful where there are repetitive measures. Not a clock time.                                                                                                                                                                     | Perm |
| ECTPTREF      | Time Point Reference                     | Char |                                       | Timing             | Name of the fixed reference point referred to by ECELTM, ECTPTNUM, and ECTPT. Examples: "PREVIOUS DOSE", "PREVIOUS MEAL".                                                                                                                                                                                                   | Perm |
| ECRFTDTC      | Date/Time of Reference Time Point        | Char | ISO 8601 datetime or interval         | Timing             | Date/time for a fixed reference time point defined by ECTPTREF.                                                                                                                                                                                                                                                             | Perm |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

EC – Assumptions

1. The EC domain model reflects protocol-specified study treatment administrations, as collected.

   a. EC should be used in all cases where collected exposure information cannot or should not be directly represented in the Exposure (EX) domain. For example, administrations collected in tablets when the protocol-specified unit is mg, or administrations collected in mL when the protocol-specified unit is mg/kg. Product accountability details (e.g., amount dispensed, amount returned) are represented in the DA domain, not in EC.

   b. Collected exposure data are in most cases represented in a combination of 1 or more of EC, DA, or Findings About Events or Interventions (FA) domains. If the entire EC dataset is an exact duplicate of the entire EX dataset, then EC is optional and at the sponsor's discretion.

   c. Collected exposure log data points descriptive of administrations typically reflect amounts at the product-level (e.g., number of tablets, number of mL).
2. Treatment description (ECTRT) is sponsor-defined and should reflect how the protocol-specified study treatment is known or referred to in data collection. In an open-label study, ECTRT should store the treatment name. In a masked study, if treatment is collected and known as tablet A to the subject or administrator, then ECTRT = "TABLET A". If, in a masked study, the treatment is not known by a synonym and the data are to be exchanged between sponsors, partners, and/or regulatory agency(s), then assign ECTRT the value of "MASKED".
3. ECMOOD is permissible; when implemented, it must be populated for all records.

   a. Values of ECMOOD, to date include:

   i. "SCHEDULED" (for collected subject-level intended dose records)

   ii. "PERFORMED" (for collected subject-level actual dose records)

   b. Qualifier variables should be populated with equal granularity across scheduled and performed records when known. For example, if ECDOSU and ECDOSFRQ are known at scheduling and administration, then the variables would be populated on both records. If ECLOC is determined at the time of administration, then it would be populated on the Performed record only.

   c. Appropriate timing variable(s) should be populated. Note: Details on Scheduled records may describe timing at a higher level than Performed records.

   d. ECOCCUR is generally not applicable for Scheduled records.

   e. An activity may be rescheduled or modified multiple times before being performed. Representation of Scheduled records is dependent on the collected, available data. If each rescheduled or modified activity is collected, then multiple Scheduled records may be represented. If only the final scheduled activity is collected, then it would be the only Scheduled record represented.
4. Doses not taken, not given, or missed

   a. The record qualifier --OCCUR, with value of "N", is available in domains based on the Interventions and Events General Observation Classes as the standard way to represent whether an intervention or event did not happen. In the EC domain, ECOCCUR value of "N" indicates a dose was not taken, not given, or missed. For example, if zero tablets are taken within a timeframe or zero mL is infused at a visit, then ECOCCUR = "N" is the standard representation of the collected doses not taken, not given, or missed. Dose amount variables (e.g., ECDOSE, ECDOSTXT) must not be set to zero (0) as an alternative method for indicating doses not taken, not given, or missed.

   b. The population of qualifier variables (e.g., grouping, record) and additional timing variables (e.g., date of collection, visit, time point) for records representing information collected about doses not taken, not given, or missed should be populated with equal granularity as administered records, when known and/or applicable. Qualifiers that indicate dose amount (e.g., ECDOSE, ECDOSTXT) may be populated with positive (non-zero) values in cases where the sponsor feels it is necessary and/or appropriate to represent specific dose amounts not taken, not given, or missed.

   c. If a reason why a dose was not given is collected, it is represented in ECREASOC, the reason why ECOCCUR = "N".
5. Timing variables

   a. Timing variables in the EC domain should reflect administrations by the intervals they were collected (e.g., constant-dosing intervals, visits, targeted dates like first dose, last dose).

   b. For administrations considered given at a point in time (e.g., oral tablet, pre-filled syringe injection), where only an administration date/time is collected, ECSTDTC should be copied to ECENDTC.
6. The degree of summarization of records from EC to EX is sponsor-defined to support study purpose and analysis. When the relationship between EC and EX records can be described in RELREC, then it should be defined. EX derivations must be described in the Define-XML document.
7. Additional interventions qualifiers

   a. --DOSTOT is under evaluation for potential deprecation and replacement with a mechanism to describe total dose over any interval of time (e.g., day, week, month). Sponsors considering ECDOSTOT may want to consider using other dose amount variables (ECDOSE or ECDOSTXT) in combination with frequency (ECDOSFRQ) and timing variables to represent the data.

   b. Any identifier variables, timing variables, or findings general observation-class qualifiers may be added to the EC domain, but the following qualifiers would generally not be used: --STAT and --REASND.

##### 6.1.3.3 Exposure/Exposure as Collected Examples

Example 1

This is an example of a double-blind study comparing drug X extended release (ER; 2 500-mg tablets once daily) vs. drug Z (2 250-mg tablets once daily). Per example CRFs, subject ABC1001 took 2 tablets from 2011-01-14 to 2011-01-28 and subject ABC2001 took 2 tablets within the same timeframe but missed dosing on 2011-01-24.

Exposure CRF:

Subject: ABC1001

| Bottle | Number of Tablets Taken Daily | Reason for Variation | Start Date | End Date   |
| ------ | ----------------------------- | -------------------- | ---------- | ---------- |
| A      | 2                             |                      | 2011-01-14 | 2011-01-28 |

Subject: ABC2001

| Bottle | Number of Tablets Taken Daily | Reason for Variation | Start Date | End Date   |
| ------ | ----------------------------- | -------------------- | ---------- | ---------- |
| A      | 2                             |                      | 2011-01-14 | 2011-01-23 |
| A      | 0                             | Patient mistake      | 2011-01-24 | 2011-01-24 |
| A      | 2                             |                      | 2011-01-25 | 2011-01-28 |

Upon unmasking, it became known that subject ABC1001 received drug X and Subject ABC2001 received drug Z. The EC dataset shows the administrations of study treatment as collected.

Rows 1-2, 4: Show treatments administered.

Row 3: Shows that the zero for Number of Tablets Taken Daily on the CRF was represented as ECOCCUR = "N". The reason this treatment did not occur is represented in ECREASOC.

ec.xpt

| Row S | TUDYID | DOMAIN | USUBJID | ECSEQ | ECLNKID      | ECTRT    | ECPRESP | ECOCCUR | ECREASOC        | ECDOSE | ECDOSU | ECDOSFRQ | EPOCH     | ECSTDTC     | ECENDTC     | ECSTDY | ECENDY |
| ----- | ------ | ------ | ------- | ----- | ------------ | -------- | ------- | ------- | --------------- | ------ | ------ | -------- | --------- | ----------- | ----------- | ------ | ------ |
| 1 A   | BC     | EC     | ABC1001 | 1     | A2- 20110114 | BOTTLE A | Y       | Y       |                 | 2      | TABLET | QD       | TREATMENT | 2011-01- 14 | 2011-01- 28 | 1      | 15     |
| 2 A   | BC     | EC     | ABC2001 | 1     | A2- 20110114 | BOTTLE A | Y       | Y       |                 | 2      | TABLET | QD       | TREATMENT | 2011-01- 14 | 2011-01- 23 | 1      | 10     |
| 3 A   | BC     | EC     | ABC2001 | 2     | A0- 20110124 | BOTTLE A | Y       | N       | PATIENT MISTAKE |        | TABLET | QD       | TREATMENT | 2011-01- 24 | 2011-01- 24 | 11     | 11     |
| 4 A   | BC     | EC     | ABC2001 | 3     | A2- 20110125 | BOTTLE A | Y       | Y       |                 | 2      | TABLET | QD       | TREATMENT | 2011-01- 25 | 2011-01- 28 | 12     | 15     |

The EX dataset shows the unmasked administrations. Two tablets from bottle A became 1000 mg of drug X extended release for subject ABC1001, but 500 mg of drug Z for subject ABC2001. Note that there is no record in the EX dataset for non-occurrence of study treatment. The non-occurrence of study drug for subject ABC2001 is reflected in the gap in time between the 2 EX records.

ex.xpt

| Row S | TUDYID | DOMAIN | USUBJID | EXSEQ | EXLNKID      | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM                 | EXDOSFRQ | EXROUTE | EPOCH     | EXSTDTC     | EXENDTC     | EXSTDY | EXENDY |
| ----- | ------ | ------ | ------- | ----- | ------------ | ------ | ------ | ------ | ------------------------ | -------- | ------- | --------- | ----------- | ----------- | ------ | ------ |
| 1 A   | BC     | EX     | ABC1001 | 1     | A2- 20110114 | DRUG X | 1000   | mg     | TABLET, EXTENDED RELEASE | QD       | ORAL    | TREATMENT | 2011-01- 14 | 2011-01- 28 | 1      | 15     |
| 2 A   | BC     | EX     | ABC2001 | 1     | A2- 20110114 | DRUG Z | 500    | mg     | TABLET                   | QD       | ORAL    | TREATMENT | 2011-01- 14 | 2011-01- 23 | 1      | 10     |
| 3 A   | BC     | EX     | ABC2001 | 2     | A2- 20110125 | DRUG Z | 500    | mg     | TABLET                   | QD       | ORAL    | TREATMENT | 2011-01- 25 | 2011-01- 28 | 12     | 15     |

The relrec.xpt example reflects a one-to-one dataset-level relationship between EC and EX using --LNKID.

relrec.xpt

| Row | STUDYID R | DOMAIN | USUBJID | IDVAR   | IDVARVAL | RELTYPE | RELID |
| --- | --------- | ------ | ------- | ------- | -------- | ------- | ----- |
| 1   | ABC E     | C      |         | ECLNKID |          | ONE     | 1     |
| 2   | ABC E     | X      |         | EXLNKID |          | ONE     | 1     |

Example 2

This example shows data from an open-label study. A subject received drug X as a 20 mg/mL solution administered across 3 injection sites to deliver a total dose of 3 mg/kg. The subject's weight was 100 kg.

Exposure CRF

| Visit             | 3          |
| ----------------- | ---------- |
| Date              | 2009-05-10 |
| Injection 1       |            |
| Volume Given (mL) | 5          |
| Location          | ABDOMEN    |
| Side              | LEFT       |
| Injection 2       |            |
| Volume Given (mL) | 5          |
| Location          | ABDOMEN    |
| Side              | CENTER     |
| Injection 3       |            |
| Volume Given (mL) | 5          |
| Location          | ABDOMEN    |
| Side              | RIGHT      |

The collected administration amounts, in mL, and their locations are represented in the EC dataset.

ec.xpt

| Row | STUDYID DO | MAIN | USUBJID | ECSEQ | ECSPID | ECLNKID | ECTRT  | ECPRESP | ECOCCUR | ECDOSE | ECDOSU | ECDOSFRM  | ECDOSFRQ | ECROUTE      | ECLOC            | ECLAT  | VISITNUM | VISIT   | EPOCH     | ECSTDTC     | ECENDTC     | ECSTDY | ECENDY |
| --- | ---------- | ---- | ------- | ----- | ------ | ------- | ------ | ------- | ------- | ------ | ------ | --------- | -------- | ------------ | ---------------- | ------ | -------- | ------- | --------- | ----------- | ----------- | ------ | ------ |
| 1   | ABC EC     |      | ABC3001 | 1     | INJ1   | V3      | DRUG X | Y       | Y       | 5      | mL     | INJECTION | ONCE     | SUBCUTANEOUS | ABDOMINAL CAVITY | LEFT   | 3        | VISIT 3 | TREATMENT | 2009-05- 10 | 2009-05- 10 | 21     | 21     |
| 2   | ABC EC     |      | ABC3001 | 2     | INJ2   | V3      | DRUG X | Y       | Y       | 5      | mL     | INJECTION | ONCE     | SUBCUTANEOUS | ABDOMINAL CAVITY | CENTER | 3        | VISIT 3 | TREATMENT | 2009-05- 10 | 2009-05- 10 | 21     | 21     |
| 3   | ABC EC     |      | ABC3001 | 3     | INJ3   | V3      | DRUG X | Y       | Y       | 5      | mL     | INJECTION | ONCE     | SUBCUTANEOUS | ABDOMINAL CAVITY | RIGHT  | 3        | VISIT 3 | TREATMENT | 2009-05- 10 | 2009-05- 10 | 21     | 21     |

The sponsor considered the 3 injections to constitute a single administration, so the EX dataset shows the total dose given in the protocol-specified unit, mg/kg. EXLOC = "ABDOMEN" is included because this location was common to all injections, but EXLAT was not included. If the sponsor had chosen to represent laterality in the EX record, this would have been handled as described in Section 4.2.8.3, Multiple Values for a Non-result Qualifier Variable.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID | EXSEQ | EXSPID E | XLNKID | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM  | EXDOSFRQ | EXROUTE      | EXLOC   | VISITNUM | VISIT   | EPOCH     | EXSTDTC    | EXENDTC    | EXSTDY | EXENDY |
| --- | ------- | ------ | ------- | ----- | -------- | ------ | ------ | ------ | ------ | --------- | -------- | ------------ | ------- | -------- | ------- | --------- | ---------- | ---------- | ------ | ------ |
| 1   | ABC     | EX     | ABC3001 | 1     | V        | 3      | DRUG X | 3      | mg/kg  | INJECTION | ONCE     | SUBCUTANEOUS | ABDOMEN | 3        | VISIT 3 | TREATMENT | 2009-05-10 | 2009-05-10 | 21     | 21     |

The relrec.xpt example reflects a many-to-one dataset-level relationship between EC and EX using --LNKID.

relrec.xpt

| Row | STUDYID | RDOMAIN | USUBJID I | DVAR    | IDVARVAL | RELTYPE | RELID |
| --- | ------- | ------- | --------- | ------- | -------- | ------- | ----- |
| 1   | ABC     | EC      |           | ECLNKID |          | MANY    | 1     |
| 2   | ABC     | EX      |           | EXLNKID |          | ONE     | 1     |

Example 3

The study in this example was a double-blind study comparing 10, 20, and 30 mg of Drug X once daily vs. placebo. Study treatment was given as 1 tablet each from bottles A, B, and C taken together once daily. The subject in this example took:

- 1 tablet from bottles A, B and C from 2011-01-14 to 2011-01-20
- 0 tablets from bottle B on 2011-01-21, then 2 tablets on 2011-01-22
- 1 tablet from bottles A and C on 2011-01-21 and 2011-01-22
- 1 tablet from ottles A, B and C from 2011-01-23 to 2011-01-28

The EC dataset shows administrations as collected, in tablets.

ec.xpt

| Row | STUDYID | DOMAIN | USUBJID | ECSEQ | ECTRT    | ECPRESP | ECOCCUR | ECDOSE | ECDOSU | ECDOSFRQ | EPOCH     | ECSTDTC    | ECENDTC    | ECSTDY | ECENDY |
| --- | ------- | ------ | ------- | ----- | -------- | ------- | ------- | ------ | ------ | -------- | --------- | ---------- | ---------- | ------ | ------ |
| 1   | ABC     | EC     | ABC4001 | 1     | BOTTLE A | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2011-01-14 | 2011-01-28 | 1      | 15     |
| 2   | ABC     | EC     | ABC4001 | 2     | BOTTLE C | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2011-01-14 | 2011-01-28 | 1      | 15     |
| 3   | ABC     | EC     | ABC4001 | 3     | BOTTLE B | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2011-01-14 | 2011-01-20 | 1      | 7      |
| 4   | ABC     | EC     | ABC4001 | 4     | BOTTLE B | Y       | N       |        | TABLET | QD       | TREATMENT | 2011-01-21 | 2011-01-21 | 8      | 8      |
| 5   | ABC     | EC     | ABC4001 | 5     | BOTTLE B | Y       | Y       | 2      | TABLET | QD       | TREATMENT | 2011-01-22 | 2011-01-22 | 9      | 9      |
| 6   | ABC     | EC     | ABC4001 | 6     | BOTTLE B | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2011-01-23 | 2011-01-28 | 10     | 15     |

Upon unmasking, it became known that the subject was randomized to drug X 20 mg and that:

- Bottle A contained 10 mg/tablet
- Bottle B contained 10 mg/tablet
- Bottle C contained placebo (i.e., 0 mg of active ingredient/tablet)

The EX dataset shows the doses administered in the protocol-specified unit (mg). The sponsor considered an administration to consist of the total amount for bottles A, B, and C. The derivation of EX records from multiple EC records should be shown in the Define-XML document.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID | EXSEQ | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM | EXDOSFRQ | EXROUTE | EPOCH     | EXSTDTC    | EXENDTC    | EXSTDY | EXENDY |
| --- | ------- | ------ | ------- | ----- | ------ | ------ | ------ | -------- | -------- | ------- | --------- | ---------- | ---------- | ------ | ------ |
| 1   | ABC     | EX     | ABC4001 | 1     | DRUG X | 20     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2011-01-14 | 2011-01-20 | 1      | 7      |
| 2   | ABC     | EX     | ABC4001 | 2     | DRUG X | 10     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2011-01-21 | 2011-01-21 | 8      | 8      |
| 3   | ABC     | EX     | ABC4001 | 3     | DRUG X | 30     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2011-01-22 | 2011-01-22 | 9      | 9      |
| 4   | ABC     | EX     | ABC4001 | 4     | DRUG X | 20     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2011-01-23 | 2011-01-28 | 10     | 15     |

Example 4

The study in this example was an open-label study examining the tolerability of different doses of drug A. The study drug was taken orally, daily for 3 months. Dose adjustments were allowed as needed in response to tolerability or efficacy issues.

The EX dataset shows administrations collected in the protocol-specified unit, mg. No EC dataset was needed because the open-label administrations were collected in the protocol-specified unit; EC would be an exact duplicate of the entire EX domain.

ex.xpt

| Row S | TUDYID | DOMAIN | USUBJID  | EXSEQ | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM | EXDOSFRQ | EXROUTE | EXADJ                                | EPOCH     | EXSTDTC    | EXENDTC    |
| ----- | ------ | ------ | -------- | ----- | ------ | ------ | ------ | -------- | -------- | ------- | ------------------------------------ | --------- | ---------- | ---------- |
| 1 3   | 7841   | EX     | 37841001 | 1     | DRUG A | 20     | mg     | TABLET   | QD       | ORAL    |                                      | TREATMENT | 2002-07-01 | 2002-10-01 |
| 2 3   | 7841   | EX     | 37841002 | 1     | DRUG A | 20     | mg     | TABLET   | QD       | ORAL    |                                      | TREATMENT | 2002-04-02 | 2002-04-21 |
| 3 3   | 7841   | EX     | 37841002 | 2     | DRUG A | 15     | mg     | TABLET   | QD       | ORAL    | Reduced due to toxicity              | TREATMENT | 2002-04-22 | 2002-07-01 |
| 4 3   | 7841   | EX     | 37841003 | 1     | DRUG A | 20     | mg     | TABLET   | QD       | ORAL    |                                      | TREATMENT | 2002-05-09 | 2002-06-01 |
| 5 3   | 7841   | EX     | 37841003 | 2     | DRUG A | 25     | mg     | TABLET   | QD       | ORAL    | Increased due to suboptimal efficacy | TREATMENT | 2002-06-02 | 2002-07-01 |
| 6 3   | 7841   | EX     | 37841003 | 3     | DRUG A | 30     | mg     | TABLET   | QD       | ORAL    | Increased due to suboptimal efficacy | TREATMENT | 2002-07-02 | 2002-08-01 |

Example 5

This is an example of a double-blind study design comparing 10 and 20 mg of drug X vs. placebo taken daily, morning and evening, for a week.

Subject ABC5001

| Bottle | Time Point | Number of Tablets Taken | Start Date | End Date   |
| ------ | ---------- | ----------------------- | ---------- | ---------- |
| A      | AM         | 1                       | 2012-01-01 | 2012-01-08 |
| B      | PM         | 1                       | 2012-01-01 | 2012-01-08 |

Subject ABC5002

| Bottle | Time Point | Number of Tablets Taken | Start Date | End Date   |
| ------ | ---------- | ----------------------- | ---------- | ---------- |
| A      | AM         | 1                       | 2012-02-01 | 2012-02-08 |
| B      | PM         | 1                       | 2012-02-01 | 2012-02-08 |

Subject ABC5003

| Bottle | Time Point | Number of Tablets Taken | Start Date | End Date   |
| ------ | ---------- | ----------------------- | ---------- | ---------- |
| A      | AM         | 1                       | 2012-03-01 | 2012-03-08 |
| B      | PM         | 1                       | 2012-03-01 | 2012-03-08 |

The EC dataset shows the administrations as collected. The time-point variables ECTPT and ECTPTNUM were used to describe the time of day of administration. This use of time-point variables is novel, representing data about multiple time points, 1 on each day of administration, rather than data for a single time point.

ec.xpt

| Row | STUDYID | DOMAIN | USUBJID | ECSEQ | ECLNKID              | ECTRT    | ECPRESP | ECOCCUR | ECDOSE | ECDOSU | ECDOSFRQ | EPOCH     | ECSTDTC    | ECENDTC    | ECSTDY | ECENDY | ECTPT | ECTPTNUM |
| --- | ------- | ------ | ------- | ----- | -------------------- | -------- | ------- | ------- | ------ | ------ | -------- | --------- | ---------- | ---------- | ------ | ------ | ----- | -------- |
| 1   | ABC     | EC     | ABC5001 | 1     | 20120101-20120108-AM | BOTTLE A | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-01-01 | 2012-01-08 | 1      | 8      | AM    | 1        |
| 2   | ABC     | EC     | ABC5001 | 2     | 20120101-20120108-PM | BOTTLE B | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-01-01 | 2012-01-08 | 1      | 8      | PM    | 2        |
| 3   | ABC     | EC     | ABC5002 | 1     | 20120201-20120208-AM | BOTTLE A | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-02-01 | 2012-02-08 | 1      | 8      | AM    | 1        |
| 4   | ABC     | EC     | ABC5002 | 2     | 20120201-20120208-PM | BOTTLE B | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-02-01 | 2012-02-08 | 1      | 8      | PM    | 2        |
| 5   | ABC     | EC     | ABC5003 | 1     | 20120301-20120308-AM | BOTTLE A | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-03-01 | 2012-03-08 | 1      | 8      | AM    | 1        |
| 6   | ABC     | EC     | ABC5003 | 2     | 20120301-20120308-PM | BOTTLE B | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-03-01 | 2012-03-08 | 1      | 8      | PM    | 2        |

The EX dataset shows the unmasked administrations in the protocol specified unit, mg. Amount of placebo was represented as 0 mg. The sponsor chose to represent the administrations at the time-point level.

Rows 1-2: Show administrations for a subject who was randomized to the 20 mg drug X arm.

Rows 3-4: Show administrations for a subject who was randomized to the 10 mg drug X arm.

Rows 5-6: Show administrations for a subject who was randomized to the placebo arm.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID | EXSEQ | EXLNKID              | EXTRT   | EXDOSE | EXDOSU | EXDOSFRM | EXDOSFRQ | EXROUTE | EPOCH     | EXSTDTC    | EXENDTC    | EXSTDY | EXENDY | EXTPT | EXTPTNUM |
| --- | ------- | ------ | ------- | ----- | -------------------- | ------- | ------ | ------ | -------- | -------- | ------- | --------- | ---------- | ---------- | ------ | ------ | ----- | -------- |
| 1   | ABC     | EX     | ABC5001 | 1     | 20120101-20120108-AM | DRUG X  | 10     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-01-01 | 2012-01-08 | 1      | 8      | AM    | 1        |
| 2   | ABC     | EX     | ABC5001 | 2     | 20120101-20120108-PM | DRUG X  | 10     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-01-01 | 2012-01-08 | 1      | 8      | PM    | 2        |
| 3   | ABC     | EX     | ABC5002 | 1     | 20120201-20120208-AM | DRUG X  | 10     | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-02-01 | 2012-02-08 | 1      | 8      | AM    | 1        |
| 4   | ABC     | EX     | ABC5002 | 2     | 20120201-20120208-PM | PLACEBO | 0      | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-02-01 | 2012-02-08 | 1      | 8      | PM    | 2        |
| 5   | ABC     | EX     | ABC5003 | 1     | 20120301-20120308-AM | PLACEBO | 0      | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-03-01 | 2012-03-08 | 1      | 8      | AM    | 1        |
| 6   | ABC     | EX     | ABC5003 | 2     | 20120301-20120308-PM | PLACEBO | 0      | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-03-01 | 2012-03-08 | 1      | 8      | PM    | 2        |

The relrec.xpt example reflects a one-to-one dataset-level relationship between EC and EX using --LNKID.

relrec.xpt

| Row | STUDYID R | DOMAIN U | SUBJID | IDVAR   | IDVARVAL | RELTYPE | RELID |
| --- | --------- | -------- | ------ | ------- | -------- | ------- | ----- |
| 1   | ABC E     | C        |        | ECLNKID |          | ONE     | 1     |
| 2   | ABC E     | X        |        | EXLNKID |          | ONE     | 1     |

Example 6

The study in this example was a single-crossover study comparing once-daily oral administration of drug A 20 mg capsules with drug B 30 mg coated tablets. The study drug was taken for 3 consecutive mornings, 30 minutes prior to a standardized breakfast. There was a 6-day washout period between treatments.

The following CRFs show data for 2 subjects.

Subject 56789001

| Period 1 |                        |                      |                   |                  | Period 2 |                        |                       |                  |                  |
| -------- | ---------------------- | -------------------- | ----------------- | ---------------- | -------- | ---------------------- | --------------------- | ---------------- | ---------------- |
| Day      | Bottle 1 # of capsules | Bottle 2 # of tablet | Start Date/Time s | End Date/Time    | Day      | Bottle 1 # of capsules | Bottle 2 # of tablets | Start Date/Time  | End Date/Time    |
| 1        | 1                      | 1                    | 2002-07-01T07:30  | 2002-07-01T07:30 | 1        | 1                      | 1                     | 2002-07-09T07:30 | 2002-07-09T07:30 |
| 2        | 1                      | 1                    | 2002-07-02T07:30  | 2002-07-02T07:30 | 2        | 1                      | 1                     | 2002-07-10T07:30 | 2002-07-10T07:30 |
| 3        | 1                      | 1                    | 2002-07-03T07:32  | 2002-07-03T07:32 | 3        | 1                      | 1                     | 2002-07-11T07:34 | 2002-07-11T07:34 |

Subject 56789003

| Period 1 |                        |                       |                  |                  | Period 2 |                        |                      |                   |                  |
| -------- | ---------------------- | --------------------- | ---------------- | ---------------- | -------- | ---------------------- | -------------------- | ----------------- | ---------------- |
| Day      | Bottle 1 # of capsules | Bottle 2 # of tablets | Start Date/Time  | End Date/Time    | Day      | Bottle 1 # of capsules | Bottle 2 # of tablet | Start Date/Time s | End Date/Time    |
| 1        | 1                      | 1                     | 2002-07-03T07:30 | 2002-07-03T07:30 | 1        | 1                      | 1                    | 2002-07-11T07:30  | 2002-07-11T07:30 |
| 2        | 1                      | 1                     | 2002-07-04T07:24 | 2002-07-04T07:24 | 2        | 1                      | 1                    | 2002-07-12T07:43  | 2002-07-12T07:43 |
| 3        | 1                      | 1                     | 2002-07-05T07:24 | 2002-07-05T07:24 | 3        | 1                      | 1                    | 2002-07-13T07:38  | 2002-07-13T07:38 |

The EC dataset shows administrations as collected.

ec.xpt

| Row | STUDYID | DOMAIN | USUBJID  | ECSEQ | ECTRT    | ECPRESP | ECOCCUR | ECDOSE | ECDOSU         | ECDOSFRM       | ECDOSFRQ | ECROUTE | EPOCH       | ECSTDTC           | ECENDTC           | ECSTDY | ECENDY | ECTPT            | ECELTM | ECTPTREF      |
| --- | ------- | ------ | -------- | ----- | -------- | ------- | ------- | ------ | -------------- | -------------- | -------- | ------- | ----------- | ----------------- | ----------------- | ------ | ------ | ---------------- | ------ | ------------- |
| 1   | 56789   | EC     | 56789001 | 1     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 01T07:30 | 2002-07- 01T07:30 | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 2   | 56789   | EC     | 56789001 | 2     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 01T07:30 | 2002-07- 01T07:30 | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 3   | 56789   | EC     | 56789001 | 3     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 02T07:30 | 2002-07- 02T07:30 | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 4   | 56789   | EC     | 56789001 | 4     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 02T07:30 | 2002-07- 02T07:30 | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 5   | 56789   | EC     | 56789001 | 5     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 03T07:32 | 2002-07- 03T07:32 | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 6   | 56789   | EC     | 56789001 | 6     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 03T07:32 | 2002-07- 03T07:32 | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 7   | 56789   | EC     | 56789001 | 7     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 09T07:30 | 2002-07- 09T07:30 | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 8   | 56789   | EC     | 56789001 | 8     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 09T07:30 | 2002-07- 09T07:30 | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 9   | 56789   | EC     | 56789001 | 9     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 10T07:30 | 2002-07- 10T07:30 | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 10  | 56789   | EC     | 56789001 | 10    | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 10T07:30 | 2002-07- 10T07:30 | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 11  | 56789   | EC     | 56789001 | 11    | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 11T07:34 | 2002-07- 11T07:34 | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 12  | 56789   | EC     | 56789001 | 12    | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 11T07:34 | 2002-07- 11T07:34 | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 13  | 56789   | EC     | 56789003 | 1     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 03T07:30 | 2002-07- 03T07:30 | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 14  | 56789   | EC     | 56789003 | 2     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 03T07:30 | 2002-07- 03T07:30 | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 15  | 56789   | EC     | 56789003 | 3     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 04T07:24 | 2002-07- 04T07:24 | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 16  | 56789   | EC     | 56789003 | 4     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 04T07:24 | 2002-07- 04T07:24 | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 17  | 56789   | EC     | 56789003 | 5     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07- 05T07:24 | 2002-07- 05T07:24 | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 18  | 56789   | EC     | 56789003 | 6     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07- 05T07:24 | 2002-07- 05T07:24 | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 19  | 56789   | EC     | 56789003 | 7     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 11T07:30 | 2002-07- 11T07:30 | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 20  | 56789   | EC     | 56789003 | 8     | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 11T07:30 | 2002-07- 11T07:30 | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 21  | 56789   | EC     | 56789003 | 9     | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 12T07:43 | 2002-07- 12T07:43 | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 22  | 56789   | EC     | 56789003 | 10    | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 12T07:43 | 2002-07- 12T07:43 | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 23  | 56789   | EC     | 56789003 | 11    | BOTTLE 1 | Y       | Y       | 1      | CAPSULE        | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07- 13T07:38 | 2002-07- 13T07:38 | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 24  | 56789   | EC     | 56789003 | 12    | BOTTLE 2 | Y       | Y       | 1      | TABLET, COATED | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07- 13T07:38 | 2002-07- 13T07:38 | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |

The EX dataset shows the unblinded administrations.

Rows 1-12: Unblinding revealed that subject 56789001 received placebo-coated tablets during the first treatment epoch and placebo capsules during the second treatment epoch.

Rows 13-24: Unblinding revealed that subject 56789003 received placebo capsules during the first treatment epoch and placebo-coated tablets during the second treatment epoch.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID  | EXSEQ | EXTRT   | EXDOSE | EXDOSU | EXDOSFRM       | EXDOSFRQ | EXROUTE | EPOCH       | EXSTDTC          | EXENDTC | EXSTDY | EXENDY | EXTPT            | EXELTM | EXTPTREF      |
| --- | ------- | ------ | -------- | ----- | ------- | ------ | ------ | -------------- | -------- | ------- | ----------- | ---------------- | ------- | ------ | ------ | ---------------- | ------ | ------------- |
| 1   | 56789   | EX     | 56789001 | 1     | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-01T07:30 |         | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 2   | 56789   | EX     | 56789001 | 2     | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-01T07:30 |         | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 3   | 56789   | EX     | 56789001 | 3     | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-02T07:30 |         | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 4   | 56789   | EX     | 56789001 | 4     | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-02T07:30 |         | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 5   | 56789   | EX     | 56789001 | 5     | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-03T07:32 |         | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 6   | 56789   | EX     | 56789001 | 6     | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-03T07:32 |         | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 7   | 56789   | EX     | 56789001 | 7     | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-09T07:30 |         | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 8   | 56789   | EX     | 56789001 | 8     | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-09T07:30 |         | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 9   | 56789   | EX     | 56789001 | 9     | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-10T07:30 |         | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 10  | 56789   | EX     | 56789001 | 10    | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-10T07:30 |         | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 11  | 56789   | EX     | 56789001 | 11    | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-11T07:34 |         | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 12  | 56789   | EX     | 56789001 | 12    | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-11T07:34 |         | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 13  | 56789   | EX     | 56789003 | 1     | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-03T07:30 |         | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 14  | 56789   | EX     | 56789003 | 2     | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-03T07:30 |         | 1      | 1      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 15  | 56789   | EX     | 56789003 | 3     | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-04T07:24 |         | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 16  | 56789   | EX     | 56789003 | 4     | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-04T07:24 |         | 2      | 2      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 17  | 56789   | EX     | 56789003 | 5     | PLACEBO | 0      | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 1 | 2002-07-05T07:24 |         | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 18  | 56789   | EX     | 56789003 | 6     | DRUG B  | 30     | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 1 | 2002-07-05T07:24 |         | 3      | 3      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 19  | 56789   | EX     | 56789003 | 7     | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-11T07:30 |         | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 20  | 56789   | EX     | 56789003 | 8     | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-11T07:30 |         | 9      | 9      | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 21  | 56789   | EX     | 56789003 | 9     | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-12T07:43 |         | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 22  | 56789   | EX     | 56789003 | 10    | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-12T07:43 |         | 10     | 10     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 23  | 56789   | EX     | 56789003 | 11    | DRUG A  | 20     | mg     | CAPSULE        | QD       | ORAL    | TREATMENT 2 | 2002-07-13T07:38 |         | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |
| 24  | 56789   | EX     | 56789003 | 12    | PLACEBO | 0      | mg     | TABLET, COATED | QD       | ORAL    | TREATMENT 2 | 2002-07-13T07:38 |         | 11     | 11     | 30 MINUTES PRIOR | -PT30M | STD BREAKFAST |

Example 7

The study in this example involved weekly infusions of drug Z 10 mg/kg. If a subject experienced a dose-limiting toxicity (DLT), the intended dose could be reduced to 7.5 mg/kg.

The example CRF below was for subject ABC123-0201, who weighed 55 kg. The CRF shows that:

- The subject's first administration of drug Z was on 2009-02-13; the intended dose was 10 mg/kg, but the actual amount given was 99 mL at 5.5 mg/mL, so the actual dose was 9.9 mg/kg.
- The subject's second administration of drug Z occurred on 2009-02-20; the intended dose was reduced to 7.5 mg/kg due to dose-limiting toxicity, and the infusion was stopped early due to an injection site reaction. However, the actual amount given was 35 mL at a concentration of 4.12 mg/mL, so the calculated actual dose was 2.6 mg/kg.
- The subject's third administration was intended to occur on 2009-02-27; the intended dose was 7.5 mg/kg but, due to a personal reason, the administration did not occur.

| Visit                                      | 1                                                                                                        | 2                                                                                                        | 3                                                                                                                        |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Intended Dose                              | • 10 mg/kg • 7.5 mg/kg                                                                                 | • 10 mg/kg • 7.5 mg/kg                                                                                 | • 10 mg/kg • 7.5 mg/kg                                                                                                 |
| Reason for Dose Adjustment                 | • Dose-limiting toxicity                                                                                | • Dose-limiting toxicity                                                                                | • Dose-limiting toxicity                                                                                                |
| Dose Administered                          | • Yes • No If no, give reason: • Treatment discontinued due to disease progression • Other, specify: | • Yes • No If no, give reason: • Treatment discontinued due to disease progression • Other, specify: | • Yes • No If no, give reason: • Treatment discontinued due to disease progression • Other, specify: Personal reason |
| Date                                       | ________________________ 13-FEB-2009                                                                     | ________________________ 20-FEB-2009                                                                     | 27-FEB-2009                                                                                                              |
| Start Time (24 hour clock)                 | 10:00                                                                                                    | 11:00                                                                                                    |                                                                                                                          |
| End Time (24 hour clock)                   | 10:45                                                                                                    | 11:20                                                                                                    |                                                                                                                          |
| Amount (mL)                                | 99 mL                                                                                                    | 35 mL                                                                                                    | 0 mL                                                                                                                     |
| Concentration                              | 5.5 mg/mL                                                                                                | 4.12 mg/mL                                                                                               | 4.12 mg/mL                                                                                                               |
| If dose was adjusted, what was the reason: | • Injection site reaction • Adverse event • Other, specify:                                           | • Injection site reaction • Adverse event • Other, specify:                                           | • Injection site reaction • Adverse event • Other, specify:                                                           |

The EC dataset shows both intended and actual doses of Drug Z, as collected.

Rows 1, 3, 5: Show the collected intended dose levels (mg/kg) and ECMOOD is "SCHEDULED". Scheduled dose is represented in mg/mL.

Rows 2, 4: Show the collected actual administration amounts (mL) and ECMOOD is "PERFORMED". Actual doses are represented using dose in mL and concentration (pharmaceutical strength) in mg/mL.

Row 6: Shows a dose that was not given. ECREASOC shows the reason that ECOCCUR = "N", and ECDOSE is null.

ec.xpt

| Row | STUDYID | DOMAIN | USUBJID      | ECSEQ | ECLNKID        | ECLNKGRP | ECTRT  | ECMOOD    | ECPRESP | ECOCCUR | ECREASOC        | ECDOSE | ECDOSU | ECPSTRG | ECPSTRGU | ECADJ                  | VISITNUM | VISIT   | EPOCH     | ECSTDTC           | ECENDTC           | ECSTDY | ECENDY |
| --- | ------- | ------ | ------------ | ----- | -------------- | -------- | ------ | --------- | ------- | ------- | --------------- | ------ | ------ | ------- | -------- | ---------------------- | -------- | ------- | --------- | ----------------- | ----------------- | ------ | ------ |
| 1   | ABC123  | EC     | ABC123- 0201 | 1     |                | V1       | DRUG Z | SCHEDULED |         |         |                 | 10     | mg/kg  |         |          |                        | 1        | VISIT 1 | TREATMENT | 2009-02-13        | 2009-02-13        | 1      | 1      |
| 2   | ABC123  | EC     | ABC123- 0201 | 2     | 20090213 T1000 | V1       | DRUG Z | PERFORMED | Y       | Y       |                 | 99     | mL     | 5.5     | mg/mL    |                        | 1        | VISIT 1 | TREATMENT | 2009-02- 13T10:00 | 2009-02- 13T10:45 | 1      | 1      |
| 3   | ABC123  | EC     | ABC123- 0201 | 3     |                | V2       | DRUG Z | SCHEDULED |         |         |                 | 7.5    | mg/kg  |         |          | Dose limiting toxicity | 2        | VISIT 2 | TREATMENT | 2009-02-20        | 2009-02-20        | 8      | 8      |
| 4   | ABC123  | EC     | ABC123- 0201 | 4     | 20090220 T1100 | V2       | DRUG Z | PERFORMED | Y       | Y       |                 | 35     | mL     | 4.12    | mg/mL    |                        | 2        | VISIT 2 | TREATMENT | 2009-02- 20T11:00 | 2009-02- 20T11:20 | 8      | 8      |
| 5   | ABC123  | EC     | ABC123- 0201 | 5     |                | V3       | DRUG Z | SCHEDULED |         |         |                 | 7.5    | mg/kg  |         |          |                        | 3        | VISIT 3 | TREATMENT | 2009-02-27        | 2009-02-27        | 15     | 15     |
| 6   | ABC123  | EC     | ABC123- 0201 | 6     | 20090227       | V3       | DRUG Z | PERFORMED | Y       | N       | PERSONAL REASON |        | mL     | 4.12    | mg/mL    |                        | 3        | VISIT 3 | TREATMENT | 2009-02-27        | 2009-02-27        | 15     | 15     |

The EX dataset shows the administrations in protocol-specified unit (mg/kg). There is no record for the intended third dose that was not given. Intended doses in EC (records with ECMOOD = "SCHEDULED") can be compared with actual doses in EX.

Row 1: Shows the subject's first dose.

Row 2: Shows the subject's second dose. The collected explanation for the adjusted dose amount administered at visit 2 is in EXADJ.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID    | EXSEQ | EXLNKID       | EXLNKGRP | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM | EXDOSFRQ   | EXROUTE     | EXADJ                   | VISITNUM | VISIT   | EPOCH     | EXSTDTC           | EXENDTC           | EXSTDY | EXENDY |
| --- | ------- | ------ | ---------- | ----- | ------------- | -------- | ------ | ------ | ------ | -------- | ---------- | ----------- | ----------------------- | -------- | ------- | --------- | ----------------- | ----------------- | ------ | ------ |
| 1   | ABC123  | EX A 0 | BC123- 201 | 1     | 20090213T1000 | V1       | DRUG Z | 9.9    | mg/kg  | SOLUTION | CONTINUOUS | INTRAVENOUS |                         | 1        | VISIT 1 | TREATMENT | 2009-02- 13T10:00 | 2009-02- 13T10:00 | 1      | 1      |
| 2   | ABC123  | EX A 0 | BC123- 201 | 2     | 20090220T1100 | V2       | DRUG Z | 2.6    | mg/kg  | SOLUTION | CONTINUOUS | INTRAVENOUS | Injection site reaction | 2        | VISIT 2 | TREATMENT | 2009-02- 20T11:00 | 2009-02- 20T11:00 | 8      | 8      |

To complete this example the relevant records from the Vital Signs domain are represented below, to show the collected weight of the subject which was used for the dosing calculations.

vs.xpt

| Row | STUDYID | DOMAIN | USUBJID     | VSSEQ | VSLNKID       | VSLNKGRP | VSTESTCD | VSTEST | VSORRES | VSORRESU | VSSTRESC | VSSTRESN | VSSTRESU | VSLOBXFL | VISITNUM | VISIT   | VSDTC      | EPOCH     |
| --- | ------- | ------ | ----------- | ----- | ------------- | -------- | -------- | ------ | ------- | -------- | -------- | -------- | -------- | -------- | -------- | ------- | ---------- | --------- |
| 1   | ABC123  | VS     | ABC123-0201 | 1     | 20090213T1000 | V1       | WEIGHT   | Weight | 55      | kg       | 55       | 55       | kg       | Y        | 1        | VISIT 1 | 2009-02-13 | TREATMENT |
| 2   | ABC123  | VS     | ABC123-0201 | 2     | 20090220T1100 | V2       | WEIGHT   | Weight | 55      | kg       | 55       | 55       | kg       |          | 2        | VISIT 2 | 2009-02-20 | TREATMENT |

The RELREC dataset represents relationships between EC, EX, and VS.

Rows 1-3: Represent the one-to-one-to-one relationship between "PERFORMED" records in EC, records in EX, and records in VS using --LNKID, .

Rows 4-6: Represent the many-to-one-to-one relationship between many records in EC (both "SCHEDULED" and "PERFORMED"), one record in EX, and one record in VS (for each visit), using --LNKGRP.

relrec.xpt

| Row | STUDYID | RDOMAIN | USUBJID | IDVAR    | IDVARVAL | RELTYPE | RELID |
| --- | ------- | ------- | ------- | -------- | -------- | ------- | ----- |
| 1   | ABC123  | EC      |         | ECLNKID  |          | ONE     | 1     |
| 2   | ABC123  | EX      |         | EXLNKID  |          | ONE     | 1     |
| 6   | ABC123  | VS      |         | VSLNKID  |          | ONE     | 1     |
| 3   | ABC123  | EC      |         | ECLNKGRP |          | MANY    | 2     |
| 4   | ABC123  | EX      |         | EXLNKGRP |          | ONE     | 2     |
| 6   | ABC123  | VS      |         | VSLNKGRP |          | ONE     | 2     |

Example 8

In this example, a 100 mg tablet is scheduled to be taken daily. Start and end of dosing were collected, along with deviations from the planned daily dosing. Note: This method of data collection design is not consistent with current CDASH standards.

| First Dose Date | Last Dose Date |
| --------------- | -------------- |
| 2012-01-13      | 2012-01-20     |

| Date       | Number of Doses Daily If/When Deviated from Plan |
| ---------- | ------------------------------------------------ |
| 2012-01-15 | 0                                                |
| 2012-01-16 | 2                                                |

The EC dataset shows administrations as collected.

Row 1: Shows the overall dosing interval from first dose date to last dose date.

Row 2: Shows the missed dose on 2012-01-15, which falls within the overall dosing interval.

Row 3: Shows a doubled dose on 2012-01-16, which also falls within the overall dosing interval.

ec.xpt

| Row | STUDYID | DOMAIN | USUBJID | ECSEQ | ECTRT    | ECCAT                       | ECPRESP | ECOCCUR | ECDOSE | ECDOSU | ECDOSFRQ | EPOCH     | ECSTDTC    | ECENDTC    | ECSTDY | ECENDY |
| --- | ------- | ------ | ------- | ----- | -------- | --------------------------- | ------- | ------- | ------ | ------ | -------- | --------- | ---------- | ---------- | ------ | ------ |
| 1   | ABC     | EC     | ABC7001 | 1     | BOTTLE A | FIRST TO LAST DOSE INTERVAL | Y       | Y       | 1      | TABLET | QD       | TREATMENT | 2012-01-13 | 2012-01-20 | 1      | 8      |
| 2   | ABC     | EC     | ABC7001 | 2     | BOTTLE A | EXCEPTION DOSE              | Y       | N       |        | TABLET | QD       | TREATMENT | 2012-01-15 | 2012-01-15 | 3      | 3      |
| 3   | ABC     | EC     | ABC7001 | 3     | BOTTLE A | EXCEPTION DOSE              | Y       | Y       | 2      | TABLET | QD       | TREATMENT | 2012-01-16 | 2012-01-16 | 4      | 4      |

The EX dataset shows the unmasked treatment for this subject, "DRUG X", and represents dosing in nonoverlapping intervals of time. There is no EX record for the missed dose, but the missed dose is reflected in a gap between dates in the EX records.

Row 1: Shows the administration from first dose date to the day before the missed dose.

Row 2: Shows the doubled dose.

Row 3: Shows the remaining administrations to the last dose date.

ex.xpt

| Row | STUDYID | DOMAIN | USUBJID | EXSEQ | EXTRT  | EXDOSE | EXDOSU | EXDOSFRM | EXDOSFRQ | EXROUTE | EPOCH     | EXSTDTC    | EXENDTC    | EXSTDY | EXENDY |
| --- | ------- | ------ | ------- | ----- | ------ | ------ | ------ | -------- | -------- | ------- | --------- | ---------- | ---------- | ------ | ------ |
| 1   | ABC     | EX     | ABC7001 | 1     | DRUG X | 100    | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-01-13 | 2012-01-14 | 1      | 2      |
| 2   | ABC     | EX     | ABC7001 | 2     | DRUG X | 200    | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-01-16 | 2012-01-16 | 4      | 4      |
| 3   | ABC     | EX     | ABC7001 | 3     | DRUG X | 100    | mg     | TABLET   | QD       | ORAL    | TREATMENT | 2012-01-17 | 2012-01-20 | 5      | 8      |
