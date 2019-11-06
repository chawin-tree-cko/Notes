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

* `docker build -t myimage -f Dockerfile .` - Builds a new Docker image called *myimage* using the *DockerFile* specified in root (".").
* `docker images` - Lists all Docker images in the local repository  
* `docker ps -a` - Lists all containers
* `docker create --name newimage myimage` - Creates a container based on the *myimage* image with the name *newimage*
* `docker stop myimage` - Stops the container called *newimage*
* `docker start myimage` - Starts the container called *newimage*
* `docker attach myimage` - Connects to the container *newimage* and watches the output
* `docker attach --sig-proxy=false` - Connects to a container while ensuring that detatchment won't stop the container process
* `docker run -it --rm myimage` - Creates and starts a container based off the image *myimage*; `-it` uses the current terminal to connect, with `-rm` deleting the image once detached
* `docker run -it --rm -p 5000:80 --name api myimage` - Creates and starts a web API on localhost:5000
* `docker rmi -f $(docker images -a -q)` - Removes all images
