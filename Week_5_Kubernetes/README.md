# MicroK8s Two-Node Cluster with Nginx Deployment

## 📌 Objective
Set up a MicroK8s cluster with one master and one worker node using Multipass. Deploy an Nginx web server as a Kubernetes Deployment and expose it using a NodePort service.

---

## 🧰 Tools Used
- **Multipass** (for launching Ubuntu VMs)
- **MicroK8s** (lightweight Kubernetes)
- **kubectl** (via MicroK8s)
- **YAML** (for resource configuration)

---

## 🖥️ Environment Setup

### 1. Launch VMs using Multipass
```bash
multipass launch --name master --cpus 2 --mem 2G --disk 10G
multipass launch --name worker --cpus 2 --mem 2G --disk 10G

#Install MicroK8s on Both VMs
sudo snap install microk8s --classic
sudo usermod -a -G microk8s $USER
sudo chown -f -R $USER ~/.kube

Enable MicroK8s Add-ons on Master
microk8s enable dns storage ingress

#Join Worker to Master
microk8s add-node

##Nginx Deployment
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_5_Kubernetes/Screenshot%202025-04-05%20131336.png?raw=true)
![Screenshot 2025-04-05 131336](https://github.com/user-attachments/assets/66313cbc-b34c-4e57-a27f-d18ad4239595)

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
