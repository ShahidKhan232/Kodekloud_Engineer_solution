# Setup Kubernetes Namespaces and PODs

The Nautilus DevOps team is planning to deploy some microservices on the Kubernetes platform. The team has already set up a Kubernetes cluster and now they want to set up some namespaces, deployments, etc.

## Requirements
- Create a namespace named `dev`.
- Deploy a pod within the `dev` namespace.
  - Name the pod `dev-nginx-pod`.
  - Use the `nginx` image with the latest tag (`nginx:latest`).

> Note: The `kubectl` utility on `jump_host` is configured to operate with the Kubernetes cluster.

# Solution

## Requirement
- Create a namespace named **dev**
- Deploy a Pod inside this namespace
- Pod name: **dev-nginx-pod**
- Image: **nginx:latest**
- `kubectl` is already configured on `jump_host`

---

## Step 1: Create the Namespace

```bash
kubectl create namespace dev
```
Verify:
```
kubectl get namespaces
```

## Step 2: Create the Pod in the dev Namespace

Run the following command to create the pod directly:

```
kubectl run dev-nginx-pod \
  --image=nginx:latest \
  --namespace=dev \
  --restart=Never
```
## Step 3: Verify the Pod

Check the pod status in the dev namespace:

```
kubectl get pods -n dev
```
