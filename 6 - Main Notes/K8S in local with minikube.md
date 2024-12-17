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
- Create deployment with `minikube kubectl -- create deployment company-review-frontend --image=company-review-frontend`
- 