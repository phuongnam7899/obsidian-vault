- Create application code
![[Pasted image 20241217084744.png]]
- Create `dockerfile`
```dockerfile
FROM node:22.2.0

WORKDIR /app

COPY company-review/package.json company-review/package-lock.json ./

RUN npm install

COPY company-review ./

RUN npm run build

EXPOSE 3000
  
CMD ["npm", "start"]
```

- Download `minikube` following this: https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
- Ensure Docker is using minikube's docker daemon with `minikube docker-env`
- Build the image with `docker build -t company-review-frontend -f company-review/Dockerfile .`
- Create `front-end-deployment.yaml`:
```yaml

# Frontend Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: company-review-frontend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: company-review-frontend
  template:
    metadata:
      labels:
        app: company-review-frontend
    spec:
      containers:
        - name: company-review-frontend
          image: company-review-frontend:latest
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 3000
---
# Frontend Service
apiVersion: v1
kind: Service
metadata:
  name: company-review-frontend
spec:
  type: ClusterIP
  ports:
    - port: 3000
      targetPort: 3000
  selector:
    app: company-review-frontend
---
# Backend Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: company-review-backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: company-review-backend
  template:
    metadata:
      labels:
        app: company-review-backend
    spec:
      containers:
        - name: company-review-backend
          image: company-review-backend:latest
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 3001
---
# Backend Service
apiVersion: v1
kind: Service
metadata:
  name: company-review-backend
spec:
  type: ClusterIP
  ports:
    - port: 3001
      targetPort: 3001
  selector:
    app: company-review-backend
# ---
# Ingress
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
    - http:
        paths:
          - pathType: Prefix
            path: /
            backend:
              service:
                name: company-review-frontend
                port:
                  number: 3000
          - pathType: Prefix
            path: /api
            backend:
              service:
                name: company-review-backend
                port:
                  number: 3001


```
- Ensure ingress controller running: `minikube addons enable ingress`
- Apply the yaml file with `minikube kubectl -- apply -f frontend-deployment.yaml`
- Verify created deployments, pods & ingress:
```sh
minikube kubectl -- get deployments
minikube kubectl -- get pods
minikube kubectl -- get ingress
```
- If using NodePort or Loadbalancer services, run `minikube ip` to expose services properly
- Get the cluster IP with `minikube ip` (get sth like `192.168.49.2`)
- Access the application with `(IP):(PORT)` (in this casew it's http://192.168.49.2:30001/)