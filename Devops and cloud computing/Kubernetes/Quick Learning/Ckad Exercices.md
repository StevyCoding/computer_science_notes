# Pod Design
## Deployment

>[!spoiler]- ### Create a deployment with image nginx:1.18.0, called nginx, having 2 replicas, defining port 80 as the port that this container exposes (don't create a service for this deployment)
> `kubectl create deployment nginx --image=nginx:1.18.0 dry-run=client -o yaml`
> `vi deploy.yaml`
> change the replicas field  from 1 to 2
> `kubectl apply -f deploy.yaml`
> or `kubectl create deployment nginx  --image=nginx:1.18.0  --dry-run=client -o yaml | sed 's/replicas: 1/replicas: 2/g'  | sed 's/image: nginx:1.18.0/image: nginx:1.18.0\n        ports:\n        - containerPort: 80/g' | kubectl apply -f -`
> or `kubectl create deploy nginx --image=nginx:1.18.0 --replicas=2 --port=80`


>[!spoiler] View the yaml of this deployment 
>`kubectl get deploy nginx -o yaml`


