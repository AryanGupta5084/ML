
# STUDENT PERFORMANCE PREDICTION

A machine learning web application built using Flask that predicts student performance based on various demographic and academic inputs. The project includes a full ML pipeline for data ingestion, transformation, training, and prediction, and is ready for deployment via Docker on AWS EC2 using GitHub Actions CI/CD.

---

## 🗂 Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Docker & AWS Deployment](#docker--aws-deployment)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)

---

## 📌 Introduction

This project implements an end-to-end machine learning pipeline that predicts outcomes based on student-related features. It uses Flask to serve a user-friendly web interface and supports containerized deployment via Docker. CI/CD is enabled using GitHub Actions, with deployment to AWS EC2 and model artifact handling via ECR.

---

## 🚀 Features

- Modular ML pipeline (`src/`)
- Flask-based web frontend
- Prediction from user input
- GitHub Actions CI/CD pipeline
- Docker containerization
- AWS EC2 deployment support
- Pretrained model artifacts

---

## 🧰 Tech Stack

- Python
- Flask
- Scikit-learn
- Pandas, NumPy
- Docker
- AWS EC2, ECR
- GitHub Actions

---

## 📁 Project Structure

```
MLPROJECT/
│
├── app.py / application.py       # Flask app (duplicate, consolidate recommended)
├── Dockerfile                    # Docker configuration
├── requirements.txt              # Python dependencies
├── setup.py                      # Installation metadata
├── templates/                    # HTML templates
├── notebook/                     # Jupyter notebooks (EDA/training)
├── artifacts/                    # Saved model and preprocessor
├── src/                          # Core ML pipeline
│   ├── components/
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   └── model_trainer.py
│   ├── pipeline/
│   │   ├── train_pipeline.py
│   │   └── predict_pipeline.py
│   ├── exception.py
│   ├── logger.py
│   └── utils.py
```

---

## ⚙️ Installation

```bash
# Clone the repository
git clone https://github.com/your-username/MLPROJECT.git
cd MLPROJECT

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the app
python app.py
```

---

## 🖥️ Usage

1. Open your browser at `http://localhost:5000`
2. Enter the following inputs:
   - Gender
   - Race/Ethnicity
   - Parental Level of Education
   - Lunch
   - Test Preparation Course
   - Reading and Writing Scores
3. Submit the form to get a prediction

---

## 🧪 Examples

| Input | Output |
|-------|--------|
| Gender: Female, Test prep: Completed, Reading: 88, Writing: 93 | ✅ High Score Prediction |
| Gender: Male, No test prep, Reading: 55, Writing: 60 | ⚠️ Low Score Prediction |

---

## 🚢 Docker & AWS Deployment

### ✅ Docker Build (on EC2)

```bash
# Optional: Update packages
sudo apt-get update -y
sudo apt-get upgrade

# Required: Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker

# Build Docker image
docker build -t mlproject .

# Run container
docker run -p 5000:5000 mlproject
```

### ⚙️ GitHub Actions Workflow

The project includes a workflow in `.github/workflows/main.yaml` for CI/CD. You must:

- Configure your EC2 instance as a **self-hosted GitHub Actions runner**
- Set GitHub Secrets:
  ```env
  AWS_ACCESS_KEY_ID=your-access-key
  AWS_SECRET_ACCESS_KEY=your-secret-key
  AWS_REGION=us-east-1
  AWS_ECR_LOGIN_URI=566373416292.dkr.ecr.ap-south-1.amazonaws.com
  ECR_REPOSITORY_NAME=simple-app
  ```

---

## 🧰 Troubleshooting

- **Model not loading?** Ensure `artifacts/model.pkl` and `artifacts/proprocessor.pkl` exist
- **Port in use?** Modify the `app.run()` port in `app.py`
- **Permission denied (Docker)?** Use `sudo` or ensure your user is in the `docker` group

---

## 👤 Contributors

- Aryan Gupta ([@aryangupta](mailto:ag5787842@gmail.com))

---
