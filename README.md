# 🚀 CI/CD Pipeline with Docker & GitHub Actions

![CI/CD Pipeline](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=white)

A production-ready CI/CD pipeline that automatically builds, containerizes, and deploys a Python Flask application on every push to the main branch.

🌐 **Live Demo:** [https://my-devops-app-latest-iz7i.onrender.com](https://my-devops-app-latest-iz7i.onrender.com)

---

## 📐 Architecture

```
Developer pushes code
        ↓
   GitHub Repository
        ↓
 GitHub Actions triggers
        ↓
  Builds Docker image
        ↓
  Pushes to Docker Hub
        ↓
 Render auto-deploys
        ↓
  App live on internet
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python + Flask | Web application |
| Docker | Containerization |
| GitHub Actions | CI/CD automation |
| Docker Hub | Container registry |
| Render | Cloud deployment |

---

## 🚀 Features

- **Automated CI/CD** — pipeline triggers on every push to `main`
- **Containerized** — app runs consistently across any environment
- **Production-ready** — uses Gunicorn as the WSGI server
- **Health check endpoint** — `/health` for monitoring
- **Zero-downtime deploys** — Render pulls the latest image automatically

---

## 📁 Project Structure

```
my-devops-app/
├── app.py                        # Flask application
├── requirements.txt              # Python dependencies
├── Dockerfile                    # Container configuration
├── .github/
│   └── workflows/
│       └── ci-cd.yml             # GitHub Actions pipeline
└── README.md
```

---

## 🔧 Running Locally

### Without Docker
```bash
pip install -r requirements.txt
python app.py
```

### With Docker
```bash
# Build the image
docker build -t my-devops-app .

# Run the container
docker run -p 5000:5000 my-devops-app
```

Visit `http://localhost:5000`

---

## ⚙️ CI/CD Pipeline

The pipeline is defined in `.github/workflows/ci-cd.yml` and runs on every push to `main`:

1. **Checkout** — pulls the latest code
2. **Login** — authenticates with Docker Hub using GitHub Secrets
3. **Build & Push** — builds the Docker image and pushes to Docker Hub
4. **Deploy** — Render detects the new image and redeploys automatically

### Required GitHub Secrets

| Secret | Description |
|--------|-------------|
| `DOCKER_USERNAME` | Docker Hub username |
| `DOCKER_PASSWORD` | Docker Hub access token |

---

## 🌐 API Endpoints

| Endpoint | Method | Response |
|----------|--------|----------|
| `/` | GET | `{"message": "Hello from my DevOps pipeline!", "status": "ok"}` |
| `/health` | GET | `{"status": "healthy"}` |

---

## 📦 Docker Hub

The Docker image is publicly available at:
```
docker pull dontlus/my-devops-app:latest
```

---

## 📄 License

MIT License — feel free to use this as a template for your own projects.
