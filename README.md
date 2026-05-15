import base64

# Function to encode local images to base64 for embedding in Markdown
def get_image_base64(path):
    try:
        with open(path, "rb") as image_file:
            return f"data:image/jpeg;base64,{base64.b64encode(image_file.read()).decode('utf-8')}"
    except:
        return ""

# Note: In a real scenario, the user would upload the images to GitHub and use those links.
# For this preview, I will create the content.

markdown_content = """# 🌐 Microservices Service Mesh with Linkerd & Kubernetes

![Service Mesh Banner](https://img.shields.io/badge/Service_Mesh-Linkerd-blueviolet?style=for-the-badge&logo=linkerd)
![Kubernetes](https://img.shields.io/badge/Kubernetes-v1.31-blue?style=for-the-badge&logo=kubernetes)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## 📖 Overview
This project demonstrates the implementation of a **Service Mesh (Linkerd)** within a **Kubernetes (Minikube)** cluster to manage, secure, and observe communication between 50+ microservices. It solves the "networking nightmare" of microservices by providing automatic observability, reliability, and security without changing application code.

---

## 🛠️ Tech Stack & Tools

### 💻 Operating Systems
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Debian](https://img.shields.io/badge/Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

### ☁️ Virtualization & Containers
![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=for-the-badge&logo=proxmox&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Minikube](https://img.shields.io/badge/Minikube-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

### 🛡️ Service Mesh & Networking
![Linkerd](https://img.shields.io/badge/Linkerd-blueviolet?style=for-the-badge&logo=linkerd&logoColor=white)
![Envoy Proxy](https://img.shields.io/badge/Envoy-635BFF?style=for-the-badge&logo=envoyproxy&logoColor=white)
![mTLS](https://img.shields.io/badge/Security-mTLS-green?style=for-the-badge)

---

## 🚀 Key Features Implemented

- **Observability**: Real-time traffic monitoring using Linkerd Viz.
- **Security (mTLS)**: Automatic mutual TLS encryption between all pods.
- **Traffic Management**: Ability to split traffic for Canary Deployments.
- **Circuit Breaking**: Preventing cascading failures across the mesh.

---

## 📊 Visual Proof of Concept

### 1. Topology Map (Service Graph)
The following graph shows how services (Web, Voting, Emoji) interact within the cluster, monitored in real-time.
*(Add your photo IMG_20260515_223652.jpg here)*

### 2. Live Health Metrics
Monitoring success rates and latency (P95/P99) across the entire namespace.
*(Add your photo IMG_20260515_223229.jpg here)*

---

## ⚙️ Installation Summary

```bash
# Start the Cluster
minikube start --driver=docker

# Install Linkerd
linkerd install --crds | kubectl apply -f -
linkerd install --set proxyInit.runAsRoot=true | kubectl apply -f -

# Deploy Demo App with Injection
curl -sL [https://run.linkerd.io/emojivoto.yml](https://run.linkerd.io/emojivoto.yml) | linkerd inject - | kubectl apply -f -
