# K8s_Manifest_files

# Install MiniKube on Ubuntu 

sudo su

# Now install docker

sudo apt update && apt -y install docker.io
# Install KubectlS

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl

sudo mv kubectl /usr/local/bin/

kubectl version --short

# install Minikube

curl -Lo minikube https://github.com/kubernetes/minikube/releases/download/v1.24.0/minikube-linux-amd64 
&& chmod +x minikube && sudo mv minikube /usr/local/bin/

*****************************************************************************
# Install Conntrack
apt install conntrack
*******************************************************************************
#Start Minikube
 minikube start --vm-driver=none
 minikube status

 # Command For Change NameSpace

kubectl config set-context $(kubectl config current-context) --namespace=dev

kubectl config view | grep namespace:

# Component.yml file to manage Autoscalling

wget -O metricserver.yml https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml


# Apply AutoScalling 

kubectl autoscale deployment mydeploy --cpu-percent=20 --min=1 --max=10

# This Command apply horizental auto scalling on the above "26_Horizental_AutoScalling.yml" Menifest.