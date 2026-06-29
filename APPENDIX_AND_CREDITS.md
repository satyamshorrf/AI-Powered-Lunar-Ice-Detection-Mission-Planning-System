# Appendix, Credits & Additional Content

---

# SLIDE A8: MOBILE COMMAND CONSOLE

## Pragyan-II Tactical Command Console

### Telemetry Display
┌─────────────────────────────────────────────────────────────┐
│ PRAGYAN-II TACTICAL COMMAND CONSOLE │
├─────────────────────────────────────────────────────────────┤
│ POWER & STORAGE GAUGES │
│ ████████████████████████████████████████████ 98% BATTERY │
│ ██████████████████████████████████████████████ 94% SOLAR │
│ │
│ CRYOGENIC THERMAL BAY │
│ ██████████████████████████████████████ -134.7 °C │
│ PSR SHADOW EQUILIBRIUM │
│ ████████████████████████████████████████████ STABLE │
│ │
│ ISRU INTELLIGENCE READOUT │
│ TOTAL TELEMETRY SOUNDINGS: 5,000 │
│ HIGH PROBABILITY ICE ZONES: 526 craters │
│ SAFE LANDING SITES: 1,501 zones │
│ │
│ LIVE HARDWARE DATASTREAM │
│ [19:10:33] THERMAL: PSR Shadow approach, temp dropping │
│ [19:10:34] THERMAL: PSR Shadow approach, temp dropping │
│ [19:10:36] POWER: Solar array adjusted +0.4° Azimuth │
│ │
└─────────────────────────────────────────────────────────────┘


---

# SLIDE A9: APPLICATION SCREENSHOTS

## Key Interface Views

### 1. Dashboard View
- Live mission metrics
- Telemetry points (5,000)
- Ice craters detected (526)
- Safe touchdown zones (1,501)
- AI Confidence (87.4%)

### 2. Interactive Map View
- NASA LROC Basemap
- Toggleable data layers
- Real-time cursor coordinates
- Subsurface ice deposit markers

### 3. Module Views
- Stage 1: Ice Detection with probability mapping
- Stage 2: Volume estimation charts
- Stage 3: Landing site distribution
- Stage 4: Route viewer with waypoints
- Stage 5: ROC curves and confusion matrix

### 4. Results View
- Consolidated metrics
- Performance visualizations
- Downloadable CSV reports
- Mission brief summary

---

# SLIDE A10: QGIS WORKFLOW

## GIS Processing Workflow

### Step 1: Data Import

QGIS Project Setup
├── Import DFSAR GeoTIFF
├── Import OHRC Orthoimage
├── Import DEM Elevation
└── Set CRS (WGS84 / EPSG:4326)

### Step 2: Terrain Analysis
Raster Processing
├── Slope Calculation (Raster > Terrain Analysis)
├── Hillshade Generation
├── Contour Extraction
└── 3D View Creation

### Step 3: PSR Mapping

Illumination Analysis
├── Sun Angle Calculation
├── Shadow Duration Mapping
├── PSR Classification
└── Doubly PSR Identification

### Step 4: Output Generation

Final Map Creation
├── Layer Styling
├── Scale Bar & Legend
├── Grid & Coordinate Labels
└── High-Resolution Export


---

# SLIDE 29: ACKNOWLEDGMENTS

## References & Credits

### Datasets
- **Chandrayaan-2 DFSAR Data** - ISRO
- **Chandrayaan-2 OHRC Imagery** - ISRO
- **NASA LROC Basemap** - NASA/GSFC
- **Lunar Reconnaissance Orbiter** - NASA

### Technologies Used
- React 19 with Tailwind CSS v4
- FastAPI & Python
- PyTorch & Transformers
- Leaflet.js for Interactive Maps
- QGIS for GIS Analysis

---

# SLIDE 30: THANK YOU

## Thank You!






