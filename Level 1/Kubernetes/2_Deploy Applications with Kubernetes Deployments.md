# Deploy Applications with Kubernetes Deployments

The Nautilus DevOps team is exploring Kubernetes for application management. One team member needs to create a deployment with the following details:

## Deployment Details
- **Name:** nginx
- **Application:** nginx
- **Image:** nginx:latest (ensure to specify the tag)

> Note: The `kubectl` utility on `jump_host` is configured to interact with the Kubernetes cluster.

# Solution

### 1️⃣ Create the deployment manifest

``` 
vi nginx-deployment.yaml
```

### 2️⃣ Add the following content

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx-container
          image: nginx:latest
```

### 3️⃣ Apply the deployment

```
kubectl apply -f nginx-deployment.yaml
```