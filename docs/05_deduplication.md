# Deduplication Strategy

## 1. Purpose

A single biological study may be represented in multiple repositories.

For example, the same study may have records in:

- GEO
- SRA
- BioProject
- BioSample
- BioStudies
- Single Cell Portal
- A publication

These records must not automatically be counted as independent biological studies.

The purpose of this document is to define the strategy used to identify and resolve duplicate or cross-referenced records.

---

# 2. Study-Level Versus Repository-Level Records

The project distinguishes between:

1. Biological studies
2. Repository records
3. Biological samples

A biological study may have multiple repository records.

Therefore:

```text
One biological study
        ↓
Multiple repository records
        ↓
Multiple samples
````

The final dataset should count biological studies rather than simply counting repository records.

---

# 3. Canonical Study Identifier

Each unique biological study receives an internal identifier:

```text
canonical_study_id
```

Recommended format:

```text
PSO_HS_XXXXXX
```

Example:

```text
PSO_HS_000001
PSO_HS_000002
PSO_HS_000003
```

The canonical study identifier remains stable even when the study has multiple repository accessions.

---

# 4. Primary Deduplication Identifiers

The following identifiers should be checked first when determining whether two records represent the same study:

1. BioProject accession
2. GEO accession
3. SRA accession
4. BioStudies accession
5. DOI
6. PMID
7. EGA accession
8. dbGaP accession
9. Sample identifiers

Exact identifier matches provide strong evidence of a shared study or dataset relationship.

---

# 5. Secondary Deduplication Evidence

When no exact shared identifier is available, additional evidence should be evaluated.

Potential evidence includes:

* Study title
* Publication title
* Authors
* Corresponding author
* Institution
* Experimental design
* Sample descriptions
* Number of samples
* Tissue
* Disease
* Species
* Sequencing technology
* Data availability statements

No single secondary field should automatically determine duplicate status.

---

# 6. Publication-Based Matching

Associated publications can provide strong evidence for linking datasets.

For each candidate study, the following should be checked:

* PMID
* DOI
* Publication title
* Authors
* Data availability statement
* Supplementary information
* Accession numbers

For example:

```text
GEO study
    ↓
Associated publication
    ↓
Data availability statement
    ↓
SRA / BioProject accession
```

This relationship should be recorded rather than treating the records as independent studies.

---

# 7. Cross-Repository Relationship

Cross-repository relationships should be stored explicitly.

Example:

```text
canonical_study_id = PSO_HS_000001

GEO:
GSEXXXXXX

SRA:
SRPXXXXXX

BioProject:
PRJNAxxxxxx

Publication:
PMID XXXXXXXX
DOI XXXXXXXX
```

All of these records may refer to the same biological study.

---

# 8. Sample-Level Matching

Sample identifiers are particularly useful for determining whether two repository records contain overlapping biological material.

Potential matching fields include:

* BioSample accession
* GEO sample accession
* SRA sample accession
* Sample name
* Donor identifier
* Tissue
* Disease status
* Experimental condition

If multiple samples can be confidently matched across repositories, this provides strong evidence of a shared study.

---

# 9. Duplicate Categories

Records should be classified into different relationship categories.

Recommended values:

* `unique_study`
* `same_study`
* `same_samples`
* `related_study`
* `partial_overlap`
* `uncertain`
* `duplicate_record`

---

# 10. Exact Duplicate

A record may be classified as an exact duplicate when:

* The repository explicitly identifies it as the same record, or
* The same accession is encountered more than once, or
* The same study record has been imported multiple times during the search process.

Exact duplicates should be removed from downstream analysis while retaining a record of the duplication.

---

# 11. Cross-Repository Duplicate

A cross-repository duplicate occurs when different repository records represent the same underlying biological study.

Example:

```text
GEO
GSE123456
        ↕
SRA
SRP123456
        ↕
