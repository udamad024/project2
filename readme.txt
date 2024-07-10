# Deploy a Python Application

In the following task, the python application will display the current time in toronto it uses the tzdata library to achieve this. In addition, the app has been contanarized and will be run using Kubernetes.

## Steps

*Build the docker image:

docker build -t project2 .

*push to dockerhub:


docker tag <username>/project2:latest <username>/project2:latest

docker push <username>/project2:latest

this remote image is referenced in deployment.yaml


*Deploy the application:


kubectl apply -f deployment.yaml

kubectl apply -f service.yaml


*create a network tunnel to make services of type LoadBalancer accessible on your local machine.

minikube tunnel


*status of deployment, service and pods:*

kubectl get deployments - info on deployment

kubectl get services - info on services(nodeport)

kubectl get pods - info on pods running



*Test the application:*

*a. Find the external ip using "kubectl get services"

access the application using the external IP and the NodePort.*

http://<service-external-ip>:32727

