# 🚀 **DevOps Real-time Project: Python Application Deployment on Kubernetes**

In this **real-time DevOps project**, I demonstrate how to **deploy a Python application** using modern DevOps tools and AWS-managed Kubernetes (Kops).  
This project covers **CI/CD automation, containerization, security scanning, and Kubernetes deployment with Helm**.  

---

## 🛠️ **Tech Stack & Tools Used**  

| Tool / Service   | Purpose |
|-----------------|----------|
| **GitHub** ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white) | Code repository |
| **Jenkins** ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white) | CI/CD pipeline automation |
| **SonarQube** ![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat-square&logo=sonarqube&logoColor=white) | Code quality and security scanning |
| **Pytest** 🧪 | Unit testing for the Python application |
| **Trivy** ![Trivy](https://img.shields.io/badge/Trivy-00979D?style=flat-square&logo=trivy&logoColor=white) | Container security scanning |
| **Docker** ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) | Containerization of the application |
| **Helm** ![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white) | Kubernetes package manager |
| **Kops** ⛵ | Kubernetes cluster management in AWS |
| **AWS Route 53 & ALB Ingress** 🌐 | Domain and Load Balancing |

---

## ⚙️ **CI/CD Pipeline Flow**  

1. **Code Commit**: Developers push code to **GitHub**  
2. **Jenkins Pipeline**:
   - **Checkout Code** from GitHub  
   - **SonarQube Scan** for code quality  
   - **Security Scans** with **Trivy** and **OWASP ZAP**  
   - **Unit Tests** using **Pytest**  
   - **Build & Push Docker Image** to a **private Docker repository**  
3. **Kubernetes Deployment**:  
   - **Helm update** with new image version  
   - **Deploy application on Kops-managed AWS cluster**  
   - **Configure Ingress with AWS ALB & Route 53** for external access  

---

## 🛳️ **Kubernetes Deployment Process**  

1. **Deploy NGINX Ingress Controller** via Helm  
2. **Use Helm Charts** to deploy application  
3. **Route traffic via AWS ALB Ingress Controller**  
4. **Update Helm values.yaml dynamically** after every image push  
5. **Access the application via domain configured in Route 53**  

---

## 📂 **Project Structure**  

```bash
├── jenkinsfile                # Jenkins pipeline script
├── helm/                      # Helm charts for Kubernetes deployment
│   ├── templates/             # Deployment, Service, Ingress YAMLs
│   ├── values.yaml            # Helm values for app configuration
├── app/                       # Python application source code
├── Dockerfile                 # Docker image build configuration
└── README.md                  # Project documentation
