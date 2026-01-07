# Pod.yaml
````
apiVersion: v1
kind: Pod
metadata:
  name: k8s
  labels:
    app: k8s-app
spec:
  containers:
    - name: c1
      image: lalit1111/kubernetes-conceps
      ports:
       - containerPort: 80
````
# Service.yaml
````
apiVersion: v1
kind: Service
metadata:
  name: svc-k8s
spec:
  selector:
    app: k8s-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: NodePort
````
# Deployment.yaml
````
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rc-games
spec:
  replicas: 3
  selector:
    matchLabels:
     env: dev
  template:
    metadata:
      name: tmp-game
      labels:
        env: dev
    spec:
      containers:
      - name: c1
        image: abhinagare/abhi-new-repo:v2
        ports:
        - containerPort: 80
````
# Service.yaml
````
apiVersion: v1
kind: Service
metadata:
  name: svc-game
spec:
  selector:
    env: dev
  ports:
   - protocol: TCP
     port: 80
     targetPort: 80
  type: NodePort
