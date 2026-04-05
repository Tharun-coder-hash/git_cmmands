# Final Exam Cheat Sheet

This contains all commands required to move your code from a local folder to a running Kubernetes cluster with 2 replicas.

---

## 1. Git Commands (Local to GitHub)

Use these to initialize your project, handle the subfolder issue, and push to the cloud.

| Command | Purpose |
|--------|--------|
| git clone <url> | Download the repository to your computer |
| cd maven_app | Enter the project directory |
| code . | Open the project in VS Code |
| git init | Initialize a new Git repository (if not cloned) |
| git add . | Stage all changes |
| git commit -m "Final Version" | Save changes locally |
| git branch -M master | Switch to master branch |
| git remote add origin <url> | Link local folder to GitHub |
| git push -u origin master | Push code to GitHub |
| git pull origin master --rebase | Fix push rejection |

---

## 2. Docker Commands (Manual Testing)

| Command | Purpose |
|--------|--------|
| docker build -t string-processor . | Build Docker image |
| docker images | List images |
| docker run -p 8080:8080 string-processor | Run container |
| docker ps | Show running containers |
| docker stop <container_id> | Stop container |
| docker rm $(docker ps -aq) | Remove all containers |
| docker rmi <image_id> | Remove image |

---

## 3. Kubernetes Commands (Deployment)

| Command | Purpose |
|--------|--------|
| minikube start | Start cluster |
| minikube docker-env | Connect to Minikube Docker |
| kubectl apply -f k8s/deployment.yaml | Deploy pods |
| kubectl get pods | Check pod status |
| kubectl get deployments | Verify replicas |
| kubectl describe pod <pod_name> | Debug pod |
| kubectl logs <pod_name> | View logs |
| kubectl delete -f k8s/deployment.yaml | Delete deployment |
| kubectl expose deployment ... | Expose service |

---

## 4. Final Exam Flow

1. git clone -> cd -> code .
2. Save all required files
3. git add . -> git commit -> git push -u origin master
4. Run Jenkins build
5. kubectl get pods

---

## Error Handling

- Git rejected: git pull origin master --rebase
- Docker COPY failed: run mvn clean package
- ImagePullBackOff: use imagePullPolicy: Never and rebuild

---

# Git Push using Personal Access Token (PAT)

## Step 1: Clone Repository
git clone https://github.com/Tharun-coder-hash/Agile_lab.git
cd Agile_lab

---

## Step 2: Add Files
git add .

---

## Step 3: Commit Changes
git commit -m "your message"

---

## Step 4: Push
git push

---

## Authentication

Username: Tharun-coder-hash  
Password: <PASTE YOUR PAT TOKEN>

---

## Alternative (No Prompt)

git remote set-url origin https://Tharun-coder-hash:<YOUR_TOKEN>@github.com/Tharun-coder-hash/Agile_lab.git
git push

---

## Important Notes

- Do not use GitHub password
- Use PAT instead
- Keep token private
- Token is case-sensitive
- Set expiry (recommended: 7 days)

---

## Quick Commands

git add .
git commit -m "lab"
git push
