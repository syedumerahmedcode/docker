# docker

Video Link: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana
Timestamp: 57:22

# Container
- A container is a way to **package** an application with **all** the necessary **dependencies** and **configuration**.

- It creates a _portable artifact_ which can be easily shared and moved around.

# Where do containers live?
- In a _container repository_, this is of two types:
- - **Private repository**: This belongs to a company as in a company has there own private repository.
- - **Public repository**: DockerHub is a public repository which anayone can access.

# Docker commands
- **docker run [image_name]:[specific_version_number_if_needed]**: This will run the docker image which is available of the machine. In simple words, it pulls the image (if it does not exist on the local machine) and starts new container. By add _-d_ flag, we can start the container in detached mode.

- docker run = _docker pull_ + _docker start_

- **docker ps**: It shows a list of running conatiners. For example, after executing 'docker run -it --rm busybox' on the machine, it will be shown with a container id when _docker ps_ is executed. here, _-a_ flag, lists running as well as stopped containers.

- **docker images**: It is used to get a list of all images on the machine.

- **docker pull [image_name]**: This pulls the docker image from the _dockerhub or some private_ repository. For example, docker pull busybox

- **docker stop [container_id]**: This will stop the container. for example: docker stop 7b601211ae47

- **docker start [container_id]**: This will start the container. for example: docker start 7b601211ae47

# Docker Image
- This is the actual image. In simple words, this is the artifactg which is shipped around and it contains the configuration, application and the start script.
- It is not running on the machine.

# Docker Container
- It actually start the application.
- A container is the running environment for the image.
- It is running on the machine.
- One can talk to the application running inside a conatiner using a port.

# Docker vs Virtual Machine
- All operating systems are made up of the following layers:
- - Application
- - OS Kernel
- - Hardware

- Docker virtualizes _only the Application layer_ whereas Virtual Machine virtualizes _both Application and OS Kernel_ layers.
- Size of docker images is much smaller comapred to virtal machine.
- Speed: Docker containers start and run much faster.
- Compatibility: VM of any OS can run on any OS host.That is not true for Docker and due to this , in th eolder versions of OS, one needs to install Docker Toolbox.



- **Scenario:** What if two different version of same application (for example, redist latest vs redis:4.0) are running on the same machine and they both listen to the same port i.e. 5000? Wat will happen now when I run both of them and try to connect with a specific vertsion?

This is resolved via port binding.

- **Container Port vs Host Port:**
- Multiple containers can run on your host machine.
- You laptop has only certain ports available.
- Conflict happens when same port is used by two or more containers on host machine.
- This is done via port binding. After port binding is done, we can connect the container port to the host port.

For eaxmple: conatiner has port: 3000 whereas host has port:3001. now, afetr port binding, if one writes command: some-app://localhost:3001, it will connect to port's 3000 port. 

In real world, the following command: docker run -p6000:6379 redis, means that _6000_ port of host machine is connected to the _6379_ port of the container.

# What to do if?

- How to fix docker: Got permission denied issue
https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue
