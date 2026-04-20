### 5.3 Subject Elements (SE)

SE – Description/Overview

A special-purpose domain that contains the actual order of elements followed by the subject, together with the start date/time and end date/time for each element.

The Subject Elements dataset consolidates information about the timing of each subject’s progress through the epochs and elements of the trial. For elements that involve study treatments, the identification of which element the subject passed through (e.g., drug X vs. placebo) is likely to derive from data in the Exposure domain or another Interventions domain. The dates of a subject’s transition from one element to the next will be taken from the Interventions domain(s) and from other relevant domains, according to the definitions (TESTRL values) in the Trial Elements (TE) dataset (see Section 7.2.2, Trial Elements).

The SE dataset is particularly useful for studies with multiple treatment periods, such as crossover studies. The SE dataset contains the date/times at which a subject moved from one element to another, so when this dataset, the Trial Arms (TA; see Section 7.2.1, Trial Arms) dataset, and the Trial Elements (TE; see Section 7.2.2, Trial Elements) dataset are included in a submission, reviewers can relate all observations made about a subject to that subject’s progression through the trial.

- Comparison of the --DTC of a finding observation to the element transition dates (values of SESTDTC and SEENDTC) identifies which element the subject was in at the time of the finding. Similarly, one can determine the element during which an event or intervention started or ended.
- “Day within Element” or “Day within Epoch” can be derived. Such variables relate an observation to the start of an element or epoch in the same way that study day (--DY) variables relate it to the reference start date (RFSTDTC) for the study as a whole. See Section 4.4.4, Use of the "Study Day" Variables.
- Having knowledge of SE start and end dates can be helpful in the determination of baseline values.

SE – Specification

se.xpt, Subject Elements — Special Purpose. One record per actual Element per subject, Tabulation.

| Variable Name | Variable Label                      | Type | Controlled Terms, Codelist or Format1 | Role              | CDISC Notes                                                                                                                                                                                                                                                                                                                                                                                                                             | Core |
| ------------- | ----------------------------------- | ---- | ------------------------------------- | ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| STUDYID       | Study Identifier                    | Char |                                       | Identifier        | Unique identifier for a study.                                                                                                                                                                                                                                                                                                                                                                                                          | Req  |
| DOMAIN        | Domain Abbreviation                 | Char | SE                                    | Identifier        | Two-character abbreviation for the domain.                                                                                                                                                                                                                                                                                                                                                                                              | Req  |
| USUBJID       | Unique Subject Identifier           | Char |                                       | Identifier        | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                                                                                                                                                                                                                                                                                            | Req  |
| SESEQ         | Sequence Number                     | Num  |                                       | Identifier        | Sequence number given to ensure uniqueness of subject records within a domain. Should be assigned to be consistent chronological order.                                                                                                                                                                                                                                                                                                 | Req  |
| ETCD          | Element Code                        | Char | *                                     | Topic             | 1. ETCD (the companion to ELEMENT) is limited to 8 characters and does not have special character restrictions. These values should be short for ease of use in programming, but it is not expected that ETCD will need to serve as a variable name. 2. If an encountered element differs from the planned element to the point that it is considered a new element, then use "UNPLAN" as the value for ETCD to represent this element. | Req  |
| ELEMENT       | Description of Element              | Char | *                                     | Synonym Qualifier | The name of the element. If ETCD has a value of "UNPLAN", then ELEMENT should be null.                                                                                                                                                                                                                                                                                                                                                  | Perm |
| TAETORD       | Planned Order of Element within Arm | Num  |                                       | Timing            | Number that gives the planned order of the element within the subject's assigned trial arm.                                                                                                                                                                                                                                                                                                                                             | Perm |
| EPOCH         | Epoch                               | Char | (EPOCH)                               | Timing            | Epoch associated with the element in the planned sequence of elements for the arm to which the subject was assigned.                                                                                                                                                                                                                                                                                                                    | Perm |
| SESTDTC       | Start Date/Time of Element          | Char | ISO 8601 datetime or interval         | Timing            | Start date/time for an element for each subject.                                                                                                                                                                                                                                                                                                                                                                                        | Req  |
| SEENDTC       | End Date/Time of Element            | Char | ISO 8601 datetime or interval         | Timing            | End date/time for an element for each subject.                                                                                                                                                                                                                                                                                                                                                                                          | Exp  |
| SESTDY        | Study Day of Start of Element       | Num  |                                       | Timing            | Study day of start of element relative to the sponsor-defined RFSTDTC.                                                                                                                                                                                                                                                                                                                                                                  | Perm |
| SEENDY        | Study Day of End of Element         | Num  |                                       | Timing            | Study day of end of element relative to the sponsor-defined RFSTDTC.                                                                                                                                                                                                                                                                                                                                                                    | Perm |
| SEUPDES       | Description of Unplanned Element    | Char |                                       | Synonym Qualifier | Description of what happened to the subject during an unplanned element. Used only if ETCD has the value of "UNPLAN".                                                                                                                                                                                                                                                                                                                   | Perm |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

