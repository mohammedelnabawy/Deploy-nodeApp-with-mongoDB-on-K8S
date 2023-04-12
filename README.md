# Deploy-nodeApp-with-mongoDB-on-K8S
The repository contain some steps to deploy nodejs express backend application with mongoDB database on a kubernates cluster.
## Create Docker image from Nodejs app
you can check the node app from: 
```
https://github.com/mohammedelnabawy/socialMedia-nodeJS-project
```
```
docker build . -t elnabawy/nodeapp
```
```
docker login
```
```
docker push elnabawy/nodeapp
```
## Getting Started
1. Create deploy NameSpace
```
kubectl apply -f namespace.yaml
```
```
kubectl config set-context --current --namespace deploy
```
2. Create persistent volume and persistent volume claim to store mongoDB data outside the pod.
```
kubectl apply -f mongo-pv.yaml
```
```
kubectl apply -f mongo-pvc.yaml
```
3. Create secret manifest file that has mongoDB credential
```
kubectl apply -f mongo-secret.yaml
```
4. Create mongoDB deployment
```
kubectl apply -f mongo-deployment.yaml
```
5. Create ClusterIP service for mongoDB deployment
```
kubectl apply -f mongo-svc.yaml
```
6. Create ConfigMap manifest file that has node application environment variables
```
kubectl apply -f node-configmap.yaml
```
7. Create nodeapp deployment
```
kubectl apply -f node-deployment.yaml
```
8. Create ClusterIP service for nodeapp
```
kubectl apply -f node-svc.yaml
```
9. Create ingress manifest file to connect to the node application from outside the cluster
```
kubectl apply -f node-ingress.yaml
```