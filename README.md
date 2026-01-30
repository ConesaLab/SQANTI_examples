# SQANTI_examples
Repository with the examples and data needed to run SQANTI3

This repository contains datasets and comprehensive examples for running [SQANTI3](https://github.com/ConesaLab/SQANTI3), a tool for the quality control and classification of long-read transcripts.

## Repository Structure

```
SQANTI_examples/
├── data/                           # Input data for examples
│   ├── UHR_chr22.gtf              # Input isoform annotations
│   ├── UHR_abundance.tsv          # Abundance data
│   ├── UHR_RQ_abundance.tsv       # RQ abundance data
│   ├── UHR_chr22_short_reads.fofn # Short reads file list
│   ├── reference/                 # Reference genome and annotations
│   │   ├── GRCh38.p13_chr22.fasta
│   │   ├── gencode.v38.basic_chr22.gtf
│   │   └── ...
│   ├── polyA_motifs/              # PolyA motif annotations
│   ├── ref_TSS_annotation/        # TSS reference annotations
│   └── short_reads/               # Short read data
│
└── example/                        # Example workflows and results
    ├── run_all_examples.sh        # Master script to run all examples
    ├── run_SQANTI3_QC.sh          # Quality control example
    ├── run_SQANTI3_MLfilter.sh    # Machine learning filter example
    ├── run_SQANTI3_rules_filter.sh # Rules-based filter example
    │
    ├── config_files/              # Configuration files for each workflow
    │   ├── qc_config.yaml         # QC configuration
    │   ├── qc_config_reference.yaml
    │   ├── filter_ml.yaml         # ML filter configuration
    │   ├── filter_rules.yaml      # Rules filter configuration
    │   ├── rescue_ml.yaml         # ML rescue configuration
    │   ├── rescue_rules.yaml      # Rules rescue configuration
    │   └── rescue_automatic.yaml  # Automatic rescue configuration
    │
    ├── QC_isoforms/               # QC results for isoforms
    ├── QC_reference/              # QC results using reference mode
    ├── filter_ml/                 # ML filtering results
    ├── filter_rules/              # Rules-based filtering results
    ├── rescue_ml/                 # ML rescue results
    ├── rescue_rules/              # Rules-based rescue results
    ├── rescue_automatic/          # Automatic rescue results
    ├── sqanti_reads_test/         # SQANTI-reads test results
    └── Figures_paper/             # Code to generate publication figures
        ├── main_figures_code.R
        └── ExtendedData_figures_code.R
```

## Examples Overview

The `example/` directory contains complete workflows demonstrating different SQANTI3 functionalities:

### 1. **Quality Control (QC)**
- **Script**: `run_SQANTI3_QC.sh`
- **Config**: `config_files/qc_config.yaml`, `config_files/qc_config_reference.yaml`
- **Output**: `QC_isoforms/`, `QC_reference/`
- **Description**: Performs quality control on long-read isoforms, generating classification files, corrected annotations, and comprehensive QC reports.

### 2. **Machine Learning Filtering**
- **Script**: `run_SQANTI3_MLfilter.sh`
- **Config**: `config_files/filter_ml.yaml`
- **Output**: `filter_ml/`
- **Description**: Uses random forest models to filter isoforms based on quality metrics. Generates classification results, confusion matrices, and filtered output files.

### 3. **Rules-Based Filtering**
- **Script**: `run_SQANTI3_rules_filter.sh`
- **Config**: `config_files/filter_rules.yaml`
- **Output**: `filter_rules/`
- **Description**: Applies user-defined rules to filter isoforms. Produces filtering reason reports and filtered annotations.

### 4. **Rescue Workflows**
- **Configs**: `rescue_ml.yaml`, `rescue_rules.yaml`, `rescue_automatic.yaml`
- **Output**: `rescue_ml/`, `rescue_rules/`, `rescue_automatic/`
- **Description**: Demonstrates how to rescue filtered isoforms using different strategies (ML-based, rules-based, or automatic).

### 5. **SQANTI-reads**
- **Output**: `sqanti_reads_test/`
- **Description**: Example workflow for SQANTI-reads, which performs read-level quality control.

### 6. **Publication Figures**
- **Directory**: `Figures_paper/`
- **Description**: R scripts to reproduce figures from the SQANTI3 publication.

## Running the Examples

To run all examples at once:
```bash
cd example/
./run_all_examples.sh
```

To run individual examples:
```bash
# Quality Control
./run_SQANTI3_QC.sh

# ML Filtering
./run_SQANTI3_MLfilter.sh

# Rules Filtering
./run_SQANTI3_rules_filter.sh
```

## Data Description

The `data/` directory contains:
- **Input isoforms**: UHR (Universal Human Reference) chr22 GTF files
- **Reference genome**: GRCh38 chromosome 22 FASTA and annotations
- **Abundance data**: Transcript expression levels
- **Short reads**: For junction validation
- **Annotation resources**: PolyA motifs and TSS (Transcription Start Site) references

## Requirements

- [SQANTI3](https://github.com/ConesaLab/SQANTI3) installed and configured
- Python 3.7+
- R 4.0+ (for filtering and rescue functions)
- Required R packages: randomForest, ggplot2, gridExtra, etc.

For detailed installation instructions and requirements, please refer to the [SQANTI3 GitHub repository](https://github.com/ConesaLab/SQANTI3).
