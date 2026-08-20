# Metadata Schema

## 1. Purpose

This document defines the standardized metadata schema used to represent studies, samples, repository records, biological characteristics, experimental characteristics, and curation information.

The schema is designed to support datasets collected from multiple repositories while preserving repository-specific information.

The schema distinguishes between:

1. Study-level metadata
2. Sample-level metadata
3. Repository-level identifiers
4. Experimental metadata
5. Biological metadata
6. Publication metadata
7. Data-access metadata
8. Curation metadata

---

# 2. Data Model

The project uses a hierarchical model:

Study
→ Repository Record
→ Sample
→ Biological / Experimental Metadata

A single biological study may have multiple repository records.

A single study may also contain multiple biological samples.

Therefore, study identifiers and sample identifiers must not be treated as interchangeable.

---

# 3. Study-Level Metadata

Study-level metadata describes the biological research study as a whole.

| Field | Description |
|---|---|
| canonical_study_id | Internal unique identifier assigned by this project |
| study_title | Study title |
| study_description | Study description |
| disease_raw | Original disease terminology |
| disease_normalized | Standardized disease category |
| study_type | Type of biological study |
| primary_repository | Repository in which the study was initially identified |
| publication_title | Associated publication title |
| publication_year | Publication year |

### canonical_study_id

This is the internal identifier assigned by the project.

Example:

`PSO_HS_000001`

The identifier must remain stable across repository-specific records.

---

# 4. Disease Metadata

Disease information should be represented using both original and normalized terminology.

| Field | Description |
|---|---|
| disease_raw | Disease terminology as provided by the source |
| disease_normalized | Standardized disease category |
| disease_status | Disease/control/other status |
| disease_ontology_id | Ontology identifier when available |

### Recommended normalized disease categories

- `psoriasis`
- `hidradenitis_suppurativa`
- `unknown`

Original terminology must be preserved in `disease_raw`.

---

# 5. Species Metadata

Species information should also preserve both original and normalized values.

| Field | Description |
|---|---|
| species_raw | Original organism description |
| species | Normalized species name |
| taxonomy_id | NCBI taxonomy identifier when available |
| organism_group | Human/animal/unknown |

### organism_group

Allowed values:

- `human`
- `animal`
- `unknown`

Examples:

| species_raw | species | taxonomy_id | organism_group |
|---|---|---:|---|
| Homo sapiens | human | 9606 | human |
| human | human | 9606 | human |
| Mus musculus | mouse | 10090 | animal |
| mouse | mouse | 10090 | animal |

---

# 6. Repository Metadata

Repository-specific information must be retained.

| Field | Description |
|---|---|
| repository | Repository name |
| accession | Primary repository accession |
| secondary_accession | Additional accession |
| repository_record_url | Repository record reference |
| record_type | Type of repository record |
| access_level | Public/controlled/restricted/unknown |

Possible repository values include:

- `GEO`
- `SRA`
- `BioStudies`
- `ArrayExpress`
- `Single Cell Portal`
- `Zenodo`
- `Figshare`
- `Synapse`
- `dbGaP`
- `EGA`
- `ImmPort`
- `Single Cell Expression Atlas`
- `Human Cell Atlas`

---

# 7. Cross-Repository Identifiers

Cross-repository relationships should be explicitly recorded.

| Field | Description |
|---|---|
| geo_accession | GEO accession |
| sra_accession | SRA accession |
| bioproject_accession | NCBI BioProject accession |
| biosample_accession | NCBI BioSample accession |
| ega_accession | EGA accession |
| dbgap_accession | dbGaP accession |
| publication_doi | DOI |
| pmid | PubMed identifier |

These fields allow records from different repositories to be linked.

---

# 8. Sample-Level Metadata

Sample-level metadata describes individual biological samples.

| Field | Description |
|---|---|
| sample_id | Internal sample identifier |
| source_sample_id | Original repository sample identifier |
| sample_name | Sample name |
| sample_type | Type of biological sample |
| tissue_raw | Original tissue description |
| tissue | Normalized tissue category |
| lesion_status | Lesional/non-lesional/etc. |
| disease_status | Disease/control/etc. |
| species | Species |
| sex | Biological sex |
| age | Age or age category |
| patient_id | De-identified participant identifier when available |

---

# 9. Tissue Metadata

Both original and normalized tissue descriptions should be retained.

| Field | Description |
|---|---|
| tissue_raw | Original tissue description |
| tissue | Normalized tissue |
| organ | Organ |
| anatomical_site | Anatomical location |

Examples of normalized tissue categories:

- `skin`
- `blood`
- `PBMC`
- `dermis`
- `epidermis`
- `hair_follicle`
- `other`
- `unknown`

---

# 10. Lesion Status

Where available, lesion status should be recorded.

Recommended values:

- `lesional`
- `non_lesional`
- `perilesional`
- `healthy`
- `unknown`

The original terminology should be retained separately.

---

# 11. Experimental Metadata

Experimental metadata describes the single-cell experiment.