SE – Assumptions

Submission of the SE dataset is strongly recommended, as it provides information needed by reviewers to place observations in context within the study. As noted in the SE - Description/Overview, the TE and TA datasets should also be submitted, as these define the design and the terms referenced by the SE dataset.

The SE domain allows the submission of data on the timing of the trial elements a subject actually passed through in their participation in the trial. Section 7.2.2, Trial Elements, and Section 7.2.1, Trial Arms, provide additional information on these datasets, which define a trial's planned elements and describe the planned sequences of elements for the arms of the trial.

1. For any particular subject, the dates in the SE table are the dates when the transition events identified in the TE table occurred. Judgment may be needed to match actual events in a subject's experience with the definitions of transition events (i.e., events that mark the start of new elements) in the TE table; actual events may vary from the plan. For instance, in a single-dose pharmacokinetics (PK) study, the transition events might correspond to study drug doses of 5 and 10 mg. If a subject actually received a dose of 7 mg when they were scheduled to receive 5 mg, a decision will have to be made on how to represent this in the SE domain.
2. If the date/time of a transition element was not collected directly, the method used to infer the element start date/time should be explained in the Comments column of the Define-XML document.
3. Judgment will also have to be used in deciding how to represent a subject's experience if an element does not proceed or end as planned. For instance, the plan might identify a trial element that is to start with the first of a series of 5 daily doses and end after 1 week, when the subject transitions to the next treatment element. If the subject actually started the next treatment epoch (see Section 7.1, Introduction to Trial Design Model Datasets, and Section 7.1.2, Definitions of Trial Design Concepts) after 4 weeks, the sponsor would have to decide whether to represent this as an abnormally long element, or as a normal element plus an unplanned non-treatment element.
4. If the sponsor decides that the subject's experience for a particular period of time cannot be represented with one of the planned elements, then that period of time should be represented as an unplanned element. The value of ETCD for an unplanned element is “UNPLAN” and SEUPDES should be populated with a description of the unplanned element.
5. The values of SESTDTC provide the chronological order of the actual subject elements. SESEQ should be assigned to be consistent with the chronological order. Note that the requirement that SESEQ be consistent with chronological order is more stringent than in most other domains, where --SEQ values need only be unique within subject.
6. When TAETORD is included in the SE domain, it represents the planned order of an element in an arm. This should not be confused with the actual order of the elements, which will be represented by their chronological order and SESEQ. TAETORD will not be populated for subject elements that are not planned for the arm to which the subject was assigned. Thus, TAETORD will not be populated for any element with an ETCD value of “UNPLAN”. TAETORD also will not be populated if a subject passed through an element that, although defined in the TE dataset, was out of place for the arm to which the subject was assigned. For example, if a subject in a parallel study of drug A vs. drug B was assigned to receive drug A but received drug B instead, then TAETORD would be left blank for the SE record for their drug B element. If a subject was assigned to receive the sequence of elements A, B, C, D, and instead received A, D, B, C, then the sponsor would have to decide for which of these SE records TAETORD should be populated. The rationale for this decision should be documented in the Comments column of the Define-XML document.
7. For subjects who follow the planned sequence of elements for the arm to which they were assigned, the values of EPOCH in the SE domain will match those associated with the elements for the subject's arm in the TA dataset. The sponsor will have to decide what value, if any, of EPOCH to assign SE records for unplanned elements and in other cases where the subject's actual elements deviate from the plan. The sponsor's methods for such decisions should be documented in the Define-XML document, in the row for EPOCH in the SE dataset table.
8. Because there are, by definition, no gaps between elements, the value of SEENDTC for one element will always be the same as the value of SESTDTC for the next element.
9. Note that SESTDTC is required, although --STDTC is not required in any other subject-level dataset. The purpose of the dataset is to record the elements a subject actually passed through. If it is known that a subject passed through a particular element, then there must be some information (perhaps imprecise) on when it started. Thus, SESTDTC may not be null, although some records may not have all the components (e.g., year, month, day, hour, minute) of the date/time value collected.
10. The following identifier variables are permissible and may be added as appropriate: --GRPID, --REFID, --SPID.
11. Care should be taken in adding additional timing variables:

    a. The purpose of --DTC and --DY is to record the date and study day on which data was collected. Elements are generally “derived” in the sense that they are a secondary use of data collected elsewhere; it is not generally useful to know when those date/times were recorded.

    b. --DUR could be added only if the duration of an element was collected, not derived.

    c. It would be inappropriate to add the variables that support time points (--TPT, --TPTNUM, --ELTM, --TPTREF, and --RFTDTC), because the topic of this dataset is elements.

