### 5.5 Subject Visits (SV)

SV – Description/Overview

A special purpose domain that contains information for each subject's actual and planned visits.

The Subject Visits domain consolidates information about the timing of subject visits that is otherwise spread over domains that include the visit variables (VISITNUM and possibly VISIT and/or VISITDY). Unless the beginning and end of each visit is collected, populating the SV dataset will involve derivations. In a simple case, where, for each subject visit, exactly 1 date appears in every such domain, the SV dataset can be created easily by populating both SVSTDTC and SVENDTC with the single date for a visit. When there are multiple dates and/or date/times for a visit for a particular subject, the derivation of values for SVSTDTC and SVENDTC may be more complex. The method for deriving these values should be consistent with the visit definitions in the Trial Visits (TV) dataset (see Section 7.3.1, Trial Visits). For some studies, a visit may be defined to correspond with a clinic visit that occurs within 1 day, whereas for other studies, a visit may reflect data collection over a multiday period.

The SV dataset provides reviewers with a summary of a subject’s visits over the course of their participation in a study. Comparison of an individual subject’s SV dataset with the TV dataset, which describes the planned visits for the trial, supports the identification of planned but not expected visits due to a subject not completing the study. Comparison of the values of SVSTDY and SVENDY to VISIT and/or VISITDY can often highlight departures from the planned timing of visits.

SV – Specification

sv.xpt, Subject Visits — Special Purpose. One record per actual or planned visit per subject, Tabulation.

| Variable Name | Variable Label                        | Type | Controlled Terms, Codelist or Format1 | Role               | CDISC Notes                                                                                                                                                                               | Core |
| ------------- | ------------------------------------- | ---- | ------------------------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| STUDYID       | Study Identifier                      | Char |                                       | Identifier         | Unique identifier for a study.                                                                                                                                                            | Req  |
| DOMAIN        | Domain Abbreviation                   | Char | SV                                    | Identifier         | Two-character abbreviation for the domain most relevant to the observation. The domain abbreviation is also used as a prefix for variables to ensure uniqueness when datasets are merged. | Req  |
| USUBJID       | Unique Subject Identifier             | Char |                                       | Identifier         | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                                              | Req  |
| VISITNUM      | Visit Number                          | Num  |                                       | Topic              | Clinical encounter number. Numeric version of VISIT, used for sorting.                                                                                                                    | Req  |
| VISIT         | Visit Name                            | Char |                                       | Synonym Qualifier  | Protocol-defined description of a clinical encounter.                                                                                                                                     | Perm |
| SVPRESP       | Pre-specified                         | Char | (NY)                                  | Variable Qualifier | Used to indicate whether the visit was planned (i.e., visits specified in the TV domain). Value is "Y" for planned visits, null for unplanned visits.                                     | Exp  |
| SVOCCUR       | Occurrence                            | Char | (NY)                                  | Record Qualifier   | Used to record whether a planned visit occurred. The value is null for unplanned visits.                                                                                                  | Exp  |
| SVREASOC      | Reason for Occur Value                | Char |                                       | Record Qualifier   | The reason for the value in SVOCCUR. If SVOCCUR="N", SVREASOC is the reason the visit did not occur.                                                                                      | Perm |
| SVCNTMOD      | Contact Mode                          | Char | (CNTMODE)                             | Record Qualifier   | The way in which the visit was conducted. Examples: "IN PERSON", "TELEPHONE CALL", "IVRS".                                                                                                | Perm |
| SVEPCHGI      | Epi/Pandemic Related Change Indicator | Char | (NY)                                  | Record Qualifier   | Indicates whether the visit was changed due to an epidemic or pandemic.                                                                                                                   | Perm |
| VISITDY       | Planned Study Day of Visit            | Num  |                                       | Timing             | Planned study day of VISIT. Should be an integer.                                                                                                                                         | Perm |
| SVSTDTC       | Start Date/Time of Observation        | Char | ISO 8601 datetime or interval         | Timing             | Start date/time of an observation represented in IS0 8601 character format.                                                                                                               | Exp  |
| SVENDTC       | End Date/Time of Observation          | Char | ISO 8601 datetime or interval         | Timing             | End date/time of the observation represented in IS0 8601 character format.                                                                                                                | Exp  |
| SVSTDY        | Study Day of Start of Observation     | Num  |                                       | Timing             | Actual study day of start of observation expressed in integer days relative to the sponsor- defined RFSTDTC in Demographics.                                                              | Perm |
| SVENDY        | Study Day of End of Observation       | Num  |                                       | Timing             | Actual study day of end of observation expressed in integer days relative to the sponsor- defined RFSTDTC in Demographics.                                                                | Perm |
| SVUPDES       | Description of Unplanned Visit        | Char |                                       | Record Qualifier   | Description of what happened to the subject during an unplanned visit. Only populated for unplanned visits.                                                                               | Perm |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

