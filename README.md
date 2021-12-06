# evaluation-aks

kubectl exec -it pod/mypod -- bash

kubectl exec -it pod/hrui-deployment-75c7dd4c44-9gxzv -n front-ns -- bash

apt update
apt-get install dnsutils
nslookup seq-cip-svc



Container ID: hrui-deployment-7966d5fcfc-pqg2b, 
Container IP: 10.244.3.5

kubectl get pods -n front-ns





----------------------------------------------------



ssh -i C:\Users\mohamed\.ssh\redhat101_key.pem mtaha@51.124.249.2

ssh -i C:\Users\mohamed\.ssh\admin_key.pem mtaha@20.101.18.200

ssh -i C:\Users\mohamed\.ssh\master1_key.pem mtaha@20.107.37.217
ssh -i C:\Users\mohamed\.ssh\master2_key.pem mtaha@
ssh -i C:\Users\mohamed\.ssh\master3_key.pem mtaha@

ssh -i C:\Users\mohamed\.ssh\worker1_key.pem mtaha@20.107.9.224
ssh -i C:\Users\mohamed\.ssh\worker2_key.pem mtaha@51.124.195.168
ssh -i C:\Users\mohamed\.ssh\worker3_key.pem mtaha@20.103.0.81


Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 172.18.0.4:6443 --token abcdef.0123456789abcdef --discovery-token-ca-cert-hash sha256:246177ba512bdd121d1bd562814f9b01afb405dfcaaf733629e01cefb23c50a2


bash k8sSecond.sh

git clone https://github.com/mtahaelmaghrabi/LFD259-LAB.git




-------------------------------



Active namespace
kubectl config set-context --current --namespace=front-ns


http://localhost:8889/api/Home

kubectl config use-context docker-desktop

kubectl config use-context AKS-LAB

kubectl config get-contexts

10.240.0.6
10.240.0.4

10.0.230.195
30160


http://10.240.0.4:30160/api/Home






kubectl get all -o wide

kubectl get all -o wide -n front-ns
20.86.195.221


kubectl get all -o wide -n back-ns

kubectl set image deployment.apps/hrui-deployment hruiservice=mtahaelmaghrabi/hrmvc:latest -n front-ns

λ kubectl set image deployment.apps/eval-deployment evaluationcontainer=mtahaelmaghrabi/evaluation:latest -n back-ns


kubectl scale --replicas=0 deployment.apps/hrui-deployment -n front-ns
kubectl scale --replicas=2 deployment.apps/hrui-deployment -n front-ns

kubectl scale --replicas=0 deployment.apps/eval-deployment -n back-ns
kubectl scale --replicas=2 deployment.apps/eval-deployment -n back-ns


kubectl exec -it pod/hrui-deployment-788d55bff-bf68b -n front-ns -- bash
apt update
apt-get install dnsutils
nslookup evaluation-clusterip-srv

  //"EvaluationApiConnection": "http://evaluation-cip-svc.back-ns.svc.cluster.local"
  //"EvaluationApiConnection": "http://20.93.174.27/"


docker build -t mtahaelmaghrabi/hrmvc:latest .
docker image push mtahaelmaghrabi/hrmvc:latest

docker run --name seq -d --restart unless-stopped -e ACCEPT_EULA=Y -p 5341:80 datalust/seq:latest

kubectl run Seq --image=datalust/seq:latest --env="ACCEPT_EULA=Y" --restart=unless-stopped
http://seq-cip-svc.default.svc.cluster.local:5341
       seq-cip-svc.default.svc.cluster.local



STORAGE_KEY=$(az storage account keys list --resource-group AKS-RG --account-name qpphrlogs --query "[0].value" -o tsv)

echo $STORAGE_KEY

kubectl create secret generic azure-secret --from-literal=azurestorageaccountname=qppaksfileshare --from-literal=azurestorageaccountkey=**********