SE – Examples

STUDYID and DOMAIN, which are required in the SE and Demographics (DM) domains, have not been included in the following examples, to improve readability.

Example 1

This example shows data for 2 subjects for a crossover trial with 4 epochs.

Row 1: The record for the SCREEN element for subject 789. Note that only the date of the start of the SCREEN element was collected, whereas for the end of the element (which corresponds to the start of IV dosing) both date and time were collected.

Row 2: The record for the IV element for subject 789. The IV element started with the start of IV dosing and ended with the start of oral dosing, and full date/times were collected for both.

Row 3: The record for the ORAL element for subject 789. Only the date, and not the time, of the start of follow-up was collected.

Row 4: The FOLLOWUP element for subject 789 started and ended on the same day. Presumably, the element had a positive duration, but no times were collected.

Rows 5-8: Subject 790 was treated incorrectly. This subject entered the IV element before the ORAL element, although the planned order of elements for this subject was ORAL, then IV. The sponsor has assigned EPOCH values for this subject according to the actual order of elements, rather than the planned order. Per Assumption 6, TAETORD is missing for the elements that were out of order. The correct order of elements is the subject's ARMCD, shown in the DM dataset.

Rows 9-10: Subject 791 was screened, randomized to the IV-ORAL arm, and received the IV treatment, but did not return to the unit for the treatment epoch or follow-up.

se.xpt

