#### 7.1.3 Current and Future Contents of the Trial Design Model

Datasets currently in the Trial Design Model include:

- Trial Arms: Describes the sequences of elements in each epoch for each arm, and thus describes the complete sequence of elements in each arm
- Trial Elements: Describes the elements used in the trial
- Trial Visits: Describes the planned schedule of visits
- Trial Disease Assessment: Provides information on the protocol-specified disease assessment schedule, and is used for comparison with the actual occurrence of the efficacy assessments in order to determine whether there was good compliance with the schedule
- Trial Disease Milestones: Describes observations or activities identified for the trial which are anticipated to occur in the course of the disease under study and which trigger the collection of data
- Trial Inclusion/Exclusion Criteria: Describes the criteria used to screen subjects
- Trial Summary: Lists key facts (parameters) about the trial that are likely to appear in a registry of clinical trials

The Trial Inclusion/Exclusion Criteria (TI) dataset is discussed in Section 7.4.1, Trial Inclusion/Exclusion Criteria. The Inclusion/Exclusion Criteria Not Met (IE) domain described in Section 6.3.4, Inclusion/Exclusion Criteria Not Met, contains the actual exceptions to those criteria for enrolled subjects.

The current Trial Design Model has limitations in representing protocols, which include:

- Plans for indefinite numbers of repeating elements (e.g., indefinite numbers of chemotherapy cycles)
- Indefinite numbers of visits (e.g., periodic follow-up visits for survival)
- Indefinite numbers of epochs
- Indefinite numbers of arms

The last 2 situations arise in dose-escalation studies where increasing doses are given until stopping criteria are met. Some dose-escalation studies enroll a new cohort of subjects for each new dose, and so, at the planning stage, have an indefinite number of arms. Other dose-escalation studies give new doses to a continuing group of subjects, and so are planned with an indefinite number of epochs.

There may also be limitations in representing other patterns of Elements within a Study Cell that are more complex than a simple sequence. For the purpose of submissions about trials that have already completed, these limitations are not critical, so it is expected that development of the Trial Design Model to address these limitations will have a minimal impact on the SDTM.
