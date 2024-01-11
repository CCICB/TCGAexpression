
<!-- README.md is generated from README.Rmd. Please edit that file -->

# TCGAexpression

> :warning: **Warning:** This package is in early development and not
> yet ready for use

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/TCGAexpression)](https://CRAN.R-project.org/package=TCGAexpression)

<!-- badges: end -->

TCGAexpression provides easy access to TCGA expression datasets in R.
Optimised for easy visualisation and analysis
[selkamand/express](https://github.com/selkamand/express)

## Installation

You can install the development version of TCGAexpression like so:

``` r
# install.packages("remotes")
remotes::install_github('CCICB/TCGAexpression')
```

## Quick Start

### High Memory System (e.g. A HPC)

If you have sufficient memory to read very large dataframes into memory:

``` r
library(TCGAexpression)

# See available datasets
tcga_expression_available()

# Load available datasets into memory
tcga_expression_load(cohorts="GBM")

# Load just specific genes memory
tcga_expression_load(cohorts="GBM", c('TP53', 'PTEN'))
```

### Database Approach

For all devices but particularly low-memory devices, it will be faster
to download this database as an sqlite db (consider Parquet files with
arrow interface as this will be easier to store and download from
github) - Bioconductor experimenthub might allow storage of these as
indexed files as a github alternative

``` r

# Download 
tcga_expression_download(cohors = "GBM") #try cohorts = "Everything" to download the full SQLITE db

# Create a Connection 
tcga_expression_connect()
```

## Finding Expression Datasets

<table>
<colgroup>
<col style="width: 23%" />
<col style="width: 76%" />
</colgroup>
<thead>
<tr class="header">
<th>Source</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a
href="https://gdc.cancer.gov/about-data/publications/pancanatlas">TCGA
PanCanAtlas</a></td>
<td><p>Contains gene expression (and lots of other modalities) for 33
tumor types profiled by TCGA</p>
<p>File:
EBPlusPlusAdjustPANCAN_IlluminaHiSeq_RNASeqV2.geneExp.tsv</p></td>
</tr>
<tr class="even">
<td><a href="https://www.cbioportal.org/datasets">cBioPortal</a></td>
<td>Many datasets including TCGA cohorts</td>
</tr>
<tr class="odd">
<td><a
href="https://github.com/d3b-center/OpenPedCan-analysis">openPBTA</a></td>
<td><p>Open paediatric brain tumour atlas includes over 1,074 pediatric
brain tumors and 22 patient-derived cell lines. This data can be
downloaded from a public <a
href="https://cavatica.sbgenomics.com/u/cavatica/openpbta">cavatica</a>
project. Note genomic and histological</p>
<p>File: pbta-gene-expression-rsem-tpm.polya.rds</p>
<p>OR if you want the stranded data</p>
<p>File: pbta-gene-expression-rsem-tpm.stranded.rds</p>
<p>See data-files-description.md for details</p></td>
</tr>
<tr class="even">
<td><a
href="https://cavatica.sbgenomics.com/u/cavatica/opentarget">OpenPedCan</a></td>
<td><p>Children’s Hospital of Philadelphia is an open analysis effort
that harmonizes pediatric cancer data from multiple sources:</p>
<ul>
<li><p>TARGET</p></li>
<li><p>Kids First Neuroblastoma</p></li>
<li><p>OpenPBTA</p></li>
<li><p>GTEx RNA-Seq</p></li>
<li><p>TCGA RNA-Seq</p></li>
<li><p>CHOP DGD Targeted DNA and Fusion Panel Sequencing</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><a
href="https://treehousegenomics.soe.ucsc.edu/public-data/#datasets">UCSCtreehouse</a></td>
<td><p>Contains expression datasets describing both child and adult
patient cancer tumors.</p>
<p>See the Newest Tumor Compendium: v11 (polyA expression data)</p>
<p>File: gene expression RNAseq - RSEM log2(TPM + 1) normalized</p></td>
</tr>
</tbody>
</table>
