### 5.1 Comments (CO)

CO – Description/Overview

A special-purpose domain that contains comments that may be collected alongside other data.

CO – Specification

co.xpt, Comments — Special Purpose. One record per comment per subject, Tabulation.

| Variable Name | Variable Label              | Type | Controlled Terms, Codelist or Format1 | Role             | CDISC Notes                                                                                                                                                                                                                                       | Core |
| ------------- | --------------------------- | ---- | ------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| STUDYID       | Study Identifier            | Char |                                       | Identifier       | Unique identifier for a study.                                                                                                                                                                                                                    | Req  |
| DOMAIN        | Domain Abbreviation         | Char | CO                                    | Identifier       | Two-character abbreviation for the domain.                                                                                                                                                                                                        | Req  |
| RDOMAIN       | Related Domain Abbreviation | Char | (DOMAIN)                              | Record Qualifier | Two-character abbreviation for the domain of the parent record(s). Null for comments collected on a general comments or additional information CRF page.                                                                                          | Perm |
| USUBJID       | Unique Subject Identifier   | Char |                                       | Identifier       | Identifier used to uniquely identify a subject across all studies for all applications or submissions involving the product.                                                                                                                      | Req  |
| COSEQ         | Sequence Number             | Num  |                                       | Identifier       | Sequence Number given to ensure uniqueness of subject records within a domain. May be any valid number.                                                                                                                                           | Req  |
| IDVAR         | Identifying Variable        | Char | *                                     | Record Qualifier | Identifying variable in the parent dataset that identifies the record(s) to which the comment applies. Examples AESEQ or CMGRPID. Used only when individual comments are related to domain records. Null for comments collected on separate CRFs. | Perm |
| IDVARVAL      | Identifying Variable Value  | Char |                                       | Record Qualifier | Value of identifying variable of the parent record(s). Used only when individual comments are related to domain records. Null for comments collected on separate CRFs.                                                                            | Perm |
| COREF         | Comment Reference           | Char |                                       | Record Qualifier | Sponsor-defined reference associated with the comment. May be the CRF page number (e.g., 650), or a module name (e.g., DEMOG), or a combination of information that identifies the reference (e.g. 650- VITALS-VISIT 2).                          | Perm |
| COVAL         | Comment                     | Char |                                       | Topic            | The text of the comment. Text over 200 characters can be added to additional columns COVAL1- COVALn. See Assumption 3.                                                                                                                            | Req  |
| COEVAL        | Evaluator                   | Char | (EVAL)                                | Record Qualifier | Role of the person who provided the evaluation. Used only for results that are subjective (e.g., assigned by a person or a group). Example: "INVESTIGATOR".                                                                                       | Perm |
| COEVALID      | Evaluator Identifier        | Char | (MEDEVAL)                             | Record Qualifier | Used to distinguish multiple evaluators with the same role recorded in --EVAL. Examples: "RADIOLOGIST", "RADIOLOGIST 1", "RADIOLOGIST 2".                                                                                                         | Perm |
| CODTC         | Date/Time of Comment        | Char | ISO 8601 datetime or interval         | Timing           | Date/time of comment on dedicated comment form. Should be null if this is a child record of another domain or if comment date was not collected.                                                                                                  | Perm |
| CODY          | Study Day of Comment        | Num  |                                       | Timing           | Study day of the comment, in integer days. The algorithm for calculations must be relative to the sponsor- defined RFSTDTC variable in the Demographics (DM) domain.                                                                              | Perm |

1In this column, an asterisk (*) indicates that the variable may be subject to controlled terminology. CDISC/NCI codelist values are enclosed in parentheses.

CO – Assumptions

1. The Comments special-purpose domain provides a solution for submitting free-text comments related to data in 1 or more SDTM domains (as described in Section 8.5, Relating Comments to a Parent Domain) or collected on a separate CRF page dedicated to comments. Comments are generally not responses to specific questions; instead, comments usually consist of voluntary free-text or unsolicited observations.
2. Although the structure for the Comments domain in the SDTM is "One record per comment", USUBJID is required in the comments domain for human clinical trials, so the structure of the Comments domain in the SDTMIG is "One record per comment per subject."
3. The CO dataset accommodates 3 sources of comments:

   a. Those unrelated to a specific domain or parent record(s), in which case the values of the variables RDOMAIN, IDVAR, and IDVARVAL are null. CODTC should be populated if captured. See Example 1, row 1.

   b. Those related to a domain but not to specific parent record(s), in which case the value of the variable RDOMAIN is set to the DOMAIN code of the parent domain and the variables IDVAR and IDVARVAL are null. CODTC should be populated if captured. See Example 1, row 2.

   c. Those related to a specific parent record or group of parent records, in which case the value of the variable RDOMAIN is set to the DOMAIN code of the parent record(s) and the variables IDVAR and IDVARVAL are populated with the key variable name and value of the parent record(s). Assumptions for populating IDVAR and IDVARVAL are further described in Section 8.5, Relating Comments to a Parent Domain. CODTC should be null because the timing of the parent record(s) is inherited by the comment record. See Example 1, rows 3-5.
