# CKA Mock Exam — Training Practice

This is an **original practice exam**, not leaked or official CKA content. It is modeled on the real CKA format: **2 hours**, command-line, performance-based Kubernetes tasks. The official CKA domains are: **Cluster Architecture / Installation / Configuration 25%**, **Workloads & Scheduling 15%**, **Services & Networking 20%**, **Storage 10%**, **Troubleshooting 30%**. The Linux Foundation FAQ currently lists the CKA exam environment as **Kubernetes v1.35**, while the CKA page says the environment tracks recent Kubernetes minor versions within roughly 4–8 weeks. ([CNCF][1]) ([Linux Foundation Documentation][2])

Passing score in the real CKA is **66%**. For this practice exam, aim for **75%+** before booking the real exam. ([Linux Foundation Documentation][2])

---

# CKA Mock Exam A

**Time:** 2 hours
**Total:** 100 points
**Allowed docs:** Kubernetes docs, Kubernetes blog, Helm docs, like the real exam environment. ([Linux Foundation Documentation][2])

Use this setup before starting:

```bash
alias k=kubectl
export do="--dry-run=client -o yaml"
export now="--force --grace-period=0"
```

Always check context and namespace before each question:

```bash
k config current-context
k config get-contexts
```

---

## Section 1 — Cluster Architecture, Installation & Configuration — 25 pts

### Task 1 — RBAC for a ServiceAccount — 5 pts

Create a namespace:

```bash
security
```

Create a ServiceAccount:

```bash
pod-reader
```

In namespace `security`, give this ServiceAccount permission to:

```text
get, list, watch pods
```

Only inside the `security` namespace.

Validate with:

```bash
k auth can-i list pods \
  --as system:serviceaccount:security:pod-reader \
  -n security
```

Expected result:

```text
yes
```

---

### Task 2 — Static Pod — 5 pts

On the control plane node, create a static Pod named:

```text
static-web
```

Image:

```text
nginx:1.27
```

It must be managed by kubelet using the static Pod manifest directory.

Validate:

```bash
k get pods -A | grep static-web
```

---

### Task 3 — Helm install — 5 pts

Using Helm, install an `nginx` chart into namespace:

```text
helm-apps
```

Release name:

```text
webserver
```

Use any public chart already available in your lab environment, or add the Bitnami repo if internet is available.

Validate:

```bash
helm list -n helm-apps
k get pods -n helm-apps
```

---

### Task 4 — Kustomize patch — 5 pts

Create a Kustomize app in `/tmp/kustom-web`.

Base Deployment:

```text
name: kustom-nginx
image: nginx:1.27
replicas: 1
```

Patch it so the final rendered Deployment has:

```text
replicas: 3
```

Apply it to namespace:

```text
kustom-lab
```

Validate:

```bash
k get deploy -n kustom-lab kustom-nginx
```

---

### Task 5 — CRD discovery — 5 pts

List all available API resources in the cluster and save the output to:

```text
/tmp/api-resources.txt
```

Then find whether the cluster has any CRDs installed.

Save the CRD list to:

```text
/tmp/crds.txt
```

Validate:

```bash
cat /tmp/api-resources.txt
cat /tmp/crds.txt
```

---

## Section 2 — Workloads & Scheduling — 15 pts

### Task 6 — Deployment with resources — 5 pts

Create namespace:

```text
apps
```

Create a Deployment:

```text
name: frontend
image: nginx:1.27
replicas: 3
```

Each container must have:

```yaml
requests:
  cpu: 100m
  memory: 128Mi
limits:
  cpu: 500m
  memory: 256Mi
```

Validate:

```bash
k get deploy -n apps frontend
k describe pod -n apps -l app=frontend
```

---

### Task 7 — Rolling update and rollback — 4 pts

Update Deployment `frontend` in namespace `apps` from:

```text
nginx:1.27
```

to:

```text
nginx:1.28
```

Then rollback to the previous version.

Validate:

```bash
k rollout history deploy/frontend -n apps
k describe deploy frontend -n apps | grep Image
```

---

### Task 8 — Scheduling with nodeSelector — 3 pts

Label one worker node:

```text
disk=ssd
```

Create a Pod:

```text
name: scheduled-pod
namespace: apps
image: busybox:1.36
command: sleep 3600
```

The Pod must run only on nodes with:

```text
disk=ssd
```

Validate:

```bash
k get pod -n apps scheduled-pod -o wide
```

---

