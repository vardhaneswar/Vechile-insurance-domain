# Vechile-insurance-domain
Project on vechile insurance domain
🚗 Vehicle Data Classification – End-to-End MLOps Project

Production-Grade MLOps | MongoDB | AWS | Docker | GitHub Actions | FastAPI

<p align="center">














</p>

This repository contains a real-world, end-to-end MLOps project demonstrating how to build, train, evaluate, version, and deploy ML models using a complete cloud-native pipeline.

The workflow includes:
✔ Project scaffolding
✔ MongoDB ingestion
✔ Automated ML pipeline
✔ AWS S3 model registry
✔ Dockerized FastAPI service
✔ Full CI/CD pipeline using GitHub Actions + EC2 self-hosted runner
✔ Production deployment on AWS

🏗️ System Architecture
                                    ┌──────────────────────────┐
                                    │        Developer         │
                                    │(Local Machine / VSCode)  │
                                    └────────────┬─────────────┘
                                                 │
                                                 ▼
                                      ┌───────────────────────┐
                                      │ 1. Project Template   │
                                      │ setup.py + pyproject  │
                                      └───────────┬───────────┘
                                                  │
                                                  ▼
                           ┌──────────────────────────────────────────┐
                           │          Local ML Pipeline (src/)        │
                           │ Ingestion → Validation → Transformation  │
                           │   → Training → Evaluation → Pusher       │
                           └──────────────────┬───────────────────────┘
                                              │
                                              ▼
                                  ┌──────────────────────┐
                                  │    MongoDB Atlas     │
                                  │ Raw + Cleaned Data   │
                                  └───────────┬──────────┘
                                              │
                                              ▼
                                  ┌──────────────────────┐
                                  │   AWS S3 Bucket      │
                                  │   Model Registry     │
                                  └───────────┬──────────┘
                                              │
                         ┌────────────────────┴───────────────────────┐
                         │         GitHub CI/CD Pipeline              │
                         │ (Build → Test → Push Image → Deploy to EC2)│
                         └───────────────┬────────────────────────────┘
                                         │
                                         ▼
                              ┌────────────────────────┐
                              │   Docker Image (ECR)   │
                              └───────────┬────────────┘
                                          │
                                          ▼
                               ┌────────────────────────┐
                               │      AWS EC2 Server    │
                               │ Runs Docker Container  │
                               │ Exposes Port :5080     │
                               └───────────┬────────────┘
                                           │
                                           ▼
                                 ┌────────────────────┐
                                 │  FastAPI Web App   │
                                 │    /predict        │
                                 │    /train          │
                                 └────────────────────┘

🌟 Features

Template-based project structure

Local package installation using setup.py + pyproject.toml

MongoDB Atlas integration for raw data ingestion

Fully modular ML pipeline (Ingestion → Validation → Transformation → Training → Evaluation → Pushing)

AWS S3 model registry

Dockerization

GitHub Actions CI/CD

Self-hosted EC2 runner

Production deployment on AWS EC2

FastAPI UI with prediction and training endpoints

🏗️ 1. Project Setup
Create project structure
python template.py

Create & activate virtual environment
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
pip list

Local package imports

Supported using:

setup.py

pyproject.toml

🍃 2. MongoDB Atlas Setup

Create MongoDB Atlas account

Create project → M0 cluster

Add DB user

Add network access 0.0.0.0/0

Copy connection URL

Load dataset via Jupyter Notebook

View records in Atlas → Collections

Set MongoDB URL

PowerShell

$env:MONGODB_URL="mongodb+srv://..."


Bash

export MONGODB_URL="mongodb+srv://..."


Add artifact/ to .gitignore.

📥 3. Data Ingestion Pipeline

Add constants

Configure DB connection

Create ingestion component

Convert MongoDB → DataFrame

Save raw & split data into artifacts

Run:

python demo.py

🔍 4. Data Validation, Transformation & Model Trainer
Data Validation

Schema checking (columns, types)

Missing values check

Dataset integrity

Data Transformation

Preprocessing pipelines

Feature engineering

Save transformers + metadata

Model Trainer

Train multiple models

Select best one

Save artifacts

☁️ 5. AWS Setup (IAM, S3, Env)
Create IAM User

Region: us-east-1

Policy: AdministratorAccess

Generate Access Key + Secret Key

Export AWS credentials
export AWS_ACCESS_KEY_ID="..."
export AWS_SECRET_ACCESS_KEY="..."

Update constants
MODEL_EVALUATION_CHANGED_THRESHOLD_SCORE = 0.02
MODEL_BUCKET_NAME = "my-model-mlopsproj"
MODEL_PUSHER_S3_KEY = "model-registry"

Create S3 bucket
my-model-mlopsproj
us-east-1

Add S3 utility modules

aws_storage/

entity/s3_estimator.py

🧪 6. Model Evaluation & Model Pusher

Evaluate new model vs existing S3 model

If improved, push model to registry

Logs versioning + promotion flow

⚡ 7. Prediction Pipeline + FastAPI App

Build prediction_pipeline.py

Create app.py

Add static/ and templates/

Run locally:

python app.py


Endpoints:

/predict
/train

🐳 8. Docker + CI/CD Deployments
Dockerize the application

Create:

Dockerfile

.dockerignore

GitHub Actions workflow

Located at:

.github/workflows/aws.yaml

AWS ECR Setup

Repository:

vehicleproj

AWS EC2 Setup

Ubuntu 24.04

t2.medium

30GB storage

Allow HTTP/HTTPS

Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker

🛰️ 9. Connect GitHub → EC2 (Self-Hosted Runner)

GitHub → Settings → Actions → Runners → Add Runner

Run all commands on EC2:

Download

Configure

Run

Add repo secrets:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO

🚀 10. Deployment
Open port 5080 in EC2:
Custom TCP | 5080 | 0.0.0.0/0

Access app:
http://<EC2-IP>:5080


Training:

/training

🛠️ Tech Stack
Machine Learning & Python

Python 3.10

Pandas, NumPy, Sklearn

Custom pipelines + artifacts

Jinja2, FastAPI

Data Engineering

MongoDB Atlas

Data validation with schema

Data ingestion pipelines

Cloud & DevOps

AWS EC2

AWS S3

AWS ECR

IAM

Docker

GitHub Actions

Self-hosted Runner

📌 Pipeline Overview
Template → Setup → MongoDB → Ingestion → Validation → Transformation → 
Trainer → Evaluation → S3 → Docker → CI/CD → EC2 → FastAPI App