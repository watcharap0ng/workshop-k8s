# Kubernetes Hands-on
# LAB-1 Create Pod
```
1. create a new pod with the nginx image
2. How many pods are created now?
3. What is the image used to create the nginx pods?
4. Which nodes are these pods placed on?
5. What does the READY column in the output of the kubectl get pods command indicate?
6. Connect localhost to nginx pod (port-forward)
7. Delete nginx pod. 

kubectl run nginx --image=nginx  --dry-run=client -oyaml | tee nginx-pod.yaml
kubectl apply -f nginx-pod.yaml
kubectl get pods
kubectl describe pods nginx
kubectl get pods -owide
kubectl port-forward pod/<POD-NAME> 8080:80
kubectl delete pods nginx

```

# LAB-2 Create Deployment
```
1. create a new deployment with hands-on2-deployment.yaml
2. create a new configmap with hands-on2-configmap.yaml
3. create a new secret with hands-on2-secret.yaml
4. How many deployments are created now?
5. How many pods are ready?
6. What is the image used to create the pods in the deployment?
7. Delete nginx deployment
8. Create a new Deployment with the below attributes using your own
deployment definition file (Copy from hands-on2-deployment.yaml)
   Name: test-app
   Replicas: 3
   Image: nginx:1.22


kubectl apply -f hands-on2-deployment.yaml
kubectl apply -f hands-on2-configmap.yaml 
kubectl apply -f hands-on2-secret.yaml
kubectl get deployments
kubectl get configmap
kubectl get secret
kubectl get pods
kubectl describe deployments deployment-1
kubectl describe pods <POD-NAME>
kubectl delete deployments deployment-1

kubectl apply -f hands-on2-deployment.yaml
```

# LAB-3 Create Service - ClusterIP, NodePort
```
1. Open hands-on3-svc.yaml and create service type ClusterIP
   kubectl apply -f hands-on3-svc.yaml
2. Check STATUS is Pending?
   kubectl get pods -owide
3. Add label worker node
   kubectl get nodes
   kubectl label node <node-name> service=app
   kubectl get pods -owide
4. Let try port-forward from your localhost to the svc
   kubectl get svc
   kubectl port-forward svc/simple-app-svc 8080:80


1. Open hands-on4-svc.yaml and create service type NodePort
2. Try request to your exposed service (nodes ip address)
   kubectl get nodes -owide
   curl http://<nodes-ipaddress>:30001
```

# LAB-4 Security Scanner Image with trivy
```
trivy image --severity HIGH,CRITICAL nginx:latest
trivy image --severity HIGH,CRITICAL -f json -o trivy-report.json nginx:latest
```