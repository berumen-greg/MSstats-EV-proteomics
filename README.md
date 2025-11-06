Project overview
This repository contains a minimal, reproducible R script to run MSstats on extracellular vesicle (EV) proteomics data used in our manuscript (Berumen et al., 2025, Proteomics).
- src/msstats_v4.8.7_mq_6349.R — reads input files, runs MSstats preprocessing and model fitting, and writes tables to tables/ with optional figures in figures/.
Raw data are available at ProteomeXchange/PRIDE: PXD063788. Place your local copies under data/ (ignored) and update the paths in the script or a config file.
Repository structure
msstats-ev-proteomics/
├─ src/
│  └─ msstats_v4.8.7_mq_6349.R
├─ config/                 # optional: YAML with paths/parameters
│  └─ analysis-config.yml
├─ figures/                # outputs (PNG/SVG/PDF)
│  └─ .gitkeep
├─ tables/                 # outputs (CSV/TSV)
│  └─ .gitkeep
├─ results/                # additional outputs
│  └─ .gitkeep
├─ data/                   # local data (ignored)
│  └─ .gitkeep
├─ renv.lock               # reproducible environment
├─ renv/activate.R
├─ README.md
├─ LICENSE
└─ .gitignore
Requirements
- R 4.3+ (tested)
- MSstats (Bioconductor)
- Recommended: renv for a pinned environment
Quick start
# 1) (Recommended) Use the pinned environment if renv files are present
install.packages("renv")
renv::activate()     # uses renv/activate.R from this repo
renv::restore()      # installs packages recorded in renv.lock

# 2) Run the analysis
source("src/msstats_v4.8.7_mq_6349.R")
# or from terminal:
# Rscript src/msstats_v4.8.7_mq_6349.R --config config/analysis-config.yml

Inputs & configuration
Expected inputs (adjust as needed):
- data/evidence_or_peptides.csv
- data/annotation.csv (columns like Condition, BioReplicate, Run)
You can keep parameters in a YAML config (e.g., config/analysis-config.yml) and pass --config on the command line.
Outputs
- tables/: protein-level summaries, model results, contrasts/q-values
- figures/: optional QC plots (if enabled in the script)
- results/: any additional exports you choose to write
Reproducibility (renv)
To capture exact package versions used in your analysis, initialize renv locally and commit renv.lock and renv/activate.R.
install.packages("renv")
renv::init()
install.packages("BiocManager")
BiocManager::install("MSstats")
renv::snapshot()
Citation
Please cite:
1) MSstats: Choi et al., Bioinformatics (2014) 30:2524–2536.
2) This repository: add Zenodo DOI after release.
Concept DOI badge (README) once minted:
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.CONCEPT.svg)](https://doi.org/10.5281/zenodo.CONCEPT)
License
Code is released under the MIT License (see LICENSE).
SPDX header you may add to R files:
# SPDX-License-Identifier: MIT
Contact / issues
Open a GitHub Issue or email gregory.i.berumen@vanderbilt.edu.
