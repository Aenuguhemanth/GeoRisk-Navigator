GeoRisk-Navigator 🧭

A U.S. multi-hazard geospatial intelligence atlas for business resilience

Understand where you’re exposed and why. GeoRisk-Navigator fuses natural-hazard histories with man-made risk signals (e.g., cyber incidents) and industry context (NAICS) to produce location-aware insights at state/county granularity. 🗺️


Overview

GeoRisk-Navigator is an interactive, data-driven atlas that helps U.S. organizations analyze multi-peril risk across hurricanes, floods, wildfires, and more—alongside cyber and operational risk signals. Business-centric views by NAICS reveal how exposure differs across industries.

Core Value

One map, many perils: natural hazards + cyber/operational signals in one view 🌪️💻

Business-aware insights: NAICS-based comparisons with county drill-downs 🏭

Transparent lineage: reproducible pipeline (Jupyter notebooks → app) 🔁

Key Features

Interactive U.S. map: national → state → county exploration 🗺️

Industry-aware scoring: slice by NAICS to compare exposure across business types 📊

Natural + man-made signals: FEMA, NOAA, VERIS VCDB, CVE/MITRE 🌧️🔥💻

Explainability: hover/expand panels show driver metrics behind each score 🔎

Scenario filters: toggle hazard families (e.g., hurricanes vs. wildfires vs. cyber) 🎛️

Reproducible pipeline: notebooks for integration, EDA, features, and prediction 🔬

Prerequisites

Python 3.9+ 🐍

OS: macOS, Linux, or Windows 💻

Installation 🛠️
# 1) Clone the repo
git clone https://github.com/Aenuguhemanth/GeoRisk-Navigator.git
cd GeoRisk-Navigator

# 2) (Recommended) Create & activate a virtual environment
python -m venv .venv

# macOS/Linux
source .venv/bin/activate

# Windows (PowerShell)
.\.venv\Scripts\Activate.ps1

# 3) Install dependencies
pip install -r requirements.txt

Run the App ▶️
# Streamlit entry point (recommended)
streamlit run Home.py

# Single-file variant (quick local run)
streamlit run GeoRisk-Navigator_Webapplication.py

How It Works
Data Pipeline (Notebooks) 🔬

A reproducible path from raw sources to model-ready features:

Data Integration.ipynb — Load & align external datasets; harmonize FIPS (state/county) and NAICS.

Data merging.ipynb — Join hazard, vulnerability, and exposure tables; resolve nulls and key mismatches.

EDA_part 2.ipynb — Explore distributions, correlations, and temporal/seasonal patterns.

Feature_Engineering.ipynb — Build signals (rolling frequencies, intensity indices, per-capita normalizations).

NOAA.ipynb — Prepare NOAA-based climate/weather features (storms, precipitation anomalies, etc.).

GeoRisk-Navigator_prediction.ipynb — Prototype models, compute risk indices, export artifacts.

Produced artifacts (used by the app):

changed_data.csv — Prepared/model outputs for map rendering

state_county_final_dict.json — Metadata for state/county selectors

Application Layer 🧩

Home.py — Streamlit entry point (hazard filters, geography, NAICS)

insights.py — Shared UI components/visuals and helpers

GeoRisk-Navigator_Webapplication.py — Single-file app variant for quick runs

GeoRisk-Navigator_prediction.html — Prebuilt/shareable HTML visualization (e.g., Folium/Plotly export)

Data Sources 🔗

NAICS — North American Industry Classification System (U.S. Census): https://www.census.gov/naics/

FEMA — Disaster Declarations Summaries: https://www.fema.gov/openfema-data-page/disaster-declarations-summaries-v2

NOAA — Climate & severe-weather indicators: https://www.noaa.gov/

VERIS VCDB — Public security-incident database: https://verisframework.org/vcdb.html

CVE/MITRE — Publicly disclosed vulnerabilities: https://cve.mitre.org/

Geographies: Use FIPS codes for state/county joins. Ensure CRS alignment when incorporating shapefiles/GeoJSON.

Configuration ⚙️

Hazard toggles — Set default families & weights (sidebar or config block)

Scoring — Start with transparent, additive indices; tune per use-case and validate on hold-out periods

Caching — Enable Streamlit caching (or equivalent) for snappier UX

Project Structure 📁
GeoRisk-Navigator/
├─ Home.py                          # Streamlit entry point
├─ GeoRisk-Navigator_Webapplication.py  # Single-file app variant
├─ insights.py                      # UI components & helpers
├─ pages/                           # Additional Streamlit pages
├─ *.ipynb                          # Notebooks for data & modeling
├─ changed_data.csv                 # Prepared dataset for the app
├─ state_county_final_dict.json     # Geo selector metadata
├─ requirements.txt                 # Python dependencies
└─ README.md                        # This file

Usage 🚀

Launch the app and select State → County.

Choose NAICS industry (single or multiple).

Toggle hazard families (hurricanes, floods, wildfires, cyber) and adjust weights.

Inspect the map and driver panel to see which metrics push scores up/down.

Export CSV/PNG for reports (add a download widget if desired).


Contributions are welcome