### Task 9 — Taint and toleration — 3 pts

Taint one worker node:

```text
dedicated=training:NoSchedule
```

Create a Pod:

```text
name: tolerant-pod
namespace: apps
image: nginx:1.27
```

The Pod must tolerate the taint.

Validate:

```bash
k get pod -n apps tolerant-pod -o wide
```

---

## Section 3 — Services & Networking — 20 pts

### Task 10 — ClusterIP Service — 4 pts

Expose Deployment `frontend` in namespace `apps` with a Service:

```text
name: frontend-svc
type: ClusterIP
port: 80
targetPort: 80
```

Validate from a temporary Pod:

```bash
k run test-curl -n apps --image=curlimages/curl -it --rm --restart=Never -- curl http://frontend-svc
```

---

### Task 11 — Fix broken Service selector — 4 pts

Create a Service named:

```text
broken-svc
```

Namespace:

```text
apps
```

It should expose the `frontend` Deployment on port `80`, but its selector is currently wrong.

Fix the selector so the Service has valid endpoints.

Validate:

```bash
k get endpoints -n apps broken-svc
```

Expected: endpoints should not be empty.

---

### Task 12 — NetworkPolicy — 5 pts

In namespace `apps`, create a NetworkPolicy named:

```text
allow-curl-to-frontend
```

Requirements:

Only Pods with label:

```text
role=curl
```

can access Pods with label:

```text
app=frontend
```

on TCP port `80`.

All other ingress traffic to `frontend` should be denied.

Validate with two test Pods:

```text
allowed pod: label role=curl
blocked pod: no label
```

---

### Task 13 — Ingress or Gateway API — 4 pts

Create an HTTP route to expose `frontend-svc` with:

```text
host: frontend.local
path: /
service: frontend-svc
port: 80
```

Use either `Ingress` or Gateway API depending on what is installed in your cluster.

Validate:

```bash
k get ingress -A
# or
k get gateway,httproute -A
```

---

### Task 14 — CoreDNS troubleshooting — 3 pts

Check whether CoreDNS is running correctly.

Save the CoreDNS Pod status to:

```text
/tmp/coredns-status.txt
```

Save CoreDNS logs to:

```text
/tmp/coredns-logs.txt
```

Validate:

```bash
cat /tmp/coredns-status.txt
cat /tmp/coredns-logs.txt
```

---

## Section 4 — Storage — 10 pts

### Task 15 — PV, PVC, and Pod mount — 10 pts

Create a PersistentVolume:

```text
name: pv-training
capacity: 1Gi
accessMode: ReadWriteOnce
hostPath: /mnt/data-training
reclaimPolicy: Retain
```

Create a PVC:

```text
name: pvc-training
namespace: apps
request: 500Mi
accessMode: ReadWriteOnce
```

Create a Pod:

```text
name: storage-pod
namespace: apps
image: busybox:1.36
command: sleep 3600
```

Mount the PVC at:

```text
/data
```

Validate:

```bash
k get pv
k get pvc -n apps
k exec -n apps storage-pod -- sh -c "echo CKA > /data/test.txt && cat /data/test.txt"
```

---

## Section 5 — Troubleshooting — 30 pts

### Task 16 — Fix ImagePullBackOff — 5 pts

A Pod named `bad-image` exists in namespace `troubleshooting`.

It is failing because of an invalid image.

Fix it so it runs with:

```text
nginx:1.27
```

Validate:

```bash
k get pod -n troubleshooting bad-image
```

---

### Task 17 — Fix CrashLoopBackOff — 5 pts

A Pod named `crash-app` exists in namespace `troubleshooting`.

It is crashing because the command exits immediately.

Fix it so the container keeps running for at least 1 hour.

Validate:

```bash
k get pod -n troubleshooting crash-app
k logs -n troubleshooting crash-app
```

---

### Task 18 — Fix Pending Pod — 5 pts

A Pod named `pending-app` exists in namespace `troubleshooting`.

It is stuck in `Pending` because of a scheduling issue.

Find the cause and fix it.

Validate:

```bash
k describe pod -n troubleshooting pending-app
k get pod -n troubleshooting pending-app -o wide
```

---

### Task 19 — Node NotReady — 7 pts

One worker node is `NotReady`.

Find the cause and restore the node to `Ready`.

Useful commands:

```bash
k get nodes
k describe node <node>
ssh <node>
sudo systemctl status kubelet
sudo journalctl -u kubelet -xe
sudo systemctl status containerd
```

