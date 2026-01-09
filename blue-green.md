# Blue.yaml
````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rc-games
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
# Service--Blue
````
apiVersion: v1
kind: Service
metadata:
  name: svc-game
spec:
  selector:
    app: blue
  ports:
   - protocol: TCP
     port: 80
     targetPort: 80
  type: NodePort
````
# Green.yaml
````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: green-app
spec:
  replicas: 3
  selector:
    matchLabels:
     app: green
  template:
    metadata:
      name: tmp-game
      labels:
        app: green
    spec:
      containers:
      - name: c1
        image: siddhi2054/cdec-b2:v4
        ports:
        - containerPort: 80
````
# Service--Green
````
apiVersion: v1
kind: Service
metadata:
  name: svc-game
spec:
  selector:
    app: green
  ports:
   - protocol: TCP
     port: 80
     targetPort: 80
  type: NodePort
````
````
kubectl apply -f blue.yaml
````
kubectl get pods
````
kubectl apply -f service.yaml
````
kubectl get svc
````
#### Hit the port ####
