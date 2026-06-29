# Technology Stack & Architecture

---

# SLIDE 11: DATA PROCESSING PIPELINE

## End-to-End Data Flow

### Input Datasets

| Stage | Dataset | Format | Size |
|-------|---------|--------|------|
| Stage 1 | 1st_stage_ice_detection_input.csv | CSV | ~200KB |
| Stage 2 | 2nd_stage_ice_volume_psrs_input.csv | CSV | ~200KB |
| Stage 3 | 3rd_stage_safe_landing_input.csv | CSV | ~200KB |
| Stage 4 | 4th_stage_path_planning_input.csv | CSV | ~200KB |
| Stage 5 | 5th_stage_ai_confidence_input.csv | CSV | ~200KB |

### Processing Pipeline
┌──────────────────────┐
│ Data Preprocessing │
│ • Normalization │
│ • Outlier Removal │
│ • Feature Extraction│
└──────────────────────┘
│
▼
┌──────────────────────┐
│ ML Pipeline │
│ • 5-Stage Models │
│ • Ensemble Methods │
│ • Validation │
└──────────────────────┘
│
▼
┌──────────────────────┐
│ Output Generation │
│ • Predictions │
│ • Confidence Scores │
│ • Visualization │
└──────────────────────┘


---

# SLIDE 12: TECHNOLOGY STACK

## Development Tools & Technologies

### Frontend Stack

| Technology | Purpose |
|------------|---------|
| **React 19** | UI Framework |
| **Tailwind CSS v4** | Styling |
| **Lucide React** | Icons |
| **React Icons** | Additional Icons |
| **Vite** | Build Tool |
| **Leaflet** | Interactive Maps |

### Backend Stack

| Technology | Purpose |
|------------|---------|
| **FastAPI** | REST API Framework |
| **Python 3.9+** | Core Language |
| **Uvicorn** | ASGI Server |

### ML Libraries

| Library | Purpose |
|---------|---------|
| **PyTorch** | Deep Learning |
| **Transformers** | Transformer Models |
| **Scikit-learn** | ML Algorithms |
| **Pandas** | Data Manipulation |
| **NumPy** | Numerical Computing |
| **Rasterio** | Geospatial Data |
| **OpenCV** | Image Processing |
| **Matplotlib** | Visualization |

### Data Tools

| Tool | Purpose |
|------|---------|
| **GDAL** | Geospatial Data Abstraction |
| **PDS4 Tools** | Planetary Data System |
| **QGIS** | GIS Analysis |

---

# SLIDE 21: SYSTEM ARCHITECTURE

## Complete System Architecture

┌──────────────────────────────────────────────────────────────────────┐
│ FRONTEND (React 19 + Tailwind CSS v4) │
│ ┌──────────────────────────────────────────────────────────────┐ │
│ │ Dashboard │ Ice Detection │ Volume │ Landing │ Path │ AI │ │
│ └──────────────────────────────────────────────────────────────┘ │
│ ┌───────────┐ │
│ │ Leaflet │ │
│ │ Maps │ │
│ └───────────┘ │
└──────────────────────────────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────────────────────────────┐
│ BACKEND API (FastAPI) │
│ ┌───────────────┐ ┌───────────────┐ ┌────────────────────────┐ │
│ │ /api/upload │ │ /api/process │ │ /api/results │ │
│ └───────────────┘ └───────────────┘ └────────────────────────┘ │
└──────────────────────────────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────────────────────────────┐
│ ML PIPELINE (Python) │
│ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌────────┐ │
│ │ Stage 1 │ │ Stage 2 │ │ Stage 3 │ │ Stage 4 │ │Stage 5 │ │
│ │ Ice │ │ Volume │ │ Landing │ │ Path │ │ AI │ │
│ │Detection│ │Estimate │ │ Site │ │ Planning│ │Confid. │ │
│ └─────────┘ └─────────┘ └─────────┘ └─────────┘ └────────┘ │
└──────────────────────────────────────────────────────────────────────┘
│
▼
┌──────────────────────────────────────────────────────────────────────┐
│ DATA STORAGE │
│ ┌─────────────┐ ┌─────────────┐ ┌────────────────────────────┐ │
│ │ Raw CSV │ │ Processed │ │ Model Weights/Checkpoints │ │
│ │ Datasets │ │ Datasets │ │ │ │
│ └─────────────┘ └─────────────┘ └────────────────────────────┘ │
└──────────────────────────────────────────────────────────────────────┘