Validate:

```bash
k get nodes
```

---

### Task 20 — etcd backup — 8 pts

On the control plane node, create an etcd snapshot at:

```text
/backup/etcd-snapshot.db
```

Use the correct certificates from the etcd static Pod manifest.

Validate:

```bash
ETCDCTL_API=3 etcdctl snapshot status /backup/etcd-snapshot.db --write-out=table
```

---

# Correction / Solution Guide

Do this part **after** attempting the mock exam.

---

## Task 1 solution — RBAC

```bash
k create ns security
k create sa pod-reader -n security

k create role pod-reader-role \
  --verb=get,list,watch \
  --resource=pods \
  -n security

k create rolebinding pod-reader-binding \
  --role=pod-reader-role \
  --serviceaccount=security:pod-reader \
  -n security

k auth can-i list pods \
  --as system:serviceaccount:security:pod-reader \
  -n security
```

---

## Task 2 solution — Static Pod

```bash
k run static-web --image=nginx:1.27 $do > /tmp/static-web.yaml
sudo cp /tmp/static-web.yaml /etc/kubernetes/manifests/static-web.yaml
```

Validate:

```bash
k get pods -A | grep static-web
```

---

## Task 3 solution — Helm

```bash
k create ns helm-apps

helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install webserver bitnami/nginx -n helm-apps
```

---

## Task 4 solution — Kustomize

```bash
mkdir -p /tmp/kustom-web
cd /tmp/kustom-web

k create ns kustom-lab

cat > deployment.yaml <<'EOF'
apiVersion: apps/v1
kind: Deployment
metadata:
  name: kustom-nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: kustom-nginx
  template:
    metadata:
      labels:
        app: kustom-nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.27
EOF

cat > kustomization.yaml <<'EOF'
resources:
  - deployment.yaml

patches:
  - target:
      kind: Deployment
      name: kustom-nginx
    patch: |-
      - op: replace
        path: /spec/replicas
        value: 3
EOF

k apply -k . -n kustom-lab
```

---

## Task 5 solution — API resources and CRDs

```bash
k api-resources > /tmp/api-resources.txt
k get crd > /tmp/crds.txt
```

---

## Task 6 solution — Deployment resources

```bash
k create ns apps

k create deploy frontend \
  --image=nginx:1.27 \
  --replicas=3 \
  -n apps \
  $do > frontend.yaml
```

Edit:

```yaml
resources:
  requests:
    cpu: 100m
    memory: 128Mi
  limits:
    cpu: 500m
    memory: 256Mi
```

Apply:

```bash
k apply -f frontend.yaml
```

Alternative patch:

```bash
k set resources deploy/frontend -n apps \
  --requests=cpu=100m,memory=128Mi \
  --limits=cpu=500m,memory=256Mi
```

---

## Task 7 solution — Rolling update and rollback

```bash
k set image deploy/frontend nginx=nginx:1.28 -n apps
k rollout status deploy/frontend -n apps

k rollout undo deploy/frontend -n apps
k rollout status deploy/frontend -n apps
```

---

## Task 8 solution — nodeSelector

```bash
k get nodes
k label node <worker-node> disk=ssd
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: scheduled-pod
  namespace: apps
spec:
  nodeSelector:
    disk: ssd
  containers:
    - name: busybox
      image: busybox:1.36
      command: ["sh", "-c", "sleep 3600"]
```

Apply:

```bash
k apply -f scheduled-pod.yaml
```

---

## Task 9 solution — taint and toleration

```bash
k taint node <worker-node> dedicated=training:NoSchedule
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: tolerant-pod
  namespace: apps
spec:
  tolerations:
    - key: dedicated
      operator: Equal
      value: training
      effect: NoSchedule
  containers:
    - name: nginx
      image: nginx:1.27
```

---

## Task 10 solution — ClusterIP Service

```bash
k expose deploy frontend \
  --name=frontend-svc \
  --port=80 \
  --target-port=80 \
  --type=ClusterIP \
  -n apps
```

---

## Task 11 solution — broken Service selector

Check labels:

```bash
k get pods -n apps --show-labels
k describe svc -n apps broken-svc
```

Patch selector:

```bash
k patch svc broken-svc -n apps \
  -p '{"spec":{"selector":{"app":"frontend"}}}'
```

Validate:

```bash
k get endpoints -n apps broken-svc
```

---

## Task 12 solution — NetworkPolicy

Label frontend Pods should already have:

