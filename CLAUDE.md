# MelbournePedestrianCountingSystem

Python data pipeline that collects and transforms pedestrian count data from the City of Melbourne's Pedestrian Counting System (January 2010 – October 2024; the end month is `END_YEAR`/`END_MONTH` in the download cell).

## What it does

1. Dynamically constructs URLs for monthly CSV files from the Melbourne Pedestrian Counting System
2. Downloads and cleans each file (coerces numeric columns, parses dates)
3. Aggregates all months into a single long-format DataFrame (one row per sensor per day)
4. Joins geolocation data (lat/lng) for each sensor. Coordinates are hand-geocoded and matched **by position** to the sensor columns of the last file downloaded; the notebook stops if the counts differ. Extending the date range almost certainly changes the sensor set, so update the coordinate lists (in order) at the same time.
5. Outputs a clean dataset ready for visualisation

The resulting dataset powers an interactive Power BI dashboard: https://cooperdenny.github.io/projects/melbourne-pedestrian-counting/

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

Files are downloaded from the legacy `https://www.pedestrian.melbourne.vic.gov.au/datadownload/` host (`{year}.csv` for 2010–2012, `{Month}_{year}.csv` from 2013). Failed downloads are listed after the loop. That host returned CloudFront 403s to a non-Australian cloud machine in Nov 2026; check it still serves files before relying on it.

City of Melbourne Open Data: https://data.melbourne.vic.gov.au/explore/dataset/pedestrian-counting-system-monthly--counts-per-hour/ holds only a rolling ~2 years of hourly counts, so it can't replace the legacy files for the 2010+ history. Its `pedestrian-counting-system-sensor-locations` dataset has official coordinates for each sensor (`sensor_description`, `latitude`, `longitude`), a better source than the hand-geocoded list if the sensor table is ever rebuilt.
