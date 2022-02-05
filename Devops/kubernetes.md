# Kubernetes Notes
This notes contains a cheatsheet of all kubernetes concepts collected from various resources

## Table of Contents
1. [References](#References)
1. [Kubernetes Components](#KubernetesComponents)
    - Pods
    - Services
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

    
