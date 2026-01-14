# Daemon 
````
1.Runs one pod on every node.
2.new node -> pod auto created.
3.used for logging,monitoring,networking.
4.It keeps the copy of pod in every node.
````
#### Daemon.yaml file ####
````
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: daemon
spec:
  selector:
    matchLabels:
     app: daemon
  template:
    metadata:
      name: tmp-game
      labels:
        app: daemon
    spec:
      containers:
      - name: daemon
        image: nginx
        ports:
        - containerPort: 80
````
#### Apply ####
````
kubectl apply -f daemon.yaml 
````
#### To check daemon ####
````
kubectl get ds
````
#### view pods in details ####
````
kubectl get pods -o wide
````
#### TO check logs ####
````
kubectl logs pod
````


