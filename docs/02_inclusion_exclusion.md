# Inclusion and Exclusion Criteria

## 1. Purpose

This document defines the criteria used to determine whether a dataset identified during repository searches is eligible for inclusion in the psoriasis and hidradenitis suppurativa single-cell dataset.

The criteria are applied during dataset screening and may be refined as the project develops. Any changes to the criteria should be documented in the Git history and project changelog.

---

# 2. General Inclusion Criteria

A study is considered potentially eligible when all of the following conditions can be established:

1. The study is associated with psoriasis or hidradenitis suppurativa.
2. The study contains single-cell or single-nucleus data.
3. The biological context of the dataset can be identified.
4. A stable identifier, accession, DOI, or other persistent reference is available.
5. Sufficient metadata is available to establish the relevance of the study.

A dataset may remain in the candidate or uncertain category when available metadata is insufficient for a definitive inclusion or exclusion decision.

---

# 3. Disease Eligibility

## 3.1 Psoriasis

The following terms may indicate potential psoriasis relevance:

* psoriasis
* psoriasis vulgaris
* plaque psoriasis
* psoriatic disease
* psoriatic skin
* psoriatic lesion
* psoriatic plaque
* psoriasis lesion

Disease relevance should not be determined solely from the study title.

Where possible, disease status should be verified using:

* Study metadata
* Sample metadata
* Experimental descriptions
* Publication information
* Supplementary metadata

---

## 3.2 Hidradenitis Suppurativa

The following terms may indicate potential hidradenitis suppurativa relevance:

* hidradenitis suppurativa
* hidradenitis
* acne inversa
* HS

As with psoriasis, disease relevance should be verified using available study- and sample-level metadata rather than relying exclusively on the title.

---

# 4. Single-Cell Eligibility

The primary dataset collection focuses on single-cell and single-nucleus technologies.

Potentially eligible modalities include:

* scRNA-seq
* single-cell RNA sequencing
* snRNA-seq
* single-nucleus RNA sequencing
* CITE-seq
* single-cell multi-omics
* other explicitly single-cell transcriptomic modalities

The specific assay should be recorded in the metadata.

---

# 5. Non-Single-Cell Data

The following datasets are not eligible for the primary single-cell collection when no single-cell or single-nucleus component is present:

* Bulk RNA-seq
* Bulk microarray
* Bulk transcriptomics
* Conventional RNA-seq without single-cell resolution
* Proteomics without a single-cell component
* Other non-single-cell molecular assays

A study containing both bulk and single-cell data may still be eligible if the single-cell component can be identified separately.

---

# 6. Species Eligibility

Human and animal datasets are both retained during the discovery and curation stages.

Species is therefore not an initial exclusion criterion.

The following categories may be represented:

* Human
* Mouse
* Rat
* Other animal species
* Unknown species

Species must be recorded whenever possible.

Human and animal datasets will be separated in the final curated dataset.

---

# 7. Biological Sample Eligibility

Relevant biological samples may include:

* Skin
* Lesional skin
* Non-lesional skin
* Perilesional tissue
* Dermis
* Epidermis
* Hair follicle
* Blood
* PBMC
* Other biologically relevant tissues or samples

Sample type alone does not determine eligibility.

The relationship between the sample and the disease must also be established.

---

# 8. Disease Status

Where possible, samples should be classified according to disease status.

Potential categories include:

* Disease
* Healthy control
* Non-lesional
* Lesional
* Perilesional
* Treatment-related
* Other disease control
* Unknown

Original metadata should be preserved.

Normalized disease-status categories may be created during curation.

---

# 9. Publication Status

A publication is not required for initial dataset discovery if the dataset contains sufficient metadata to establish eligibility.

Datasets with an associated publication should have the relevant publication identifiers recorded, including when available:

* PMID
* DOI
* Publication title
* Journal
* Publication year

A dataset should not be excluded solely because no publication has yet been identified.

---

# 10. Data Accessibility

A dataset does not need to provide a directly downloadable expression matrix to remain eligible.

The following situations may be recorded separately:

* Raw sequencing data available
* Processed matrix available
* Cell-level metadata available
* Raw data only
* Metadata only
* Controlled-access data
* Restricted data
* Unknown availability

The absence of publicly downloadable data should not automatically result in exclusion if the study otherwise satisfies the inclusion criteria.

---

# 11. Repository Eligibility

