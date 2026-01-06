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

