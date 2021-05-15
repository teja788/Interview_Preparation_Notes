# Docker

### Section 1

* Docker makes it very easy to install and run software without worrying about setup and dependencies. It can run on any kind of hardware and supports multiple underlying architecture
* 
* Container is a program with own set of isolated set of hardware resources. It is a instance of an image. It's sole pourpse is to run a program.
* Docker Image is a single file with all the dependencies and configurations required to run a program.
* Docker contains two things mainly Docker Client(Docker CLI) and Docker Server(Docker Dameon)
    * Docker CLI is the tool which we issue commands to
    * Docker server is the tool responsible for Creating images, Running container and all other things.
* Simple commands to test
    * docker version - gives version and other details, used to see whether docker installed succesfully
    * docker run hello-world - command to run a simple docker image to see if everything is working fine
* Steps done when you type docker run hello-world in terminal
    * first command is taken by docker-cli and processed and sent to docker server.
    * Docker server first checks if hello-world image local copy is present in image cache or not.
    * If it is not present docker server connects to docker hub(free repository of images) and downloads the required image file and save it in local image cache.
    * Docker server now took the image loaded into memory created a container out of it and ran a single program inside it.
    * If we run the same command again we don't need to download it as it can be used directly from local.
* Namespacing - isolating the resources(hardware, access, network etc.) for a process or group of processes 
* Control groups - Limit the amount of resources(memory, cpu etc) used per process
* Container is a process or set of process with certain resources avaialable
* Docker image has file system(copy paste of specific set of directories) snapshot. Image also contains specific startup commands
* Image is taken a subset of hardware and other resources allocated and files from filesystem are pasted and commands run.
* Namespacing and control groups belong to linux. When docker is installed Linux virtual machine is installed.

### Section 2
* Docker Image contains File System snapshot and startup command after creating container.
* Docker run <name of image> - gets the image, makes container and runs startup command
* Docker run <Image name> <some command> - this will override the startup command in image and runs the command we provided
   * Ex: Docker run busybox echo hi there!
* The command which is overriding should be present in the Filesystem otherwise we get error
* docker ps - gives list of all the running containers
* docker ps --all - gives list of all the containers created
* docker run is equivalent to docker create + docker start
* docker create hello-world - creates the container and gives a string where container is located
* docker start -a <string where container is> this runs the container and gives output in console, without -a output is not displayed
* docker ps -all gives status of containers present in the system. If it shows exited that means container was started and stopped.
* Exited container can be run again using docker start -a <container id>
* while running the container if you use command to overide start. While running the container again same command is executed.
* docker system prune - deletes all containers, network allocations, related images
* docker logs <container id> gives the output logs when container was ran previously. if you excluded -a while starting. you can use this.
* docker stop <container id> - gives sigterm(signal termination) command to container which gives time for container to close the required things and stop
* docker kill <sontainer id> - instantaneously stops the container
* if after giving docker stop if container takes more than 10 seconds it is killed instantly.
* docker exec <container id> <command> - runs the command inside the container
* docker exec -it <container id> <command> - runs the command inside the container and allows us to give the input
* when you are running a process in container you are actually running in a linux vm
* Every process inside a linux channel has three(STDIN, STDOUT, STDERR) communication process attached to it.
* docker exec -it <container id> sh - gives shell access to the container
* docker run -it <container id> sh - starts the container and gives us shell access to it
* two containers are completely seperate and isolated from each other

### Section 3
