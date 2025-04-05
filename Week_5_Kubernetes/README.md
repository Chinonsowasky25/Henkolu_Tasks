

##Nginx Deployment
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_5_Kubernetes/Screenshot%202025-04-05%20131336.png?raw=true)

ubuntu@master:~$ cat nginx-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  type: NodePort
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30007
Apply the Service
sudo microk8s kubectl apply -f nginx-deployment.yaml

Test the Deployment
microk8s kubectl get nodes -o wide
Find the node's internal IP:
then open the browser
http://172.21.230.112:30007/
you should see a welcome nginx page
