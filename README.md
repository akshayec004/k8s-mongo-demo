# k8s-mongo-demo
Yaml files to run mong-express and mong-db in Minikube

## Install Docker on Amazon Linux:
1. sudo yum update -y
2. sudo yum install docker
3. sudo service docker start
4. sudo usermod -a -G docker ec2-user
5. service docker status
6. chkconfig docker on

## Minikube Installation:
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -ivh minikube-latest.x86_64.rpm
minikube start

## To install kubectl :
minikube kubectl -- get pods -A
or 
curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.19.0/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl

## To check installation:
kubectl version --client
kubectl get nodes

## To create mongo-db:
kubectl apply -f mongo-secret.yaml
kubectl get secret

kubectl apply -f mongo-db.yaml
kubectl get service
kubectl describe service <name>
kubectl get pod -o wide


## To create mongo-express:
kubectl apply -f mongo-configmap.yaml
kubectl get configmap

kubectl apply -f mongo-express.yaml
kubectl get pod
kubectl logs <pod-name>


Service of LoadBalancer type has internal as well as external IP address. In minikube, the external IP address should assigned explicitly
To assign IP address to the external service, run
minikube service <service-name>