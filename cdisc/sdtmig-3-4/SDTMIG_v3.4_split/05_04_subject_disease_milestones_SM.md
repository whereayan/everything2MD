### 5.4 Subject Disease Milestones (SM)

SM – Description/Overview

A special-purpose domain that is designed to record the timing, for each subject, of disease milestones that have been defined in the Trial Disease Milestones (TM) domain.

SM – Specification

sm.xpt, Subject Disease Milestones — Special Purpose. One record per Disease Milestone per subject, Tabulation.

| Variable Name | Variable Label                  | Type | Controlled Terms, Codelist or Format1 | Role             | CDISC Notes                                                                                                                                                        | Core |
| ------------- | ------------------------------- | ---- | ------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---- |
| STUDYID       | Study Identifier                | Char |                                       | Identifier       | Unique identifier for a study.                                                                                                                                     | Req  |
| DOMAIN        | Domain Abbreviation             | Char | SM                                    | Identifier       | Two-character abbreviation for the domain.                                                                                                                         | Req  |
| USUBJID       | Unique Subject Identifier       | Char |                                       | Identifier       | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                       | Req  |
| SMSEQ         | Sequence Number                 | Num  |                                       | Identifier       | Sequence number to ensure uniqueness of subject records. Should be assigned to be consistent chronological order.                                                  | Req  |
| MIDS          | Disease Milestone Instance Name | Char | *                                     | Topic            | Name of the specific disease milestone. For types of disease milestones that can occur multiple times, the name will end with a sequence number. Example: "HYPO1". | Req  |
| MIDSTYPE      | Disease Milestone Type          | Char | *                                     | Record Qualifier | The type of disease milestone. Example: "HYPOGLYCEMIC EVENT".                                                                                                      | Req  |
| SMSTDTC       | Start Date/Time of Milestone    | Char | ISO 8601 datetime or interval         | Timing           | Start date/time of milestone instance (if milestone is an intervention or event) or date of milestone (if Milestone is a finding).                                 | Exp  |
| SMENDTC       | End Date/Time of Milestone      | Char | ISO 8601 datetime or interval         | Timing           | End date/time of disease milestone instance.                                                                                                                       | Exp  |
| SMSTDY        | Study Day of Start of Milestone | Num  |                                       | Timing           | Study day of start of disease milestone instance, relative to the sponsor-defined RFSTDTC.                                                                         | Exp  |
| SMENDY        | Study Day of End of Milestone   | Num  |                                       | Timing           | Study day of end of disease milestone instance, relative to the sponsor-defined RFSTDTC.                                                                           | Exp  |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

SM – Assumptions

1. Disease milestones are observations or activities whose timings are of interest in the study. The types of disease milestones are defined at the study level in the TM dataset. The purpose of the SM dataset is to provide a summary timeline of the milestones for a particular subject.
2. The name of the disease milestone is recorded in MIDS.

   a. For disease milestones that can occur only once (TMRPT = "N"), the value of MIDS may be the value in MIDSTYPE or may an abbreviated version.

   b. For types of disease milestones that can occur multiple times, MIDS will usually be an abbreviated version of MIDSTYPE and will always end with

   a sequence number. Sequence numbers should start with 1 and indicate the chronological order of the instances of this type of disease milestone.
3. The timing variables SMSTDTC and SMENDTC hold start and end date/times of data collected for the disease milestone(s) for each subject. SMSTDY and SMENDY represent the corresponding study day variables.

   a. The start date/time of the disease milestone is the critical date/time, and must be populated. If the disease milestone is an event, then the meaning of “start date” for the event may need to be defined.

   b. The start study day will not be populated if the start date/time includes only a year or only a year and month.

   c. The end date/time for the disease milestone is less important than the start date/time. It will not be populated if the disease milestone is a finding without an end date/time or if it is an event or intervention for which an end date/time has not yet occurred or was not collected.

   d. The end study day will not be populated if the end date/time includes only a year or only a year and month.

SM – Examples

Example 1

In this study, the disease milestones of interest were initial diagnosis and hypoglycemic events, as shown in Section 7.3.3, Trial Disease Milestones, Example 1.

