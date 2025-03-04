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
├── Jenkinsfile                  # Jenkins pipeline script
├── README.md                    # Project documentation
├── build/                        # Docker build related files
│   └── Dockerfile                # Docker image build configuration
├── python-helm-chart/            # Helm charts for Kubernetes deployment
│   ├── Chart.yaml                # Helm chart metadata
│   ├── Chart.yaml:Zone.Identifier # Windows-specific file (ignore)
│   ├── charts/                   # Dependencies for the chart
│   ├── templates/                # Kubernetes YAML templates
│   │   ├── NOTES.txt             # Notes for Helm users
│   │   ├── _helpers.tpl          # Helper functions for templates
│   │   ├── deployment.yaml       # Kubernetes deployment definition
│   │   ├── hpa.yaml              # Horizontal Pod Autoscaler
│   │   ├── ingress.yaml          # Ingress controller definition
│   │   ├── secret.yaml           # Secrets configuration
│   │   ├── service.yaml          # Service definition
│   │   ├── serviceaccount.yaml   # Service account configuration
│   │   └── tests/                # Helm chart test files
│   │       └── test-connection.yaml # Test connection to the app
│   ├── values.yaml               # Helm values for app configuration
│   └── values.yaml:Zone.Identifier # Windows-specific file (ignore)
└── src/                          # Python application source code
    ├── app/                       # Application module
    │   ├── __init__.py            # Package initialization
    │   ├── __pycache/             # Cached Python files
    │   │   └── __init__.cpython-310.pyc # Python cache
    │   ├── apis.py                # API definitions
    │   ├── conftest.py            # Pytest configuration
    │   ├── static/                # Static files (CSS, JS, Images)
    │   ├── templates/             # HTML templates
    │   ├── tests/                 # Test files for the application
    │   └── views.py               # Flask views
    ├── requirements.txt           # Python dependencies
    └── run.py                     # Application entry point
```
# 🔥 Why This Project Matters?

- ✅ **End-to-End DevOps Workflow**: From CI/CD to production deployment.
- ✅ **Security-Focused Pipeline**: Integrated with SonarQube & Trivy for vulnerability scanning.
- ✅ **Fully Automated Kubernetes Deployment**: Using Helm for seamless orchestration.
- ✅ **Real-World AWS Infrastructure**: Leveraging Route 53 & ALB for scalable and reliable deployments.

---

## 📢 Share Your Thoughts!
If you find this project useful, give it a ⭐ on GitHub! 💙  

---

## 🤝 Connect with Me
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/balabadrasaikumar/)  

---

> “Automate everything and make deployments seamless! 🚀”
