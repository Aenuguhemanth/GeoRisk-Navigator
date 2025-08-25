# GeoRisk-Navigator
A U.S. multi‑hazard geospatial intelligence atlas for business resilience

Overview

GeoRisk‑Navigator is an interactive, data‑driven atlas that helps U.S. organizations understand where they’re exposed and why. It fuses natural‑hazard histories with indicators of man‑made risk (e.g., cyber incidents) and industry context (NAICS) to produce location‑aware insights at state/county granularity.

Core value

One map, many perils: hurricanes, floods, wildfires, and more, alongside cyber and operational risk signals.

Business‑centric views by NAICS industry, with drill‑downs for counties.

Transparent data lineage and a reproducible pipeline (Jupyter notebooks → app).

Key Features

Interactive U.S. Map — Explore multi‑peril risk patterns at national, state, and county levels.

Industry‑Aware Scoring — Slice risk by NAICS to compare exposure across business types.

Natural + Man‑Made Signals — Blend FEMA disaster history, NOAA climate indicators, and public cyber incident/vulnerability datasets.

Explainability — Hover/expand panels show the driver metrics behind each risk score.

Scenario Filters — Toggle hazard families (e.g., hurricanes vs. wildfires vs. cyber) to see how patterns shift.

Reproducible Pipeline — Notebooks for data integration, EDA, feature engineering, and prediction feed the app.

Prerequisites

Python ≥ 3.9

OS: macOS, Linux, or Windows

Installation
# clone the repo
git clone https://github.com/Aenuguhemanth/GeoRisk-Navigator.git
cd GeoRisk-Navigator


# (recommended) create a virtual environment
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate


# install dependencies
pip install -r requirements.txt
Run the app


How It Works
Data pipeline (notebooks)

The notebooks in the repo document a reproducible path from raw sources to model‑ready features:

Data Integration.ipynb — Load and align external datasets, harmonize geographic keys (state, county FIPS), and NAICS codes.

Data merging.ipynb — Join hazard, vulnerability, and exposure tables; resolve nulls and mismatched keys.

EDA_part 2.ipynb — Explore distributions, correlations, and temporal/seasonal patterns.

Feature_Engineering.ipynb — Build signals (rolling frequencies, intensity indices, per‑capita normalizations).

NOAA.ipynb — Prepare NOAA‑based climate/weather features (storms, precipitation anomalies, etc.).

GeoRisk-Navigator_prediction.ipynb — Prototype models, compute risk indices, and export artifacts.

Outputs such as changed_data.csv and state_county_final_dict.json support the front‑end map and selectors.

Application layer

Home.py — Streamlit entry point with high‑level controls (hazard filters, geography, NAICS).

insights.py — Shared components/visuals and helper functions for the UI.

GeoRisk-Navigator_Webapplication.py — Single‑file app variant; useful for quick local runs.

GeoRisk-Navigator_prediction.html — A prebuilt, shareable HTML visualization artifact (e.g., Folium/Plotly export).

Data Sources

NAICS — North American Industry Classification System (U.S. Census).
https://www.census.gov/naics/

FEMA — OpenFEMA Disaster Declarations Summaries (multi‑hazard history).
https://www.fema.gov/openfema-data-page/disaster-declarations-summaries-v2

NOAA — Climate and severe‑weather indicators used in feature engineering.
https://www.noaa.gov/

VERIS VCDB — Public community database of security incidents (cyber/operational).
https://verisframework.org/vcdb.html

CVE/MITRE — Catalog of publicly disclosed vulnerabilities (contextual risk).
https://cve.mitre.org/

Geographies: Use FIPS codes for state/county joins. Ensure CRS alignment when adding shapefiles/GeoJSON.

Configuration

Hazard toggles: Configure default hazard families and weights in the app sidebar or a config block.

Scoring: Start with transparent, additive indices; tune weights by use‑case and validate against hold‑out periods.

Caching: Enable Streamlit caching (or equivalent) for faster interactions.

Project Structure
RiskTitans/
├─ Home.py                      # Streamlit entry point
├─ GeoRisk-Navigator_Webapplication.py # Single-file app variant
├─ insights.py                  # UI components & helpers
├─ pages/                       # Additional Streamlit pages
├─ *.ipynb                      # Notebooks for data & modeling
├─ changed_data.csv             # Prepared dataset for the app
├─ state_county_final_dict.json # Geo selector metadata
├─ requirements.txt             # Python dependencies
└─ README.md                    # This file (rebranded)
Usage

Launch the app and select State → County.

Choose your NAICS industry (or a set of industries).

Toggle hazard families (e.g., hurricanes, floods, wildfires, cyber) and adjust weights.

Inspect the map and driver panel to see what pushes a location’s score up or down.

Export a CSV or PNG for reports (optional: add a download widget).

Contributions are welcome! Please:
