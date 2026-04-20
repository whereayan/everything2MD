#### 6.4.2 Naming Findings About Domains

Findings About domains are defined to store findings about events or interventions. Sponsors may choose to represent FA data collected in the study in a single FA dataset (potentially splitting the FA domain into physically separate datasets following the guidance described in Section 4.1.6, Additional Guidance on Dataset Naming), or separate datasets, assigning unique custom 2-character domain codes (see examples in Section 6.4.5, Skin Response).

For example, if findings about clinical events and findings about medical history are collected in a study, these could be represented as:

1. A single FA domain, perhaps separated with different FACAT and/or FASCAT values
2. A split FA domain following the guidance in Section 4.1.7, Splitting Domains:

   - The DOMAIN value would be “FA”.
   - Variables that require a prefix would use “FA”.
   - The dataset names would be the domain name plus up to 2 additional characters indicating the parent domain (e.g., FACE for Findings About Clinical Events, FAMH for Findings About Medical History). This naming convention may be used for an FA domain that has a parent domain even when the study has only 1 FA dataset that is not being split.
   - FASEQ must be unique within USUBJID for all records across the split datasets.
   - Supplemental qualifier datasets would need to be managed at the split-file level (e.g., suppface.xpt, suppfamh.xpt). Within each supplemental qualifier dataset, RDOMAIN would be "FA".
   - If a dataset-level RELREC is defined (e.g., between the CE and FACE datasets), then RDOMAIN may contain up to 4 characters to effectively describe the relationship between the CE parent records and the FACE child records.
3. Separate domains where:

   - The DOMAIN value is sponsor-defined and does not begin with FA, following examples in Section 6.4.5, Skin Response, which has a domain code of SR.
   - All published FA guidance applies, specifically:

     - The --OBJ variable cannot be added to a standard Findings domain. A domain is either a Findings domain or a Findings About domain, not one or the other depending on the situation.
     - When the --OBJ variable is included in a domain, this identifies it as an FA domain, and the --OBJ variable must be populated for all records.
   - All published domain guidance applies, specifically:

     - Variables that require a prefix would use the 2-character domain code chosen.

For the naming of datasets with findings about events or interventions for associated persons, refer to the SDTMIG: Associated Persons (available at https://www.cdisc.org/standards/foundational/sdtm).
