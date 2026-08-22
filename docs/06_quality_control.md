# Quality Control

## 1. Purpose

This document defines the quality-control procedures used to validate candidate datasets before they are included in the final curated collection.

Quality control is performed after dataset discovery and metadata extraction and before final dataset construction.

---

# 2. QC Principles

Quality control should verify:

1. Dataset identity
2. Disease relevance
3. Single-cell status
4. Species
5. Biological sample
6. Experimental technology
7. Metadata completeness
8. Data availability
9. Cross-repository relationships
10. Duplicate status

A dataset should not be considered fully validated until the relevant QC checks have been completed.

---

# 3. Dataset Identity

The following should be checked:

- Repository
- Accession
- Study title
- Study description
- Repository record availability

The accession should be valid and traceable to the original repository.

---

# 4. Disease Validation

Disease assignment should be verified using available evidence.

Preferred evidence sources include:

1. Sample metadata
2. Study metadata
3. Experimental description
4. Associated publication
5. Supplementary information

The disease should be assigned to one of:

- `psoriasis`
- `hidradenitis_suppurativa`
- `unknown`

A dataset should not be assigned to a disease solely because a search-result snippet contains the disease name.

---

# 5. Single-Cell Validation

The presence of single-cell or single-nucleus data should be explicitly verified.

Potential evidence includes:

- Assay metadata
- Platform information
- Study description
- Publication
- Processed matrix
- Cell-level metadata

The following categories should be distinguished:

- `scRNA-seq`
- `snRNA-seq`
- `CITE-seq`
- `single-cell_multiome`
- `other`
- `unknown`

Bulk RNA-seq should not be classified as single-cell data.

---

# 6. Species Validation

Species should be validated whenever possible.

The following fields should be checked:

- Organism
- Taxonomy identifier
- Sample metadata
- Publication

The final metadata should contain:

- `species_raw`
- `species`
- `taxonomy_id`
- `organism_group`

Recommended organism groups:

- `human`
- `animal`
- `unknown`

---

# 7. Tissue and Sample Validation

The biological sample should be reviewed.

Important fields include:

- Tissue
- Organ
- Anatomical site
- Sample type
- Lesion status
- Disease status

Original descriptions should be preserved.

Normalized categories should be generated separately.

---

# 8. Disease and Control Samples

Where sample-level information is available, disease and control samples should be distinguished.

Possible categories include:

- Disease
- Healthy control
- Non-lesional
- Lesional
- Perilesional
- Treatment-related
- Other
- Unknown

Sample-level classification should be preferred over study-level assumptions.

---

# 9. Experimental Validation

The following experimental characteristics should be checked where available:

- Sequencing technology
- Assay
- Single-cell platform
- Library preparation
- Sequencing platform
- Data modality

Inconsistent or ambiguous experimental information should be documented in the notes.

---

# 10. Metadata Completeness

Metadata completeness should be evaluated using required fields.

At minimum, an included study should have:

- Repository
- Accession
- Study title
- Disease
- Single-cell status
- Species or unresolved species status

Additional fields should be populated whenever available.

Missing optional metadata does not automatically exclude a dataset.

---

# 11. Required Fields

The following fields are considered important for final inclusion:

```text
canonical_study_id
repository
accession
study_title
disease_normalized
species
organism_group
single_cell
single_cell_type
inclusion_status
curation_status
12. Data Availability QC

The following should be checked:

Raw sequencing data
Processed expression matrix
Cell metadata
Repository accessibility
Controlled-access requirements

Data availability should be recorded even when data cannot be downloaded directly.

13. Cross-Repository QC

Cross-repository identifiers should be checked when available.

Examples:

GEO ↔ SRA
GEO ↔ BioProject
SRA ↔ BioProject
BioProject ↔ BioSample
Repository ↔ Publication

Conflicting identifiers should be flagged for review.

14. Duplicate QC

Each candidate should be evaluated for duplication.

Potential duplicate evidence includes:

Same accession
Same BioProject
Same BioSample
Same DOI
Same PMID
Same publication
Same sample identifiers
Explicit repository cross-reference

The deduplication strategy is defined in:

docs/05_deduplication.md

15. Publication QC

When a publication is available, the following should be checked:

PMID
DOI
Publication title
Authors
Publication year
Data availability statement
Repository accession

Publication information should be used as supporting evidence rather than automatically overriding repository metadata.

16. Quality-Control Status

Each dataset should have a QC status.

Recommended values:

not_checked
in_progress
passed
passed_with_warnings
failed
needs_manual_review
17. QC Flags

Potential QC flags include:

missing_species
missing_disease
ambiguous_disease
unclear_single_cell_status
missing_tissue
missing_sample_metadata
controlled_access
duplicate_candidate
cross_repository_conflict
publication_not_found
accession_not_verified

Multiple flags may be assigned to the same dataset.

18. Manual Review

Datasets should be manually reviewed when automated validation cannot establish eligibility.

Manual review is particularly important when:

Disease terminology is ambiguous
HS is used without clarification
Single-cell status is unclear
Species is missing
Multiple studies appear to share samples
Repository metadata conflicts with publication information
Dataset relationships are unclear
19. QC Decision

After QC, a dataset may be assigned one of the following outcomes:

passed
passed_with_warnings
failed
needs_manual_review

A failed QC status should include an explanatory note.

20. QC Audit Trail

QC decisions should be traceable.

For each manually reviewed dataset, the project should retain:

Accession
Date reviewed
QC status
QC flags
Evidence source
Reviewer
Notes
21. Quality-Control Workflow

The recommended workflow is:

Dataset discovery
        ↓
Metadata extraction
        ↓
Disease validation
        ↓
Single-cell validation
        ↓
Species validation
        ↓
Sample/tissue validation
        ↓
Experimental validation
        ↓
Data availability check
        ↓
Cross-repository check
        ↓
Duplicate check
        ↓
QC decision
        ↓
Final inclusion
22. QC and Inclusion Are Different

Quality control and eligibility screening are related but distinct.

A dataset may satisfy the inclusion criteria but still require additional QC.

For example:

Eligible dataset
        ↓
QC reveals missing species
        ↓
passed_with_warnings

This dataset should not necessarily be excluded.

Similarly:

Candidate dataset
        ↓
Single-cell status cannot be verified
        ↓
needs_manual_review

The dataset should remain in the intermediate collection until a final decision is possible.

23. Final QC Principle

The purpose of quality control is not to remove datasets unnecessarily.

The goal is to ensure that every dataset in the final collection has:

A traceable source
A documented disease assignment
A documented experimental type
A species classification when possible
Sufficient metadata for downstream interpretation
A documented curation decision

All unresolved issues should remain visible through QC flags and notes.