```text
app=frontend
```

Create allowed test pod:

```bash
k run allowed-curl -n apps \
  --image=curlimages/curl \
  --labels=role=curl \
  --restart=Never \
  -- sleep 3600
```

NetworkPolicy:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-curl-to-frontend
  namespace: apps
spec:
  podSelector:
    matchLabels:
      app: frontend
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              role: curl
      ports:
        - protocol: TCP
          port: 80
```

---

## Task 13 solution — Ingress example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: frontend-ingress
  namespace: apps
spec:
  rules:
    - host: frontend.local
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: frontend-svc
                port:
                  number: 80
```

Apply:

```bash
k apply -f ingress.yaml
```

---

## Task 14 solution — CoreDNS

```bash
k -n kube-system get pods -l k8s-app=kube-dns -o wide > /tmp/coredns-status.txt
k -n kube-system logs deploy/coredns > /tmp/coredns-logs.txt
```

---

## Task 15 solution — PV, PVC, Pod

```bash
sudo mkdir -p /mnt/data-training
```

PV:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-training
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  hostPath:
    path: /mnt/data-training
```

PVC:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-training
  namespace: apps
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
```

Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: storage-pod
  namespace: apps
spec:
  containers:
    - name: busybox
      image: busybox:1.36
      command: ["sh", "-c", "sleep 3600"]
      volumeMounts:
        - name: data
          mountPath: /data
  volumes:
    - name: data
      persistentVolumeClaim:
        claimName: pvc-training
```

---

## Task 16 solution — ImagePullBackOff

```bash
k describe pod bad-image -n troubleshooting
k set image pod/bad-image <container-name>=nginx:1.27 -n troubleshooting
```

If `kubectl set image pod` does not work depending on the Pod, export/edit/recreate:

```bash
k get pod bad-image -n troubleshooting -o yaml > bad-image.yaml
vim bad-image.yaml
k delete pod bad-image -n troubleshooting $now
k apply -f bad-image.yaml
```

---

## Task 17 solution — CrashLoopBackOff

```bash
k logs crash-app -n troubleshooting --previous
k get pod crash-app -n troubleshooting -o yaml > crash-app.yaml
```

Change command to:

```yaml
command: ["sh", "-c", "sleep 3600"]
```

Then:

```bash
k delete pod crash-app -n troubleshooting $now
k apply -f crash-app.yaml
```

---

## Task 18 solution — Pending Pod

Check cause:

```bash
k describe pod pending-app -n troubleshooting
```

Common fixes:

```bash
# If nodeSelector mismatch:
k label node <node> <key>=<value>

# If taint issue:
# Add toleration to Pod, or remove taint if task allows:
k taint node <node> <key>=<value>:NoSchedule-

# If resource issue:
# Lower requests or free capacity.

# If PVC issue:
k get pvc -n troubleshooting
k get pv
```

---

## Task 19 solution — Node NotReady

On the broken node:

```bash
sudo systemctl status kubelet
sudo journalctl -u kubelet -xe
sudo systemctl status containerd
```

Common fix:

```bash
sudo systemctl restart containerd
sudo systemctl restart kubelet
```

Then from control plane:

```bash
k get nodes
```

---

## Task 20 solution — etcd backup

Find certs:

```bash
sudo cat /etc/kubernetes/manifests/etcd.yaml
```

Typical command:

```bash
sudo mkdir -p /backup

sudo ETCDCTL_API=3 etcdctl snapshot save /backup/etcd-snapshot.db \
  --endpoints=https://127.0.0.1:2379 \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key
```

Validate:

```bash
sudo ETCDCTL_API=3 etcdctl snapshot status /backup/etcd-snapshot.db --write-out=table
```

---

## Scoring guide

|  Score | Level                              |
| -----: | ---------------------------------- |
| 90–100 | Very ready                         |
|  75–89 | Good, but polish speed             |
|  66–74 | Borderline pass                    |
|  50–65 | Need more troubleshooting practice |
|    <50 | Rebuild fundamentals first         |

Best training method: do this exam once with the correction hidden, then redo it the next day aiming to finish in **90 minutes**.

[1]: https://www.cncf.io/training/certification/cka/ "Certified Kubernetes Administrator (CKA) | CNCF"
[2]: https://docs.linuxfoundation.org/tc-docs/certification/faq-cka-ckad-cks "Frequently Asked Questions: CKA and CKAD & CKS | T&C DOCS (Candidate Facing Resources)"
