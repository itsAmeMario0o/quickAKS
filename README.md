# quickAKS
Notes for AKS and Panoptica from team

az group create --name AKS --location eastus


az aks get-versions --location eastus.  (This command will show the available versions in th AZ, replace 1.27.1 in the next command where 1.27.1 )

az aks create --resource-group AKS --name AKScluster --node-count 3 --enable-addons monitoring --generate-ssh-keys --kubernetes-version 1.27.1

az aks get-credentials --resource-group AKS --name AKScluster

kubectl create namespace sock-shop

gh auth login.   (GitHub authentication)
Open a  browser and paste https://github.com/login/device then type the code showed in azure console

gh repo clone microservices-demo/microservices-demo

Cd microservices-demo/deploy/kubernetes

kubectl apply -f complete-demo.yaml -n sock-shop 




Panoptica,

 From Panoptica GUI, deployment---->.  +connect cluster ---> complete the information and get the installation steps.

1 kubectl label namespace sock-shop SecureApplication-protected=full --overwrite.   (Change "NAME" for the right name, in this case sock-shop)

2. kubectl label namespace $(kubectl get namespaces | awk '{print$1}' | grep -v -e NAME -e kube-public -e kube-system -e istio-system -e portshift) SecureApplication-protected=full --overwrite


Download the installer and paste into the AZURE console
tar -xzvf AKS_sock_shop_lemilher.tar.gz.     

./install_bundle.sh 
