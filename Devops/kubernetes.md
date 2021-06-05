# Kubernetes Notes

## References
- AWS EKS workshop 
  - https://www.eksworkshop.com/010_introduction/basics/concepts_nodes/

## Kubernetes nodes
+ The machines that make up a Kubernetes cluster are called nodes.
+ Nodes in a Kubernetes cluster may be physical, or virtual.
+ There are two types of nodes:
  + A Control-plane-node type, which makes up the Control Plane, acts as the “brains” of the cluster.
  + A Worker-node type, which makes up the Data Plane, runs the actual container images (via pods).


- kubectl
    - used in `managing containers` in the node
    - used in both development and production environments
    - ```kubectl cluster-info```

- minikube
    - used to `manage virtual machine` itself
    - used only in local development environment
    - ```minicube status```

> 

> 


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

  ##### eksctl commands
  1. create kubernetes cluster
  ```
  eksctl create cluster --name test-cluster --version 1.17 --region ap-south-1 --nodegroup-name linux-nodes --node-type t2.micro --nodes2
  ```

  check  .kube/config file created by above command

  2. check the cluster nodes
  `kubectl get nodes`

  3. delete the kubernetes cluster
  `eksctl delete cluster --name test-cluster`




    
    