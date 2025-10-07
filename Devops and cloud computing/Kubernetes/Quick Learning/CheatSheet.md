+Perfect idea 💪 — here’s a **CKAD (Certified Kubernetes Application Developer) Command Cheat Sheet** to help you review and practice efficiently.

This cheat sheet focuses on **kubectl commands** and **concepts** you need to master for the **CKAD exam** — all grouped by topic.

---

## 🧠 **CKAD Command Cheat Sheet**

---

### 🧩 **Basic Commands**

| Task                              | Command                                      |
| --------------------------------- | -------------------------------------------- |
| View cluster info                 | `kubectl cluster-info`                       |
| List all resources in a namespace | `kubectl get all -n <namespace>`             |
| List all pods                     | `kubectl get pods`                           |
| Describe a resource               | `kubectl describe pod <pod-name>`            |
| Show current context              | `kubectl config current-context`             |
| Switch context                    | `kubectl config use-context <context>`       |
| View all contexts                 | `kubectl config get-contexts`                |
| Get detailed output in YAML/JSON  | `kubectl get pod <pod> -o yaml` or `-o json` |
| Run an interactive shell in a pod | `kubectl exec -it <pod> -- /bin/sh`          |

---

### 🚀 **Pods**

| Task                               | Command                                               |
| ---------------------------------- | ----------------------------------------------------- |
| Create a Pod (imperative)          | `kubectl run nginx --image=nginx`                     |
| Expose a Pod as a Service          | `kubectl expose pod nginx --port=80 --type=ClusterIP` |
| Create from YAML                   | `kubectl apply -f pod.yaml`                           |
| Delete Pod                         | `kubectl delete pod <pod>`                            |
| Get logs from a Pod                | `kubectl logs <pod>`                                  |
| Stream logs                        | `kubectl logs -f <pod>`                               |
| Get logs from a specific container | `kubectl logs <pod> -c <container>`                   |

---

### 🧱 **Deployments**

| Task                    | Command                                               |
| ----------------------- | ----------------------------------------------------- |
| Create Deployment       | `kubectl create deployment nginx --image=nginx`       |
| Scale Deployment        | `kubectl scale deployment nginx --replicas=3`         |
| Update image            | `kubectl set image deployment/nginx nginx=nginx:1.25` |
| Rollback Deployment     | `kubectl rollout undo deployment/nginx`               |
| Check rollout status    | `kubectl rollout status deployment/nginx`             |
| Edit Deployment live    | `kubectl edit deployment nginx`                       |
| View Deployment details | `kubectl describe deployment nginx`                   |

---

### ⚙️ **Services**

| Type          | Command Example                                                 |
| ------------- | --------------------------------------------------------------- |
| ClusterIP     | `kubectl expose pod nginx --port=80 --target-port=8080`         |
| NodePort      | `kubectl expose deployment nginx --port=80 --type=NodePort`     |
| LoadBalancer  | `kubectl expose deployment nginx --port=80 --type=LoadBalancer` |
| List Services | `kubectl get svc`                                               |

---

### 📦 **ConfigMaps & Secrets**

| Task                          | Command                                                                                     |            |
| ----------------------------- | ------------------------------------------------------------------------------------------- | ---------- |
| Create ConfigMap from literal | `kubectl create configmap app-config --from-literal=APP_MODE=prod`                          |            |
| Create ConfigMap from file    | `kubectl create configmap app-config --from-file=app.properties`                            |            |
| Get ConfigMaps                | `kubectl get configmap`                                                                     |            |
| Create Secret from literal    | `kubectl create secret generic db-secret --from-literal=USER=admin --from-literal=PWD=1234` |            |
| Decode Secret                 | `kubectl get secret db-secret -o jsonpath='{.data.PWD}'                                     | base64 -d` |
| View Secret YAML              | `kubectl get secret db-secret -o yaml`                                                      |            |

---

### 🧩 **Namespaces**

| Task                  | Command                                                |
| --------------------- | ------------------------------------------------------ |
| List namespaces       | `kubectl get ns`                                       |
| Create namespace      | `kubectl create ns dev`                                |
| Run pod in namespace  | `kubectl run nginx --image=nginx -n dev`               |
| Set default namespace | `kubectl config set-context --current --namespace=dev` |

---

### 🧰 **Probes & Resources**

| Task                    | Command                                              |
| ----------------------- | ---------------------------------------------------- |
| Liveness Probe example  | `kubectl explain pod.spec.containers.livenessProbe`  |
| Readiness Probe example | `kubectl explain pod.spec.containers.readinessProbe` |
| Resource limits         | `kubectl explain pod.spec.containers.resources`      |

---

### 💾 **Volumes & Persistent Volumes**

| Task         | Command                           |
| ------------ | --------------------------------- |
| Create PVC   | `kubectl apply -f pvc.yaml`       |
| Get PVCs     | `kubectl get pvc`                 |
| Describe PVC | `kubectl describe pvc <pvc-name>` |
| Get PVs      | `kubectl get pv`                  |

---

### 🔁 **Jobs & CronJobs**

| Task           | Command                                                                                      |
| -------------- | -------------------------------------------------------------------------------------------- |
| Create Job     | `kubectl create job hello-job --image=busybox -- echo "Hello CKAD"`                          |
| Create CronJob | `kubectl create cronjob hello-cron --image=busybox --schedule="*/1 * * * *" -- echo "Hello"` |
| Get Jobs       | `kubectl get jobs`                                                                           |
| Get CronJobs   | `kubectl get cronjobs`                                                                       |

---

### 🔍 **Debugging & Troubleshooting**

| Task                 | Command                                                    |
| -------------------- | ---------------------------------------------------------- |
| Get Pod logs         | `kubectl logs <pod>`                                       |
| Execute inside a Pod | `kubectl exec -it <pod> -- sh`                             |
| Get events           | `kubectl get events --sort-by=.metadata.creationTimestamp` |
| Describe Pod         | `kubectl describe pod <pod>`                               |
| Dry-run mode         | `kubectl apply -f pod.yaml --dry-run=client`               |
| Validate YAML        | `kubectl apply --dry-run=client -f <file>`                 |

---

### ⚡ **Imperative Shortcuts**

| Resource   | Command                                                           |
| ---------- | ----------------------------------------------------------------- |
| Pod        | `kubectl run mypod --image=nginx --restart=Never`                 |
| Deployment | `kubectl create deployment mydeploy --image=nginx`                |
| Service    | `kubectl expose deployment mydeploy --port=80 --type=NodePort`    |
| Namespace  | `kubectl create ns dev`                                           |
| ConfigMap  | `kubectl create configmap myconfig --from-literal=key=value`      |
| Secret     | `kubectl create secret generic mysecret --from-literal=key=value` |

---

### 🧾 **YAML Quick Tips**

Generate YAML without applying:

```bash
kubectl run nginx --image=nginx --dry-run=client -o yaml > pod.yaml
```

---

### 🧭 **Useful Aliases (time-saver for exam)**

```bash
alias k='kubectl'
alias kgp='kubectl get pods'
alias kga='kubectl get all'
alias kgn='kubectl get nodes'
alias kd='kubectl describe'
alias kaf='kubectl apply -f'
alias kdf='kubectl delete -f'
```

---

Would you like me to turn this cheat sheet into a **PDF printable version** (formatted for quick reference during CKAD practice)?