Potentially relevant records may be collected from multiple repositories, including:

* GEO
* SRA
* ArrayExpress
* BioStudies
* Single Cell Portal
* Zenodo
* Figshare
* Synapse
* dbGaP
* EGA
* ImmPort
* Single Cell Expression Atlas
* Human Cell Atlas

Additional repositories may be added if relevant datasets are identified.

---

# 12. Duplicate Records

A repository record should not automatically be considered an independent biological study.

The same study may be represented across multiple repositories.

Examples include:

* GEO and SRA
* GEO and BioProject
* SRA and BioProject
* Repository record and publication
* Multiple repository records referring to the same samples

Duplicate and cross-repository records will be identified during deduplication.

The records will be linked using a canonical study identifier.

---

# 13. Primary Exclusion Criteria

A dataset should be excluded when one or more of the following conditions are clearly established:

### 13.1 Wrong Disease

The dataset is unrelated to psoriasis or hidradenitis suppurativa.

### 13.2 No Single-Cell Component

The dataset contains only bulk or non-single-cell data.

### 13.3 Duplicate Study

The record is a duplicate representation of a study already included in the curated dataset.

### 13.4 Insufficient Evidence of Relevance

Available information is insufficient to establish a relationship with either target disease or a single-cell modality, after reasonable verification attempts.

### 13.5 Non-Biological or Technical Dataset

The record represents a technical demonstration, computational benchmark, synthetic dataset, or other dataset that does not contain relevant biological data.

### 13.6 Irrelevant Study Type

The record does not represent an original biological dataset relevant to the project.

---

# 14. Uncertain Category

Not all datasets should immediately be classified as included or excluded.

A dataset should be classified as `uncertain` when:

* Disease information is ambiguous.
* Single-cell status cannot be confirmed.
* Species information is missing.
* Metadata is incomplete.
* Repository records conflict.
* The relationship between study and samples is unclear.
* Additional publication or repository information is required.

Uncertain datasets should be retained in the intermediate dataset until additional evidence becomes available.

---

# 15. Screening Status

Each candidate dataset should receive one of the following screening statuses:

* `candidate`
* `screened`
* `included`
* `excluded`
* `uncertain`
* `duplicate`

These statuses represent the progression of dataset curation.

---

# 16. Exclusion Reasons

When a dataset is excluded, a standardized exclusion reason should be recorded.

Suggested values include:

* `wrong_disease`
* `not_single_cell`
* `bulk_data`
* `duplicate`
* `insufficient_metadata`
* `not_biological_dataset`
* `technical_dataset`
* `irrelevant_study`
* `accession_invalid`
* `other`

A free-text note may be added when additional explanation is necessary.

---

# 17. Evidence Hierarchy

Disease and experimental relevance should preferably be verified using multiple sources.

The following evidence hierarchy is recommended:

1. Sample-level metadata
2. Study-level metadata
3. Experimental description
4. Supplementary metadata
5. Associated publication
6. Abstract
7. Study title
8. Search-result snippet

Higher-level evidence should be preferred when available.

Search-result snippets should not be considered sufficient evidence for final inclusion when stronger evidence can be obtained.

---

# 18. Human and Animal Dataset Handling

Human and animal datasets are retained within the overall project.

They are not mixed without explicit annotation.

Each dataset should contain:

* `species`
* `taxonomy_id`
* `organism_group`

The `organism_group` field should classify the dataset as:

* `human`
* `animal`
* `unknown`

The final dataset will provide separate human and animal subsets.

---

# 19. Screening Workflow

Candidate datasets should follow this general workflow:

Discovery
→ Candidate
→ Screening
→ Eligibility assessment
→ Metadata extraction
→ Validation
→ Cross-repository matching
→ Deduplication
→ Final inclusion

Datasets with unresolved eligibility should remain in the `uncertain` category until sufficient evidence is obtained.

---

# 20. Changes to Eligibility Criteria

Any modification to the inclusion or exclusion criteria must be documented.

Changes should include:

* Date of change
* Previous criterion
* New criterion
* Reason for modification

This information should be preserved through Git history and project documentation.

---

# 21. Final Inclusion Principle

The primary goal of screening is to maximize the completeness of relevant single-cell datasets while maintaining transparent and reproducible eligibility decisions.

When evidence is insufficient for a definitive exclusion, the dataset should generally remain in the `uncertain` category rather than being discarded prematurely.
