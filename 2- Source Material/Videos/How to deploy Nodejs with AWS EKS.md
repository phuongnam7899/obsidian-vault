Source link: 

Status: #source-eating 

---

# init nodejs project

- `npm init`
- `npm install express`
- Add code for express project
# Docker setup
- Create `dockerfile`:
```dockerfile
FROM node:16
WORKDIR /usr/src/app

COPY package.json .

RUN npm install

COPY . .

CMD ["node", "app.js"]
```
- Build image: `docker build -t express-eks`
- Try run container in local: `dockerr run -p 3000:3000 --it --rm --name express-eks-run express eks`
	- `-p 3000:3000`
	- `--it`
	- `--rm`
	- `--name`
# Push to ECR
- Go to ECR (Elastic Container Registry) in AWS
![[Pasted image 20241201144901.png]]
- Create new repository
![[Pasted image 20241201144931.png]]
- Open created repo
![[Pasted image 20241201145106.png]]
- View push command
![[Pasted image 20241201145132.png]]
- Follow the commands
	- `aws ecr get-login-password ...`
	- `docker build ...` again
	- `docker tag ...`
	- `docker push ...`: push the image to ECR
# Create K8S cluster
- Create cluster `eksctl create cluster --name new-cluster --region us-west-2`
- Check service: `kubectl get svc`
- Create k8s config file:
```yaml
...
spec:
	containers:
		- name: my-app
	      image: ...
	      resources: ...
	      ports: ..
...
```
- Apply config file: `kubectl apply -f k8s.yaml`
# Check
- Get pods: `kubectl get pod`
- Open container shell: `kubectl exed -it [pod-id] -- bash`
- List service again: `kubectl get svc`
- Try send request; `curl [service_url]`
# Deploy new version
- Create git repo for code
- Create a deploy script (deploy.sh):
```sh
LATEST_SHA=$(git rev-parse HEAD)

docker build -t express-eks:$LATEST_SHA .
docker tag express-eks:$LATEST_SHA [link_to_aws_ecr_repo]
docker push [link_to_aws_ecr_repo]

kubectl set image deployment/myapp myapp=[link_to_aws_ecr_repo] -n default

```
- run the deploy script
- Check the deployment:
	- `kubectl get deployment`
	- `kubectl describe deployment myapp`
- 

---