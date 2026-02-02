```
# ตรวจสอบ K8s Cluster 
kubectl config current-context
kubectl get nodes


# Deploy nginx ด้วย Deployment 
kubectl create deployment web --image=nginx
kubectl get deployments
kubectl get pods


# ตรวจสอบรายละเอียด Deployment
kubectl describe deployment web | head -n 30


# Scale replicas = 3
kubectl scale deployment web --replicas=3
kubectl get pods -o wide


# Self-healing: ลบ pod
kubectl get pods
kubectl delete pod <POD_NAME>
kubectl get pods -owide


# Expose service Type=ClusterIP
kubectl expose deployment web --port=80 --type=ClusterIP
kubectl get svc


# Verify
kubectl exec -it <POD_NAME> -- curl http://web.default.svc
kubectl run curlbox --image=curlimages/curl:8.5.0 --restart=Never --rm -it -- curl http://web.default.svc


# Port-forward
kubectl port-forward svc/web 8080:80


# Cleanup
kubectl delete svc web
kubectl delete deployment web

```
