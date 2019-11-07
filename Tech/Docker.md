# Docker

## DockerFile

### Example

``` docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0
WORKDIR /app
COPY app/bin/Release/netcoreapp3.0/publish/ app/
ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

* **FROM** retrieves the image from the mcr.microsoft.com repository
* **COPY** copies the specified folder into the container
* **ENTRYPOINT** configures the container to run as an executable, running the specified command

----

## Common images

* Use `mcr.microsoft.com/dotnet/core/aspnet:X.X` for .NET Core web APIs
* Use `mcr.microsoft.com/dotnet/core/runtime:X.X` for .NET Core console apps / services

----

## Useful commands

### Management

* `docker images` - lists all Docker images in the local repository  
* `docker ps -a` - lists all containers
* `docker rm mycontainer` - removes the container named *mycontainer*
* `docker rmi -f $(docker images -a -q)` - removes all images

### Creation

* `docker build -t myimage -f Dockerfile .` - builds a new Docker image called *myimage* using the *DockerFile* specified in root (".").
* `docker create --name newimage myimage` - creates a container based on the *myimage* image with the name *newimage*
* `docker tag myimage:latest 0123456789.dkr.ecr.us-east-2.amazonaws.com/myrepository:latest` - tags the image *myimage* to an AWS ECR repository
* `docker push 0123456789.dkr.ecr.us-east-2.amazonaws.com/myrepository:latest` - pushes all relevantly tagged images to an AWS ECR repository

### Running

* `docker stop myimage` - stops the container called *newimage*
* `docker start myimage` - starts the container called *newimage*
* `docker attach myimage` - connects to the container *newimage* and watches the output
* `docker attach --sig-proxy=false` - connects to a container while ensuring that detatchment won't stop the container process
* `docker run -it --rm myimage` - creates and starts a container based off the image *myimage*; `-it` uses the current terminal to connect, with `-rm` deleting the image once detached
* `docker run -it --rm -p 5000:80 --name api myimage` - creates and starts a web API on localhost:5000
* `docker stop $(docker ps -a -q)` - stops all containers
