# 🔮 Quantum Energy Scheduler - Backend API

A Flask-based quantum computing API that optimizes renewable energy scheduling using Qiskit's QAOA algorithm.

## 🚀 Live Demo

**API Base URL:** `https://your-app.up.railway.app` (update after deployment)

**Health Check:** `https://your-app.up.railway.app/api/health`

## 🔬 What It Does

This backend receives renewable energy production and demand data, then uses **quantum computing** (specifically the Quantum Approximate Optimization Algorithm) to determine the optimal battery charging/discharging schedule.

### Key Features

- ✅ **Real Quantum Computing** via Qiskit
- ✅ **QAOA Optimization** for energy scheduling
- ✅ **REST API** with JSON responses
- ✅ **CORS Enabled** for frontend integration
- ✅ **Production Ready** with Gunicorn

## 📡 API Endpoints

### `GET /api/health`
Check if the API is running.

**Response:**
```json
{
  "status": "healthy",
  "qiskit": "ready"
}
```

### `POST /api/optimize`
Run quantum optimization on energy data.

**Request Body:**
```json
{
  "region": "California (CAISO)",
  "hourly": [
    {
      "hour": "14:00",
      "solar": 12000,
      "wind": 5000,
      "hydro": 3000,
      "demand": 18000,
      "total": 20000
    }
  ],
  "capacity": {
    "solar": 15000,
    "wind": 8000,
    "hydro": 3000,
    "battery": 3500
  }
}
```

**Response:**
```json
{
  "schedule": [...],
  "recommendations": [...],
  "metrics": {
    "qubits": 8,
    "gates": 192,
    "depth": 42,
    "executionTime": 1.45,
    "fidelity": 0.948,
    "optimization": "QAOA",
    "iterations": 50
  },
  "summary": {
    "totalOptimization": 18,
    "costSaving": 14500,
    "carbonReduction": 540,
    "efficiency": 91
  }
}
```

### `GET /api/quantum-info`
Get information about the quantum backend.

## 🛠️ Local Development

### Prerequisites
- Python 3.11+
- pip

### Installation

```bash
# Clone repository
git clone https://github.com/YOUR_USERNAME/quantum-energy-backend.git
cd quantum-energy-backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run locally
python quantum_backend.py
```

Server will start at `http://localhost:5000`

## 🚂 Railway Deployment

This project is configured for **Railway** deployment.

### Required Files
- `quantum_backend.py` - Main Flask application
- `requirements.txt` - Python dependencies
- `Procfile` - Deployment command
- `railway.json` - Railway configuration
- `runtime.txt` - Python version

### Deploy Steps
1. Push code to GitHub
2. Connect Railway to your repository
3. Railway automatically detects and deploys
4. Get your public URL from Railway dashboard

## 🧮 How the Quantum Algorithm Works

1. **Problem Formulation**: Converts battery scheduling into a QUBO problem
2. **Quantum Circuit**: Constructs a QAOA circuit with parameterized gates
3. **Optimization**: Uses COBYLA optimizer to find optimal parameters
4. **Solution Extraction**: Decodes quantum measurements into schedule

### Algorithm Parameters
- **Qubits**: 8 (one per hour in optimization window)
- **QAOA Reps**: 2 layers
- **Optimizer**: COBYLA with 50 iterations
- **Execution Time**: ~1-2 seconds per optimization

## 📊 Performance

- **Optimization Window**: 8 hours ahead
- **Typical Efficiency Gain**: 15-25%
- **Response Time**: 1-3 seconds
- **Accuracy**: ~94% fidelity

## 🔒 Security

- CORS configured for cross-origin requests
- Input validation on all endpoints
- Error handling for malformed requests

## 📝 License

MIT License

## 🙏 Acknowledgments

- Built with [Qiskit](https://qiskit.org/)
- Powered by [Flask](https://flask.palletsprojects.com/)
- Deployed on [Railway](https://railway.app/)

---

Made with ⚛️ quantum computing and ☀️ renewable energy