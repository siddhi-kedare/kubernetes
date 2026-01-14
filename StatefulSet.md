# StatefulSet
````
1.used for stateful apps(Redis,DB).
2.pods have fixed names.
3.pods start one by one.
4.pod is recreated with the same identity.
````
# Difference between StatefulSet and Deployment
````
````
#### Deployment ####
````
1.used for normal app(website,API).
2.Any pod is same as another.
3.Pod name can change.
4.If a pod deleted,new pod = new identity.
5.data is not important.
````
#### StatefulSet ####
````
1.used for data apps(Redis, MYSQL).
2.Each pod is unique.
3.pod name stays same.
4.If a pod is deleted,same pod comes back.
5.data is important.
````
#### StatefulSet.yaml file ####
````
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: redis
spec:
  serviceName: redis
  replicas: 3
  selector:
    matchLabels:
     app: redis
  template:
    metadata:
      name: tmp-game
      labels:
        app: redis
    spec:
      containers:
      - name: redis
        image: redis:5.0.5
        ports:
        - containerPort: 6379
````

