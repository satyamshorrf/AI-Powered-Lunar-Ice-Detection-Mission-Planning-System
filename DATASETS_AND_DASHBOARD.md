```
```
# SLIDE 13: DATASET STRUCTURE

## Input Dataset Schema

### Stage 1: Ice Detection

| Column | Type | Description |
|--------|------|-------------|
| Crater ID | String | Unique crater identifier |
| Name | String | Crater name |
| Latitude | Float | Latitude in degrees |
| Longitude | Float | Longitude in degrees |
| Raw Backscatter | Float | DFSAR backscatter (dB) |
| Thermal K | Float | Thermal emission (K) |
| Albedo | Float | Surface albedo |

### Stage 2: Ice Volume & PSRs

| Column | Type | Description |
|--------|------|-------------|
| Zone ID | String | Zone identifier |
| DEM Elevation | Float | Elevation (m) |
| Shadow Duration | Float | Hours in shadow |
| PSR Classification | String | Standard/Doubly PSR |
| Estimated Depth | Float | Ice depth (m) |
| Calculated Volume | Float | Volume (m³) |

### Stage 3: Safe Landing Site

| Column | Type | Description |
|--------|------|-------------|
| Target ID | String | Landing zone identifier |
| Slope deg | Float | Slope in degrees |
| Boulder Density | Float | Boulder density index |
| Touchdown Grade | String | Grade A+/A/B |
| Hazard Score | Float | AI hazard score |
| Safety Probability | Float | Safety % |

---

# SLIDE 14: OUTPUT DATASET STRUCTURE

## Output Dataset Schema

### Stage 1: Ice Detection Output

| Column | Type | Description |
|--------|------|-------------|
| Crater ID | String | Unique identifier |
| Detected Ice Flag | Boolean | Ice presence (YES/NO) |
| Ice Probability | Float | Probability (0-100%) |
| Confidence Class | String | High/Moderate-Low |
| Estimated Area | Float | Ice area (m²) |

### Stage 2: Ice Volume Output

| Column | Type | Description |
|--------|------|-------------|
| Zone ID | String | Zone identifier |
| PSR Classification | String | Standard/Doubly PSR |
| Estimated Depth | Float | Ice depth (m) |
| Calculated Volume | Float | Volume (m³) |
| Core Temp | Float | Core temperature (K) |

### Stage 3: Safe Landing Output

| Column | Type | Description |
|--------|------|-------------|
| Target ID | String | Landing zone identifier |
| Touchdown Grade | String | Grade A+/A/B |
| Hazard Score | Float | AI hazard score |
| Safety Probability | Float | Safety % |
| Earth Ls | String | Line of sight status |

---

# SLIDE 15: INTERACTIVE DASHBOARD

## Dashboard Features

### Key Metrics Display

┌─────────────────────────────────────────────────────────────┐
│ DASHBOARD OVERVIEW │
├─────────────────────────────────────────────────────────────┤
│ DSFAR POINTS │ OHRC SAMPLES │ DETECTED ICE │
│ 2,000 │ 2,000 │ 14.85% │
│ │ │ │
│ LANDING SAFETY │ MISSION CONFIDENCE │ │
│ 45.3% │ 96.8% │ │
└─────────────────────────────────────────────────────────────┘



### Interactive Viewer
- **Live Telemetry Overlay**
- **Real-time Map Layer Controls**
- **Toggleable Data Layers**
  - Original Moon Basemap
  - Ice Detection Layer
  - Landing Site Zones
  - Rover Path Trajectory

### Map Controls

### Interactive Viewer
- **Live Telemetry Overlay**
- **Real-time Map Layer Controls**
- **Toggleable Data Layers**
  - Original Moon Basemap
  - Ice Detection Layer
  - Landing Site Zones
  - Rover Path Trajectory

### Map Controls

Map Layer Controls
├── Original Moon Basemap (NASA LROC)
├── Stage 1: Ice Detection Layer
├── Stage 2: Ice Volume Zones
├── Stage 3: Safe Landing Sites
└── Stage 4: Rover Path


---

# SLIDE 26: VISUALIZATION EXAMPLES

## Map Layer Examples

### Interactive Lunar Viewer Features
┌─────────────────────────────────────────────────────────────┐
│ INTERACTIVE LUNAR VIEWER │
├─────────────────────────────────────────────────────────────┤
│ Layer Controls: │
│ ☑ Original Moon Basemap (NASA LROC) │
│ ☑ Stage 1: Ice Detection Layer │
│ ☑ Stage 2: PSR Zones │
│ ☑ Stage 3: Landing Sites │
│ ☑ Stage 4: Rover Path │
├─────────────────────────────────────────────────────────────┤
│ │
│ [Interactive Map Display] │
│ │
│ Cursor: LAT -88.5852° | LON 334.3389° | ALT -2048m │
│ │
│ Subsurface Ice Deposit │
│ Real Latitude: -88.9739° │
│ Real Longitude: 347.7012° │
│ Radar Probability: 77.2% │
│ Surface Temp: 55.4586 K │
├─────────────────────────────────────────────────────────────┤
│ TELEMETRY POINTS: 5,000 │
│ ICE CRATERS (>50%): 526 │
│ SAFE TOUCHDOWN: 1,501 │
│ AI CONFIDENCE: 87.4% │
└─────────────────────────────────────────────────────────────┘



---

# SLIDE A1: ICE DETECTION - INPUT DATASET

## Stage 1 - Complete Input Schema

