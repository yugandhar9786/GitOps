step-1:

setup a kubernetes cluster in my case i am using minikube

step-2:

go to argocd docs and install argo cd namespace in the minikube cluster

kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


step-3:

check the pods are running or not by using the command

kubectl get pods -n argocd -w


step-4:

check the services by using the command

kubectl get svc -n argocd

then change the loadbalancer from clusterip to nodeport mode by using the command

kubectl edit svc argocd-server -n argocd

step-5:
 

to host the application in the browser we use the command 

minikube service argocd-server -n argocd

it will open the arcd ui 

username: admin
password: here we use the command to get password
kubectl get secret -n argocd
it will generate the argocd-initial-admin-secret
after edit that argocd-initial-admin-secret by using the command

 kubectl edit secret argocd-initial-admin-secret -n argocd

 by default it gives encoded password here we have to decrypt that password by using the command called

 echo password== | base64 --decode



