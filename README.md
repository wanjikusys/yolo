E-Commerce Application Kubernetes Deployment
This guide explains how to deploy an e-commerce application stack to a Google Kubernetes Engine (GKE) cluster. The application consists of:

A MongoDB database (with persistent storage)
A Backend API (Node.js)
A Frontend UI (React)

The application is exposed to the internet via a Kubernetes LoadBalancer service, accessible at:
http://http://35.232.135.122
 Prerequisites
Before you begin, ensure you have:

A Google Cloud account
gcloud CLI installed and authenticated
kubectl installed
Docker installed (for building and pushing images)

 Project Structure
├── manifests/
│   ├── mongodb.yaml
│   ├── mongo-service.yaml
│   ├── mongo-volume.yaml
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   └── frontend-service.yaml
├── e-commerce-backend/
├── e-commerce-frontend/
└── README.md

🚀 Deploy the App
1. Create MongoDB with Persistent Volume
kubectl apply -f manifests/mongo-volume.yaml
kubectl apply -f manifests/mongo-deployment.yaml
kubectl apply -f manifests/mongo-service.yaml

2. Deploy the E-Commerce Backend
kubectl apply -f manifests/backend-deployment.yaml
kubectl apply -f manifests/backend-service.yaml

3. Deploy the E-Commerce Frontend
kubectl apply -f manifests/frontend-deployment.yaml
kubectl apply -f manifests/frontend-service.yaml

🌐 Accessing the App
Once the frontend service is deployed, GKE provisions a LoadBalancer with an external IP. To find the external IP:
kubectl get svc frontend-service

📍 Access the frontend at:
http://http://35.232.135.122
🛠️ Features Implemented

MongoDB: Persistent storage with a Kubernetes PersistentVolume.
Backend: Node.js API handling product management and MongoDB interactions.
Frontend: React-based UI for browsing and adding products.
Networking: Kubernetes services for inter-component communication and a LoadBalancer for external access.

✅ Testing the Application

Navigate to
Frontend: http://localhost:3000
Backend API: http://localhost:5000
Use the "Add Product" feature to test functionality.
View products in the store section.

🛠️ Troubleshooting
If you encounter issues:

Check pod status: kubectl get pods
View pod logs: kubectl logs <pod-name>
Describe services: kubectl describe svc <service-name>
Verify external IP: kubectl get svc frontend-service

