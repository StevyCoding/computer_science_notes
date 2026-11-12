---
title: "CKA — Révision express avant l'examen"
aliases:
  - "CKA — Antisèche"
tags: [cka, kubernetes, revision, express]
created: 2026-11-07
---

# CKA — Révision express

> [!important] Mode d'emploi (15–20 minutes)
> Cache les réponses, **récite les règles et écris les commandes de mémoire**. Pour les explications, exemples YAML et labs, ouvre [[CKA_Fiche_Revision_Obsidian|la fiche maîtresse]]. **Cette note est réservée à l'entraînement ; les notes personnelles ne sont pas autorisées dans l'environnement d'examen.**

## Carte de l'examen

| Domaine | Poids | À maîtriser |
|---|---:|---|
| Troubleshooting | **30 %** | Pod, Node, API, logs, DNS, endpoints, PVC |
| Architecture/installation/configuration | **25 %** | kubeadm, etcd, static Pods, RBAC, Helm, Kustomize, CRD |
| Services/réseau | **20 %** | ClusterIP, selectors, DNS, NetworkPolicy, Gateway |
| Workloads/scheduling | **15 %** | Deployment, probes, autoscaling, scheduling |
| Storage | **10 %** | PV/PVC/SC, access modes, reclaim |

**Architecture en une phrase :** `kubectl → API → etcd ; controllers → Pods ; scheduler → Node ; kubelet → CRI/runtime ; CNI → réseau ; CSI → stockage ; Service/CoreDNS → accès stable`.

## Six pièges à ne plus faire (issus de ton QCM)

- [ ] **RBAC :** `RoleBinding` + `ClusterRole` = permissions **dans le namespace du binding**, pas sur tout le cluster. `ClusterRoleBinding` donne portée cluster.
- [ ] **Ajout worker :** `kubeadm token create --print-join-command` sur control plane, puis **`kubeadm join`** sur worker.
- [ ] **NetworkPolicy :** `podSelector: {}` + `policyTypes: [Ingress]` sans règles = **isolation entrante** des Pods du namespace ; **egress non isolé par cette policy**. Le CNI doit supporter les policies.
- [ ] **Gateway API :** `GatewayClass → Gateway → HTTPRoute → Service`. `HTTPRoute` route host/path ; **NetworkPolicy ne route pas HTTP**.
- [ ] **Probes :** readiness = exclure du trafic ; liveness = redémarrer ; startup = attendre démarrage avant autres probes.
- [ ] **API KO :** passer sur le control plane : `systemctl status kubelet`, `journalctl -u kubelet`, `crictl ps -a`, `/etc/kubernetes/manifests/`.

## 1. Les commandes de création / modification

```bash
# Toujours vérifier le contexte + namespace
kubectl config current-context
kubectl config get-contexts
kubectl config use-context <contexte>

kubectl run demo --image=nginx:1.27 --restart=Never --dry-run=client -o yaml > pod.yaml
kubectl create deployment web --image=nginx:1.27 --replicas=3 --dry-run=client -o yaml > deploy.yaml
kubectl expose deployment web --port=80 --target-port=80 --dry-run=client -o yaml > svc.yaml
kubectl apply -f fichier.yaml
kubectl apply -k ./overlay
kubectl explain pod.spec.containers --recursive
kubectl get pods -A -o wide
kubectl get events -A --sort-by=.metadata.creationTimestamp
```

## 2. Les commandes de dépannage

```bash
kubectl describe pod <pod> -n <ns>
kubectl logs <pod> -n <ns> --previous
kubectl get pod <pod> -n <ns> -o yaml
kubectl get nodes -o wide
kubectl describe node <node>
kubectl top nodes
kubectl top pods -A
kubectl get pods -n <ns> --show-labels
kubectl get endpointslices -n <ns> -l kubernetes.io/service-name=<service>
kubectl describe pvc <pvc> -n <ns>

# API indisponible : sur le nœud control plane
sudo systemctl status kubelet
sudo journalctl -u kubelet -n 100 --no-pager
sudo crictl ps -a
sudo crictl logs <container-id>
sudo ls /etc/kubernetes/manifests/
```

**Diagnostic mental :** `Pending` → placement/PVC ; `ImagePullBackOff` → registre ; `CrashLoopBackOff` → logs précédents ; `NotReady` → kubelet/runtime ; Service sans endpoints → selector/readiness ; DNS KO → CoreDNS/policy ; PVC Pending → StorageClass/CSI.

## 3. Administration du cluster

