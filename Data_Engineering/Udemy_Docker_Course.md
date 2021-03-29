# Docker

* Docker makes it very easy to install and run software without worrying about setup and dependencies.
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