BioProject
PRJNA123456
```

These records should share the same:

```text
canonical_study_id
```

---

# 12. Related but Distinct Studies

Not every study from the same publication or research group is necessarily a duplicate.

Two records may be related but represent:

* Different experiments
* Different patient cohorts
* Different tissues
* Different time points
* Different sequencing technologies
* Independent biological samples

Such records should remain separate studies when the evidence indicates that they represent distinct biological experiments.

---

# 13. Partial Sample Overlap

Two datasets may share some biological samples but also contain additional independent samples.

These should not automatically be merged.

Instead, the relationship should be recorded as:

```text
partial_overlap
```

The overlapping samples should be identified where possible.

---

# 14. Reanalysis Datasets

A publication or repository record may contain a reanalysis of previously published data.

Reanalysis datasets should be linked to the original study when the underlying biological samples are the same.

The project should distinguish:

```text
original study
```

from:

```text
reanalysis
```

The reanalysis should not automatically be counted as a new biological cohort.

---

# 15. Duplicate Detection Workflow

The recommended workflow is:

```text
Candidate records
        ↓
Exact accession matching
        ↓
Cross-repository identifier matching
        ↓
Publication matching
        ↓
Sample-level matching
        ↓
Study metadata comparison
        ↓
Relationship classification
        ↓
Canonical study assignment
```

---

# 16. Deduplication Priority

Evidence should generally be evaluated in the following order:

### Level 1 — Exact Identifier

Examples:

* Same accession
* Same BioProject
* Same BioSample
* Same DOI
* Same PMID

### Level 2 — Explicit Cross-Reference

Repository metadata explicitly references another accession.

### Level 3 — Publication Evidence

The same publication identifies multiple repository records.

### Level 4 — Sample Evidence

Sample identifiers or biological characteristics strongly overlap.

### Level 5 — Study Metadata

Study title, authors, tissue, disease, species, and experimental design are highly similar.

### Level 6 — Manual Review

If automated evidence is insufficient, the record should be classified as:

```text
uncertain
```

until manually reviewed.

---

# 17. Canonical Record Selection

When multiple repository records represent the same study, one record may be selected as the primary repository representation.

The selection should consider:

1. Completeness of metadata
2. Availability of sample information
3. Availability of raw data
4. Availability of processed data
5. Stability of the accession
6. Accessibility
7. Quality of metadata

Other repository records should remain linked to the same canonical study.

---

# 18. Deduplication Table

A dedicated cross-reference table should be maintained.

Recommended fields:

```text
canonical_study_id
repository
accession
relationship
matched_accession
evidence_type
confidence
notes
```

Example:

```text
PSO_HS_000001
GEO
GSE123456
same_study
SRP123456
explicit_cross_reference
high
```

---

# 19. Confidence

Deduplication decisions should include a confidence level.

Recommended values:

* `high`
* `medium`
* `low`
* `uncertain`

### High confidence

Exact identifier or explicit repository cross-reference.

### Medium confidence

Strong publication or sample-level evidence.

### Low confidence

Similarity based mainly on study metadata.

### Uncertain

Insufficient evidence for a reliable decision.

---

# 20. Manual Review

Automated deduplication should not be considered sufficient for all cases.

Records with:

* conflicting identifiers
* partial sample overlap
* ambiguous publication relationships
* similar but non-identical study titles
* unclear cohort relationships

should be flagged for manual review.

---

# 21. Preservation of Duplicate Information

Duplicate records should not simply be deleted.

The original repository record and its relationship should remain documented.

This allows the project to maintain an audit trail of how the final dataset was constructed.

---

# 22. Example

Suppose the following records are identified:

```text
GSE200001
SRP300001
PRJNA400001
PMID500001
```

Repository metadata and the associated publication indicate that all four records correspond to the same biological study.

They should therefore be represented as:

```text
canonical_study_id = PSO_HS_000001
```

with the corresponding repository identifiers stored separately.

The study should be counted once in study-level analyses.

---

# 23. Important Distinction

The number of repository records is not necessarily equal to the number of biological studies.

For example:

```text
10 GEO records
+ 8 SRA records
+ 5 BioProject records
```

may represent only:

```text
12 unique biological studies
```

Therefore, study counts should be calculated after cross-repository deduplication.

---

# 24. Final Deduplication Principle

The objective of deduplication is not simply to minimize the number of records.

The objective is to correctly determine which repository records represent:

* the same biological study
* related studies
* partially overlapping studies
* genuinely independent studies

All decisions should be evidence-based, reproducible, and documented.
