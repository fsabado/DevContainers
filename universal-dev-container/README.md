

# Universal Dev Container

A ready-to-use development environment image that comes preloaded with common tools for coding, testing, and automation.  
It’s ideal for use in VS Code Dev Containers, CI/CD runners, or as a lightweight general-purpose development base.

---

## Quick Start

```bash
docker pull fs8080/universal-dev-container:latest

```

## Instructions


Run an Interactive Shell

```bash
docker run -it --rm fs8080/universal-dev-container:latest bash
```


```bash
export DOCKER_LOGIN=fs8080
export DOCKER_NAME=universal-dev-container
# Build the image
docker build -t fs8080/universal-dev-container:latest .


# Run docker image
docker run --rm -p 8080:8080 --name universal-dev-container fs8080/universal-dev-container:latest

```



## Using in VS Code Dev Containers

Add this to your `.devcontainer/devcontainer.json`:

```json
{
  "name": "Universal Dev Container",
  "image": "fs8080/universal-dev-container:latest",
}
```


```bash
# List running containers
docker ps

# Stop and remove container
docker stop universal-dev-container && docker rm universal-dev-container

# Open new shell into a running container
docker exec -it universal-dev-container bash

# See logs
docker logs -f universal-dev-container

# Prune old layers
docker system prune -f
```