| Field | Description |
|---|---|
| assay | Main assay |
| single_cell | Whether single-cell resolution is present |
| single_cell_type | scRNA-seq/snRNA-seq/etc. |
| sequencing_platform | Sequencing platform |
| library_preparation | Library preparation method |
| technology | Experimental technology |
| modality | Transcriptomic/multi-omic/etc. |

### Recommended single_cell_type values

- `scRNA-seq`
- `snRNA-seq`
- `CITE-seq`
- `single-cell_multiome`
- `other`
- `unknown`

---

# 12. Data Availability

Data availability should be represented explicitly.

| Field | Description |
|---|---|
| raw_data_available | Whether raw sequencing data are available |
| processed_data_available | Whether processed data are available |
| matrix_available | Whether an expression matrix is available |
| cell_metadata_available | Whether cell-level metadata are available |
| raw_data_access | Access mechanism |
| processed_data_access | Access mechanism |

Recommended access categories:

- `open`
- `controlled`
- `restricted`
- `metadata_only`
- `unknown`

---

# 13. Publication Metadata

Publication information should be retained when available.

| Field | Description |
|---|---|
| pmid | PubMed identifier |
| doi | DOI |
| publication_title | Publication title |
| journal | Journal |
| publication_year | Publication year |
| authors | Authors |

A missing publication does not automatically exclude a dataset.

---

# 14. Curation Metadata

Curation information records the decisions made during this project.

| Field | Description |
|---|---|
| inclusion_status | Current screening status |
| exclusion_reason | Reason for exclusion |
| curation_status | Current curation stage |
| curator | Person responsible for curation |
| curation_date | Date of curation |
| last_updated | Last metadata update |
| notes | Free-text notes |

### inclusion_status

Recommended values:

- `candidate`
- `included`
- `excluded`
- `uncertain`
- `duplicate`

### curation_status

Recommended values:

- `discovered`
- `screened`
- `metadata_extracted`
- `validated`
- `deduplicated`
- `final`

---

# 15. Evidence Metadata

Important curation decisions should be traceable to their evidence.

| Field | Description |
|---|---|
| disease_evidence | Evidence supporting disease assignment |
| single_cell_evidence | Evidence supporting single-cell classification |
| species_evidence | Evidence supporting species assignment |
| publication_evidence | Evidence from associated publication |
| evidence_notes | Additional evidence notes |

Possible evidence sources include:

- Repository metadata
- Sample metadata
- Publication
- Supplementary material
- Data availability statement
- Cross-repository record

---

# 16. Raw Versus Normalized Metadata

The project must preserve original metadata whenever possible.

For fields that require normalization, both the original and normalized values should be retained.

Examples:

```text
species_raw
species

disease_raw
disease_normalized

tissue_raw
tissue
Original metadata must not be overwritten.
```

# 17. Missing Data

Missing metadata should not be silently converted into a biological interpretation.

Recommended values:

empty / null when truly missing
unknown when the field was checked but could not be determined

The distinction between missing and unknown should be preserved whenever possible.

# 18. Study and Sample Identifiers

The project will use internal identifiers in addition to repository identifiers.

Study identifier

Format:

PSO_HS_XXXXXX

Example:

PSO_HS_000001

Sample identifier

Format:

PSO_HS_SXXXXXX

Example:

PSO_HS_S000001

Repository identifiers must remain stored separately.

# 19. Duplicate Handling

Multiple repository records may correspond to the same biological study.

The following identifiers should be considered during duplicate detection:

BioProject accession
GEO accession
SRA accession
DOI
PMID
Sample identifiers
Study title
Publication authors

Duplicate records should be linked to the same canonical_study_id.

# 20. Recommended Master Study Table

The final study-level table should contain at minimum:

canonical_study_id
study_title
disease_raw
disease_normalized
species
organism_group
primary_repository
accession
geo_accession
sra_accession
bioproject_accession
pmid
doi
assay
single_cell_type
access_level
raw_data_available
processed_data_available
inclusion_status
exclusion_reason
curation_status
curation_date
notes
# 21. Recommended Master Sample Table

The final sample-level table should contain at minimum:

canonical_study_id
sample_id
source_sample_id
sample_name
species
organism_group
disease_raw
disease_normalized
disease_status
tissue_raw
tissue
organ
anatomical_site
lesion_status
sex
age
patient_id
assay
single_cell_type
# 22. Data Model Summary

The overall structure can be represented as:

Study
│
├── Repository Records
│ ├── GEO
│ ├── SRA
│ ├── BioStudies
│ └── Other repositories
│
├── Publications
│ ├── PMID
│ └── DOI
│
└── Samples
├── Biological metadata
├── Experimental metadata
└── Disease metadata

This structure prevents repository records from being incorrectly treated as independent biological studies.

# 23. Schema Evolution

The metadata schema may evolve as new repositories and dataset types are evaluated.

Changes to the schema should:

Be documented.
Preserve existing information.
Avoid unnecessary renaming of established fields.
Be reflected in scripts and validation rules.
Be recorded through Git commits.

Schema changes should not silently invalidate previously curated data.



---
