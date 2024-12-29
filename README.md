# Assignment 2 - Gene Expression Analysis and Interpretation

## Author
Binhan XIAO (Student ID: 24207808)

## Overview
This project performs a gene expression analysis on breast cancer data, focusing on the HER2-amplified subtype. The analysis involves downloading data from cBioPortal, preprocessing it, and performing various computational analyses, including:

- Differential expression analysis
- Pathway enrichment
- Principal Component Analysis (PCA)
- Heatmap generation
- Survival analysis using LASSO-regularized Cox regression

The project is implemented in R and utilizes several Bioconductor and CRAN packages to process and analyze RNA-Seq and clinical data.



## Requirements
- R (version >= 4.0.0)
- RStudio (recommended)

### Required R Libraries
Ensure the following R packages are installed:
- `DESeq2`
- `clusterProfiler`
- `org.Hs.eg.db`
- `glmnet`
- `pheatmap`
- `ggplot2`
- `survival`

You can install missing libraries using:
```R
install.packages(c("ggplot2", "pheatmap", "glmnet", "survival"))
BiocManager::install(c("DESeq2", "clusterProfiler", "org.Hs.eg.db"))
```

## Data
The dataset is sourced from [cBioPortal](https://www.cbioportal.org/study/summary?id=brca_tcga_pan_can_atlas_2018). Place the downloaded files in the `data/` directory.

Required files:
- `data_mrna_seq_v2_rsem.txt`
- `data_clinical_patient.txt`
- `data_cna.txt`

## Steps to Reproduce

### 1. Preprocess Data
- Match patient IDs across RNA-Seq, CNA, and clinical datasets.
- Generate metadata for ERBB2 amplification status.

### 2. Normalize Data
- Use the `DESeq2` package to normalize RNA-Seq data.

### 3. Perform Differential Expression Analysis
- Identify genes differentially expressed between HER2-amplified and non-amplified samples.
- Save results to `differential_expression_results.csv`.

### 4. Pathway Enrichment Analysis
- Map significant genes to ENTREZ IDs.
- Perform KEGG pathway enrichment analysis.
- Save results to `pathway_enrichment_results.csv`.

### 5. Generate Visualizations
- Create a PCA plot using variance-stabilized data.
- Generate a heatmap of the top 50 differentially expressed genes.

### 6. Survival Analysis
- Use LASSO-regularized Cox regression to identify genes associated with overall survival.
- Save selected genes to `lasso_selected_genes.csv`.

### 7. Save Workspace
- Save the complete R workspace to `analysis_workspace.RData`.

## Example Commands
Run the analysis by executing the main script in R:
```R
source("scripts/main_analysis.R")
```

## Outputs
The following outputs are generated:
1. **Differential Expression Results**: `differential_expression_results.csv`
2. **Pathway Enrichment Results**: `pathway_enrichment_results.csv`


## Notes
- Ensure all file paths are correctly set in the R scripts.
- Data preprocessing steps are critical for successful analysis.

## References
- Love, M. I., Huber, W., & Anders, S. (2014). Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. *Genome Biology*, 15(12), 550.
- Yu, G., Wang, L. G., Han, Y., & He, Q. Y. (2012). clusterProfiler: An R package for comparing biological themes among gene clusters. *OMICS: A Journal of Integrative Biology*, 16(5), 284-287.
- Tibshirani, R. (1997). The LASSO method for variable selection in the Cox model. *Statistics in Medicine*, 16(4), 385-395.