4. When the comment text is longer than 200 characters, the first 200 characters of the comment will be in COVAL, the next 200 in COVAL1, and additional text stored as needed to COVALn. See Example 1, rows 3-4. Additional information about how to relate comments to parent SDTM records is provided in Section 8.5, Relating Comments to a Parent Domain.
5. The variable COREF may be null unless it is used to identify the source of the comment. See Example 1, rows 1 and 5.
6. Identifier variables and Timing variables may be added to the CO domain, but the following qualifiers would generally not be used in CO: --GRPID, --REFID, --SPID, TAETORD, --TPT, --TPTNUM, --ELTM, --TPTREF, --RFTDTC.

CO – Examples

Example 1

Row 1: Shows a comment collected on a separate comments page. Since it was unrelated to any specific domain or record, RDOMAIN, IDVAR, and IDVARVAL are null.

Row 2: Shows a comment that was collected on the bottom of the PE page for Visit 7, without any indication of specific records it applied to. Since the comment related to a specific domain, RDOMAIN is populated. Since it was related to a specific visit, VISIT, COREF is "VISIT 7". However, since it does not relate to a specific record, IDVAR and IDVARVAL are null.

Row 3: Shows a comment related to a single AE record having its AESEQ=7.

Row 4: Shows a comment related to multiple EX records with EXGRPID = "COMBO1".

Row 5: Shows a comment related to multiple VS records with VSGRPID = "VS2".

Row 6: Shows one option for representing a comment collected on a visit-specific comments page not associated with a particular domain. In this case, the comment is linked to the Subject Visit record in SV (RDOMAIN = "SV") and IDVAR and IDVARVAL are populated link the comment to the particular visit.

Row 7: Shows a second option for representing a comment associated only with a visit. In this case, COREF is used to show that the comment is related to the particular visit.

Row 8: Shows a third option for representing a comment associated only with a visit. In this case, the VISITNUM variable was populated to indicate that the comment was associated with a particular visit.

co.xpt

| Row | STUDYID | DOMAIN | RDOMAIN | USUBJID | COSEQ | IDVAR    | IDVARVAL | COREF         | COVAL                | COVAL1              | COVAL2         | COEVAL                 | VISITNUM | CODTC       |
| --- | ------- | ------ | ------- | ------- | ----- | -------- | -------- | ------------- | -------------------- | ------------------- | -------------- | ---------------------- | -------- | ----------- |
| 1   | 1234    | CO     |         | AB-99   | 1     |          |          |               | Comment text         |                     |                | PRINCIPAL INVESTIGATOR |          | 2003-11- 08 |
| 2   | 1234    | CO     | PE      | AB-99   | 2     |          |          | VISIT 7       | Comment text         |                     |                | PRINCIPAL INVESTIGATOR |          | 2004-01- 14 |
| 3   | 1234    | CO     | AE      | AB-99   | 3     | AESEQ    | 7        | PAGE 650      | First 200 characters | Next 200 characters | Remaining text | PRINCIPAL INVESTIGATOR |          |             |
| 4   | 1234    | CO     | EX      | AB-99   | 4     | EXGRPID  | COMBO1   | PAGE 320- 355 | First 200 characters | Remaining text      |                | PRINCIPAL INVESTIGATOR |          |             |
| 5   | 1234    | CO     | VS      | AB-99   | 5     | VSGRPID  | VS2      |               | Comment text         |                     |                | PRINCIPAL INVESTIGATOR |          |             |
| 6   | 1234    | CO     | SV      | AB-99   | 6     | VISITNUM | 4        |               | Comment Text         |                     |                | PRINCIPAL INVESTIGATOR |          |             |
| 7   | 1234    | CO     |         | AB-99   | 7     |          |          | VISIT 4       | Comment Text         |                     |                | PRINCIPAL INVESTIGATOR |          |             |
| 8   | 1234    | CO     |         | AB-99   | 8     |          |          |               | Comment Text         |                     |                | PRINCIPAL INVESTIGATOR | 4        |             |
