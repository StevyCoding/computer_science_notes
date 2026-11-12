# 🧠 CKAD Command Cheat Sheet

This cheat sheet focuses on **kubectl commands** and **concepts** essential for the **CKAD exam**, all grouped by topic.

---

## 🧩 Basic Commands

| **Task**                          | **Command**                                  |
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

## 🚀 Pods

| **Task**                           | **Command**                                           |
| ---------------------------------- | ----------------------------------------------------- |
| Create a Pod (imperative)          | `kubectl run nginx --image=nginx`                     |
| Expose a Pod as a Service          | `kubectl expose pod nginx --port=80 --type=ClusterIP` |
| Create from YAML                   | `kubectl apply -f pod.yaml`                           |
| Delete Pod                         | `kubectl delete pod <pod>`                            |
| Get logs from a Pod                | `kubectl logs <pod>`                                  |
| Stream logs                        | `kubectl logs -f <pod>`                               |
| Get logs from a specific container | `kubectl logs <pod> -c <container>`                   |

---

## 🏷️ Labels

| **Task**                                                                | **Command**                                                                                                                                                |
| ----------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Show label for a resource                                               | `kubectl get <resource> --show-labels`                                                                                                                     |
| Create labels on a pod                                                  | `kubectl run nginx --image=nginx --labels=app=v1`                                                                                                          |
| Change label of a resource                                              | `kubectl label <resource> <resourceName> app=v2 --overwrite`<br>`kubectl edit <resource> <resourceName>`                                                   |
| label value of resources                                                | `kubectl get <resource> -L app`<br>`kubectl get <resource> --label-column=app  `                                                                           |
| Get only  pod with  label with specific value                           | `kubectl get po -l app=v2`<br>`kubectl get po -l '<labelName> in (value)'`<br>`kubectl get po --selector=<labelName>=value`<br>                            |
| Get 'app=v2' and not 'tier=frontend' pods                               | `kubectl get po -l app=v2,tier!=frontend`<br>`kubectl get po -l 'app in (v2), tier notin (frontend)'`<br>`kubectl get po --selector=app=v2,tier!=frontend` |
| Add a new label tier=web to all pods having 'app=v2' or 'app=v1' labels | `kubectl label po -l "app in(v1,v2)" tier=web`                                                                                                             |
| Remove the 'app' label from the pods we create before                   | `kubectl label po nginx{1..3} app-`                                                                                                                        |



---
## 🗒️ Annotation

| **Task**                                                                       | **Command**                                                    |
| ------------------------------------------------------------------------------ | -------------------------------------------------------------- |
| kubectl annotate po -l "app=v2" owner=marketing                                | `kubectl annotation -l 'app=v1' owner=marketing`               |
| Annotate pods nginx1, nginx2, nginx3 with "description='my description'" value | `kubectl annotate po nginx{1--3} description='my description'` |
| check annotation for pod nginx1                                                | `kubectl annotate pod nginx1 --list`                           |
| Remove the annotation for these three pods                                     | `kubectl annotate po nginx{1..3} description- owener-`         |

---

## 🧱 Deployments

| **Task**                | **Command**                                           |
| ----------------------- | ----------------------------------------------------- |
| Create Deployment       | `kubectl create deployment nginx --image=nginx`       |
| Scale Deployment        | `kubectl scale deployment nginx --replicas=3`         |
| Update image            | `kubectl set image deployment/nginx nginx=nginx:1.25` |
| Rollback Deployment     | `kubectl rollout undo deployment/nginx`               |
| Check rollout status    | `kubectl rollout status deployment/nginx`             |
| Edit Deployment live    | `kubectl edit deployment nginx`                       |
| View Deployment details | `kubectl describe deployment nginx`                   |
|                         |                                                       |

---

## ⚙️ Services

| **Type**      | Command **Example**                                             |
| ------------- | --------------------------------------------------------------- |
| ClusterIP     | `kubectl expose pod nginx --port=80 --target-port=8080`         |
| NodePort      | `kubectl expose deployment nginx --port=80 --type=NodePort`     |
| LoadBalancer  | `kubectl expose deployment nginx --port=80 --type=LoadBalancer` |
| List Services | `kubectl get svc`                                               |

---

## 📦 ConfigMaps & Secrets

| **Task**                      | **Command**                                                        |
| ----------------------------- | ------------------------------------------------------------------ |
| Create ConfigMap from literal | `kubectl create configmap app-config --from-literal=APP_MODE=prod` |
| Create ConfigMap from file    | `kubectl create configmap app-config --from-file=app.properties`   |
| Get ConfigMaps                | `kubectl get cm`                                                   |
| Edit ConfigMap                | `kubectl edit cm <configmap>`                                      |
| Create Secret from literal    | `kubectl create secret generic mysecret --from-literal=key=value`  |
| Get Secrets                   | `kubectl get secrets`                                              |
| Edit Secret                   | `kubectl edit secret <secret>`                                     |
|                               |                                                                    |

---

## ⚡ Imperative Shortcuts

| **Resource** | **Command**                                                       |
| ------------ | ----------------------------------------------------------------- |
| Pod          | `kubectl run mypod --image=nginx --restart=Never`                 |
| Deployment   | `kubectl create deployment mydeploy --image=nginx`                |
| Service      | `kubectl expose deployment mydeploy --port=80 --type=NodePort`    |
| Namespace    | `kubectl create ns dev`                                           |
| ConfigMap    | `kubectl create configmap myconfig --from-literal=key=value`      |
| Secret       | `kubectl create secret generic mysecret --from-literal=key=value` |
