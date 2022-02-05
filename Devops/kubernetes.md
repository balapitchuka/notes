# Kubernetes Notes
This notes contains a cheatsheet of all kubernetes concepts collected from various resources

## Table of Contents
1. [References](#References)
1. [Kubernetes Components](#KubernetesComponents)
    - Pods
    - Services
    - Deployments
    - Controllers
    - ConfigMaps And Secrets
 
1. [Kubernetes Networking](#kube_networking)    
1. [Learning Resources](#Learning)
1. [Additional Examples](#AddEx)




- Open source container orchestration tool
- Developed by Google
- Helps you manage containerized applications in different deployment environments like physical, virtual machines or cloud environments.



## References <a name="References"></a>
- AWS EKS workshop 
  - https://www.eksworkshop.com/010_introduction/basics/concepts_nodes/

## Tools Installation
- AWS Shell:
    - It is an integrated shell that works with the AWS CLI. It uses the AWS CLI configuration and improves productivity with an autocomplete feature.
    - Install aws shell:
        - `sudo apt-get install aws-shell && aws-shell`
        -  You can use AWS commands with aws-shell with less typing. Press the F10 key to exit the shell


## Kubernetes nodes
+ The machines that make up a Kubernetes cluster are called nodes.
+ Nodes in a Kubernetes cluster may be physical, or virtual.
+ There are two types of nodes:
  + A Control-plane-node type, which makes up the Control Plane, acts as the “brains” of the cluster.
  + A Worker-node type, which makes up the Data Plane, runs the actual container images (via pods).

+ Hence A Kubernetes cluster is split into two parts:
  + The Kubernetes Control Plane
  + The (worker) nodes


### Components of the Control Plane
The Control Plane is what controls and makes the whole cluster function. 
The components that make up the Control Plane are:
  ```
  The etcd distributed persistent storage
  The API server
  The Scheduler
  The Controller Manager
  ```
These components store and manage the state of the cluster, but they aren’t what runs the application containers.

### Components running on the worker nodes
The task of running your containers is up to the components running on each worker node:
```
The Kubelet
The Kubernetes Service Proxy (kube-proxy)
The Container Runtime (Docker, rkt, or others)
```

- kubectl
    - used in `managing containers` in the node
    - used in both development and production environments
    - ```kubectl cluster-info```

- minikube
    - used to `manage virtual machine` itself
    - used only in local development environment
    - ```minicube status```

## Namespaces
A namespace can be in one of two phases:
- Active the namespace is in use
- Terminating the namespace is being deleted, and can not be used for new objects

### Namespace 


## Kubernetes Components <a name="KubernetesComponents"></a>

|                   Kubernetes Components         |
| :---------------------------------------------: |
| ![mean_stack](static/kubernetes/kubernetes_cluster_components.png) |

### Pods
- Smallest units of k8s
- Abstraction over container
- Usally 1 application per pod
- Each pod gets its own IP address(New IP address on re-creation of pod once its dies)

### Services
Getting Started with Communication
- Kubernetes service span across worker nodes

#### How services are useful? 
- Services enable connectivity between groups of pods
  - example:
        - services enables the frontend application to be made availabel to end users
        - It helps communication between backend and frontend pods
        - Also helps communication between backend and external datasource



+ Since Pods are unreliable, short-lived, and volatile, we cannot assume that the database would always be accessible through the IP of a Pod. 
+ When that Pod gets destroyed (or fails), the ReplicaSet would create a new one and assign it a new address.
+ We need a stable, never-to-be-changed address that will forward requests to whichever Pod is currently running.

#### The Solution 
Kubernetes Services provide addresses through which associated Pods can be accessed.

Creating a cluster
```
cd k8s-specs

git pull

minikube start --vm-driver=virtualbox

kubectl config current-context
```

#### Sequential Breakdown of the Process


#### Creating Services through Declarative Syntax
```
apiVersion: v1
kind: Service
metadata:
  name: go-demo-2
spec:
  type: NodePort
  ports:
  - port: 28017
    nodePort: 30001
    protocol: TCP
  selector:
    type: backend
    service: go-demo-2
```

+ Line 1-4: You should be familiar with the meaning of apiVersion, kind, and metadata, so we’ll jump straight into the spec section.

+ Line 5: Since we already explored some of the options through the kubectl expose command, the spec should be relatively easy to grasp.

+ Line 6: The type of the Service is set to NodePort meaning that the ports will be available both within the cluster as well as from outside by sending requests to any of the nodes.

+ Line 7-10: The ports section specifies that the requests should be forwarded to the Pods on port 28017. The nodePort is new. Instead of letting the service expose a random port, we set it to the explicit value of 30001. Even though, in most cases, that is not a good practice, I thought it might be a good idea to demonstrate that option as well. The protocol is set to TCP. The only other alternative would be to use UDP. We could have skipped the protocol altogether since TCP is the default value but, sometimes, it is a good idea to leave things as a reminder of an option.

+ Line 11-13: The selector is used by the Service to know which Pods should receive requests. It works in the same way as ReplicaSet selectors. In this case, we defined that the service should forward requests to Pods with labels type set to backend and service set to go-demo. Those two labels are set in the Pods spec of the ReplicaSet.

##### Creating the Service
```
kubectl create -f svc/go-demo-2-svc.yml
kubectl get -f svc/go-demo-2-svc.yml
```

### Kubernetes Endpoints
- When we create a service, kubernetes create Endpoint object
    - > kubectl get endpoints
- Endpoints have same name as Service
- Endpoints keeps track of, which pods are the members/endpoints of the service

Service Template
```
apiVersion: v1
kind: Service
metadata:
  name: <service_name>
  namespace: <k8s_namespace>
spec:
  type: NodePort
  selector:
    component: webserver
    release: airflow
  ports:
    - name: mongodb
      port: 8080
      targetPort: 8080
      protocol: TCP
    - name: mongodb-exporter
      port: 27012
      targetPort: 2345
      nodePort: 30000
      protocol:  TCP
```

### Types of kubernetes services
1. ClusterIP
- Default, type not needed in definition file
- Internal service 
- ClusteerIP only accessible within cluster
- Headless Service

Headless service definition file template
```
apiVersion: v1
kind: Service
metadata:
  name: <service_name>
  namespace: <k8s_namespace>
spec:
  clusteerIP: None
  selector:
    component: webserver
    release: airflow
  ports:
    - name: mongodb
      port: 8080
      targetPort: 8080
      protocol: TCP

```

> kubectl get svc

Usecases for Headless Service
- Client wants to communicate with 1 specific pod diretly
- Pods want to talk direclty with specific pod
- So not randomly selected
- Use Case: Stateful applications like databases, elasticsearch
  - In stateful applications like databases pod replicas are not identical


How can client know Pods IP addresses?
- Client needs to figure out IP addresses of each pod
    - Option 1 - API call to k8s API Server
        - makes app too tied to k8s api
        - inefficient
    - Option 2 - DNS Lookup
        - DNS lookup for service returns single IP address(Cluster IP)

2. NodePort
- External traffic has access to fixed port on each worker node
- Nodeport range is [30000 - 32767]
- Nodeport services are not secure
- NodePort service is an extension of ClusterIP service
- NodePort is not generally using for external connection  to test some service
  quicly but not for production usecases


3. LoadBalancer
- Service becomes accessible externally through cloud providers LoadBalancer
- When we create load balancer service, NodePort and ClusterIP service are
  created automatically by kubernetes, to which external cloud load balances routes traffice to 
- Loadbalance service is an extension of NodePort service


Services wrapup:
- Configure ingress or loadbalancer for production environments


### Kubernetes Deployments
Verify the status of the Deployment and troubleshoot it if needed
> kubectl rollout status deployment <deployment_name>

Fetch deployments in current namespace
> kubectl get deployments

Fetch replicasets and pods in the namespace
> kubectl get rs,pods

Check the details and events for the Deployment and note recent ScalingReplicaSet events
> kubectl describe deployments


Get the rollout history of the deployment
> kubectl rollout history deployment <deployment_name>
```
REVISION CHANGE-CAUSE
1        <none>
2        image updated to 1.16.0
3        image updated to 1.17.0 and scaled up to 3 replicas
```
**Note:**
- Notice that the rollback command only takes the Deployments back to different image version rollouts, and does not undo the other spec changes, such as the number of replicas.



Roll back the last rollout
> kubectl rollout undo deployment <deployment_name>


Roll back to a specific revision
> kubectl rollout undo deployment nginx-deployment --to-revision=1

**Important**
- Kubernetes schedules resources on the worker nodes based on the availability of resources. If you are using a small cluster with limited CPU and memory resources, you may easily run out of resources, which would cause new Deployments to fail to get scheduled on worker nodes. 

Delete a Deployment:
> kubectl delete deployment nginx-deployment



### Kubernetes Controllers

What is a controller?
- A controller is an object that ensures that your application runs in the `desired state` for its `entire runtime`

Kubernetes supports different controllers that you can use for replication.  Each of these controllers is useful for specific use cases`.
- ReplicaSets
- Deployments
- DaemonSets
- StatefulSets
- Jobs

**ReplicaSets**
- A ReplicaSet is a Kubernetes controller that `keeps a certain number of Pods running at any given time`.
- Even if someone deletes the only running Pod, the ReplicaSet will ensure that a new Pod is created to replace it, thereby ensuring that one Pod is always running.
- A ReplicaSet can be used to reliably run a single Pod indefinitely or to run multiple instances of the same Pod.


**Deployment**
- A Deployment is a Kubernetes object that acts as a wrapper around a ReplicaSet and makes it easier to use.
- In order to `manage replicated services`, it's `recommended that` you `use Deployments` that, in turn, manage the ReplicaSet and the Pods created by the ReplicaSet
- The `major motivation` for using a Deployment is that it `maintains a history of revisions`. Every time a change is made to the ReplicaSet or the underlying Pods, a new revision of the ReplicaSet is recorded by the Deployment.


**StatefulSets**
- StatefulSets are used to manage stateful replicas


**DaemonSets**
- 

**Jobs**
- A Job is a supervisor in Kubernetes that can be used to `manage Pods` that are supposed to `run a determined task and then terminate gracefully`.
- The Pods created by a Job aren't deleted following completion of the job. The Pods run to completion and stay in the cluster with a Completed status.



### kubernetes Volumes
How to persist data in kubernetes using volumes
- Persistent Volumes
- Persistent Volume Claims
- Storage Class


Our storage requirement is:
-  We need storage that does not depend on the pod lifecycle
- Storage must be available on all nodes
- Storage needs to survive even if cluster crashes

Persistent Volume
- a clusteer resource just like ram, cpu
- created using YAML file


Persistent volume YAML example
```
apiVersion: v1
kind: PersistentVolume
metadata:
  name: efs-pvc
spec:
  capacity:
    storage: 10Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  storageClassName: efs-sc
  csi:
    driver: efs.csi.aws.com
    volumeHandle: fs-2ad6c0fb
```
Note:  
- Persistent volumes are not namespaced
- PV outside of the namespaces
- Accessible to the whole cluster


Local vs Remote Volume Types

- Each volume type has its own use case
- Local volumes types violate 2 and 3 requirement for data persistence
    - Being tied to 1 specific node
    - Surviving cluster crashes

Who configures storage in kubernetes
- Storage resource is provisioned by Admin
eg: nfs-storage or cloud-storage has to be made available to the cluster
- k8s admin create the persistent volume components from these storage backends

#### Persistent volume claim

Persistent volume claim example
```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: efs-storage-claim
  namespace: storage
spec:
  volumeMode: Filesystem
  accessModes:
    - ReadWriteMany
  storageClassName: efs-sc
  resources:
    requests:
      storage: 5Gi

```


Create a pod using the pvc in above step
```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      volumeMounts:
        - mounthPath: "/var/www/html"
          name: mypd
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: efs-storage-claim
        
```

Levels of Volume abstractions
- Pod request the volume through the PV claim
- Claim tries to find a volume in cluster
- Volume has the actual storage backend

Note: Claims must be in the same namespace as pod

Who creates storage 
- Admin provisions storage resource(PV)
- users/developers create claim to PV(pvc)


#### Storage Class
Why Storage Class
- Another abstraction level
- abstracts underlying storage provider
- parameters for that storage

- SC provisions persistent volumes dynamically when persistentVolumeClaim claims it

- StorageBackend is definede  in the SC component
- via "provisioner" attribute
- each storage backend has own provisioner
- internal provisioner - "kubernetes.io"
- external provisioner
- configure parameters for storage we want to request for PV

StorageClass YAML Definition
```
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: storage-class-name
provisioner: kubernetes.io/aws-ebs
parameters:
  type: io1
  iopsPerGB: "10"
  fsType: ext4
```

Storage drivers

- kubernetes cluster does not have any additional storage drivers installed
- list storage drivers in cluster
    - > kubectl get csidrivers


### Kubernetes ConfigMap and Secret
- Both are local volumes
- not created via PV and PVC
- managed by Kubernetes

Eg:
- Configuration file for your pod
- Certificate file for your pod


Steps:
1. Create ConfigMap and/or Secret component
2. Mount that into your pod/container



### Kubernetes Networking

Kubernetes is all about networking. There are threee types of networks in kubernetes:

1. Node
2. Cluster
3. Pod

### Roles in Kubernetes
Roles in kubernetes

- k8s Administrator setups and maintains the cluster and also make sure cluster  has enough resources
- k8s user who deploys the applications in the cluster


====================================================

### Kuberntes Ingress
Ingress Controller
- The function of ingress controller is to evaluate all the rules that you have defined in your cluster
- way to manage all the redirections
- This will be the entrypoint to cluster
- Inorder to install this implementation of ingress in your cluster you have to 
decide which one of the many different third party implementations you want to choose from
- There is one ingress controller from kubernetes itself which is Kubernetes
  Nginx Ingress Controller


Install Ingress Controller in Minikube

> minikube addons enable ingress
This command automatically starts K8s Nginx Implementation of Ingress Controller

Check ingres controller (it is present as pod)
> kubectl get pod -n kube-system

Configure ingress for kubernetes dashboard

- Reference:
    - https://www.youtube.com/watch?v=80Ew_fsV4rM&ab_channel=TechWorldwithNana

> kubectl get all -n kubernetes-dashboard

```
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
  name: dashboard-ingress
  namespace: kubernetes-dashboard
  annotations:
    kubernetes.io/ingress.class: alb
    alb.ingress.kubernetes.io/scheme: internet-facing
  labels:
    app: airflow-ingress
spec:
  rules:
    - http:
        paths:
          - path: /*
            backend:
              serviceName: kubernetes-dashboard
              servicePort: 80

```


## Kubernetes Cluster Setup

### Locally 

1.a configure a self-managed Kubernetes cluster
  - [Minikube](https://kubernetes.io/docs/tasks/tools/) – Development and Learning
  - [Kops](https://github.com/kubernetes/kops) – Learning, Development, Production
  - [Kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/) – Learning, Development, Production
  - [Docker for Mac](https://docs.docker.com/docker-for-mac/#kubernetes) - Learning, Development
  - [Kubernetes IN Docker](https://github.com/kubernetes-sigs/kind) - Learning, Development

### On Cloud
- AWS EKS
  - Managed kubernetes service
  - Necessary apps preinstalled
    - Container runtime
    - Master processes
  - Scaling and  backups
  - You create and worry about worker nodes
  - AWS manages master nodes

  Steps:
  1. Setup or preparation steps:
      - create aws account
      - create vpc
      - create an iam role with security group (create aws user with list of permissions)
  2. Create  cluster control plane (with iam role)
      - choose cluster name,k8s version
      - choose region and vpc for the cluster
      - set security for the cluster
  3. Create worker nodes and connect to cluster
      - create as a node group(group of nodes) not separate ec2 machines
      - choose cluster it will attach to
      - define security group, selecct instance type, resources
      - define max and min number number of nodes

  `eksctl` to achieve above steps using command line tool 
    - not an aws tool
    - from weaveworks
    - avoid creating above steps manually from management console or from command line
    - eksctl create cluster command will create eks cluster with default values

## Kubernetes Commands
1. create kubernetes cluster
```
> eksctl create cluster --name test-cluster --version 1.17 --region ap-south-1 --nodegroup-name linux-nodes --node-type t2.micro --nodes2

Provisioning a managed Kubernetes cluster on Amazon EKS
Create kubernetes as a service cluster on aws eks
> eksctl create cluster
> eksctl create cluster --name my-clusteer --version 1.17 --manged --asg-access

- By default, eksctl deploys a cluster with workers on two m5.large instances using the AWS EKS AMI in the us-west-2 region. 
- eksctl creates and exports the Kubernetes configuration under ~/.kube/config. Therefore, no additional steps are required to connect your clusters using kubectl
```

check  .kube/config file created by above command

2. check the cluster nodes
```
kubectl get nodes
```

3. delete the kubernetes cluster
```
eksctl delete cluster --name test-cluster
```


4. Update kubectl configuration to aws eks cluster
```
aws eks --region <region> update-kubeconfig --name <clustername>
```
5. Get kubernetes cluster information and workers
```
kubectl cluster-info && kubectl get nodes
```

    
