# Movie App with Full CI/CD and Kubernetes

## 🧾 Project Overview

This project demonstrates a complete microservice-based application using a React frontend and Python Flask backend deployed via Docker, Kubernetes (EKS), and CI/CD pipelines through GitHub Actions.

---

## 🛠 Technologies Used

- React, Flask
- Docker
- AWS EKS (Elastic Kubernetes Service)
- GitHub Actions
- Amazon ECR (Elastic Container Registry)
- Kustomize

---

## 🚀 Live Application

- **Frontend URL**: [Movie List Frontend](http://aac2ebe128db64df6ae87b1e2a2fbc90-1777867250.us-east-1.elb.amazonaws.com)
- **Backend API (Movie List)**: [Movie API](http://a679460dcf66a40e486c661da3f8665f-1449950342.us-east-1.elb.amazonaws.com/movies)

---

## 🔁 CI/CD Pipelines

### ✅ Frontend Continuous Integration (`frontend-ci.yaml`)
- Trigger: Pull Requests to `main`
- Jobs:
  - `lint` – Checks code formatting
  - `test` – Runs unit tests
  - `build` – Docker build of frontend image using `REACT_APP_MOVIE_API_URL`
- Status: **Passing**

### ✅ Backend Continuous Integration (`backend-ci.yaml`)
- Trigger: Pull Requests to `main`
- Jobs:
  - `lint` – Runs `flake8` on Python code
  - `test` – Executes test suite with `pipenv`
  - `build` – Docker build of backend image
- Status: **Passing**

### ✅ Frontend Continuous Deployment (`frontend-cd.yaml`)
- Trigger: Push to `main`
- Actions:
  - Runs Lint/Test/Build
  - Logs into ECR
  - Pushes Docker image to ECR
  - Deploys to EKS using `kubectl`
- Status: **Passing**

### ✅ Backend Continuous Deployment (`backend-cd.yaml`)
- Trigger: Push to `main`
- Actions:
  - Lint/Test/Build
  - ECR login & push
  - Kustomize updates
  - Kubernetes deployment
- Status: **Passing**

---

## 🧪 How to Test

1. **Frontend**:
   - Navigate to the [frontend URL](http://aac2ebe128db64df6ae87b1e2a2fbc90-1777867250.us-east-1.elb.amazonaws.com)
   - Verify the list of movies loads successfully.

2. **Backend**:
   - Open [backend endpoint](http://a679460dcf66a40e486c661da3f8665f-1449950342.us-east-1.elb.amazonaws.com/movies)
   - Should return JSON with movies list.

---

## 📁 Folder Structure

