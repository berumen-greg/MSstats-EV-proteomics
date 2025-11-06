# MSstats-EV-Proteomics-Script

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![R](https://img.shields.io/badge/R-4.3%2B-blue)](#requirements)
[![DOI](https://img.shields.io/badge/DOI-zenodo_pending-lightgrey)](#citation)

This repository provides a minimal, reproducible R script for running **MSstats** on EV proteomics data used in Berumen et al. manuscript.

- **`src/run_msstats_analysis.R`** — reads input evidence/annotation files, runs MSstats processing and model fitting, and writes summarized results to `tables/` with optional figure outputs in `figures/`.

> Raw data: PRIDE **PXD063788**. Place your local copies under `data/` (ignored) or edit paths in the config.

## Requirements
- **R 4.3+** (tested)
- **renv** for a pinned environment (recommended)
- **MSstats** via Bioconductor

## Quick start
Clone or download this repo, then in R:
```r
# 1) Activate reproducible environment
install.packages("renv")
renv::activate()     # uses renv/activate.R from this repo
renv::restore()      # installs exact package versions from renv.lock

# 2) Run the analysis
source("src/run_msstats_analysis.R")
# Or from CLI:
# Rscript src/run_msstats_analysis.R --config config/analysis-config.yml