| Row | USUBJID | SESEQ | ETCD     | SESTDTC          | SEENDTC          | SEUPDES | TAETORD | EPOCH       |
| --- | ------- | ----- | -------- | ---------------- | ---------------- | ------- | ------- | ----------- |
| 1   | 789     | 1     | SCREEN   | 2006-06-01       | 2006-06-03T10:32 |         | 1       | SCREENING   |
| 2   | 789     | 2     | IV       | 2006-06-03T10:32 | 2006-06-10T09:47 |         | 2       | TREATMENT 1 |
| 3   | 789     | 3     | ORAL     | 2006-06-10T09:47 | 2006-06-17       |         | 3       | TREATMENT 2 |
| 4   | 789     | 4     | FOLLOWUP | 2006-06-17       | 2006-06-17       |         | 4       | FOLLOW-UP   |
| 5   | 790     | 1     | SCREEN   | 2006-06-01       | 2006-06-03T10:14 |         | 1       | SCREENING   |
| 6   | 790     | 2     | IV       | 2006-06-03T10:14 | 2006-06-10T10:32 |         |         | TREATMENT 1 |
| 7   | 790     | 3     | ORAL     | 2006-06-10T10:32 | 2006-06-17       |         |         | TREATMENT 2 |
| 8   | 790     | 4     | FOLLOWUP | 2006-06-17       | 2006-06-17       |         | 4       | FOLLOW-UP   |
| 9   | 791     | 1     | SCREEN   | 2006-06-01       | 2006-06-03T10:17 |         | 1       | SCREENING   |
| 10  | 791     | 2     | IV       | 2006-06-03T10:17 | 2006-06-07       |         | 2       | TREATMENT 1 |

Row 1: Subject 789 was assigned to the IV-ORAL arm and was treated accordingly.

Row 2: Subject 790 was assigned to the ORAL-IV arm, but their actual treatment was IV, then oral.

Row 3: Subject 791 was assigned to the IV-ORAL arm, received the first of the 2 planned treatment elements, and were following the assigned treatment when they withdrew early. The actual arm variables are populated with the values for the arm to which subject 791 was assigned.

dm.xpt

| Row | USUBJID | SUBJID | RFSTDTC     | RFENDTC     | SITEID | INVNAM   | BIRTHDTC   | AGE | AGEU  | SEX | RACE  | ETHNIC                 | ARMCD | ARM      | ACTARMCD | ACTARM  | ARMNRS | ACTARMUD | COUNTRY |
| --- | ------- | ------ | ----------- | ----------- | ------ | -------- | ---------- | --- | ----- | --- | ----- | ---------------------- | ----- | -------- | -------- | ------- | ------ | -------- | ------- |
| 1   | 789     | 001    | 2006-06- 03 | 2006-06- 17 | 01     | SMITH, J | 1948-12-13 | 57  | YEARS | M   | WHITE | HISPANIC OR LATINO     | IO    | IV- ORAL | IO       | IV-ORAL |        |          | USA     |
| 2   | 790     | 002    | 2006-06- 03 | 2006-06- 17 | 01     | SMITH, J | 1955-03-22 | 51  | YEARS | M   | WHITE | NOT HISPANIC OR LATINO | OI    | ORAL- IV | IO       | IV-ORAL |        |          | USA     |
| 3   | 791     | 003    | 2006-06- 03 | 2006-06- 07 | 01     | SMITH, J | 1956-07-17 | 49  | YEARS | M   | WHITE | NOT HISPANIC OR LATINO | IO    | IV- ORAL | IO       | IV-ORAL |        |          | USA     |

Example 2

The following data represent 2 subjects enrolled in a trial in which assignment to an arm occurs in 2 stages.

See Section 7.2.1, Trial Arms, Example Trial 3. In this trial, subjects were randomized at the beginning of the blinded treatment epoch, then assigned to treatment for the open treatment epoch according to their response to treatment in the blinded treatment epoch. See Section 5.2, Demographics, for other examples of ARM and ARMCD values for this trial.

In this trial, start of dosing was recorded as dates without times, so SESTDTC values include only dates. Epochs could not be assigned to observations that occurred on epoch transition dates on the basis of the SE dataset alone, so the sponsor's algorithms for dealing with this ambiguity were documented in the Define-XML document.

Rows 1-2: Show data for a subject who completed only 2 elements of the trial.

Rows 3-6: Show data for a subject who completed the trial, but received the wrong drug for the last 2 weeks of the double-blind treatment period. This has been represented by treating the period when the subject received the wrong drug as an unplanned element. Note that TAETORD, which represents the planned order of elements within an arm, has not been populated for this unplanned element. Even though this element was unplanned, the sponsor assigned a value of BLINDED TREATMENT to EPOCH.

