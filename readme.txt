Deploy a Python Application

the python application will display the current time in toronto it uses the tzdata library to achieve this. In addition, the app has been contanarized and will be run using Kubernetes.

Steps - 

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

access the application using the external IP and the port 3030.*

http://<service-external-ip>:3030

The same deployment can be accessed via the internal IP and nodeport however there is a known issue with using Mac m2 with a networking issue 
can be found here - https://github.com/kubernetes/minikube/issues/11193 

can be accessed without running "minikube tunnel" after deployment of both pods and service via the http://internal-ip:nodeport