Row 1: Shows that subject 001's initial diagnosis of diabetes occurred in October 2005. Because this is a partial date, SMDY is not populated. No end date/time was recorded for this milestone.

Rows 2-3: Show that subject 001 had 2 hypoglycemic events. In this case, only start date/times have been collected. Because these date/times include full dates, SMSTDY has been populated in each case.

Row 4: Shows that subject 002’s initial diagnosis of diabetes occurred on May 15, 2010. Because a full date was collected, the study day of this milestone was populated. Diagnosis was pre-study, so the study day of the disease milestone is negative. No hypoglycemic events were recorded for this subject.

sm.xpt

| Row | STUDYID | DOMAIN | USUBJID | SMSEQ | MIDS  | MIDSTYPE           | SMSTDTC          | SMENDTC | SMSTDY | SMENDY |
| --- | ------- | ------ | ------- | ----- | ----- | ------------------ | ---------------- | ------- | ------ | ------ |
| 1   | XYZ     | SM     | 001     | 1     | DIAG  | DIAGNOSIS          | 2005-10          |         |        |        |
| 2   | XYZ     | SM     | 001     | 2     | HYPO1 | HYPOGLYCEMIC EVENT | 2013-09-01T11:00 |         | 25     |        |
| 3   | XYZ     | SM     | 001     | 3     | HYPO2 | HYPOGLYCEMIC EVENT | 2013-09-24T8:48  |         | 50     |        |
| 4   | XYZ     | SM     | 002     | 1     | DIAG  | DIAGNOSIS          | 2010-05-15       |         | -1046  |        |

Information in SM is taken from records in other domains. In this study, diagnosis was represented in the Medical History (MH) domain, and hyypoglycemic events were represented in the Clinical Events (CE) domain.

The MH records for diabetes (MHEVDTYP = "DIAGNOSIS") are the records which represent the disease milestones for the defined MIDSTYPE of "DIAGNOSIS", so these records include the MIDS variable with the value "DIAG". Because these are records for disease milestones rather than associated records, the variables RELMIDS and MIDSDTC are not needed.

mh.xpt

| Row | STUDYID | DOMAIN | USUBJID | MHSEQ | MHTERM          | MHDECOD                  | MHEVDTYP  | MHPRESP | MHOCCUR | MHDTC      | MHSTDTC    | MHENDTC | MHDY | MIDS |
| --- | ------- | ------ | ------- | ----- | --------------- | ------------------------ | --------- | ------- | ------- | ---------- | ---------- | ------- | ---- | ---- |
| 1   | XYZ     | MH     | 001     | 1     | TYPE 2 DIABETES | Type 2 diabetes mellitus | DIAGNOSIS | Y       | Y       | 2013-08-06 | 2005-10    |         | 1    | DIAG |
| 2   | XYZ     | MH     | 002     | 1     | TYPE 2 DIABETES | Type 2 diabetes mellitus | DIAGNOSIS | Y       | Y       | 2013-08-06 | 2010-05-15 |         | 1    | DIAG |

In this study, information about hypoglycemic events was collected in a separate CRF module, and CE records recorded in this module were represented with CECAT = "HYPOGLYCEMIC EVENT". Each CE record for a hypoglycemic event is a disease milestone, and records for a study have distinct values of MIDS.

ce.xpt

| Row | STUDYID | DOMAIN | USUBJID | CESEQ | CETERM             | CEDECOD       | CECAT              | CEPRESP | CEOCCUR | CESTDTC          | CEENDTC          | MIDS  |
| --- | ------- | ------ | ------- | ----- | ------------------ | ------------- | ------------------ | ------- | ------- | ---------------- | ---------------- | ----- |
| 1   | XYZ     | CE     | 001     | 1     | HYPOGLYCEMIC EVENT | Hypoglycaemia | HYPOGLYCEMIC EVENT | Y       | Y       | 2013-09-01T11:00 | 2013-09-01T2:30  | HYPO1 |
| 2   | XYZ     | CE     | 001     | 1     | HYPOGLYCEMIC EVENT | Hypoglycaemia | HYPOGLYCEMIC EVENT | Y       | Y       | 2013-09-24T8:48  | 2013-09-24T10:00 | HYPO2 |
