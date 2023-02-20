# docker
[tutorial](https://www.youtube.com/watch?v=p28piYY_wv8)
## container vs VMs
| *                                          | docker                     | VM             |
| ------------------------------------------ | -------------------------- | -------------- |
| **boot time**                              | short (no need to boot os) | long           |
| **disk space**                             | less                       | OS reqs + apps |
| **memory**                                 | varies (but less)          | OS reqs + apps |
| **scalling** (lunching multiple instances) | easy                       | difficult      |
| **Hardware Utilization Efficency**         | low (hard coded)           | efficient      |


## docker commands

| command                                               | description                                                                  |
| ----------------------------------------------------- | ---------------------------------------------------------------------------- |
| `docker image ls`                                     | list images                                                                  |
| `docker container ls  / docker ps (--all) (--format)` | list containers                                                              |
| `docker stop <pid>`                                   | stop container. rum `docker rm -f $(docker ps -aq)` to remove all containers |
| `docker rm <pid / name>`                              | stop container                                                               |
| `docker build -t <name> <loc of dockerfile>`          | build image from dockerfile                                                  |
| `docker run  <image name>`                            | run image.Use (-it) for interactive mode (-d) to detached (-p) to set port   |
| `docker build -t <name> <loc of dockerfile>`          | build image from dockerfile                                                  |
####  eg. format:
```
"ID\t{{.ID}}\nNAME\t{{.Names}}\nImage\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"
```
## `docker run <image name>:<tag>` 
- `-it` for interactive mode
- `-d` to detached
- `-p` to map port eg. `docker run -d -p 8080:80 nginx:latest`  `-p 8080:80` maps port 8080 to 80.
- `-t` to set tag
- `--name` to set name


## `docker build -t <name> <loc of dockerfile>`
- `-t` to set tag. eg. `docker build -t mynginx:1.0.0 .`
- `--no-cache` to build without cache
- `--build-arg` to set build args eg. `--build-arg VERSION=1.0.0`

## dockerFile

- `FROM` to set base image
- `RUN` to run command eg. `RUN apt-get update`. Runs when building image
- `COPY` to copy files from host to container eg. `COPY . /usr/share/nginx/html`
- `CMD` to run command eg. `CMD ["nginx", "-g", "daemon off;"]`. Runs when running container