```bash
# Joindre un worker (commande générée sur le control plane)
sudo kubeadm token create --print-join-command
# Sur le worker : sudo kubeadm join ...

# Maintenance
kubectl cordon <node>
kubectl drain <node> --ignore-daemonsets
kubectl uncordon <node>

# Upgrade : séquence complète à adapter à la version
sudo kubeadm upgrade plan
sudo kubeadm upgrade apply v<version>  # 1er control plane
sudo kubeadm upgrade node              # autres control planes/workers

# Certificats / etcd
sudo kubeadm certs check-expiration
etcdctl snapshot save /tmp/etcd.db    # avec endpoint TLS/certificats configurés
etcdutl snapshot status /tmp/etcd.db -w table
```

**Attention :** sauvegarde etcd ≠ restauration ; restauration avec `etcdutl` et procédure complète, uniquement en lab. Upgrade/drain : suivre procédure et version exactes. `kubectl get all` n'est pas une sauvegarde etcd.

## 4. Workloads / scheduling

```bash
kubectl rollout status deployment/web -n demo
kubectl rollout history deployment/web -n demo
kubectl rollout undo deployment/web -n demo
kubectl rollout restart deployment/web -n demo
kubectl set image deployment/web nginx=nginx:1.28 -n demo
kubectl scale deployment/web --replicas=3 -n demo
kubectl taint nodes worker-1 dedicated=infra:NoSchedule
kubectl taint nodes worker-1 dedicated=infra:NoSchedule-  # enlève
kubectl auth can-i list pods -n demo
```

- **Deployment** = stateless ; **StatefulSet** = identité stable ; **DaemonSet** = un Pod par nœud éligible ; **Job/CronJob** = traitement à terminer/planifié.
- **Request CPU/RAM** = réservation pour placement ; **limit CPU** = throttling ; **limit mémoire** = OOM possible.
- **HPA CPU** = besoin de mesures + `requests.cpu` ; `kubectl describe hpa`.
- **Taint** repousse ; **toleration** permet mais **ne force pas** le placement ; **nodeSelector**/affinity sélectionnent des nœuds.
- **Secret base64** = encodage, **pas** chiffrement.

## 5. Réseau / stockage en 10 lignes

1. **ClusterIP** = interne ; **NodePort** = port sur les nœuds ; **LoadBalancer** = point d'entrée externe selon infrastructure.
2. **Service `port`** ≠ **backend `targetPort`**.
3. **Service endpoints** = Pod labels cohérents + readiness (via EndpointSlices).
4. DNS Service = `<service>.<namespace>.svc.cluster.local` (domaine par défaut).
5. **NetworkPolicy** = permissions ingress/egress *additives* ; dépend du CNI.
6. **Ingress / HTTPRoute** = règles de routage HTTP ; nécessitent contrôleur adapté.
7. **PV** = ressource ; **PVC** = demande ; **StorageClass** = provisioning ; **CSI** = driver.
8. **RWO** = un nœud en lecture-écriture ; **RWOP** = un Pod ; **RWX** = plusieurs nœuds en écriture.
9. **Retain** = conserver le PV/données ; **Delete** = supprimer volume via stockage sous-jacent si supporté.
10. **PVC Pending** = examiner StorageClass, disponibilité PV, CSI, topologie, Events.

## 6. Test de rappel actif — sans regarder

- [ ] **Q1 :** Un RoleBinding référence un ClusterRole. Dans quels namespaces sont les droits ?
- [ ] **Q2 :** Comment un worker rejoint-il un cluster kubeadm ?
- [ ] **Q3 :** Quelles sont les 3 différences entre readiness, liveness et startup ?
- [ ] **Q4 :** Quelle ressource Gateway API route `/api` vers un Service ?
- [ ] **Q5 :** Quelle est la portée d'une NetworkPolicy `Ingress` sans règles ?
- [ ] **Q6 :** Quelle commande permet de lire les logs du conteneur précédent ?
- [ ] **Q7 :** Où sont les static Pod manifests d'un cluster kubeadm ?
- [ ] **Q8 :** Quelles commandes locales utiliser si le kube-apiserver est indisponible ?
- [ ] **Q9 :** Pourquoi un Service peut-il ne pas avoir d'endpoints ?
- [ ] **Q10 :** Quelle différence entre un PVC RWO et RWOP ?
- [ ] **Q11 :** Comment revenir à la révision précédente d'un Deployment ?
- [ ] **Q12 :** Pourquoi le HPA CPU peut-il afficher `unknown` ?

> [!success] Test d'acquisition
> Tu es prêt à passer aux **simulations pratiques chronométrées** quand tu sais répondre à ces questions **et** exécuter les tâches correspondantes sans cette fiche. Reprends la note [[CKA_Fiche_Revision_Obsidian#8. Exercices pratiques d'entraînement|20 labs]] pour le travail manuel.
