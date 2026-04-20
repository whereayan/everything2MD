#### 6.4.3 Variables Unique to Findings About

The variable --OBJ is unique to Findings About. In conjunction with FATESTCD, it describes what the topic of the observation is; therefore, both are required to be populated for every record. FATESTCD describes the measurement/evaluation and FAOBJ describes the event or intervention that the measurement/evaluation is about.

When collected data fit a qualifier variable (see SDTM Sections 3.1.1, 3.1.2, and 3.1.3) and are represented in the FA domain, the name of the variable should be used as the value of FATESTCD. For example,

| FATESTCD | FATEST               |
| -------- | -------------------- |
| OCCUR    | Occurrence Indicator |
| SEV      | Severity/Intensity   |
| TOXGR    | Toxicity Grade       |

The use of the same names (e.g., SEV, OCCUR) for both qualifier variables in the observation classes and FATESTCD is deliberate, but should not lead users to conclude that the collection of such data (e.g., severity/intensity, occurrence) must be stored in the FA domain. In fact, data should only be stored in the FA domain if they do not fit in the general observation-class domain. If the data describe the underlying event or intervention as a whole and share its timing, then the data should be stored as a qualifier of the general observation- class record.

A record in FA may or may not have a parent record in an events or interventions domain. If an FA record does have a parent record, the value in FAOBJ should match the value in --TERM or --TRT, unless the parent domain is dictionary coded or subject to controlled terminology, in which case FAOBJ should match the value in --DECOD.

Examples for the FA and Skin Response (SR) domains include the use of RELREC to represent the relationship between an FA domain and a parent domain.
