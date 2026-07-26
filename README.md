# CyberTech Platform - Cybersecurity SaaS Demo

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Python](https://img.shields.io/badge/Python-3.9+-blue)
![React](https://img.shields.io/badge/React-18+-61dafb)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ed)

A modern, production-ready Cybersecurity SaaS demo platform showcasing **Identity & Access Management (IAM)** and **Real-time Threat Detection** microservices. Built with Flask, React + Vite, Docker, Kubernetes manifests, comprehensive test coverage, and a live analytics dashboard.

## Overview

CyberTech Platform demonstrates enterprise-grade software engineering practices:

- **Microservices Architecture**: Decoupled IAM and Threat Detection services
- **Full Stack**: Flask backends + React + Vite frontend
- **Containerized**: Docker Compose for easy local development; Kubernetes manifests for production
- **Test Coverage**: Unit tests (pytest for Python, Vitest for React)
- **Real-time Dashboard**: Live threat detection analytics with Recharts
- **Security Best Practices**: JWT authentication, password hashing, environment-based config

## Project Structure

```
cybertech-platform/
├─ frontend/                          # React + Vite + Tailwind UI
│  ├─ src/
│  │  ├─ components/
│  │  │  └─ CyberTechPlatform.jsx    # Main app component with tabs & live dashboard
│  │  ├─ __tests__/
│  │  │  └─ CyberTechPlatform.test.jsx
│  │  ├─ index.js
│  │  └─ index.css
│  ├─ package.json
│  ├─ vite.config.js
│  ├─ vitest.config.mts
│  ├─ src/setupTests.js
│  └─ index.html
│
├─ services/
│  ├─ iam/                           # Identity & Access Management
│  │  ├─ app.py                      # Flask IAM service
│  │  ├─ requirements.txt
│  │  ├─ Dockerfile
│  │  └─ tests/
│  │     └─ test_auth.py             # Unit tests
│  └─ threat-detection/              # Threat Detection Engine
│     ├─ app.py                      # Flask threat analysis service
│     ├─ requirements.txt
│     ├─ Dockerfile
│     └─ tests/
│        └─ test_threats.py          # Unit tests
│
├─ k8s/                              # Kubernetes manifests
│  ├─ namespace.yaml
│  ├─ iam.yaml
│  ├─ threat.yaml
│  ├─ frontend.yaml (optional)
│  └─ iam-secret.yaml
│
├─ docker-compose.yml                # Full stack local dev setup
├─ README.md
├─ CHANGELOG.md
└─ .gitignore
```

## Quick Start

### Prerequisites

- Docker & Docker Compose (v2.0+)
- Node.js (v16+) & npm
- Python 3.9+ (if running services locally)
- kubectl (for Kubernetes deployment)

### Option 1: Full Stack with Docker Compose (Recommended)

```bash
# Clone the repository
git clone https://github.com/yveszamor21/cybertech-platform.git
cd cybertech-platform

# Start all services (Postgres, Redis, Elasticsearch, IAM, Threat Detection)
docker compose up --build

# Verify services are running:
# - IAM Service:       http://localhost:5001/health
# - Threat Service:    http://localhost:5002/api/v1/threats/analyze
# - Postgres:          localhost:5432
# - Redis:             localhost:6379
# - Elasticsearch:     http://localhost:9200
```

### Option 2: Frontend Development Mode

```bash
# In another terminal, start the React dev server
cd frontend
npm install
npm run dev

# Access the UI at: http://localhost:5173
# The Vite dev server proxies backend requests to the Docker services
```

## Services

### IAM Service (Port 5001)

Identity & Access Management service with JWT-based authentication.

**Endpoints:**
- `GET /health` - Service health check
- `POST /api/v1/auth/login` - User authentication

**Demo Credentials:**
```json
{
  "username": "admin",
  "password": "admin123"
}
```

**Example Request:**
```bash
curl -X POST http://localhost:5001/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "admin123"}'
```

**Response:**
```json
{
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGc...",
  "role": "admin",
  "message": "Login successful"
}
```

### Threat Detection Service (Port 5002)

Real-time threat analysis using scikit-learn Isolation Forest anomaly detection.

**Endpoints:**
- `POST /api/v1/threats/analyze` - Analyze logs for threats

**Example Request:**
```bash
curl -X POST http://localhost:5002/api/v1/threats/analyze \
  -H "Content-Type: application/json" \
  -d '{
    "logs": [
      {"failed_logins": 50, "bytes": 1000000, "duration": 9999, "after_hours": true},
      {"failed_logins": 0, "bytes": 1000, "duration": 10, "after_hours": false}
    ]
  }'
```

**Response:**
```json
{
  "threats_detected": 1,
  "threats": [
    {"failed_logins": 50, "bytes": 1000000, "duration": 9999, "after_hours": true}
  ]
}
```

## Frontend Features

### Multi-Tab UI
1. **Overview** - Marketing introduction to the platform
2. **Entry-Level Demo** - IAM login flow demonstration
3. **Enterprise Demo** - Advanced threat detection features
4. **Testing** - Live API demo buttons + curl command examples
5. **Analytics** - Real-time threat trend chart (auto-updates every 10 seconds)

### Real-Time Threat Dashboard

The Analytics tab displays a line chart of threat detections over time:
- Auto-fetches threat data every 10 seconds
- Plots threat count on Y-axis, time index on X-axis
- Uses Recharts for smooth, interactive visualization
- Stores last 30 data points for performance

## Running Tests

### Backend Tests (pytest)

```bash
# IAM Service
cd services/iam
pip install -r requirements.txt
pytest tests/test_auth.py -v

# Threat Detection Service
cd services/threat-detection
pip install -r requirements.txt
pytest tests/test_threats.py -v
```

### Frontend Tests (Vitest)

```bash
cd frontend
npm install
npm run test
```

## Kubernetes Deployment

Basic local Kubernetes setup using minikube or kind:

```bash
# Create namespace and secrets
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/iam-secret.yaml

# Deploy services
kubectl apply -f k8s/iam.yaml
kubectl apply -f k8s/threat.yaml
kubectl apply -f k8s/frontend.yaml  # optional

# Verify deployment
kubectl -n cybertech get pods
kubectl -n cybertech get svc

# Port forward for local testing
kubectl -n cybertech port-forward svc/iam-service 5001:5001
kubectl -n cybertech port-forward svc/threat-service 5002:5002
kubectl -n cybertech port-forward svc/frontend-service 3000:80
```

## Environment Variables

All services load configuration from environment variables:

**IAM Service:**
- `JWT_SECRET_KEY` - Secret for JWT signing (⚠️ CHANGE IN PRODUCTION)
- `DATABASE_URL` - PostgreSQL connection string
- `FLASK_ENV` - Environment mode (development/production)

**Threat Detection:**
- `ELASTICSEARCH_URL` - Elasticsearch endpoint for log storage
- `FLASK_ENV` - Environment mode

**Frontend:**
- `VITE_IAM_BASE_URL` - IAM service URL
- `VITE_THREAT_BASE_URL` - Threat service URL

## Security Considerations

⚠️ **This is a demonstration platform.** For production use:

1. **JWT Secret** - Use a strong, unique secret and rotate regularly
2. **Database** - Enable SSL, use managed services, implement row-level security
3. **Passwords** - Implement salted hashing (bcrypt/argon2), enforce strong policies
4. **HTTPS/TLS** - Enforce TLS, use managed certificates
5. **Rate Limiting** - Implement per-IP and per-user rate limits
6. **CORS** - Configure specific allowed origins
7. **Logging** - Centralize logs, mask sensitive data
8. **Secrets Management** - Use HashiCorp Vault, AWS Secrets Manager, etc.

## Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | React 18 + Vite + Tailwind CSS + Recharts |
| IAM Backend | Flask + Flask-JWT-Extended |
| Threat Detection | Flask + scikit-learn (Isolation Forest) |
| Database | PostgreSQL 15 |
| Cache | Redis 7 |
| Search/Logging | Elasticsearch 8.10 |
| Containerization | Docker + Docker Compose |
| Orchestration | Kubernetes |
| Testing | pytest (Python) + Vitest (React) |

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                    Client Browser                           │
│              (http://localhost:5173)                        │
└──────────────────────────┬──────────────────────────────────┘
                           │
                    ┌──────▼──────┐
                    │ React UI    │
                    │ + Vite Dev  │
                    └──────┬──────┘
                           │
              ┌────────────┼────────────┐
              │            │            │
        ┌─────▼────┐ ┌─────▼────┐ ┌─────▼────┐
        │   IAM    │ │ Threat   │ │Postgres/ │
        │ Service  │ │Detection │ │ Redis/ES │
        │ :5001    │ │ :5002    │ │          │
        └──────────┘ └──────────┘ └──────────┘
```

## Contributing

Feel free to fork, modify, and submit PRs. This is a demonstration project for learning purposes.

## License

MIT License - see LICENSE file for details.

## Roadmap

- [ ] Machine learning model for threat prediction
- [ ] Advanced authentication (OAuth2, SAML)
- [ ] Multi-tenancy support
- [ ] Custom threat rule engine
- [ ] Mobile app (React Native)
- [ ] Kafka integration for event streaming
- [ ] Helm charts for Kubernetes

## FAQ

**Q: How do I reset the demo?**
A: Run `docker compose down -v` to remove containers and volumes, then restart with `docker compose up --build`.

**Q: Can I use this in production?**
A: Not directly. This is a learning/demo project. Use it as a reference for architecture and best practices.

**Q: How do I modify the demo credentials?**
A: Update the in-memory user store in `services/iam/app.py` and rebuild the container.

## Support

For issues, questions, or suggestions, open a GitHub issue in the repository.

---

**Created with ❤️ for cybersecurity & software engineering enthusiasts**