| Column | Type | Example | Description |
|--------|------|---------|-------------|
| Crater ID | String | CR-SHK-01 | Unique identifier |
| Name | String | Shackleton Crater | Crater name |
| Latitude | Float | -89.9 | Latitude in degrees |
| Longitude | Float | 0 | Longitude in degrees |
| Raw Backscatter | Float | -12.4 | DFSAR backscatter (dB) |
| Thermal K | Float | 88.5 | Diviner thermal emission |
| Albedo | Float | 0.42 | Surface reflectance |

### Sample Data

R-SHK-01, Shackleton Crater, -89.9, 0, -12.4, 88.5, 0.42
CR-SPH-02, Shoemaker Crater, -88.1, 44.9, -14.1, 92.1, 0.39
CR-FST-03, Faustini Crater, -87.3, 84.5, -11.8, 95.4, 0.35



---

# SLIDE A2: ICE DETECTION - OUTPUT DATASET

## Stage 1 - Complete Output Schema

| Column | Type | Example | Description |
|--------|------|---------|-------------|
| Crater ID | String | CR-SHK-01 | Unique identifier |
| Detected Ice Flag | String | YES | Ice presence indicator |
| Ice Probability | Float | 98.9% | Ice likelihood |
| Confidence Class | String | High Cryogenic | Confidence level |
| Estimated Area | Float | 7931.8 | Ice area (m²) |

### Sample Data

CR-SHK-01, YES, 98.9%, High Cryogenic, 7931.8
CR-SPH-02, YES, 95.4%, High Cryogenic, 7714.8
CR-FST-03, YES, 89.2%, Moderate-High, 6420.1
CR-HMT-04, YES, 94.1%, High Cryogenic, 7105.4
CR-DGR-05, YES, 99.4%, Confirmed Matrix, 8540.0


---

# SLIDE A3: VOLUME ESTIMATION DETAILS

## Stage 2 - Volume Calculation Details

### PSR & Doubly PSR Classification Methodology

**Standard PSR:**
- 0% direct sunlight
- Temperature < 100K
- Shadow duration ≈ 8760 hours (1 lunar year)

**Doubly PSR:**
- Ultra-cold traps (< 40K)
- Nested shadow zones
- Longest volatile preservation

### Volume Calculation Examples

| Zone | Area (m²) | Depth (m) | Ice Fraction | Volume (m³) |
|------|-----------|-----------|--------------|-------------|
| D-PSR-ZONE-B | 9,060 | 31.5 | 0.7685 | 285,400.0 |
| D-PSR-ZONE-D | 9,467 | 36.0 | 0.7237 | 340,800.0 |
| PSR-ZONE-A | 7,844 | 24.8 | 0.7019 | 194,512.4 |

---

# SLIDE A4: LANDING SITE DETAILS

## Stage 3 - Complete Analysis

### Landing Zone Distribution

| Grade | Sites | Safety % | Description |
|-------|-------|----------|-------------|
| A+ | 4 | 99.8% | Optimal Flat |
| A | 1,497 | 95-99% | Safe Descent |
| B | 500 | 88-95% | Caution Advised |
| C | 500 | <88% | High Risk |

### Top Landing Sites

| Site | Latitude | Longitude | Slope | Hazard | Safety |
|------|----------|-----------|-------|--------|--------|
| LZ-PRAGYAN-1 | -84.9 | 12.9 | 1.2° | 0 | 99.8% |
| LZ-ANANDSEN-4 | -84.5 | 83.1 | 1.8° | 0.1 | 99.1% |
| LZ-VIKRAM-2 | -89.4 | 120.5 | 2.1° | 0.2 | 98.5% |

---

# SLIDE A5: PATH PLANNING DETAILS

## Stage 4 - Complete Waypoint Analysis

### Complete Waypoint Sequence

| Waypoint | Latitude | Longitude | Elevation (m) | Hazard Score |
|----------|----------|-----------|---------------|--------------|
| KP-START | -89.48 | 94.36 | 1250 | 0 |
| KP-MID-1 | -89.4 | 110.15 | 980 | 0.2 |
| KP-MID-2 | -89.32 | 145.5 | 450 | 1.8 |
| KP-MID-3 | -89.25 | 180.2 | -850 | 2.4 |
| KP-TARGET | -89.21 | 238.88 | -2450 | 4.1 |

### Navigation Status

| Segment | Status | Power Drain |
|---------|--------|-------------|
| Start | Initiate Traverse at 5cm/s | 45W |
| Crater Rim | Maintain Nominal Speed | 48W |
| Gentle Slope | Engage Traction Control | 62W |
| Descent Ramp | Activate Floodlights | 85W |
| Target | Arrive Ice Sampling Target | Sampling |

---

# SLIDE A6: AI CONFIDENCE DETAILS

## Stage 5 - Complete Model Validation

### Ensemble Model Performance Details

| Model | Architecture | Epochs | Loss | Accuracy | F1 | Confidence |
|-------|--------------|--------|------|----------|-----|------------|
| Ice CNN | ResNet-50 3D SAR | 150 | 0.0142 | 98.4% | 0.982 | 98.9% |
| PSR UNET | U-Net Dual-Attention | 280 | 0.0089 | 99.1% | 0.990 | 99.4% |
| Landing | Ensemble XGBoost+CNN | 100 | 0.0195 | 96.8% | 0.965 | 97.2% |
| Astar | DQN + A* | 300 | 0.0051 | 97.5% | 0.974 | 98.1% |
| Fusion | Transformer | 250 | 0.011 | 98.8% | 0.986 | 98.8% |

---


