# aks-setup
Docs repo to help in setting up aks &amp; ingress 

```bash

sudo apt update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install zip
sudo apt install azure-cli
snap install kubectl --classic
sudo snap install helm --classic
#k9s

#Docker
<https://docs.docker.com/engine/install/ubuntu/>
<https://docs.docker.com/engine/install/linux-postinstall/>


#ingress
<https://learn.microsoft.com/en-us/azure/aks/internal-lb>



helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

helm repo update

helm install nginx-ingress ingress-nginx/ingress-nginx \
    --namespace ingress-nginx --create-namespace \
    --set controller.replicaCount=1 \
    --set controller.service.externalTrafficPolicy=Local \
    --set controller.service.annotations."service\.beta\.kubernetes\.io/azure-load-balancer-ipv4"=192.168.180.80 \
    --set controller.service.annotations."service\.beta\.kubernetes\.io/azure-load-balancer-internal"="true" \
    --create-namespace \
    --wait

kubectl get svc -A
```
