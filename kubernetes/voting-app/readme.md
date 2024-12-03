1. we created yaml file for every pod.
2. we are creating the services
3. postgres, and redis are internal services
4. voting, and result are external or user services
5. will try to access the app on the web browser
6. go to our pc's terminal
7. commands
ls
kubectl create -f voting-app-pod.yaml
kubectl create -f voting-app-service.yaml
# to run the pod and service through one command:
kubectl get pods,svc ----> checking their status
# we use the port number of the service which is 30004 to view it on a browser
# if we don't know it -->
minikube service voting-service --url
# we copy the url and paste it in the browser but we still have to run other pods so we can use it correctly

# to run the redis-pod & redis-service.yaml
kubectl create -f redis-pod.yaml
kubectl create -f redis-service.yaml

# postgres db creation
kubectl create -f postgres-pod.yaml
kubectl create -f postgres-service.yaml

# worker pod
kubectl create -f worker-app-pod.yaml

# result-app pod and service
kubectl create -f result-app-pod.yaml
kubectl create -f result-app-service.yaml

# get it's url using the minikube command then paste it.


# deploying pods doesn't help us scale our app easily if we wanted to add
# more instances of a particular service and if you wanted to update
# the app like an image that was used in the app then your app will have 
# to be taken down while the new pod is created so that may result in a 
# down time.

# DEPLOYMENTS is the solution
# ==> image: deployments in the voting app

1. created a voting app deploy .yaml (same for all pods)
2. after creating all deployments
3. go to the terminal and run them

# TERMINAL


$kubectl get pods
$kubectl get svc
$kubectl create -f voting-app-deploy.yaml
$kubectl create -f voting-app-service.yaml
$kubectl get deployment


========> same for all

$kubectl get deployments,svc

=========>
$minikube service voting-service --url
$minikube service result-service --url

