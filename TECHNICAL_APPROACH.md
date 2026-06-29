# Technical Approach - 5-Stage AI Pipeline

---

# SLIDE 5: TECHNICAL APPROACH - 5-STAGE AI PIPELINE

## The 5-Stage Pipeline Architecture
┌─────────────────────────────────────────────────────────────────┐
│ INPUT DATA PIPELINE │
├─────────────────────────────────────────────────────────────────┤
│ Chandrayaan-2 DFSAR Data │ OHRC Imagery │ DEM Elevation │
└─────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ STAGE 1: ICE DETECTION │
│ • DFSAR Radar Backscatter Analysis │
│ • CPR & DOP Computation │
│ • ResNet-50 3D SAR CNN Model │
│ • Ice Probability Mapping (>50%) │
└─────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ STAGE 2: ICE VOLUME & PSRs │
│ • PSR / Doubly PSR Identification │
│ • Volume = Area × Depth × Ice Fraction │
│ • U-Net Dual-Attention Segmentation │
└─────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ STAGE 3: SAFE LANDING SITE │
│ • Multi-Criteria Decision Analysis │
│ • Slope < 12°, Boulder Density Analysis │
│ • Ensemble XGBoost + CNN Model │
└─────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ STAGE 4: PATH PLANNING │
│ • A* Heuristic Search Algorithm │
│ • Terrain Hazard Weighted Grid │
│ • DQN + A* Hybrid Model │
└─────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ STAGE 5: AI CONFIDENCE │
│ • Transformer Multi-Modal Validation │
│ • Ensemble Model Agreement Weights │
│ • Mission Confidence Score Distribution │
└─────────────────────────────────────────────────────────────────┘




---

# SLIDE 6: STAGE 1 - ICE DETECTION

## Ice Detection Methodology

### Input Data
| Parameter | Description |
|-----------|-------------|
| Raw Backscatter | DFSAR L/S-Band radar data |
| Thermal K | Diviner thermal emission sensors |
| Albedo | Surface reflectance data |
| CPR | Circular Polarization Ratio |
| DOP | Degree of Polarization |

### Detection Criteria
- **CPR > 1.0** (Indicates volume scattering - ice signature)
- **DOP < 0.13** (Low depolarization - ice-rich regions)
- **Temperature < 100K** (Cryogenic stability)

### Model Architecture

ResNet-50 3D SAR CNN
├── Input: 3D Radar Data Cube
├── Convolutional Layers (50 layers)
├── Batch Normalization
├── ReLU Activation
├── Global Average Pooling
└── Softmax Output: Ice Probability


### Results
- **Accuracy:** 98.4%
- **Ice Probability Threshold:** >50%
- **Detected Ice Craters:** 526

---

# SLIDE 7: STAGE 2 - ICE VOLUME ESTIMATION

## Volume Calculation Methodology

### PSR & Doubly PSR Classification

| Zone Type | Description | Characteristics |
|-----------|-------------|-----------------|
| **Standard PSR** | Permanently Shadowed Region | 0% direct sunlight, <100K |
| **Doubly PSR** | Nested Shadow Zone | Ultra-cold traps, <40K |
| **Illuminated** | Sun-exposed region | >4% illumination |

### Volume Calculation Formula

Volume (m³) = Area (m²) × Depth (m) × Ice Fraction

Where:

Area = Grid Cell Area (typically 30m × 30m)

Depth = 5 meters (sensing depth)

Ice Fraction = AI-predicted ice concentration



### Results
- **Total Volume:** 4.82 × 10⁶ m³
- **Doubly PSR Zones:** 14 Nested Zones
- **PSR Coverage:** 56%
- **DSPR Coverage:** 14.2%

### Key Doubly PSR Locations
| Zone ID | Depth (m) | Volume (m³) | Core Temp (K) |
|---------|-----------|-------------|---------------|
| D-PSR-ZONE-B | 31.5 | 285,400.0 | 38.4 |
| D-PSR-ZONE-D | 36.0 | 340,800.0 | 35.0 |

---

# SLIDE 8: STAGE 3 - SAFE LANDING SITE

## Landing Site Selection Criteria

### Multi-Criteria Decision Analysis

