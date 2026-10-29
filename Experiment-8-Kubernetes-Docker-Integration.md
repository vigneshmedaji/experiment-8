# Experiment 8: Integrate Kubernetes and Docker

## Aim
To understand and demonstrate the integration of Docker containers with Kubernetes for container orchestration and application management.

## Objectives
1. To understand Docker containerization and Kubernetes orchestration.
2. To learn how Kubernetes manages containerized applications.
3. To create a Kubernetes Deployment for a Docker image.
4. To expose an application using a Kubernetes Service.
5. To inspect and manage application pods.

## Software Requirements
- Docker
- Kubernetes
- kubectl command-line tool
- Minikube or another Kubernetes cluster
- Web browser

## Introduction
Docker is a containerization platform used to package applications and their dependencies into containers. Kubernetes is a container orchestration platform that manages the deployment, scaling, and operation of containerized applications. Docker images can be deployed and managed by Kubernetes, allowing applications to run reliably across a cluster.

## Procedure
1. Install Docker and start the Docker service.
2. Set up a Kubernetes environment using Minikube or another Kubernetes cluster.
3. Verify the cluster using `kubectl cluster-info`.
4. Create a Deployment using a Docker image.
5. Check the running pods.
6. Expose the Deployment using a Kubernetes Service.
7. Verify that the application is accessible.
8. Inspect the Deployment and Service status.

## Kubernetes Commands

- `docker --version` – Checks the Docker version.
- `kubectl version --client` – Displays the kubectl client version.
- `kubectl cluster-info` – Displays Kubernetes cluster information.
- `kubectl create deployment nginx --image=nginx` – Creates a Deployment using the Nginx image.
- `kubectl get deployments` – Lists Kubernetes Deployments.
- `kubectl get pods` – Lists the pods in the current namespace.
- `kubectl expose deployment nginx --type=NodePort --port=80` – Exposes the Deployment as a NodePort Service.
- `kubectl get services` – Lists Kubernetes Services.
- `kubectl describe deployment nginx` – Displays detailed Deployment information.
- `kubectl delete service nginx` – Deletes the Service named nginx.
- `kubectl delete deployment nginx` – Deletes the Deployment named nginx.

## Sample Kubernetes Deployment

Save the following configuration as `nginx-deployment.yaml`.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

Apply the configuration using:

```bash
kubectl apply -f nginx-deployment.yaml
kubectl get deployments
kubectl get pods
```

## Expected Output
- The Kubernetes cluster is accessible.
- The Nginx Deployment is created successfully.
- Two pod replicas are requested and should become available when the cluster has sufficient resources.
- The application can be exposed through a Kubernetes Service.

## Result
Studied the integration of Docker container images with Kubernetes and learned to create Deployments, manage pods, and expose applications through Services.

## Applications
- Container orchestration
- Application deployment
- Scaling containerized applications
- High availability
- DevOps automation
