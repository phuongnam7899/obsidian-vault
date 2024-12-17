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
apiVersion: v1
kind: Service
metadata:
  name: company-review-frontend
spec:
  type: NodePort
  ports:
    - port: 3000
      targetPort: 3000
      nodePort: 30001
  selector:
    app: company-review-frontend

```
- Apply the yaml file with `minikube kubectl -- apply -f frontend-deployment.yaml`
- Verify created deployments and pods:
```sh
minikube kubectl -- get deployments
minikube kubectl -- get pods
```
- Get the cluster IP with `minikube ip` (get sth like `192.168.49.2`)
- Access the application with `(IP):(PORT)` (in this casew it's http://192.168.49.2:30001/)