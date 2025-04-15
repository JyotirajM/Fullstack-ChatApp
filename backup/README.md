# Full Stack ChatApp - DevOps Engineer Setup

[![GitHub Profile](https://img.shields.io/badge/GitHub-JyotirajM-purple?logo=github&style=flat)](https://github.com/JyotirajM)
![Docker Image](https://img.shields.io/github/forks/JyotirajM/Fullstack-ChatApp)

## 📝 **Introduction**

This repository contains a Full Stack Chat Application that is designed for scalability, maintainability, and high availability using modern DevOps practices and tools. The application includes real-time messaging, user authentication, and a modern UI built with **React** and **Node.js**.

## 🚀 **DevOps Setup**

As part of the DevOps lifecycle, this project implements CI/CD pipelines, containerization, orchestration, monitoring, and logging to ensure smooth deployment and high availability.

### 🛠️ **Tech Stack**
- **Backend**: Node.js, Express, MongoDB, Socket.io
- **Frontend**: React, TailwindCSS
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **CI/CD**: Jenkins (for automating builds and deployments)
- **Version Control**: Git/GitHub
- **Monitoring**: Prometheus
- **Logging**: ELK Stack (planned)
- **Cloud Deployment**: AWS (Planned)

## 🔧 **Tools and Technologies**
This project utilizes several DevOps tools to improve the application’s lifecycle and deployment.

### **Version Control**: 
- **Git**: Source code management using Git and GitHub for version control.
  
### **Continuous Integration / Continuous Deployment (CI/CD)**:
- **Jenkins**: For automating the build, test, and deployment process. This ensures that code changes are continuously integrated and deployed.

### **Containerization**:
- **Docker**: Used for containerizing both the backend and frontend applications for portability across environments.
  
### **Orchestration**:
- **Kubernetes**: Used to deploy, scale, and manage containerized applications across a cluster of machines. Kubernetes ensures the application's high availability and automatic scaling.

### **Monitoring & Logging**:
- **Prometheus**: Used for collecting metrics and monitoring the health of the application.
- **ELK Stack** (Planned): For centralized logging to monitor application logs in real-time.

---

## 🏗️ **Build and Run the Application**

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/JyotirajM/Fullstack-ChatApp.git
    ```

2. **Docker Setup**:
    - Navigate to the project directory:
      ```bash
      cd Fullstack-ChatApp
      ```

    - **Build & Run the Containers** using Docker Compose:
      ```bash
      docker-compose up -d --build
      ```

3. **Access the Application**:
    - Open your browser and go to [http://localhost](http://localhost) to access the application.

---

## 📜 **CI/CD Pipeline Configuration with Jenkins**

### **Jenkins Pipeline**

The **Jenkinsfile** contains the pipeline stages to automate the build, test, and deployment process.

#### Key Stages:
1. **Build**: This stage will compile the code and create Docker images for the frontend and backend applications.
2. **Test**: Automated unit and integration tests will be run on the code.
3. **Deploy**: Once tests pass, the Docker images are pushed to a Docker registry (e.g., Docker Hub) and then deployed to the cloud or a staging environment.

#### Jenkinsfile Example:

```groovy
pipeline {
    agent any
    environment {
        DOCKER_IMAGE_BACKEND = 'your_dockerhub_account/full-stack-backend'
        DOCKER_IMAGE_FRONTEND = 'your_dockerhub_account/full-stack-frontend'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker-compose build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }
        stage('Push Docker Images') {
            steps {
                script {
                    sh 'docker push $DOCKER_IMAGE_BACKEND'
                    sh 'docker push $DOCKER_IMAGE_FRONTEND'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh 'kubectl apply -f k8s/deployment.yml'
                    sh 'kubectl apply -f k8s/service.yml'
                }
            }
        }
    }
}
