# Search Strategy

## 1. Purpose

This document defines the systematic search strategy used to identify single-cell and single-nucleus datasets associated with psoriasis and hidradenitis suppurativa (HS).

The strategy is designed to maximize the identification of relevant datasets while maintaining a reproducible record of search terms, repositories, search dates, and screening procedures.

---

# 2. Search Concepts

The search strategy is based on three major concepts:

1. Disease
2. Single-cell technology
3. Data repository

The exact implementation of the search varies according to the capabilities and metadata structure of each repository.

---

# 3. Disease Search Terms

## 3.1 Psoriasis

The following terms are used to identify psoriasis-related datasets:

* psoriasis
* psoriatic
* psoriasis vulgaris
* plaque psoriasis
* psoriatic disease
* psoriatic skin
* psoriatic lesion
* psoriatic plaque

Additional disease-related terms may be added if relevant datasets are identified using alternative terminology.

---

## 3.2 Hidradenitis Suppurativa

The following terms are used to identify hidradenitis suppurativa-related datasets:

* hidradenitis suppurativa
* hidradenitis
* acne inversa
* HS

Because `HS` is an ambiguous abbreviation, records identified solely through `HS` should undergo additional manual validation.

---

# 4. Single-Cell Search Terms

The following terms may be used to identify single-cell or single-nucleus datasets:

* single-cell
* single cell
* single-cell RNA
* single-cell RNA-seq
* single-cell RNA sequencing
* scRNA-seq
* scRNAseq
* single-nucleus
* single nucleus
* single-nucleus RNA-seq
* snRNA-seq
* snRNAseq
* CITE-seq
* single-cell multi-omics
* single-cell transcriptomics

The exact terminology used depends on the search functionality of the repository.

---

# 5. Core Search Combinations

The primary conceptual search structure is:

Disease AND Single-cell terminology

Examples include:

### Psoriasis

* `psoriasis AND single-cell`
* `psoriasis AND scRNA-seq`
* `psoriasis AND single-cell RNA`
* `psoriatic AND single-cell`
* `psoriatic AND scRNA-seq`
* `psoriatic skin AND single-cell`
* `psoriatic lesion AND single-cell`

### Hidradenitis Suppurativa

* `"hidradenitis suppurativa" AND single-cell`
* `"hidradenitis suppurativa" AND scRNA-seq`
* `"hidradenitis suppurativa" AND single-cell RNA`
* `hidradenitis AND single-cell`
* `"acne inversa" AND single-cell`
* `"acne inversa" AND scRNA-seq`

The ambiguous abbreviation `HS` should generally be used only as a supplementary search term and requires additional validation.

---

# 6. Repository Search Strategy

The following repositories and data portals are included in the initial search:

1. NCBI GEO
2. NCBI SRA
3. ArrayExpress / BioStudies
4. Single Cell Portal
5. Zenodo
6. Figshare
7. Synapse
8. dbGaP
9. EGA
10. ImmPort
11. Single Cell Expression Atlas
12. Human Cell Atlas

Additional repositories may be added during the project.

---

# 7. Repository-Specific Search

Each repository will have its own documented search protocol.

Repository-specific documentation is maintained under:

`docs/repositories/`

Each repository protocol should document:

* Search date
* Search interface or API
* Search terms
* Filters
* Metadata fields examined
* Candidate identification procedure
* Limitations
* Output files

---

# 8. Search Date

Every search should be associated with a search date.

The date should be recorded using ISO 8601 format:

`YYYY-MM-DD`

For example:

`2026-08-20`

Search dates are important because public repositories are continuously updated.

---

# 9. Search Result Preservation

Where possible, the original search results should be preserved before screening.

Raw search results should be stored under:

`data/raw/<repository>/`

The original search output should not be overwritten during normalization or curation.

---

# 10. Candidate Dataset Identification

A search result becomes a candidate dataset when it appears potentially relevant based on the available repository metadata.

At the candidate stage, inclusion should not yet be considered final.

Candidate datasets should be recorded before detailed screening.

