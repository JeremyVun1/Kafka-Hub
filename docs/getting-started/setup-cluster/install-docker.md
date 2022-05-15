# Install Docker

We'll be using Docker to run a kafka cluster locally

## Windows
### 1. Install Docker Desktop
Your machine should have virtualisation enabled (see PC Info tools). 

Download and install Docker Desktop from [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

### 2. Install WSL2
Install WSL 2 to run linux based containers. [https://docs.docker.com/desktop/windows/wsl/](https://docs.docker.com/desktop/windows/wsl/)

### 3. Add to Docker User Group
Add your lan id to the Docker User Group

### 4. Running Docker
!!! warning
    If you are using Myras, first disconnect before running docker desktop.

Once the Docker Engine has started, open up a shell and pull down the Docker Tutorial from the internal docker hub mirror

``` powershell
docker pull hub.internal.abc/docker/getting-started
```

Test that you can run the container,

``` powershell
docker run -d --name docker_tutorial -p 80:80 docker/getting-started
```

The Docker tutorial should now be hosted at [http://localhost:80](http://localhost:80){target=_blank}. Feel free to go through this if you are new to docker.

Remove the Docker Container when done

``` powershell
docker rm -f docker_tutorial
```