se.xpt

| Row | USUBJID | SESEQ | ETCD   | SESTDTC    | SEENDTC    | SEUPDES                   | TAETORD | EPOCH                |
| --- | ------- | ----- | ------ | ---------- | ---------- | ------------------------- | ------- | -------------------- |
| 1   | 123     | 1     | SCRN   | 2006-06-01 | 2006-06-03 |                           | 1       | SCREENING            |
| 2   | 123     | 2     | DBA    | 2006-06-03 | 2006-06-10 |                           | 2       | BLINDED TREATMENT    |
| 3   | 456     | 1     | SCRN   | 2006-05-01 | 2006-05-03 |                           | 1       | SCREENING            |
| 4   | 456     | 2     | DBA    | 2006-05-03 | 2006-05-31 |                           | 2       | BLINDED TREATMENT    |
| 5   | 456     | 3     | UNPLAN | 2006-05-31 | 2006-06-13 | Drug B dispensed in error |         | BLINDED TREATMENT    |
| 6   | 456     | 4     | RSC    | 2006-06-13 | 2006-07-30 |                           | 3       | OPEN LABEL TREATMENT |

Row 1: Shows the record for a subject who was randomized to blinded treatment A, but withdrew from the trial before the open treatment epoch and did not have a second treatment assignment. They were thus incompletely assigned to an arm. The code used to represent this incomplete assignment, "A", is not in the TA table for this trial design, but is the first part of the codes for the 2 arms to which subject 123 could have been assigned ("AR" or "AO").

Row 2: Shows the record for a subject who was randomized to blinded treatment A, but was erroneously treated with drug B for part of the blinded treatment epoch. ARM and ARMCD for this subject reflect the planned treatment and are not affected by the fact that treatment deviated from plan. The subject's assignment to Rescue treatment for the open treatment epoch proceeded as planned. The sponsor decided that the subject's treatment, which consisted partly of drug A and partly of drug B, did not match any planned arm, so ACTARMCD and ACTARM were left null. ARMNRS was populated with "UNPLANNED TREATMENT" and the way in which this treatment was unplanned was described in ACTARMUD.

dm.xpt

| Row | USUBJID | SUBJID | RFSTDTC     | RFENDTC     | SITEID | INVNAM   | BIRTHDTC   | AGE | AGEU  | SEX | RACE  | ETHNIC             | ARMCD | ARM A | CTARMCD | ACTARM | ARMNRS | ACTARMUD | COUNTRY |
| --- | ------- | ------ | ----------- | ----------- | ------ | -------- | ---------- | --- | ----- | --- | ----- | ------------------ | ----- | ----- | ------- | ------ | ------ | -------- | ------- |
| 1   | 123     | 012    | 2006-06- 03 | 2006-06- 10 | 01     | JONES, D | 1943-12-08 | 62  | YEARS | M   | ASIAN | HISPANIC OR LATINO | A     | A A   |         | A      |        |          | USA     |

| Row | USUBJID | SUBJID | RFSTDTC     | RFENDTC     | SITEID | INVNAM   | BIRTHDTC   | AGE | AGEU  | SEX | RACE  | ETHNIC                 | ARMCD | ARM       | ACTARMCD | ACTARM | ARMNRS              | ACTARMUD                                    | COUNTRY |
| --- | ------- | ------ | ----------- | ----------- | ------ | -------- | ---------- | --- | ----- | --- | ----- | ---------------------- | ----- | --------- | -------- | ------ | ------------------- | ------------------------------------------- | ------- |
| 2   | 456     | 103    | 2006-05- 03 | 2006-07- 30 | 01     | JONES, D | 1950-05-15 | 55  | YEARS | F   | WHITE | NOT HISPANIC OR LATINO | AR    | A- Rescue |          |        | UNPLANNED TREATMENT | Drug B dispensed for part of Drug A element | USA     |
