# Project Scope

## 1. Overview

This project aims to systematically identify, collect, annotate, validate, and curate publicly available single-cell and single-nucleus datasets associated with psoriasis and hidradenitis suppurativa (HS).

The project focuses on dataset discovery and metadata curation across multiple public and controlled-access repositories.

The resulting resource is intended to provide a structured and reproducible collection of studies that can subsequently be used for downstream single-cell analysis.

---

## 2. Diseases of Interest

The project currently focuses on two diseases:

### 2.1 Psoriasis

Psoriasis is considered the primary disease category for datasets associated with psoriasis and its relevant clinical or biological terminology.

Potential terminology includes:

* Psoriasis
* Psoriasis vulgaris
* Plaque psoriasis
* Psoriatic skin
* Psoriatic lesion
* Psoriatic disease

### 2.2 Hidradenitis Suppurativa

Hidradenitis suppurativa (HS) is considered the second disease category.

Potential terminology includes:

* Hidradenitis suppurativa
* Hidradenitis
* Acne inversa
* HS

Disease terminology will be normalized during metadata curation while preserving the original repository-provided terminology.

---

## 3. Data Type

The primary focus is on single-cell and single-nucleus datasets.

The following data types may be included:

* scRNA-seq
* snRNA-seq
* CITE-seq
* single-cell multi-omics
* other single-cell modalities

The specific assay or modality will be recorded in the metadata.

Bulk RNA-seq and other non-single-cell datasets will not be considered eligible for the primary dataset collection.

---

## 4. Species

Both human and animal datasets are retained during the dataset discovery and curation process.

Species will be explicitly annotated rather than used as an initial exclusion criterion.

The final curated dataset will allow separation of:

* Human datasets
* Animal datasets
* Datasets with unknown or unresolved species information

Human and animal datasets will therefore be maintained as separate categories in the final dataset.

---

## 5. Biological Samples

Relevant biological samples may include, but are not limited to:

* Skin
* Lesional skin
* Non-lesional skin
* Perilesional tissue
* Blood
* PBMC
* Dermis
* Epidermis
* Hair follicle
* Other disease-relevant tissues

Original tissue descriptions will be retained, while normalized tissue categories may be generated during curation.

---

## 6. Data Repositories

The project will investigate multiple repositories and data portals, including:

* NCBI Gene Expression Omnibus (GEO)
* Sequence Read Archive (SRA)
* ArrayExpress / BioStudies
* Single Cell Portal
* Zenodo
* Figshare
* Synapse
* dbGaP
* European Genome-phenome Archive (EGA)
* ImmPort
* Single Cell Expression Atlas
* Human Cell Atlas

Additional repositories may be added if relevant datasets are identified.

---

## 7. Dataset Discovery

Dataset discovery will be performed using repository-specific search strategies.

Searches will use combinations of:

1. Disease-related terminology
2. Single-cell terminology
3. Relevant assay terminology
4. Repository-specific metadata fields

Search strategies and search dates will be documented to support reproducibility.

---

## 8. Metadata Curation

For each identified study, relevant metadata will be extracted and standardized.

Metadata may include:

* Study identifier
* Repository
* Accession
* Study title
* Disease
* Species
* Assay
* Tissue
* Sample information
* Patient/donor information
* Disease status
* Lesion status
* Publication information
* Data availability
* Cross-repository identifiers

Original metadata will be preserved whenever possible.

Normalized metadata will be generated separately.

---

## 9. Cross-Repository Relationships

A single biological study may be represented in multiple repositories.

For example, a study may have records in GEO, SRA, BioProject, and a publication.

These records should not automatically be treated as independent studies.

Cross-repository relationships will therefore be identified and represented using a canonical study identifier.

---

## 10. Deduplication

Duplicate or cross-referenced records will be identified during curation.

Potential matching identifiers include:

* GEO accession
* SRA accession
* BioProject accession
* BioSample accession
* PMID
* DOI
* Study title
* Sample identifiers

The final dataset will distinguish biological studies from their repository-specific records.

---

## 11. Data Access

The project will record the availability and access level of relevant data.

Possible categories include:

* Open access
* Controlled access
* Restricted access
* Metadata only
* Unknown

The presence or absence of downloadable raw or processed data will also be recorded.

---

## 12. Reproducibility

All major dataset discovery and curation decisions should be documented.

The project will maintain:

* Search strategies
* Inclusion and exclusion criteria
* Repository-specific methods
* Metadata schemas
* Normalization rules
* Deduplication rules
* Quality-control procedures
* Curation status
* Dataset release versions

The goal is to make the dataset curation process transparent and reproducible.

---

## 13. Project Phases

The project is divided into the following major phases:

### Phase 1 — Dataset Discovery

Identify potentially relevant datasets across public and controlled-access repositories.

### Phase 2 — Eligibility Screening

Determine whether candidate datasets satisfy the inclusion criteria.

### Phase 3 — Metadata Extraction

Extract study-level and sample-level metadata.

### Phase 4 — Metadata Normalization

Standardize disease, species, tissue, assay, and other metadata fields.

### Phase 5 — Cross-Repository Matching

Identify relationships between records representing the same biological study.

### Phase 6 — Deduplication

Create canonical study identifiers and remove duplicate study representations.

### Phase 7 — Quality Control

Validate metadata completeness, disease relevance, single-cell status, species, and data accessibility.

### Phase 8 — Final Dataset Construction

Generate curated datasets separated by disease and species.

---

## 14. Current Scope

The initial project scope includes psoriasis and hidradenitis suppurativa and retains both human and animal datasets.

Additional disease categories, data modalities, or repositories may be incorporated in future versions of the project.
