# Pakistan Environmental Monitoring — Web GIS

Open `index.html` in a browser (Leaflet is bundled in `lib/`; only map tiles need internet).

## Data
`data/` contains `pakistan_boundary`, `cities`, `weatherstation`, `rainfall`, `environment` (.geojson).
**The values in cities/weatherstation/rainfall/environment are SAMPLE data** (a badge on the page says so).
To use your real data, just replace those .geojson files. No code changes are needed:
`script.js` auto-detects field names (AQI/aqi/air_quality_index, Humidity/relative_humidity,
Category/air_quality_category, Temperature/temp, Rainfall/precipitation, Station Name/name ...).
The list of accepted names is `FIELD_ALIASES` at the top of `script.js`.
Missing / null / NaN / empty values are hidden from popups. Stations are merged across files by name.

## Important when editing data
Double-clicking `index.html` (file://) uses `data/embedded-data.js` because browsers block fetch() there.
After editing a .geojson run `python tools/make_embedded.py`, or use a local server:
`python -m http.server 8000` then open http://localhost:8000
(the sample badge disappears once the files no longer contain `"sample": true`).
