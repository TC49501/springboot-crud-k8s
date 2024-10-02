# springboot-crud-k8s
Run &amp; Deploy Spring Boot CRUD Application With MySQL on K8S

minikube start <br>
#allow minikube talk to docker <br>
eval $(minikube docker-env) <br>
#create docker image of a spring-boot project, make sure Dockerfile exists in root folder <br>
docker build -t springboot-k8s-example:1.0 . <br>
docker images <br>
#create k8 deployment yaml file <br>
kubectl apply -f deployment.yaml <br>
kubectl get deployments <br>
kubectl get pods <br>
#create k8 service yaml file for LB route <br>
kubectl apply -f service.yaml <br>
kubectl get service <br>
kubectl get nodes -o wide <br>
minikube ip <br>
#look for nodeIp and port, http://192.168.64.14:32208/helloworld <br>
minikube dashboard <br>
#connect into the pod <br>
kubectl exec -it mysql-pod-123 /bin/bash <br>
mysql -h mysql -u root -p <br>
#encrypt the db user/pwd <br>
echo -n 'root' | base64 <br>
kubectl apply -f configmap.yaml <br>
kubectl apply -f secrets.yaml <br>
#create helm chart <br>
helm create spring-app-chart <br>
tree spring-app-chart <br>
helm install myapp-chart spring-app-chart #install chart <br>
kubectl get all <br>
minikube service myapp-chart-spring-app-chart --url  #get proxy url to access the app <br>
curl http://127.0.0.1:50220/customers <br>
helm list <br>