SV – Assumptions

1. The Subject Visits domain allows the submission of data on the timing of the trial visits for a subject, including both those visits they actually passed through in their participation in the trial and those visits that did not occur. Refer to Section 7.3.1, Trial Visits (TV), as the TV dataset defines the planned visits for the trial.
2. Subjects can have 1 and only 1 record per VISITNUM.
3. Subjects who screen fail, withdraw, die, or otherwise discontinue study participation will not have records for planned visits subsequent to their final disposition event.
4. Planned and unplanned visits with a subject, whether or not they are physical visits to the investigational site, are represented in this domain.

   a. SVPRESP = "Y" identifies rows for planned visits.

   b. For planned visits, SVOCCUR indicates whether the visit occurred.

   c. For unplanned visits, SVPRESP and SVOCCUR are null.

   d. See Section 4.5.7, Presence or Absence of Prespecified Interventions and Events, for more information on the use of --PRESP and --OCCUR.
5. The identification of an actual visit with a planned visit sometimes calls for judgment. In general, data collection forms are prepared for particular visits, and the fact that data was collected on a form labeled with a planned visit is sufficient to make the association. Occasionally, the association will not be so clear, and the sponsor will need to make decisions about how to label actual visits. The sponsor's rules for making such decisions should be documented in the Define-XML document.
6. Records for unplanned visits should be included in the SV dataset. For unplanned visits, SVUPDES can be populated with a description of the reason for the unplanned visit. Some judgment may be required to determine what constitutes an unplanned visit. When data are collected outside a planned visit, that act of collecting data may or may not be described as a "visit." The encounter should generally be treated as a visit if data from the encounter are included in any domain for which VISITNUM is included; a record with a missing value for VISITNUM is generally less useful than a record with VISITNUM populated. If the occasion is considered a visit, its date/times must be included in the SV table and a value of VISITNUM must be assigned. Refer to Section 4.4.5, Clinical Encounters and Visits, for information on the population of visit variables for unplanned visits.
7. The variable SVCNTMOD is used to record the way in which the visit was conducted. For example, for visits to a clinic, SVCNTMOD = "INPERSON", visits conducted remotely might have values such as "TELEPHONE", "REMOTE AUDIO VIDEO", or "IVRS". If there are multiple contact modes, refer to Section 4.2.8.3, Multiple Values for a Non-result Qualifier Variable.
8. The planned study day of visit variable (VISITDY) should not be populated for unplanned visits.
9. If SVSTDY is included, it is the actual study day corresponding to SVSTDTC. In studies for which VISITDY has been populated, it may be desirable to populate SVSTDY, as this will facilitate the comparison of planned (VISITDY) and actual (SVSTDY) study days for the start of a visit.
10. If SVENDY is included, it is the actual day corresponding to SVENDTC.
11. For many studies, all visits are assumed to occur within 1 calendar day, and only 1 date is collected for the visit. In such a case, the values for SVENDTC duplicate values in SVSTDTC. However, if the data for a visit is actually collected over several physical visits and/or over several days, then SVSTDTC and SVENDTC should reflect this fact. Note that it is fairly common for screening data to be collected over several days, but for the data to be treated as belonging to a single planned screening visit, even in studies for which all other visits are single-day visits.
12. Differentiating between planned and unplanned visits may be challenging if unplanned assessments (e.g., repeat labs) are performed during the time period of a planned visit.
13. Algorithms for populating SVSTDTC and SVENDTC from the dates of assessments performed at a visit may be particularly challenging for screening visits, since baseline values collected at a screening visit are sometimes historical data from tests performed before the subject started screening for the trial. Therefore dates prior to informed consent are not part of the determination of SVSTDTC.
14. The following Identifier variables are permissible and may be added as appropriate: --SEQ, --GRPID, --REFID, and --SPID.
15. Care should be taken in adding additional timing variables:

    a. If TAETORD and/or EPOCH are added, then the values must be those at the start of the visit.

    b. The purpose of --DTC and --DY in other domains with start and end dates (Event and Intervention Domains) is to record the date on which data was collected. For a visit that occurred, it is not necessary to submit the date on which information about the visit was recorded. When SVPRESP = "Y" and SVOCCUR = "N", --DTC and --DY are available for use to represent the date on which it was recorded that the visit did not take place.

    c. --DUR could be added if the duration of a visit was collected.

    d. It would be inappropriate to add the variables that support time points (--TPT, --TPTNUM, --ELTM, --TPTREF, and --RFTDTC), because the topic of this dataset is visits.

    e. --STRF and --ENRF could be used to say whether a visit started and ended before, during, or after the study reference period, although this seems unnecessary.

    f. --STRTPT, --STTPT, --ENRTPT, and --ENTPT could be used to say that a visit started or ended before or after particular dates, although this seems unnecessary.