---

# SLIDE 22: CODE STRUCTURE

## Project Directory Organization
BharatiyaAntarikshHackathon2026-PS-08/
├── frontend/
│ ├── src/
│ │ ├── components/
│ │ │ ├── Dashboard.jsx
│ │ │ ├── IceDetection.jsx
│ │ │ ├── IceVolume.jsx
│ │ │ ├── SafeLanding.jsx
│ │ │ ├── PathPlanning.jsx
│ │ │ ├── AIConfidence.jsx
│ │ │ ├── Results.jsx
│ │ │ └── Settings.jsx
│ │ ├── services/
│ │ │ └── api.js
│ │ ├── styles/
│ │ │ └── index.css
│ │ ├── App.jsx
│ │ └── main.jsx
│ ├── package.json
│ └── vite.config.js
│
├── ml-pipeline/
│ ├── stage1_ice_detection/
│ │ ├── model.py
│ │ ├── train.py
│ │ └── inference.py
│ ├── stage2_ice_volume/
│ │ ├── model.py
│ │ ├── volume_calculator.py
│ │ └── inference.py
│ ├── stage3_landing_site/
│ │ ├── model.py
│ │ ├── hazard_analysis.py
│ │ └── inference.py
│ ├── stage4_path_planning/
│ │ ├── astar.py
│ │ ├── terrain_analyzer.py
│ │ └── inference.py
│ ├── stage5_ai_confidence/
│ │ ├── model.py
│ │ ├── metrics.py
│ │ └── inference.py
│ ├── data/
│ │ ├── raw/
│ │ └── processed/
│ ├── requirements.txt
│ └── main.py
│
├── backend/
│ ├── app.py
│ ├── routes/
│ └── utils/
│
└── README.md




---

# SLIDE 23: DEPENDENCIES

## Complete Package Requirements

### Frontend Dependencies
```json

```
{
  "dependencies": {
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "react-router-dom": "^6.0.0",
    "lucide-react": "^0.344.0",
    "react-icons": "^5.0.0",
    "leaflet": "^1.9.0",
    "react-leaflet": "^4.0.0",
    "tailwindcss": "^4.0.0",
    "axios": "^1.6.0"
  }
}

```
```
Backend Dependencies

fastapi==0.104.1
uvicorn==0.24.0
python-multipart==0.0.6
pandas==2.1.0
numpy==1.26.0
scikit-learn==1.3.0
torch==2.1.0
transformers==4.35.0
rasterio==1.3.9
opencv-python==4.8.1
matplotlib==3.7.0
pds4-tools==0.5.0
gdal==3.7.0



SLIDE 24: INSTALLATION & SETUP
Setup Instructions
1. Clone Repository
   
git clone https://github.com/yourusername/BharatiyaAntarikshHackathon2026-PS-08.git
cd BharatiyaAntarikshHackathon2026-PS-08

2. Setup Frontend
cd frontend
npm install
npm run dev

3. Setup Backend
bash
cd backend
pip install -r requirements.txt
uvicorn app:app --reload --port 8080
4. Setup ML Pipeline
bash
cd ml-pipeline
pip install -r requirements.txt
python main.py
5. Access Application
Frontend: http://localhost:5173

Backend API: http://localhost:8080

API Documentation: http://localhost:8080/docs

SLIDE 25: API ENDPOINTS
FastAPI Endpoints
Upload Endpoints

POST /api/upload/stage1
POST /api/upload/stage2
POST /api/upload/stage3
POST /api/upload/stage4
POST /api/upload/stage5
Processing Endpoints

POST /api/process/stage1
POST /api/process/stage2
POST /api/process/stage3
POST /api/process/stage4
POST /api/process/stage5
Results Endpoints

GET /api/results/stage1
GET /api/results/stage2
GET /api/results/stage3
GET /api/results/stage4
GET /api/results/stage5
GET /api/results/consolidated
Health Check
GET /api/health




git clone https://github.com/yourusername/BharatiyaAntarikshHackathon2026-PS-08.git
cd BharatiyaAntarikshHackathon2026-PS-08
