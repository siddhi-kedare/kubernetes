# NameSpace
````
A Namespace is a logical partition used to organize,isolate and manage the resources within single cluster
````
#### 1. To create namespace ####
````
kubectl create ns test
````
````
kubectl create namespace test
````
#### 2. To check namespace ####
````
kubectl get ns
````
````
kubectl get namespace
````
#### 3. TO check current active namespace ####
````
kubectl config view --minify | grep namespace:
````
#### 4. TO check object version ####
````
kubectl api-resources
````
#### 5. To delete pods ####
````
kubectl delete pod (pod name)
````
#### 6. To delete deploy file ####
````
kubectl delete deploy (deploy name)
````
#### 7. To check deploy ####
````
kubectl get deploy
````
#### 8. To create and apply namespace ####
````
kubectl apply -f deploy.yaml -n test
````
#### 9. To check pods is created in test ####
````
kubectl get pods -n test
````
#### 10. To check deploy in created in test ####
````
kubectl get deploy -n test
````
#### 11. To login/To work inside the namespace ####
````
kubectl config set-context --current --namespace=test
````
#### 12. To edit in deploy.yaml(Add only Namespace) ####
````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rc-games
  namespace: ecom
spec:
  replicas: 3
  selector:
    matchLabels:
     app: blue
  template:
    metadata:
      name: tmp-game
      labels:
        app: blue
    spec:
      containers:
      - name: c1
        image: siddhi2054/cdec-b2:v3
        ports:
        - containerPort: 80
````
#### 13. To apply ####
````
kubectl apply -f deploy.yaml
````
# Namespace File 
````
apiVersion: v1
kind: Namespace
metadata:
 name: dev
````
#### 14. To check running pods ####
````
kubectl get pods --all-namespace
````
#### 15. TO check running deploy ####
````
kubectl get deploy --all-namespace
````
#### 16. To check svc in namespace ####
````
kubectl get svc -n test
````
 