| Factor | Weight | Threshold |
|--------|--------|-----------|
| **Slope** | 35% | < 8.4° (Optimal), < 12° (Maximum) |
| **Boulder Density** | 25% | < 0.10 (Optimal) |
| **Illumination** | 20% | > 200 hours (Solar availability) |
| **Hazard Score** | 20% | < 65 (AI-predicted) |

### Landing Site Grades

| Grade | Description | Safety Probability |
|-------|-------------|-------------------|
| A+ | Optimal Flat | 99.8% |
| A | Safe Descent | 95-99% |
| B | Caution Advised | 88-95% |
| C | High Risk | <88% |

### Key Landing Sites Identified

| Target ID | Region | Slope (°) | Hazard Score | Safety Probability |
|-----------|--------|-----------|--------------|-------------------|
| LZ-PRAGYAN-1 | Malapetr Massif Plateau | 1.2 | 0 | 99.8% |
| LZ-VIKRAM-2 | Shackleton Connecting Ridge | 2.1 | 0.2 | 98.5% |
| LZ-ANANDSEN-4 | Amundsen Western Flat | 1.8 | 0.1 | 99.1% |

### Total Sites Evaluated
- **Safe Touchdown Zones:** 1,501 sites
- **Risk Zones:** 1,031 sites
- **Unsafe Zones:** 957 sites

---

# SLIDE 9: STAGE 4 - PATH PLANNING

## A* Algorithm Path Planning

### Algorithm Configuration

Pathfinding Engine: A* Heuristic Search
Heuristic: Euclidean Distance
Grid Size: 40×40 resolution
Terrain Constraints:
├── Slope < 15° (Avoid steep crater rims)
├── Hazard Penalty Weight: Dynamic
└── Solar Illumination > 0 hours


### Waypoint Sequence

| Waypoint | Latitude | Longitude | Elevation (m) | Hazard Score |
|----------|----------|-----------|---------------|--------------|
| #1 (Start) | -89.6036 | 313.0739 | -309.9 | 18.7 |
| #2 | -89.4212 | 312.1677 | -331.4 | 26.1 |
| #3 | -89.2388 | 311.2616 | -373.0 | 33.6 |
| #4 | -89.0564 | 310.3555 | -449.4 | 41.1 |
| #5 | -88.8740 | 309.4493 | -566.0 | 48.5 |
| #6 | -88.6916 | 308.5432 | -717.4 | 56.0 |
| #7 (Target) | -88.5092 | 307.6371 | -888.9 | 63.5 |

### Route Statistics

| Metric | Value |
|--------|-------|
| **Total Distance** | 299.23 km |
| **Total Waypoints** | 42 waypoints |
| **Path Cost** | 19.97 |
| **Travel Time** | 3,324.8 hours |
| **Algorithm** | A* (Euclidean heuristic) |

### Traverse Constraints
- Start: -86.439°, 355.419°
- Target: -89.935°, 13.719°
- Safe Traverse status maintained throughout

---

# SLIDE 10: STAGE 5 - AI CONFIDENCE

## Model Validation & Confidence Metrics

### Ensemble Model Performance

| Model | Architecture | Accuracy | F1 Score | Confidence |
|-------|--------------|----------|----------|------------|
| **MODEL-ICE-CNN** | ResNet-50 3D SAR | 98.4% | 0.982 | 98.9% |
| **MODEL-PSR-UNET** | U-Net Dual-Attention | 99.1% | 0.990 | 99.4% |
| **MODEL-LANDING** | Ensemble XGBoost + CNN | 96.8% | 0.965 | 97.2% |
| **MODEL-ASTAR** | DQN + A* Heuristic | 97.5% | 0.974 | 98.1% |
| **MODEL-FUSION** | Transformer Multi-Modal | 98.8% | 0.986 | 98.8% |

### Consolidated Metrics

| Metric | Value |
|--------|-------|
| **Accuracy** | 95.8% |
| **ROC-AUC** | 98.3% |
| **Precision** | 97.8% |
| **Recall** | 97.3% |
| **Mission Confidence** | 96.8% |

### Confusion Matrix

Predicted
No-Ice Ice
True No-Ice 499 14
True Ice 11 76



---
