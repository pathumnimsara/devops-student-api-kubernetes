# Student API on Kubernetes

A DevOps learning project deploying a Node.js Student REST API and MongoDB on Kubernetes using Docker Desktop.

## Kubernetes Features

- Student API with 3 replicas
- MongoDB Deployment and ClusterIP Service
- NodePort service on port 30001
- ConfigMap and Kubernetes Secret references
- Readiness and liveness probes
- CPU and memory requests and limits
- Metrics Server monitoring
- Self-healing tested by deleting a Pod and observing its replacement

## Technologies

- Node.js and Express
- MongoDB
- Docker and Docker Hub
- Kubernetes and kubectl
- Git and GitHub

## Deploy

Run from the repository root:

```powershell
kubectl apply -f k8s/configmap.yaml
kubectl apply -f k8s/mongodb.yaml
kubectl apply -f k8s/student-api.yaml
```

The `student-api-secret` Secret must exist with the required `DEMO_TOKEN` key before deploying the API.

## Verify and Monitor

```powershell
kubectl get pods
kubectl get deployments
kubectl get services
kubectl rollout status deployment/student-api
kubectl top pods
kubectl top nodes
```

## Access the API

http://localhost:30001/

Expected response:

```json
{"message":"Student API is running!"}
```

## Docker Image

`pathumnimsara/student-api:latest`

Docker Hub: https://hub.docker.com/u/pathumnimsara

## Notes

This project runs locally on Docker Desktop Kubernetes. The local Metrics Server may require `--kubelet-insecure-tls` to work around a certificate issue. Do not use this workaround in production.

Never commit real credentials or API keys.

## Author

Pathum Nimesh Nimsara

GitHub: https://github.com/pathumnimsara
