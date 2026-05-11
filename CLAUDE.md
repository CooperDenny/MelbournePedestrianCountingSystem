# MelbournePedestrianCountingSystem

Python data pipeline that collects and transforms pedestrian count data from the City of Melbourne's Pedestrian Counting System (January 2010 – present).

## What it does

1. Dynamically constructs URLs for monthly CSV files from the Melbourne Pedestrian Counting System
2. Downloads and cleans each file (coerces numeric columns, parses dates)
3. Aggregates all months into a single long-format DataFrame (one row per sensor per day)
4. Joins geolocation data (lat/lng) for each sensor
5. Outputs a clean dataset ready for visualisation

The resulting dataset powers an interactive Power BI dashboard: https://cooperdenny.github.io/projects/melbourne-pedestrian-counting.html

## Files

- `Melbourne-Pedestrian-Data-Collection.ipynb` — Main Jupyter notebook (run top to bottom)
- `requirements.txt` — Python dependencies

## Setup

```bash
pip install -r requirements.txt
jupyter notebook Melbourne-Pedestrian-Data-Collection.ipynb
```

## Dependencies

- `pandas>=2.1.0`
- `numpy>=1.26.0`
- `requests>=2.31.0`

Python 3.11+ recommended.

## Data source

City of Melbourne Open Data: https://data.melbourne.vic.gov.au/explore/dataset/pedestrian-counting-system-monthly--counts-per-hour/