16. SVOCCUR = "N" records are only to be created for planned visits that were expected to occur before the end of the subject's participation.

SV – Examples

Example 1

This example shows the planned visit schedule for a study, along with disposition and study events data for 3 subjects. For this study, data on screen failures were submitted. The study was disrupted by the COVID-19 pandemic after many subjects had completed the study.

This is the planned schedule of visits for the study in this example.

Row 1: The activities for the SCREEN visit may occur over up to 7 days.

Row 2: The day 1 visit is planned to start before the start of treatment and end after the start of treatment.

Rows 3-7: These visits are scheduled relative to the start of the treatment epoch.

Row 8: The follow-up visit is generally scheduled relative to the start of the treatment epoch, but may occur earlier if treatment is stopped early.

tv.xpt

| Row | STUDYID | DOMAIN | VISITNUM | VISIT      | VISITDY | TVSTRL                                                                                                      | TVENRL                                                     |
| --- | ------- | ------ | -------- | ---------- | ------- | ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| 1   | 123456  | TV     | 1        | SCREEN     |         | Start of Screening Epoch                                                                                    | Up to 7 days after start of the Screening Epoch            |
| 2   | 123456  | TV     | 2        | DAY 1      | 1       | On the day of, but before, the end of the Screen Epoch                                                      | On the day of, but after, the start of the Treatment Epoch |
| 3   | 123456  | TV     | 3        | WEEK 1     | 8       | 1 week after the start of the Treatment Epoch                                                               |                                                            |
| 4   | 123456  | TV     | 4        | WEEK 2     | 15      | 2 weeks after the start of the Treatment Epoch                                                              |                                                            |
| 5   | 123456  | TV     | 5        | WEEK 4     | 29      | 4 weeks after the start of the Treatment Epoch                                                              |                                                            |
| 6   | 123456  | TV     | 6        | WEEK 6     | 43      | 6 weeks after the start of the Treatment Epoch                                                              |                                                            |
| 7   | 123456  | TV     | 7        | WEEK 8     | 57      | 8 weeks after the start of the Treatment Epoch                                                              |                                                            |
| 8   | 123456  | TV     | 8        | FOLLOW- UP |         | The earlier of 14 days after the last dose of treatment and 10 weeks after the start of the Treatment Epoch | At Trial Exit                                              |

This table shows the disposition records for the subjects in this example.

Row 1: Shows informed consent for subject 37.

Row 2: Shows the subject 37 was discontinued due to screen failure. Note that because the subject did not start treatment, DSSTDY is not populated in their records.

Row 3: Shows informed consent for subject 85.

Row 4: Shows that subject 85 completed the study.

Row 5: Shows informed consent for subject 101

Row 6: Shows that subject 101 chose to withdraw early.

ds.xpt

| Row | STUDYID | DOMAIN | USUBJID | DSSEQ | DSTERM                    | DSDECOD                   | DSCAT              | DSSCAT              | EPOCH     | DSDTC       | DSSTDTC     | DSSTDY |
| --- | ------- | ------ | ------- | ----- | ------------------------- | ------------------------- | ------------------ | ------------------- | --------- | ----------- | ----------- | ------ |
| 1   | 123456  | DS     | 37      | 1     | INFORMED CONSENT OBTAINED | INFORMED CONSENT OBTAINED | PROTOCOL MILESTONE |                     | SCREENING | 2019-09- 10 | 2019-09- 10 |        |
| 2   | 123456  | DS     | 37      | 2     | SCREEN FAILURE            | SCREEN FAILURE            | DISPOSITION EVENT  | STUDY PARTICIPATION | SCREENING | 2019-09- 16 | 2019-09- 16 |        |
| 3   | 123456  | DS     | 85      | 1     | INFORMED CONSENT OBTAINED | INFORMED CONSENT OBTAINED | PROTOCOL MILESTONE |                     | SCREENING | 2019-12- 13 | 2019-12- 13 | -6     |
| 4   | 123456  | DS     | 85      | 2     | COMPLETED                 | COMPLETED                 | DISPOSITION EVENT  | STUDY PARTICIPATION | TREATMENT | 2020-02- 27 | 2020-02- 27 | 72     |

| Row | STUDYID | DOMAIN | USUBJID | DSSEQ D | STERM                   | DSDECOD                   | DSCAT              | DSSCAT              | EPOCH     | DSDTC       | DSSTDTC     | DSSTDY |
| --- | ------- | ------ | ------- | ------- | ----------------------- | ------------------------- | ------------------ | ------------------- | --------- | ----------- | ----------- | ------ |
| 5   | 123456  | DS     | 101     | 1 I O   | NFORMED CONSENT BTAINED | INFORMED CONSENT OBTAINED | PROTOCOL MILESTONE |                     | SCREENING | 2020-02- 13 | 2020-02- 13 | -6     |
| 6   | 123456  | DS     | 101     | 2       | WITHDRAWAL BY SUBJECT   | WITHDRAWAL BY SUBJECT     | DISPOSITION EVENT  | STUDY PARTICIPATION | TREATMENT | 2020-03- 16 | 2020-03- 16 | 26     |

Because the study in this example was disrupted by an epidemic, the permissible variable SVEPCHGI (Epi/Pandemic Related Change Indicator) was included in the SV dataset. As originally planned, visits were to be conducted in person, but pandemic disruption included conducting some visits remotely. When the change to a remote visit was a change due to the pandemic, SVEPCHGI = "Y".

Row 1: Shows that screening data for subject 37 was collected during a period of 4 days. This subject is shown as a screen failure in ds.xpt and therefore would have a null DM.RFSTDTC, hence the study day values in SVSTDY and SVENDY, which are based on the sponsor-defined reference start date, are null.

Rows 2-3: Show normal completion of the first 2 visits for subject 85.

Row 4: Shows that for subject 85, the visit called "WEEK 1" did not occur; the reason it did not occur is represented in SVREASOC.

Rows 5-9: Normal completion of remaining visits for subject 85.

Row 10: Data for the screening visit was gathered over the course of six days. For this and subsequent visits, SVPRESP = "Y" indicates that a visit was planned and SVOCCUR = "Y" indicates that the visit occurred.

Row 11: The visit called "DAY 1" started and ended as planned, on Day 1.

Row 12: The visit scheduled for Day 8 occurred one day early, on Day 7.

Row 13: The visit called "WEEK 2" did not occur due to clinic closure. SVOCCUR = "N" and SVREASOC contains the reason the visit did not occur.

Row 14: Shows an unscheduled visit. SVUPDES provides the information that this visit dealt with evaluation of an adverse event. Since this visit was not planned, VISITDY was not populated, SVPRESP and SVOCCUR are both null. VISITNUM is populated as required, but the sponsor chose not to populate VISIT. Data collected at this encounter may be in a Findings domain such as EG, LB, or VS, in which VISITNUM is treated as an important timing variable. This visit was over remote audio video due to having an adverse event during a pandemic.

