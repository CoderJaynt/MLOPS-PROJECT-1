<h1 align="center">🏨 Hotel Reservation Cancellation Prediction</h1>

<p align="center">
<b>End-to-End Production MLOps Pipeline using GCP, Docker & Jenkins</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Machine%20Learning-LightGBM-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/MLOps-GCP-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/CI/CD-Jenkins-red?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Container-Docker-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Registry-GCR-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Deployment-Cloud%20Run-black?style=for-the-badge"/>
</p>

---

# 📌 Project Overview

This project predicts whether a hotel customer will cancel their reservation based on booking details.

The goal of this project is not just Machine Learning —  
but building a **complete production-level MLOps pipeline**.

Users provide booking details → Model predicts → System deployed on Google Cloud.

---

# 🧠 Problem Statement

Hotels lose significant revenue due to booking cancellations.

We built a classification system that predicts:

> **Will the customer cancel the reservation?**
>
> - `0` → Not Cancelled  
> - `1` → Cancelled  

---

# 📥 Model Input Features

| Feature | Description |
|----------|-------------|
| lead_time | Days between booking and arrival |
| no_of_special_requests | Number of special requests |
| avg_price_per_room | Average room price |
| arrival_month | Month of arrival |
| arrival_date | Date of arrival |
| market_segment_type | Market segment type |
| no_of_week_nights | Weekday nights stayed |
| no_of_weekend_nights | Weekend nights stayed |
| room_type_reserved | Reserved room type |
| type_of_meal_plan | Selected meal plan |

---

---

# 🏗️ System Architecture

🧑‍💻 **User**  
⬇  
🌐 **Flask API**  
⬇  
🐳 **Docker Container**  
⬇  
☁️ **Google Cloud Run**  
⬇  
🤖 **LightGBM Model**  
⬇  
📊 **Prediction Output**

---

# 🔁 MLOps CI/CD Workflow

🔄 **Step 1 – Developer Push Code (GitHub)**  
⬇  
🧪 **Step 2 – Jenkins Pipeline Triggered**  
⬇  
📦 **Step 3 – Create Virtual Environment**  
⬇  
📚 **Step 4 – Install Dependencies**  
⬇  
🧠 **Step 5 – Train Model + Log MLflow**  
⬇  
🐳 **Step 6 – Build Docker Image**  
⬇  
📦 **Step 7 – Push Image to GCR**  
⬇  
☁️ **Step 8 – Deploy to Cloud Run**  
⬇  
🚀 **Live Public Endpoint Generated**

---
## 🔁 CI/CD Stages Breakdown
### 1️⃣ Jenkins Setup

Jenkins runs inside Docker (DinD)

GitHub integrated via credentials

GCP Service Account authentication configured

### 2️⃣ GitHub Integration

Pipeline auto-triggers on code push

Jenkinsfile defines full CI/CD steps

Secure SCM checkout

### 3️⃣ Virtual Environment Setup
python -m venv venv
source venv/bin/activate
pip install -e .

Ensures:

Dependency isolation

Clean builds

Reproducibility

### 4️⃣ Model Training & Experiment Tracking

#### Algorithm: LightGBM

#### Hyperparameter tuning: RandomizedSearchCV

#### Experiment tracking: MLflow

### Metrics Logged:

* Accuracy

* Precision

* Recall

* F1 Score

mlflow.set_tracking_uri("file:./mlruns")
mlflow.set_experiment("mlops-project")
### 5️⃣ Dockerization
#### FROM python:slim
#### WORKDIR /app
#### COPY . .
#### RUN pip install --no-cache-dir -e .
#### RUN python -m pipeline.training_pipeline

### Purpose:

* Containerized training

* Portable deployment

* Reproducible environment

### 6️⃣ Push Image to Google Container Registry (GCR)
#### gcloud auth activate-service-account --key-file=$GOOGLE_APPLICATION_CREDENTIALS
#### gcloud config set project $GCP_PROJECT
#### gcloud auth configure-docker

docker build -t gcr.io/$GCP_PROJECT/ml-project:latest .
docker push gcr.io/$GCP_PROJECT/ml-project:latest
### 7️⃣ Deploy to Google Cloud Run
* gcloud run deploy ml-project \
####  --image gcr.io/$GCP_PROJECT/ml-project:latest \
####  --platform managed \
####  --region asia-south1 \
####  --allow-unauthenticated

### Features:

* Serverless

* Auto-scaling

* Secure

* Public HTTPS endpoint

### ☁️ Cloud Services Used
* Service	Purpose
* GCP Bucket	Data Ingestion
* Jenkins	CI/CD Automation
* Docker	Containerization
* GCR	Docker Image Storage
* Cloud Run	Deployment
* MLflow	Experiment Tracking

## 📂 Project Structure

```mermaid
flowchart TB
    A[MLOPS-PROJECT-1]

    A --> B[config]
    A --> C[pipeline]
    A --> D[src]
    A --> E[utils]
    A --> F[Dockerfile]
    A --> G[Jenkinsfile]
    A --> H[requirements.txt]
    A --> I[README.md]
```

🚀 Fully Automated Flow
🎯 What This Project Demonstrates

✔ End-to-End MLOps Pipeline
✔ CI/CD Automation
✔ Model Lifecycle Management
✔ Cloud-Native Deployment
✔ Dockerized ML Workflow
✔ Experiment Tracking with MLflow
✔ Production-Grade Infrastructure

👨‍💻 Author

Jayant Yadav
B.Tech 
MLOps | Machine Learning | Cloud

<p > ⭐ If you like this project, consider giving it a star! </p> 


