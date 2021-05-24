# Docker Notes



### Docker Installation

1. For linux ubunutu,
> https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

### Docker references
1. [Udemy Docker-and-Kubernetes-The-Complete-Guide](https://github.com/StephenGrider/DockerCasts)



### Docker vs Virtual Machines
|                   VirtualMachines Vs Docker     |
| :---------------------------------------------: |
| ![mean_stack](static/docker/docker_vs_vm.png)   |

### Docker Terminology
- Docker Image
  - Image = File System Snapshot + default run command
- Docker Run
  - 

### Docker Commands
- Check docker installation

```
docker version
```

- Get Docker information
```
docker info
```

- Run hello-world image
```
docker run hello-world
```

- List all docker images
```
docker images
```
- Override default run command
```
docker run busybox <override-command-here>

Eg:  docker run busybox echo hi there
```

- List all running containers
```
docker ps
```

- List all container ran till now and there status
```
docker ps --all
Eg:
root@linux:/home/bala# docker ps --all
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                         PORTS               NAMES
904035cc9ad0        busybox             "ping google.com"   4 minutes ago       Exited (0) 9 seconds ago                           sleepy_shamir
3630c151ab75        busybox             "echo hi there"     10 minutes ago      Exited (0) 10 minutes ago                          pensive_ganguly
9c99caf87d2a        busybox             "ls"                12 minutes ago      Exited (0) 12 minutes ago                          naughty_margulis
64dda0d56dbf        busybox             "sh"                13 minutes ago      Exited (0) 12 minutes ago                          romantic_keller
f18e5aecdd72        busybox             "sh"                13 minutes ago      Exited (0) 13 minutes ago                          compassionate_buck
783ddc77ff89        hello-world         "/hello"            About an hour ago   Exited (0) About an hour ago                       boring_heyrovsky

```



### Docker Network Types

1. Closed Network/None Network(complete isolated from network)
2. Bridge Network
3. Host Network
4. Overlay Network

- list all docker networks

	```
	docker network ls
	```

- inspect details of a specific network type

	```
	docker network inspect bridge
	```

	

- create a none network type container

	```
	docker run -d --net none busybox sleep 1000
	```

	