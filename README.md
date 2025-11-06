# MSstats EV Proteomics Script

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![R](https://img.shields.io/badge/R-4.3%2B-blue)](#requirements)
[![DOI](https://img.shields.io/badge/DOI-zenodo_pending-lightgrey)](#citation)

This repository contains a minimal, reproducible R script to run **MSstats** on extracellular vesicle (EV) proteomics data used in our manuscript (Berumen et al., 2025, *Proteomics*).

- **`src/msstats_v4.8.7_mq_6349.R`** — reads input files, runs MSstats preprocessing and model fitting, and writes tables to `tables/` with optional figures in `figures/`.

> Raw data are available at ProteomeXchange/PRIDE: **PXD063788**. Place your local copies under `data/` (ignored) and update the paths in the script or a config file.

---

## Repository structure
```
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
```

## Requirements
- R 4.3+ (tested)
- MSstats (Bioconductor)
- Recommended: `renv` for a pinned environment

## Quick start

**1) (Recommended) Use the pinned environment if `renv` files are present**
```r
install.packages("renv")
renv::activate()     # uses renv/activate.R from this repo
renv::restore()      # installs packages recorded in renv.lock
```

**2) Run the analysis**
```r
source("src/msstats_v4.8.7_mq_6349.R")
```
or from terminal:
```bash
Rscript src/msstats_v4.8.7_mq_6349.R --config config/analysis-config.yml
```

## Inputs & configuration
Expected inputs (adjust as needed):
- `data/evidence_or_peptides.csv`
- `data/annotation.csv` (columns like `Condition`, `BioReplicate`, `Run`)

You can keep parameters in a YAML config (e.g., `config/analysis-config.yml`) and pass `--config` on the command line.

## Outputs
- `tables/`: protein-level summaries, model results, contrasts/q-values  
- `figures/`: optional QC plots (if enabled in the script)  
- `results/`: any additional exports you choose to write

## Reproducibility (renv)
To capture the exact package versions:
```r
install.packages("renv")
renv::init()
install.packages("BiocManager")
BiocManager::install("MSstats")
renv::snapshot()
```

## Citation
Please cite:
1. **MSstats:** Choi *et al.* *Bioinformatics* (2014) 30:2524–2536.  
2. **This repository:** 10.5281/zenodo.17546119

Once the concept DOI is minted, add this badge near the top:
```markdown
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.CONCEPT.svg)](https://doi.org/10.5281/zenodo.CONCEPT)
```

## License
Code is released under the **MIT License** (see [`LICENSE`](LICENSE)).  
SPDX header you may add to R files:
```r
# SPDX-License-Identifier: MIT
```

## Contact / issues
Open a GitHub Issue or email gregory.i.berumen@vanderbilt.edu.
