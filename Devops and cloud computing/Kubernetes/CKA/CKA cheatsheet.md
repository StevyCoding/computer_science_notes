# CKA Cheatsheet — practical exam survival guide

The CKA is a **2-hour, online, proctored, performance-based exam** where you solve Kubernetes tasks from the command line. Current official domain weights are: **Troubleshooting 30%**, **Cluster Architecture / Installation / Configuration 25%**, **Services & Networking 20%**, **Workloads & Scheduling 15%**, **Storage 10%**. The CNCF page says to check the FAQ for the current Kubernetes version; the Linux Foundation FAQ currently lists the CKA environment as **Kubernetes v1.35**. ([CNCF](https://www.cncf.io/training/certification/cka/ "Certified Kubernetes Administrator (CKA) | CNCF"))

During the exam, you are allowed to use the browser inside the exam VM to access the **Kubernetes docs**, **Kubernetes blog**, and **Helm docs**; Kubernetes docs search is allowed, but not external search results. The exam hosts already include `kubectl` with alias `k`, Bash autocompletion, `yq`, `curl`, `wget`, and `man`. ([Linux Foundation Documentation](https://docs.linuxfoundation.org/tc-docs/certification/certification-resources-allowed "Resources Allowed: All LF Certification Programs | T&C DOCS (Candidate Facing Resources)"))

---

## 0. Exam setup commands

Use these immediately:

```bash
alias k=kubectl
export do="--dry-run=client -o yaml"
export now="--force --grace-period=0"

# Optional but useful
source <(kubectl completion bash)
complete -o default -F __start_kubectl k
```

Official Kubernetes docs also recommend `alias k=kubectl` with shell completion for faster usage. ([Kubernetes](https://kubernetes.io/docs/reference/kubectl/quick-reference/ "kubectl Quick Reference | Kubernetes"))

Check context before every task:

```bash
k config get-contexts
k config current-context
k config use-context <context-name>
```

Use namespaces fast:

```bash
k get ns
k create ns dev
k -n dev get pods
k config set-context --current --namespace=dev
```

---

# 1. Core kubectl commands

## Get / describe / logs

```bash
k get pods
k get pods -A
k get pod nginx -o wide
k describe pod nginx
k logs nginx
k logs nginx -c container-name
k logs nginx --previous
```

## Watch resources

```bash
k get pods -w
k get deploy -w
k get events --sort-by=.metadata.creationTimestamp
```

## Delete fast

```bash
k delete pod nginx
k delete pod nginx $now
k delete deploy nginx
```

## Explain YAML fields

Very important for exam:

```bash
k explain pod
k explain pod.spec
k explain pod.spec.containers
k explain deployment.spec.strategy
```

---

# 2. Generate YAML quickly

Do not write everything from scratch. Generate, edit, apply.

## Pod

```bash
k run nginx --image=nginx $do > pod.yaml
vim pod.yaml
k apply -f pod.yaml
```

## Deployment

```bash
k create deploy nginx --image=nginx --replicas=3 $do > deploy.yaml
k apply -f deploy.yaml
```

## Service

```bash
k expose deploy nginx --port=80 --target-port=80 --type=ClusterIP $do > svc.yaml
k apply -f svc.yaml
```

## Job

```bash
k create job hello --image=busybox -- /bin/sh -c "echo hello" 
```

## CronJob

```bash
k create cronjob hello \
  --image=busybox \
  --schedule="*/5 * * * *" \
  -- /bin/sh -c "date; echo hello"
```

---

# 3. Workloads & Scheduling — 15%

## Pod minimal YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

## Deployment minimal YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
```

## Scale

```bash
k scale deploy web --replicas=5
```

## Rolling update

```bash
k set image deploy/web nginx=nginx:1.27
k rollout status deploy/web
k rollout history deploy/web
k rollout undo deploy/web
```

## Node selector

```yaml
spec:
  nodeSelector:
    disktype: ssd
```

Commands:

```bash
k label node node01 disktype=ssd
k get nodes --show-labels
```

## Taints and tolerations

Taint node:

```bash
k taint node node01 key=value:NoSchedule
```

Remove taint:

```bash
k taint node node01 key=value:NoSchedule-
```

Pod toleration:

```yaml
spec:
  tolerations:
    - key: "key"
      operator: "Equal"
      value: "value"
      effect: "NoSchedule"
```

## Node affinity

```yaml
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: disktype
                operator: In
                values:
                  - ssd
```

## Resource requests / limits

```yaml
resources:
  requests:
    cpu: "100m"
    memory: "128Mi"
  limits:
    cpu: "500m"
    memory: "256Mi"
```

## Static Pod

Static Pods are usually in:

```bash
/etc/kubernetes/manifests/
```

Example:

```bash
sudo cp pod.yaml /etc/kubernetes/manifests/
```

Kubelet will create it automatically.

---

# 4. Services & Networking — 20%

## Service types

|Type|Use|
|---|---|
|`ClusterIP`|Internal access inside cluster|
|`NodePort`|Expose on node IP + port|
|`LoadBalancer`|External LB, usually cloud|
|`ExternalName`|DNS alias to external name|

## Create service

```bash
k expose deploy web --port=80 --target-port=80 --type=ClusterIP
```

## NodePort

```bash
k expose deploy web --port=80 --target-port=80 --type=NodePort
k get svc web
```

## Test service from temporary pod

```bash
k run test --image=busybox:1.36 -it --rm --restart=Never -- sh
wget -qO- http://web
nslookup web
```

Alternative:

```bash
k run curl --image=curlimages/curl -it --rm --restart=Never -- curl http://web
```

## DNS pattern

Inside same namespace:

```bash
http://service-name
```

Across namespace:

```bash
http://service-name.namespace.svc.cluster.local
```

## Ingress basic

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ingress
spec:
  rules:
    - host: app.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: web
                port:
                  number: 80
```

## NetworkPolicy default deny ingress

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: default-deny-ingress
spec:
  podSelector: {}
  policyTypes:
    - Ingress
```

## Allow traffic from selected pods

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-from-frontend
spec:
  podSelector:
    matchLabels:
      app: backend
  policyTypes:
    - Ingress
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: frontend
      ports:
        - protocol: TCP
          port: 80
```

## CoreDNS debug

```bash
k -n kube-system get pods -l k8s-app=kube-dns
k -n kube-system logs deploy/coredns
k -n kube-system get configmap coredns -o yaml
```

---

# 5. Storage — 10%

## PersistentVolume

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv1
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /data/pv1
```

## PersistentVolumeClaim

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc1
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

## Mount PVC in Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: app
spec:
  containers:
    - name: app
      image: nginx
      volumeMounts:
        - name: data
          mountPath: /usr/share/nginx/html
  volumes:
    - name: data
      persistentVolumeClaim:
        claimName: pvc1
```

## Useful storage commands

```bash
k get pv
k get pvc
k describe pv pv1
k describe pvc pvc1
k get storageclass
```

## EmptyDir volume

Temporary storage, deleted when Pod is deleted:

```yaml
volumes:
  - name: cache
    emptyDir: {}
```

---

# 6. ConfigMap & Secret

## ConfigMap from literal

```bash
k create configmap app-config \
  --from-literal=APP_ENV=prod \
  --from-literal=APP_DEBUG=false
```

## ConfigMap from file

```bash
k create configmap nginx-conf --from-file=nginx.conf
```

## Use ConfigMap as env

```yaml
envFrom:
  - configMapRef:
      name: app-config
```

## Secret from literal

```bash
k create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password='pass123'
```

## Use Secret as env

```yaml
env:
  - name: DB_PASSWORD
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: password
```

## Decode secret

```bash
k get secret db-secret -o jsonpath='{.data.password}' | base64 -d
```

---

# 7. Security / RBAC

## ServiceAccount

```bash
k create serviceaccount app-sa
```

Use in Pod:

```yaml
spec:
  serviceAccountName: app-sa
```

## Role

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: pod-reader
  namespace: dev
rules:
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["get", "list", "watch"]
```

## RoleBinding

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: dev
subjects:
  - kind: ServiceAccount
    name: app-sa
    namespace: dev
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

## Check permission

```bash
k auth can-i get pods
k auth can-i get pods --as system:serviceaccount:dev:app-sa -n dev
k auth can-i create deployments --as user1 -n dev
```

## ClusterRole / ClusterRoleBinding

Use for cluster-wide access:

```bash
k create clusterrole node-reader --verb=get,list,watch --resource=nodes
k create clusterrolebinding node-reader-binding \
  --clusterrole=node-reader \
  --serviceaccount=dev:app-sa
```

---

# 8. Cluster Architecture, Installation & Configuration — 25%

## Important components

|Component|Role|
|---|---|
|`kube-apiserver`|Main API entrypoint|
|`etcd`|Cluster database|
|`kube-scheduler`|Assigns Pods to Nodes|
|`kube-controller-manager`|Runs controllers|
|`kubelet`|Runs on every node, manages Pods|
|`kube-proxy`|Networking rules for Services|
|`containerd`|Container runtime|
|`CoreDNS`|Cluster DNS|

## Check system pods

```bash
k -n kube-system get pods -o wide
```

## Static control plane manifests

Usually here:

```bash
/etc/kubernetes/manifests/
```

Files:

```bash
ls /etc/kubernetes/manifests/
# kube-apiserver.yaml
# kube-controller-manager.yaml
# kube-scheduler.yaml
# etcd.yaml
```

## Kubelet service

```bash
sudo systemctl status kubelet
sudo systemctl restart kubelet
sudo journalctl -u kubelet -xe
```

## containerd

```bash
sudo systemctl status containerd
sudo crictl ps
sudo crictl images
sudo crictl logs <container-id>
```

---

# 9. etcd backup and restore

Very high-value CKA topic.

## Backup

Find etcd cert paths from manifest:

```bash
sudo cat /etc/kubernetes/manifests/etcd.yaml
```

Typical backup command:

```bash
sudo ETCDCTL_API=3 etcdctl snapshot save /backup/etcd.db \
  --endpoints=https://127.0.0.1:2379 \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key
```

Check snapshot:

```bash
sudo ETCDCTL_API=3 etcdctl snapshot status /backup/etcd.db --write-out=table
```

## Restore

```bash
sudo ETCDCTL_API=3 etcdctl snapshot restore /backup/etcd.db \
  --data-dir=/var/lib/etcd-restore
```

Then edit:

```bash
sudo vim /etc/kubernetes/manifests/etcd.yaml
```

Change etcd data dir to restored path:

```yaml
--data-dir=/var/lib/etcd-restore
```

Also update hostPath volume if needed:

```yaml
volumes:
  - hostPath:
      path: /var/lib/etcd-restore
    name: etcd-data
```

---

# 10. kubeadm upgrade

Typical flow:

```bash
k drain controlplane --ignore-daemonsets
sudo apt update
sudo apt-cache madison kubeadm

sudo apt-mark unhold kubeadm
sudo apt-get install -y kubeadm=<version>
sudo apt-mark hold kubeadm

sudo kubeadm upgrade plan
sudo kubeadm upgrade apply v1.xx.x

sudo apt-mark unhold kubelet kubectl
sudo apt-get install -y kubelet=<version> kubectl=<version>
sudo apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet

k uncordon controlplane
```

Worker node:

```bash
k drain node01 --ignore-daemonsets

ssh node01
sudo apt-mark unhold kubeadm
sudo apt-get install -y kubeadm=<version>
sudo apt-mark hold kubeadm
sudo kubeadm upgrade node

sudo apt-mark unhold kubelet kubectl
sudo apt-get install -y kubelet=<version> kubectl=<version>
sudo apt-mark hold kubelet kubectl

sudo systemctl daemon-reload
sudo systemctl restart kubelet
exit

k uncordon node01
```

---

# 11. Troubleshooting — 30%

This is the biggest domain. Your reflex should be:

```bash
k get pods -A
k get nodes
k describe pod <pod>
k logs <pod>
k get events --sort-by=.metadata.creationTimestamp
```

## Pod pending

Check:

```bash
k describe pod <pod>
```

Common causes:

|Symptom|Cause|
|---|---|
|`0/3 nodes available`|scheduling problem|
|`Insufficient cpu`|requests too high|
|`node(s) had taint`|missing toleration|
|`unbound immediate PersistentVolumeClaims`|PVC/PV issue|
|node selector mismatch|wrong label|

## Pod CrashLoopBackOff

```bash
k logs pod-name
k logs pod-name --previous
k describe pod pod-name
```

Common causes:

|Cause|Fix|
|---|---|
|Bad command|fix `command` / `args`|
|App exits immediately|use correct process|
|Missing env/config|check ConfigMap/Secret|
|Bad image|fix image/tag|

## ImagePullBackOff

```bash
k describe pod pod-name
```

Common causes:

|Cause|Fix|
|---|---|
|Wrong image name|correct image|
|Private registry|add imagePullSecret|
|Bad tag|use existing tag|

## Service not working

Checklist:

```bash
k get svc
k describe svc <service>
k get endpoints <service>
k get endpointslice
k get pods --show-labels
```

Most common issue: **Service selector does not match Pod labels**.

Service:

```yaml
selector:
  app: web
```

Pod must have:

```yaml
labels:
  app: web
```

## DNS not working

```bash
k -n kube-system get pods -l k8s-app=kube-dns
k -n kube-system logs deploy/coredns
```

Test:

```bash
k run test --image=busybox:1.36 -it --rm --restart=Never -- nslookup kubernetes.default
```

## Node NotReady

```bash
k get nodes
k describe node node01
ssh node01
sudo systemctl status kubelet
sudo journalctl -u kubelet -xe
sudo systemctl status containerd
```

Common fixes:

```bash
sudo systemctl restart containerd
sudo systemctl restart kubelet
```

## Control plane issue

```bash
sudo ls /etc/kubernetes/manifests/
sudo crictl ps -a
sudo crictl logs <container-id>
sudo journalctl -u kubelet -xe
```

Check static Pod YAML syntax:

```bash
sudo vim /etc/kubernetes/manifests/kube-apiserver.yaml
```

One wrong indentation can break the control plane.

---

# 12. JSONPath / custom output

## Get pod names only

```bash
k get pods -o jsonpath='{.items[*].metadata.name}'
```

## Get node internal IPs

```bash
k get nodes -o jsonpath='{range .items[*]}{.metadata.name}{" "}{.status.addresses[?(@.type=="InternalIP")].address}{"\n"}{end}'
```

## Sort by creation time

```bash
k get pods --sort-by=.metadata.creationTimestamp
```

## Custom columns

```bash
k get pods -o custom-columns=NAME:.metadata.name,NODE:.spec.nodeName,STATUS:.status.phase
```

---

# 13. Helm basics

CKA now includes Helm in the allowed resources list and the exam resources mention Helm docs as allowed. ([Linux Foundation Documentation](https://docs.linuxfoundation.org/tc-docs/certification/certification-resources-allowed "Resources Allowed: All LF Certification Programs | T&C DOCS (Candidate Facing Resources)"))

Useful commands:

```bash
helm version
helm repo list
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm search repo nginx
helm install my-nginx bitnami/nginx
helm list
helm uninstall my-nginx
helm upgrade my-nginx bitnami/nginx
```

Render manifests without installing:

```bash
helm template my-nginx bitnami/nginx
```

---

# 14. Gateway API / Ingress quick idea

The Linux Foundation CKA competencies include using **Gateway API** to manage ingress traffic and knowing Ingress controllers/resources. ([Linux Foundation - Education](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/ "Certified Kubernetes Administrator (CKA) - Linux Foundation - Education"))

Basic mental model:

```text
Client → Gateway / Ingress → Service → Pod
```

For classic Ingress, remember:

```bash
k get ingress
k describe ingress <name>
k get svc
k get endpoints <svc-name>
```

For Gateway API, check:

```bash
k get gatewayclass
k get gateway
k get httproute
```

---

# 15. Fast YAML patching

## Edit live object

```bash
k edit deploy web
```

## Patch replicas

```bash
k patch deploy web -p '{"spec":{"replicas":5}}'
```

## Patch service type

```bash
k patch svc web -p '{"spec":{"type":"NodePort"}}'
```

---

# 16. Useful imperative commands

## Create namespace

```bash
k create ns prod
```

## Create deployment

```bash
k create deploy web --image=nginx --replicas=3
```

## Expose deployment

```bash
k expose deploy web --port=80 --target-port=80
```

## Run temporary debug pod

```bash
k run debug --image=busybox:1.36 -it --rm --restart=Never -- sh
```

## Execute command in pod

```bash
k exec -it pod-name -- sh
k exec pod-name -- cat /etc/resolv.conf
```

## Copy file

```bash
k cp pod-name:/path/file ./file
k cp ./file pod-name:/path/file
```

---

# 17. Must-know resource abbreviations

```bash
po      pods
deploy  deployments
rs      replicasets
sts     statefulsets
ds      daemonsets
svc     services
ep      endpoints
cm      configmaps
sa      serviceaccounts
ns      namespaces
no      nodes
pv      persistentvolumes
pvc     persistentvolumeclaims
ing     ingress
netpol  networkpolicies
```

Use:

```bash
k api-resources
```

---

# 18. CKA exam strategy

## Priority by score

Focus your prep in this order:

1. **Troubleshooting** — biggest domain, 30%.
    
2. **Cluster architecture / kubeadm / etcd / upgrades** — 25%.
    
3. **Networking** — 20%.
    
4. **Workloads / scheduling** — 15%.
    
5. **Storage** — 10%.
    

## During the exam

Use this rhythm:

```text
1. Read task carefully.
2. Switch context.
3. Check namespace.
4. Generate YAML if possible.
5. Apply.
6. Verify.
7. Move on.
```

Always verify:

```bash
k get ...
k describe ...
k logs ...
curl / wget test if networking task
```

## Time rule

Do not spend 15 minutes on one task. If blocked:

```text
Mark it.
Move on.
Return later.
```

CKA is not about perfect theory. It is about solving many small real Kubernetes admin problems quickly.

---

# 19. Mini practice checklist

Before taking CKA, you should be able to do these without thinking:

```text
[ ] Create Pod, Deployment, Service quickly
[ ] Debug Pending / CrashLoopBackOff / ImagePullBackOff
[ ] Fix Service selector / labels
[ ] Create ConfigMap / Secret and mount as env or volume
[ ] Create PV + PVC + mount into Pod
[ ] Create NetworkPolicy
[ ] Use nodeSelector, affinity, taints/tolerations
[ ] Drain / cordon / uncordon node
[ ] Backup and restore etcd
[ ] Upgrade cluster with kubeadm
[ ] Debug kubelet / containerd / static Pods
[ ] Use jsonpath and custom-columns
[ ] Use k explain instead of guessing YAML
```

---

# 20. The “golden” debug commands

Memorize these:

```bash
k get pods -A -o wide
k get nodes -o wide
k describe pod <pod> -n <ns>
k logs <pod> -n <ns>
k logs <pod> -n <ns> --previous
k get events -A --sort-by=.metadata.creationTimestamp
k get svc,ep -n <ns>
k get deploy,rs,pods -n <ns>
sudo systemctl status kubelet
sudo journalctl -u kubelet -xe
sudo crictl ps -a
```

This set alone can solve a lot of CKA troubleshooting tasks.