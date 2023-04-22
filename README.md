<h1> Updating Kubernetes Resources Requests and Limits </h1>
<body>
# personal study note 

<p>Deploying pod without resource requests causes lack of specifying required amounts of 
CPU and memory, leading to scheduling pods on unsuitable nodes with insufficient 
processing power or memory. On the other hand, starting pods without resource limits 
results in indefinitely use of CPU or memory, causing node failure or performance 
issues when the resources are finished. Well-configured containers should inform 
Kubernetes the amount of memory and CPU used in reserving on a worker node </p>

<h2>Resource requests and limits set up</h2>

1) add resource sections under image in deployment.yaml (by referencing to https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/)

2) "kubectl apply -f (deployment).yaml" applies and updates deployment.yaml

3) "kubectl get pods -n development" gets pods from the development namespace
-> old pods without resource requests and limits are terminating  
-> new pods with updated respurce requests and limits are running 
<br>
<h2>Encountered Errors</h2> 
1) Unable to connect to the server: dial tcp 127.0.0.1 xxxx
  -> Kubernetes is not running 
<br>
  i) open docker 
<br>
  ii) make sure Kubernetes is started by running "minikube start" 
<br>
  expected outcome: "Done! kubectl is now configured to use "minikube" cluster" 
<br>
  iii) check if Kubernetes displays the correct cluster information
<br>
  expected outcome: "Kubernetes control plane is running at https://127.0.0.1:54747"
<br>
<br>
2) Error: error parsing <deployment>.yaml: xxxx
   -> the specific yaml file has some issues - indentation problems in this case
<br>
<h2>Additional info </h2> 

Resources = the amount of available CPU and memory on worker node

Node = a worker machine (- physical or virtual machine) that runs containers and 
is managed by the control plane of the cluster

</body>