Row 15: This subject had their last visit, a follow-up visit on study day 26, eight days after the unscheduled visit.

sv.xpt

| Row | STUDYID | DOMAIN | USUBJID | VISITNUM | VISIT      | SVPRESP | SVOCCUR | SVREASOC                         | SVCNTMOD           | SVEPCHGI | VISITDY | SVSTDTC     | SVENDTC     | SVSTDY | SVENDY | SVUPDES          |
| --- | ------- | ------ | ------- | -------- | ---------- | ------- | ------- | -------------------------------- | ------------------ | -------- | ------- | ----------- | ----------- | ------ | ------ | ---------------- |
| 1   | 123456  | SV     | 37      | 1        | SCREEN     | Y       | Y       |                                  | IN PERSON          |          |         | 2019-09- 10 | 2019-09- 16 |        |        |                  |
| 2   | 123456  | SV     | 85      | 1        | SCREEN     | Y       | Y       |                                  | IN PERSON          |          |         | 2019-12- 13 | 2019-12- 18 | -6     | -1     |                  |
| 3   | 123456  | SV     | 85      | 2        | DAY 1      | Y       | Y       |                                  | IN PERSON          |          | 1       | 2019-12- 19 | 2019-12- 19 | 1      | 1      |                  |
| 4   | 123456  | SV     | 85      | 3        | WEEK 1     | Y       | N       | SUBJECT LACKED TRANSPORTATION    |                    |          | 8       |             |             |        |        |                  |
| 5   | 123456  | SV     | 85      | 4        | WEEK 2     | Y       | Y       |                                  | IN PERSON          |          | 15      | 2020-01- 02 | 2020-01- 02 | 15     | 15     |                  |
| 6   | 123456  | SV     | 85      | 5        | WEEK 4     | Y       | Y       |                                  | IN PERSON          |          | 29      | 2020-01- 16 | 2020-01- 16 | 30     | 30     |                  |
| 7   | 123456  | SV     | 85      | 6        | WEEK 6     | Y       | Y       |                                  | IN PERSON          |          | 43      | 2020-01- 30 | 2020-01- 30 | 43     | 43     |                  |
| 8   | 123456  | SV     | 85      | 7        | WEEK 8     | Y       | Y       |                                  | IN PERSON          |          | 57      | 2020-02- 13 | 2020-02- 13 | 57     | 57     |                  |
| 9   | 123456  | SV     | 85      | 8        | FOLLOW- UP | Y       | Y       |                                  | IN PERSON          |          |         | 2020-02- 27 | 2020-02- 27 | 72     | 72     |                  |
| 10  | 123456  | SV     | 101     | 1        | SCREEN     | Y       | Y       |                                  | IN PERSON          |          |         | 2020-02- 13 | 2020-02- 18 | -6     | -1     |                  |
| 11  | 123456  | SV     | 101     | 2        | DAY 1      | Y       | Y       |                                  | IN PERSON          |          | 1       | 2020-02- 19 | 2020-02- 19 | 1      | 1      |                  |
| 12  | 123456  | SV     | 101     | 3        | WEEK 1     | Y       | Y       |                                  | IN PERSON          |          | 8       | 2020-02- 25 | 2020-02- 25 | 7      | 7      |                  |
| 13  | 123456  | SV     | 101     | 4        | WEEK 2     | Y       | N       | CLINIC CLOSED DUE TO BAD WEATHER |                    |          | 15      |             |             |        |        |                  |
| 14  | 123456  | SV     | 101     | 4.1      |            |         |         |                                  | REMOTE AUDIO VIDEO | Y        |         | 2020-03- 07 | 2020-03- 07 | 18     | 18     | EVALUATION OF AE |
| 15  | 123456  | SV     | 101     | 8        | FOLLOW- UP | Y       | Y       |                                  | TELEPHONE CALL     | Y        |         | 2020-03- 16 | 2020-03- 16 | 26     | 26     |                  |
