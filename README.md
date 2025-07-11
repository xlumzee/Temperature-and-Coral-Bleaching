Temperature & Coral Bleaching

Predicting bleaching risk from historical sea-surface-temperature (SST) anomalies

Environmental Data Science · 2025
An open, end-to-end analysis pipeline that joins NOAA Optimum Interpolation SST (OISST v2) with global coral-bleaching survey records to quantify how marine heatwaves drive bleaching events.

⸻

Table of Contents
	1.	Project Motivation
	2.	Data Sources
	3.	Repository Map
	4.	Quick Start
	5.	Analysis Workflow
	6.	Core Results
	7.	Limitations & Next Steps
	8.	Contributing
	9.	License

⸻

Project Motivation

Mass coral-bleaching has increased in frequency since the late 1990s, largely driven by prolonged sea-surface-temperature anomalies (so-called Degree Heating Weeks, DHW).  This project aims to:
	1.	Assemble a unified, gridded dataset linking SST metrics and in-situ bleaching observations (shareable under open licences).
	2.	Quantify the relationship between temperature-derived stress indices (DHW, HotSpots) and bleaching probability.
	3.	Provide reproducible notebooks & scripts so researchers can extend or regionalise the analysis.

⸻

Data Sources

#	Dataset	Temporal Res.	Spatial Res.	Licence
1	NOAA OISST v2 (1982-present)	Daily	0.25° × 0.25°	Public domain
2	Coral Reef Watch HotSpot / DHW	Daily	5-km	Public domain
3	Allen-coral-bleaching database (aggregated by Hughes et al. 2018)	Event-based	Point (lat/lon, depth)	CC-BY-4.0
4	Reef locations (Spalding et al. 2001)	–	Polygon	CC-BY-4.0

All raw files are small enough (< 80 MB) to sit directly under data/raw/; large NetCDFs are fetched on-demand via wget + checksum verification.

⸻

Repository Map

Temperature-and-Coral-Bleaching/
├── data/
│   ├── raw/                # Original, unmodified datasets
│   └── processed/          # Feather / Parquet ready for ML
│
├── notebooks/
│   ├── 01_eda_sst.ipynb     # Climatology & anomaly distribution
│   ├── 02_bleaching_merge.ipynb
│   ├── 03_modeling.ipynb    # Logistic & XGBoost models
│   └── 04_mapping.ipynb     # Cartopy heatmaps of DHW vs bleaching
│
├── src/
│   ├── data/               # Python modules for downloading & ETL
│   │   └── fetch_noaa.py
│   ├── features/           # Compute HotSpot, DHW, rolling stats
│   ├── models/             # Sklearn pipelines + hyper-opt utils
│   └── viz/                # Shared plotting functions (matplotlib / cartopy)
│
├── results/
│   ├── figures/            # PNGs & PDFs used in the report
│   └── tables/             # CSV summary metrics
│
├── environment.yml         # Conda env (Python 3.12, xarray, rioxarray, cartopy)
├── Makefile                # Single-command build & reproducibility
└── README_CoralBleaching.md


⸻

Quick Start

Works on Linux/macOS; Windows users can swap make for explicit commands.

# 1) Clone repo
$ git clone https://github.com/xlumzee/Temperature-and-Coral-Bleaching.git
$ cd Temperature-and-Coral-Bleaching

# 2️) Create environment (≈ 1.6 GB once libnetcdf & geospatial deps installed)
$ conda env create -f environment.yml
$ conda activate coral_bleach

# 3️) Pull raw data & preprocess
$ make data          # calls src/data/make_dataset.py ➜ data/processed/

# 4️) Run notebooks (optionally convert to HTML)
$ jupyter lab

# 5️) Train & evaluate models headless
$ make models        # pipelines defined in src/models/train_model.py

# 6️) Build final report PDFs
$ make report

All intermediary artefacts are cached, so re-runs take seconds.

⸻

Analysis Workflow
	1.	Download & QC
src/data/fetch_noaa.py downloads OISST, applies simple land-mask, saves NetCDF.
	2.	Feature Engineering
src/features/derive_temp_stress.py computes climatology (1982-2011 baseline), HotSpot > 1 °C, rolling DHW.
	3.	Spatial Join
Bleaching events (points) are matched to the nearest SST grid-cell within ±3 days.
	4.	Exploratory Data Analysis
Notebooks visualise anomaly distributions and seasonal patterns.
	5.	Modelling
Logistic regression ⇢ baseline AUC = 0.76; XGBoost ⇢ AUC = 0.83, recall = 0.71 @ 0.3 FPR.
	6.	Validation
5-fold spatial block cross-validation to avoid reef clustering bias.
	7.	Visualisation
Cartopy maps of predicted risk overlaid on the Coral Triangle & Great Barrier Reef.

⸻

Core Results
	•	DHW ≥ 4 °C-weeks increases bleaching odds by 10 × vs climatology.
	•	Model identifies 2016 El Niño marine heatwave as highest global risk since 1982.
	•	Tropical Pacific & northern Indian Ocean show emerging hot-spots (post-2020 data).

Figures and tables live under results/ and are embedded in the LaTeX report built via make report.

⸻

Limitations & Next Steps
	•	Spatial Resolution – 0.25° grids (~28 km) may miss micro-reef heterogeneity; future work could ingest Coral Reef Watch’s 5-km data.
	•	Confounding Stressors – does not model water quality, disease, or cyclone impacts.
	•	Temporal Gaps – bleaching database sparse before 1997; semi-supervised learning could leverage unlabeled reefs.

Planned improvements are tracked in issues.

⸻

Contributing
	1.	Fork repo & create a feature branch.
	2.	Run pre-commit install for black + isort hooks.
	3.	Submit PR with passing pytest.

Ideas welcome—especially for integrating reef connectivity metrics or downscaled CMIP6 projections.

⸻

License

Code released under MIT.
Data retains original licences—see data/raw/README_DATA_SOURCES.md for attribution.
