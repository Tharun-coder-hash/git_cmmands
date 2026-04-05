This is your **Final Exam Cheat Sheet**. It contains every command required to move your code from a local folder to a running Kubernetes cluster with 2 replicas.

---

## 🛠️ 1. Git Commands (Local to GitHub)
Use these to initialize your project, handle the subfolder issue, and push to the cloud.

| Command | Purpose |
| :--- | :--- |
| `git clone <url>` | Download the repository to your computer. |
| `cd maven_app` | Enter the project directory. |
| `code .` | Open the project in VS Code for editing. |
| `git init` | Initialize a new Git repository (if not cloned). |
| `git add .` | Stage all changes (pom.xml, Dockerfile, etc.) for commit. |
| `git commit -m "Final Version"` | Save your changes locally with a message. |
| `git branch -M master` | Ensure you are on the `master` branch. |
| `git remote add origin <url>` | Link your local folder to GitHub (if not cloned). |
| `git push -u origin master` | **The Final Push:** Sends your code to GitHub. |
| `git pull origin master --rebase` | **Fix Error:** Run this if your push is "rejected." |

---

## 🐳 2. Docker Commands (Manual Testing)
Use these to build and test your container locally before Jenkins does it.

| Command | Purpose |
| :--- | :--- |
| `docker build -t string-processor .` | Build the image using the `Dockerfile` in the current folder. |
| `docker images` | List all images to verify `string-processor` exists. |
| `docker run -p 8080:8080 string-processor` | Run the container and map port 8080. |
| `docker ps` | See all running containers. |
| `docker stop <container_id>` | Stop the running application. |
| `docker rm $(docker ps -aq)` | **Cleanup:** Remove all stopped containers. |
| `docker rmi <image_id>` | Remove a specific image. |

---

## ☸️ 3. Kubernetes Commands (Deployment)
Use these to deploy your 2 replicas and verify they are healthy.

| Command | Purpose |
| :--- | :--- |
| `minikube start` | Start your local Kubernetes cluster. |
| `minikube docker-env` | **CRITICAL:** Connects your terminal to Minikube's Docker. |
| `kubectl apply -f k8s/deployment.yaml` | **The Deploy:** Creates the 2 pods from your YAML. |
| `kubectl get pods` | Check if your 2 replicas are "Running." |
| `kubectl get deployments` | Verify that `READY` shows `2/2`. |
| `kubectl describe pod <pod_name>` | **Debug:** Use this if a pod shows `Error`. |
| `kubectl logs <pod_name>` | See the Java console output inside the pod. |
| `kubectl delete -f k8s/deployment.yaml` | Remove the deployment from the cluster. |
| `kubectl expose deployment ...` | Create a Service to access the app via a URL. |

---

## 🚀 4. The "Final Exam" Flow
If you are in an exam, follow this exact sequence:

1.  **Clone/Edit:** `git clone` -> `cd` -> `code .`
2.  **Save Files:** Ensure `pom.xml`, `Dockerfile`, and `deployment.yaml` are saved.
3.  **Push:** `git add .` -> `git commit` -> `git push -u origin master`.
4.  **Jenkins:** Go to Jenkins UI -> **Build Now**.
5.  **Verify:** `kubectl get pods`.

### 🛑 What to do if an error occurs?
* **Git Rejected?** Run `git pull origin master --rebase`.
* **Docker COPY fail?** Ensure you ran `mvn clean package` in Jenkins first.
* **K8s ImagePullBackOff?** Ensure `imagePullPolicy: Never` is in your YAML and you ran the build after setting `minikube docker-env`.

# 🔑 Git Push using Personal Access Token (PAT)

## 📌 Step 1: Clone Repository
git clone https://github.com/Tharun-coder-hash/Agile_lab.git
cd Agile_lab

---

## 📌 Step 2: Add Files
git add .

---

## 📌 Step 3: Commit Changes
git commit -m "your message"

---

## 📌 Step 4: Push to GitHub
git push

---

## 🔐 Authentication (IMPORTANT)

When prompted:

Username: Tharun-coder-hash  
Password: <PASTE YOUR PAT TOKEN>

---

## ⚡ Alternative (No Prompt Method)

git remote set-url origin https://Tharun-coder-hash:<YOUR_TOKEN>@github.com/Tharun-coder-hash/Agile_lab.git
git push

---

## ⚠️ Important Notes

- Do NOT use your GitHub password
- Always use PAT instead
- Keep your token safe and private
- Token is case-sensitive
- Set expiry (recommended: 7 days)

---

## 🔥 Quick Cheat Sheet

git add .
git commit -m "lab"
git push


