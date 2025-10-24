# 🛰️ Rason Monitoring v2.0 — React + Flask Edition

Rason Monitoring v2.0 is a modernized web application for **Radiosonde (weather-balloon) data monitoring and analysis**, rebuilt with a **React frontend** and a **Flask-based Python backend**.  

The platform provides real-time visualization and quality-control analytics for upper-air observations collected from multiple sites (e.g., BUFR/BFR/BIN files from Meteomodem M10/M20 systems).

---

## 🚀 Key Features

- **React + Vite Frontend** — modern SPA dashboard with Chart.js/Recharts visualization  
- **Flask API Backend** — RESTful endpoints for BUFR decoding, Time Accuracy, Height Reach, and Deep Physics Analysis  
- **Separation of Concerns** — clean architecture between UI (React) and computation engine (Python)  
- **Interactive Modules:**
  - Time Accuracy analysis (AA/BB/CC/DD message timing)
  - Error & Physics analysis (tropopause, RH freeze-out, wind shear, etc.)
  - Balloon Burst & Height Reach tracking
  - Data availability summaries per site  
- **Responsive Sidebar Layout** — gradient UI with glassmorphism style  
- **Cross-Origin Ready** — integrated Flask-CORS for local React development  
- **Scalable Roadmap** — future support for Go microservices & WebSocket real-time tracking  

---

## 🧩 Tech Stack

| Layer | Technology |
|-------|-------------|
| **Frontend** | React (Vite), React Router, Axios, Chart.js/Recharts |
| **Backend** | Flask, pybufrkit / eccodes, pandas, numpy |
| **Deployment** | Gunicorn + Nginx or Docker Compose |
| **Language** | Python 3.12, JavaScript (ES2023) |

---

## 🧠 Project Vision

> “Rason Monitoring v2.0 brings a unified and modern interface for upper-air meteorological data, combining scientific accuracy from Python with interactive and real-time visualization power from React.”

---

## 🗂️ Repository Structure

```
rason-v2/
├─ backend-flask/          # Flask API backend (existing app.py)
│   ├─ app.py
│   ├─ static/
│   └─ templates/
│
└─ frontend-react/         # React UI (SPA dashboard)
    ├─ src/
    ├─ public/
    ├─ package.json
    └─ vite.config.js
```

---

## ⚙️ Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/rason-v2.git
cd rason-v2
```

### 2. Setup Python Backend
```bash
cd backend-flask
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

Default Flask runs at: **http://localhost:5000**

---

### 3. Setup React Frontend
```bash
cd frontend-react
npm install
npm run dev
```

Default React runs at: **http://localhost:5173**

> React will fetch data from Flask API (`http://localhost:5000/api/...`).  
> If needed, enable CORS in Flask with:
> ```python
> from flask_cors import CORS
> CORS(app)
> ```

---

## 🧱 Build for Production

Once frontend is stable:
```bash
cd frontend-react
npm run build
```
Then serve the built files via Flask:

```python
from flask import send_from_directory

@app.route('/')
def index():
    return send_from_directory('../frontend-react/dist', 'index.html')

@app.route('/<path:path>')
def static_proxy(path):
    return send_from_directory('../frontend-react/dist', path)
```

---

## 🧭 Roadmap
- [ ] Replace jQuery pages with React pages (Time Accuracy, Error Analysis, Height Reach)  
- [ ] Integrate Meteomodem BUFR decoding via pybufrkit  
- [ ] Add WebSocket live tracking for in-flight balloons  
- [ ] Containerize with Docker Compose  
- [ ] Implement Go microservice for heavy analytics  

---

Developed by Nanda Miftahul Khoyri
for Terrindo & BMKG Upper-Air Division
2025 © All Rights Reserved.
