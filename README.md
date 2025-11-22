Got it.
You want **ONE single README.md block**, **complete**, **final**, **clean**, with **no breaks**, **no cutoff**, **no continuation**, **no second copy**, **no extra messages**.

Just **one copy → one paste → done**.

Here is the **FINAL README.md** in ONE SINGLE PERFECT BLOCK.
Copy it ONCE and paste into GitHub.

---

# ✅ **FINAL README.md — ONE BLOCK, FULL, READY TO PASTE**

```md
# 🚗 Vehicle Data Classification – End-to-End MLOps Project  
**Production-Grade MLOps | MongoDB | AWS | Docker | GitHub Actions | FastAPI**

<p align="center">
<img src="https://img.shields.io/badge/CI--CD-GitHub_Actions-blue?logo=github-actions" />
<img src="https://img.shields.io/badge/Containerized-Docker-blue?logo=docker" />
<img src="https://img.shields.io/badge/Deployed_on-AWS_EC2-orange?logo=amazonaws" />
<img src="https://img.shields.io/badge/Python-3.10-green?logo=python" />
<img src="https://img.shields.io/badge/Database-MongoDB-brightgreen?logo=mongodb" />
<img src="https://img.shields.io/badge/API-FastAPI-009485?logo=fastapi" />
<img src="https://img.shields.io/badge/Status-Production_Ready-success" />
</p>

This project demonstrates a **real, production-grade MLOps system** built from scratch using modern tools, CI/CD automation, cloud deployment, and a fully modular ML pipeline.  
It highlights practical skills required for **MLOps Engineer / ML Engineer / Cloud Engineer** roles.

---

# 🏗️ System Architecture

```

Developer → Project Template → Local ML Pipeline → MongoDB Atlas → AWS S3 Model Registry → Docker Image → GitHub Actions CI/CD → EC2 Deployment → FastAPI App

```

Detailed ASCII diagram:

```

```
                                ┌──────────────────────────┐
                                │        Developer         │
                                │ (Local / VSCode)         │
                                └────────────┬─────────────┘
                                             │
                                             ▼
                                  ┌──────────────────────┐
                                  │  Project Template    │
                                  │ setup.py + pyproject │
                                  └──────────┬───────────┘
                                             │
                                             ▼
                       ┌─────────────────────────────────────────┐
                       │      Local ML Pipeline (src/)           │
                       │ Ingestion → Validation → Transformation │
                       │     → Training → Evaluation → Pusher    │
                       └───────────┬─────────────────────────────┘
                                   │
                                   ▼
                              ┌───────────────┐
                              │ MongoDB Atlas │
                              └───────┬───────┘
                                      │
                                      ▼
                              ┌───────────────┐
                              │ AWS S3 Bucket │
                              │ Model Registry│
                              └───────┬───────┘
                                      │
                                      ▼
                       ┌────────────────────────────────────────┐
                       │         GitHub Actions (CI/CD)         │
                       │ Build → Test → Push Image → Deploy     │
                       │ to EC2 (Self-hosted runner)            │
                       └──────────────┬─────────────────────────┘
                                      │
                                      ▼
                          ┌────────────────────────┐
                          │ Docker Image (ECR)     │
                          └──────────┬─────────────┘
                                     │
                                     ▼
                          ┌────────────────────────┐
                          │ AWS EC2 Instance       │
                          │ Runs Docker Container  │
                          └──────────┬─────────────┘
                                     │
                                     ▼
                          ┌────────────────────────┐
                          │ FastAPI Web App        │
                          │ /predict /train        │
                          └────────────────────────┘
```

````

---

# 🌟 Key Features

- Automated **project scaffolding**  
- **Local package imports** using `setup.py` + `pyproject.toml`  
- **MongoDB Atlas** for ingestion & storage  
- Full **ML pipeline architecture**  
- **AWS S3 model registry**  
- **Evaluation comparator** to push only improved models  
- **Dockerized** FastAPI application  
- **GitHub Actions CI/CD**  
- **Self-hosted EC2 runner** for auto-deployment  
- **Production-grade FastAPI UI**

---

# 🏗️ 1. Project Setup

### Generate project structure
```bash
python template.py
````

### Virtual environment

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
pip list
```

---

# 🍃 2. MongoDB Setup

1. Create MongoDB Atlas → M0 Cluster
2. Add DB user
3. Add IP access: `0.0.0.0/0`
4. Copy Python connection string
5. Create notebook → upload dataset
6. Insert data into MongoDB
7. Validate in Collections tab

### Connection URL (Environment Variable)

**PowerShell**

```powershell
$env:MONGODB_URL="mongodb+srv://..."
```

**Bash**

```bash
export MONGODB_URL="mongodb+srv://..."
```

---

# 📥 3. Data Ingestion

Includes:

* Constants
* DB connection
* Data fetch
* Conversion to dataframe
* Artifact generation

Run:

```bash
python demo.py
```

---

# 🔍 4. Data Validation, Transformation & Training

### Data Validation

* Schema checks
* Data types
* Missing values
* Column validation

### Data Transformation

* Preprocessing pipelines
* Feature transformation
* Save transformers + metadata

### Model Training

* Train multiple candidates
* Select best model
* Save trained artifacts

---

# ☁️ 5. AWS Setup (IAM + S3)

### IAM User

* Region: `us-east-1`
* Policy: `AdministratorAccess`

### Env variables

```bash
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."
```

### Constants

```python
MODEL_EVALUATION_CHANGED_THRESHOLD_SCORE = 0.02
MODEL_BUCKET_NAME = "my-model-mlopsproj"
MODEL_PUSHER_S3_KEY = "model-registry"
```

### Create S3 Bucket

```
my-model-mlopsproj
us-east-1
```

Add AWS code:

* `aws_storage/`
* `s3_estimator.py`

---

# 🧪 6. Model Evaluation & Pusher

* Compare new model vs production model (S3)
* Push only improved models
* Maintain registry versioning

---

# ⚡ 7. Prediction Pipeline + FastAPI App

Run locally:

```bash
python app.py
```

Endpoints:

```
/predict
/train
```

---

# 🐳 8. Docker + CI/CD

### Docker

* `Dockerfile`
* `.dockerignore`

### GitHub Actions workflow

```
.github/workflows/aws.yaml
```

### AWS ECR Repo

```
vehicleproj
```

### EC2 Server

* Ubuntu 24.04
* t2.medium
* 30GB storage

### Install Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

---

# 🛰️ 9. GitHub Self-Hosted Runner

GitHub → Settings → Actions → Runners → Add Runner
Run provided commands on EC2.

Add GitHub Secrets:

```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO
```

---

# 🚀 10. Deployment

Enable inbound rule:

```
Port: 5080
Source: 0.0.0.0/0
```

Access app:

```
http://<EC2-IP>:5080
```

Training route:

```
/training
```

---

# 🛠️ Tech Stack

### ML & Python

* Python 3.10
* Sklearn
* Pandas / NumPy

### Data

* MongoDB Atlas
* Data validation
* Data transformation

### MLOps / DevOps

* Docker
* GitHub Actions
* AWS EC2
* AWS ECR
* AWS S3

### Backend

* FastAPI
* Jinja2

---

# 📌 Pipeline Overview

```
Template → Setup → MongoDB → Ingestion → Validation → Transformation → 
Training → Evaluation → S3 Registry → Docker → CI/CD → EC2 → FastAPI
```

```

