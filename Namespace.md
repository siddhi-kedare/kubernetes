# NameSpace
````
A Namespace is a logical partition used to organize,isolate and manage the resources within single cluster
````
#### To create namespace ####
````
kubectl create ns test
````
````
kubectl create namespace test
````
#### To check namespace ####
````
kubectl get ns
````
````
kubectl get namespace
````
#### TO check current active namespace ####
````
kubectl config view --minify | grep namespace:
````
#### TO check object version ####
````
kubectl api-resources
````
#### To delete pods ####
````
kubectl delete pod (pod name)
````
#### To delete deploy file ####
````
kubectl delete deploy (deploy name)
````
#### To check deploy ####
````
kubectl get deploy
````
#### To create and apply namespace ####
````
kubectl apply -f deploy.yaml -n test
````
#### To check pods is created in test ####
````
kubectl get pods -n test
````
#### To check deploy in created in test ####
````
kubectl get deploy -n test
````
#### To login/To work inside the namespace ####
````
kubectl config set-context --current --namespace=test
````
#### To edit in deploy.yaml(Add only Namespace) ####
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
#### To apply ####
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
#### To check running pods ####
````
kubectl get pods --all-namespace
````
#### TO check running deploy ####
````
kubectl get deploy --all-namespace
````
#### To check svc in namespace ####
````
kubectl get svc -n test
````
 
