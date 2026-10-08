# GPCRdb Structural Alignment Benchmark Dataset

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23243974.svg)](https://doi.org/10.5281/zenodo.23243974)

This repository provides a comprehensive benchmark dataset for the evaluation of **multiple sequence alignment (MSA) methods**, with a particular emphasis on **structure-aware and transmembrane-aware alignment of G protein-coupled receptors (GPCRs)**.

The dataset integrates **sequence data, AlphaFold2-predicted structures, distance matrices, transmembrane region annotations, reference alignments**, and **processed alignment results** obtained from multiple software tools.

It is designed to support **reproducible research** in structural bioinformatics, topology-aware alignment, and multi-objective optimization of MSAs.

**Dataset Overview:**
- **Total human GPCR sequences:** 284 (or 133 in the reduced 19-protein version)
- **GPCR classes covered:** 9 main classes/subclasses
- **Sequence source:** GPCRdb, with UniProt-linked identifiers used for structure retrieval
- **Structure data:** AlphaFold Protein Structure Database coordinate models (PDB) and Predicted Aligned Error records (JSON)
- **Alignment tools evaluated:** sequence-based baselines plus major structure-based tools
- **New additions:** dedicated experiment outputs and workflow scripts for Mustang, Caretta, mTM-align, FoldMason, and US-align

---

## Archived dataset release

The dataset version described in the companion *Data in Brief* article is permanently archived in Zenodo.

- **Version:** 1.0.0
- **Version DOI:** [10.5281/zenodo.23243974](https://doi.org/10.5281/zenodo.23243974)
- **DOI for all versions:** [10.5281/zenodo.23243973](https://doi.org/10.5281/zenodo.23243973)
- **GitHub release:** [v1.0.0](https://github.com/TM-M2StructAlign/Dataset_Structural_GPCRs/releases/tag/v1.0.0)
- **Source snapshot:** Git commit `75287f1da907248aa29b8fb5adf17a4c63891797`

For reproducible use of the dataset described in the associated publication, please cite the version-specific Zenodo DOI above. The GitHub repository is the active development location and may receive documentation or future data updates after this archived release.

---

## Project ecosystem

This benchmark is part of the TM-M2StructAlign research ecosystem:

| Resource | Repository |
| --- | --- |
| **TM-M2StructAlign source code** | [TM-M2StructAlign](https://github.com/TM-M2StructAlign/TM-M2StructAlign) |
| **GPCR structural benchmark and experimental resources** | [Dataset_Structural_GPCRs](https://github.com/TM-M2StructAlign/Dataset_Structural_GPCRs) |
| **Main manuscript and supplementary material** | [TM-M2StructAlign-Paper](https://github.com/JOELITO07/TM-M2StructAlign-Paper) |

The companion data-article manuscript is maintained in [TM-M2StructAlign_Dataset_paper](https://github.com/JOELITO07/TM-M2StructAlign_Dataset_paper).

---

## Dataset Versions

The dataset is provided in **two complementary versions** to support different experimental scenarios.

### 1. Full Dataset (Complete Version)

The complete dataset includes **all available human GPCR sequences** grouped by biologically meaningful subclasses. This version is intended for:

- Large-scale MSA benchmarking
- Statistical and evolutionary analysis
- Scalability evaluation of alignment algorithms

**Composition of the full dataset:**

| Class (group)                    | Number of sequences |
| -------------------------------- | ------------------- |
| Class Aα (Rhodopsin – Aminergic) | 36                  |
| Class Aβ (Rhodopsin – Peptide)   | 76                  |
| Class Aγ (Rhodopsin – Protein)   | 30                  |
| Class Aδ (Rhodopsin – Lipid)     | 36                  |
| Class B1 (Secretin)              | 15                  |
| Class B2 (Adhesion)              | 33                  |
| Class C (Glutamate)              | 22                  |
| Class F (Frizzled)               | 11                  |
| Class T2 (Taste 2)               | 25                  |
| **Total**                        | **284**             |

Sequence characteristics:
- **Length range:** Approximately 290 to 6,000+ amino acids
- **Longest sequences:** Adhesion GPCRs (Class B2), with multiple extracellular domains
- **Alignment focus:** Transmembrane (TM) regions identified and extracted
- **Sequence coverage:** All major human GPCR classes and well-studied subfamilies

---

### 2. Reduced Dataset (_19 Version)

A reduced version of the dataset was constructed, containing **exactly 19 proteins per class/subclass** (where applicable).

This version was created to accommodate methodological constraints of certain structure-based alignment tools:

> Dong et al., *mTM-align: an algorithm for fast and accurate multiple protein structure alignment*, Bioinformatics, 34:1719–1725 (2018)

The original **mTM-align** implementation enforces a hard limit of **19 PDB structures per input**.

**Reduced Dataset Composition:**
- **Seven deterministic 19-protein subsets:** `classA_001_19`, `classA_002_19`, `classA_003_19`, `classA_004_19`, `classB2_19`, `classC_19`, and `classT2_19`
- **Total sequence instances:** 133 (7 × 19)
- **Classes B1 and F:** used directly from the full collection because they contain 15 and 11 proteins, respectively
- **Suffix notation:** `_19` appended to the seven reduced subset names
- **Purpose:** Standardize structural-alignment input size and support workflows with practical input-size constraints

---

## Directory Structure

```
📦 Datasets/
├── 📄 README.md                    # This file
├── 📁 GPCRdb/                      # Main dataset directory
│   ├── 📄 List19Proteins.txt       # List of proteins in reduced 19-protein version
│   ├── 📁 sequences/               # Sequence data in multiple formats
│   ├── 📁 alphafold_pdb/           # AlphaFold2 structures (PDB format)
│   ├── 📁 alphafold_json/          # AlphaFold2 structures (JSON format)
│   ├── 📁 distances/               # Distance matrices from structures
│   ├── 📁 weights/                 # Auxiliary PAE-derived confidence-weight matrices
│   ├── 📁 reference_alignments/    # GPCRdb-derived reference alignments
│   ├── 📁 precomputed/             # Precomputed structural-alignment experiment outputs
│   │   ├── classA_001/
│   │   ├── classA_001_19/
│   │   ├── classA_002/
│   │   ├── classA_002_19/
│   │   ├── classA_003/
│   │   ├── classA_003_19/
│   │   ├── classA_004/
│   │   ├── classA_004_19/
│   │   ├── classB1/
│   │   ├── classB2/
│   │   ├── classB2_19/
│   │   ├── classC/
│   │   ├── classC_19/
│   │   ├── classF/
│   │   ├── classT2/
│   │   ├── classT2_19/
│   │   └── resultados_precomputed.txt
│   └── 📁 resultados_software/     # Alignment results from sequence-based baseline tools
│       ├── clustalw/
│       ├── kalign/
│       ├── mafft/
│       ├── tcoffee/
│       └── tm-aligner/
├── 📁 Tests/                      # Outputs from structural-alignment experiments
│   ├── 📁 mustang/
│   ├── 📁 caretta/
│   │   ├── caretta_execution_summary.tsv
│   │   ├── caretta_global.log
│   │   └── logs/
│   ├── 📁 mtmalign/
│   ├── 📁 foldmason/
│   └── 📁 usalign/
└── 📁 scripts/                     # Utility scripts for data processing and workflow execution
    ├── 📄 download.py
    ├── 📄 downloadsequences.py
    ├── 📄 downloadmsareferences_19.py
    ├── 📄 generar.py
    ├── 📄 generar_19version.py
    ├── 📄 organizar.py
    ├── 📄 groupfiles.py
    ├── 📄 groupsfiles2.py
    ├── 📄 mustang_run.sh
    ├── 📄 run_caretta.sh
    ├── 📄 ejecutar_mtmalign_parallel.sh
    ├── 📄 run_foldmason.sh
    ├── 📄 run_usalign.sh
    ├── 📄 gpcr_list.csv
    └── 📄 adhesion_gpcr_human_33.csv
```

---

## Data Components and Usage

### Sequences (`sequences/`)
- **FASTA files:** High-quality protein sequences in FASTA format
- **Dataset Summary:** CSV file with metadata for all sequences
- **GFF3 annotations:** Gene feature format annotations
- **Transmembrane regions:** Pre-identified and annotated TM regions for each protein

### Structural Data
- **AlphaFold Protein Structure Database records:**
  - **PDB format** (`alphafold_pdb/`): Predicted coordinate models used for structural analysis
  - **JSON format** (`alphafold_json/`): Predicted Aligned Error (PAE) records associated with the retrieved models

### Derived Data
- **Distance Matrices** (`distances/`): Pairwise Cα distance matrices computed from the predicted structures
- **Weights** (`weights/`): Auxiliary PAE-derived confidence-weight matrices retained for reproducible confidence-aware analyses and alternative scoring workflows. These matrices are not consumed by the current TM-M2StructAlign structural objective.

### Reference Alignments (`reference_alignments/`)
The repository contains **GPCRdb-derived reference multiple alignments** named with the same dataset identifiers used by the sequence and structure folders. Reduced reference alignments were generated for the explicit 19-protein subsets and are stored in FASTA and MSF-compatible representations for reproducible scoring and benchmarking.

---

## Software Evaluation Results

The repository now contains both baseline sequence-based alignments and a dedicated set of structural-alignment experiments. The main resources are organized as follows:

| Tool | Category | Repository location | Notes |
|---|---|---|---|
| **ClustalW / Kalign / MAFFT / T-Coffee** | Sequence-based baselines | GPCRdb/resultados_software/ | Standard MSA outputs organized by GPCR class |
| **mTM-align** | Structure-based | Tests/mtmalign/ | Per-dataset execution folders and parallel log files |
| **Mustang** | Structure-based | Tests/mustang/ | Class-based result folders for structural alignment experiments |
| **Caretta** | Structure-based | Tests/caretta/ | Includes execution summary, global logs, and per-dataset outputs |
| **FoldMason** | Structure-based | Tests/foldmason/ | Dataset-level result directories generated by the workflow script |
| **US-align** | Structure-based | Tests/usalign/ | Batch outputs produced from the US-align workflow |

**Results organization:**
- Each tool has its own result directory under Tests/
- The outputs are organized by GPCR class, including both full and reduced (_19) datasets where applicable
- A consolidated summary of precomputed results is available in GPCRdb/precomputed/resultados_precomputed.txt

### Structural-alignment workflow scripts
- scripts/mustang_run.sh
- scripts/run_caretta.sh
- scripts/ejecutar_mtmalign_parallel.sh
- scripts/run_foldmason.sh
- scripts/run_usalign.sh

These scripts automate the execution of the structure-based workflows and prepare the result folders used for downstream analysis.

---

## Key Features

✅ **Comprehensive Dataset:** 284 human GPCR sequences across 9 major classes  
✅ **Dual Versions:** Full dataset and reduced 19-protein version for flexibility  
✅ **Multi-format Structure Data:** PDB and JSON formats for diverse use cases  
✅ **Reference Alignments:** GPCRdb-derived reference alignments for reproducible evaluation  
✅ **Reproducible Results:** Outputs from both sequence-based and structural-alignment tools  
✅ **Structural Alignment Benchmarks:** Dedicated experiment folders for Mustang, Caretta, mTM-align, FoldMason, and US-align  
✅ **Precomputed Results:** Consolidated outputs stored under GPCRdb/precomputed/ for rapid reuse  
✅ **Transmembrane-aware:** Emphasis on TM region alignment accuracy  
✅ **Utility Scripts:** Python and shell scripts for dataset generation, organization, and workflow execution  

---

## Usage Example

To evaluate a new MSA method on this dataset:

1. Use FASTA sequences from `sequences/fasta/`
2. Optionally incorporate structural information from `alphafold_pdb/` or `alphafold_json/`
3. Compare results against `reference_alignments/`
4. Benchmark against outputs in `resultados_software/`
5. Use `distances/` for distance-based structure-aware scoring; `weights/` contains auxiliary PAE-derived matrices for alternative confidence-aware analyses

For structure-based methods, extract PDB files from the corresponding class directory.

---

## Citation

If you use this dataset or the associated software, please cite the relevant methodological publications and data resource.

**Dataset (recommended citation for version 1.0.0)**

Zambrano-Vega, C., Cedeño-Muñoz, J., & Nebro, A. J. (2026). *A Curated Dataset of Human GPCR Sequences, AlphaFold-Predicted Structures, Transmembrane Topologies, and Reference Alignments for Structural Bioinformatics* (Version 1.0.0) [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.23243974

**Published predecessor**

Cedeño-Muñoz, J., Zambrano-Vega, C., and Nebro, A. J. (2025). *TMP-M2Align: A Topology-Aware Multiobjective Approach to the Multiple Sequence Alignment of Transmembrane Proteins*. **Algorithms, 18**(10), 640. https://doi.org/10.3390/a18100640

**Current structure-guided method**

Cedeño-Muñoz, J., Zambrano-Vega, C., and Nebro, A. J. *TM-M2StructAlign: A Multiobjective Tool for Structure-Guided Multiple Sequence Alignment of G Protein-Coupled Receptors Using AlphaFold2-Derived Constraints*. Manuscript prepared for **Computational Biology and Chemistry**. Manuscript source: [TM-M2StructAlign-Paper](https://github.com/JOELITO07/TM-M2StructAlign-Paper).

**Companion data article**

*A Curated Dataset of Human GPCR Sequences, AlphaFold-Predicted Structures, Transmembrane Topologies, and Reference Alignments for Structural Bioinformatics*. Data-article manuscript source: [TM-M2StructAlign_Dataset_paper](https://github.com/JOELITO07/TM-M2StructAlign_Dataset_paper). Archived dataset: [Zenodo v1.0.0](https://doi.org/10.5281/zenodo.23243974).

---

## License and Terms of Use

The **compiled and derived dataset** is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license, as indicated in the Zenodo record.

Upstream sequence, annotation, and structure resources retain their respective licenses, terms of use, and attribution requirements. Users reusing GPCRdb, UniProt-linked, or AlphaFold Protein Structure Database records should also comply with the conditions of the corresponding upstream resource.

---

## Changelog

### v1.0.0 (Zenodo archival release)
- Archived the dataset in Zenodo: https://doi.org/10.5281/zenodo.23243974
- 284 human GPCR sequences across nine classes/subclasses
- Seven deterministic 19-protein subsets (133 sequence instances)
- AlphaFold Protein Structure Database coordinate models and PAE records
- Cα distance matrices, residue-index maps, and auxiliary PAE-derived confidence-weight matrices
- GPCRdb-derived reference alignments
- Precomputed outputs and execution artifacts for sequence- and structure-based aligners
- Workflow and utility scripts for reproducible data preparation and structural-alignment experiments
- Exact archived source snapshot: commit `75287f1da907248aa29b8fb5adf17a4c63891797`
