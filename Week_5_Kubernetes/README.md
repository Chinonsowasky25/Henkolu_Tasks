# MicroK8s Two-Node Cluster with Nginx Deployment
##  Objective
Set up a MicroK8s cluster with one master and one worker node using Multipass. Deploy an Nginx web server as a Kubernetes Deployment and expose it using a NodePort service.

## Tools Used
- **Multipass** (for launching Ubuntu VMs)
- **MicroK8s** (lightweight Kubernetes)
- **kubectl** (via MicroK8s)
- **YAML** (for resource configuration)

##  Environment Setup

### Launch VMs using Multipass
multipass launch --name master --cpus 2 --mem 2G --disk 10G
multipass launch --name worker --cpus 2 --mem 2G --disk 10G

## Install MicroK8s on Both VMs

sudo snap install microk8s --classic
sudo usermod -a -G microk8s $USER
sudo chown -f -R $USER ~/.kube

## Enable MicroK8s Add-ons on Master
microk8s enable dns storage ingress

## Join Worker to Master
In the Master node
microk8s add-node
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Screenshot%202025-04-06%20115826.png?raw=true)

## Nginx Deployment


##Nginx Deployment
vim nginx-deployment.yaml
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_5_Kubernetes/Screenshot%202025-04-05%20131336.png?raw=true)

## Apply the Service
sudo microk8s kubectl apply -f nginx-deployment.yaml

## Test the Deployment
microk8s kubectl get nodes -o wide
will list all the services currently running in your MicroK8s Kubernetes cluster

Find the node's internal IP:
then open the browser
http://172.21.230.112:30007/
you should see a welcome nginx page
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_5_Kubernetes/Screenshot%20(65).png?raw=true)