Each candidate should receive a repository-specific identifier such as:

* GEO accession
* SRA accession
* BioStudies accession
* Single Cell Portal study identifier
* DOI
* Other persistent identifier

---

# 11. Screening After Search

Search results are subject to subsequent screening.

The following questions should be considered:

1. Is the study related to psoriasis or HS?
2. Does it contain single-cell or single-nucleus data?
3. What species was studied?
4. What biological sample was analyzed?
5. Can the disease/sample relationship be established?
6. Is the record a duplicate or cross-reference of another study?
7. What data are available?
8. Is additional validation required?

Search relevance alone is not sufficient for final inclusion.

---

# 12. Search Result Categories

Search results may be classified as:

* `candidate`
* `included`
* `excluded`
* `uncertain`
* `duplicate`

The reason for exclusion or uncertainty should be recorded whenever applicable.

---

# 13. Human and Animal Search

The initial search does not exclude animal datasets.

Both human and animal datasets should be collected and subsequently annotated using species metadata.

The search process should therefore avoid applying a human-only filter unless a specific repository-level analysis requires it.

---

# 14. Publication-Assisted Discovery

Associated publications may be used to identify additional datasets.

When a relevant publication is identified, the following should be checked when available:

* Supplementary information
* Data availability statement
* GEO accession
* SRA accession
* BioProject accession
* BioSample identifiers
* Other repository identifiers

Publication-based discoveries should be incorporated into the same screening workflow as repository-based discoveries.

---

# 15. Cross-Repository Searching

When a candidate dataset is identified in one repository, associated identifiers should be used to search other repositories.

For example:

GEO accession
→ SRA
→ BioProject
→ BioSample
→ Publication

This process helps identify the complete repository representation of a biological study.

---

# 16. Search Completeness

No single repository is assumed to contain all relevant datasets.

The project therefore uses multiple repositories to improve coverage.

A dataset identified in one repository may lead to additional records in another repository.

Searches should continue across all planned repositories even after relevant studies have been identified.

---

# 17. Search Limitations

Potential limitations include:

* Inconsistent terminology across repositories
* Missing or incomplete metadata
* Different search interfaces
* Different indexing strategies
* Ambiguous disease abbreviations
* Studies deposited under generic titles
* Studies represented by multiple accessions
* Controlled-access datasets
* Changes in repository metadata over time

These limitations should be documented during curation.

---

# 18. Search Log

A search log should be maintained for each repository.

The minimum recommended fields are:

| Field           | Description                  |
| --------------- | ---------------------------- |
| repository      | Repository searched          |
| search_date     | Date of search               |
| disease         | Target disease               |
| query           | Exact search query           |
| filters         | Repository filters used      |
| result_count    | Number of returned records   |
| candidate_count | Number of candidate datasets |
| notes           | Additional observations      |

---

# 19. Search Workflow

The general search workflow is:

Repository selection
→ Search-term definition
→ Repository search
→ Raw result preservation
→ Candidate identification
→ Metadata extraction
→ Eligibility screening
→ Validation
→ Cross-repository matching
→ Deduplication

---

# 20. Search Strategy Versioning

Search terminology and search procedures may evolve during the project.

Changes should be versioned and documented.

Examples of changes include:

* Addition of new disease synonyms
* Addition of new single-cell terminology
* Addition of new repositories
* Modification of repository filters
* Changes to search logic

All substantial changes should be recorded through Git commits and documented in the repository-specific search protocol.

---

# 21. Initial Search Scope

The initial search scope includes:

### Diseases

* Psoriasis
* Hidradenitis suppurativa

### Organisms

* Human
* Animal

### Primary technologies

* scRNA-seq
* snRNA-seq

### Repositories

* GEO
* SRA
* ArrayExpress / BioStudies
* Single Cell Portal
* Zenodo / Figshare
* Synapse
* dbGaP / EGA
* ImmPort
* Single Cell Expression Atlas
* Human Cell Atlas

This scope may be expanded as the project develops.
