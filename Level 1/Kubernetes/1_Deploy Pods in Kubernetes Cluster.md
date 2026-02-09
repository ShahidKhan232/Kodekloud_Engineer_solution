# Deploy Pods in Kubernetes Cluster

The Nautilus DevOps team is diving into Kubernetes for application management. One team member has a task to create a pod according to the details below:

## Task Details

- Create a pod named `pod-httpd` using the `httpd` image with the latest tag. Ensure to specify the tag as `httpd:latest`.
- Set the app label to `httpd_app`, and name the container as `httpd-container`.

> Note: The `kubectl` utility on `jump_host` is configured to operate with the Kubernetes cluster.


---

# Solution

### 1️⃣ Create the manifest file

```
vi pod-httpd.yaml
```

### 2️⃣ Add the following content

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
```

### 3️⃣ Apply the pod

```
kubectl apply -f pod-httpd.yaml
```