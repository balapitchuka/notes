### Docker Installation
1. For linux ubunutu,
> https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

### Docker references
1. [Udemy Docker-and-Kubernetes-The-Complete-Guide](https://github.com/StephenGrider/DockerCasts)

### Docker Terminology
- Docker Image
  - Image = File System Snapshot + default run command

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
