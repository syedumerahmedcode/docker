# Docker

Video Link: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana

Timestamp: 2:09:30

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

- It is also possible to name the containers with a specific name. For example, if we run the following command: _docker run -d -p6001:6379 --name redis-older redis:4.0_. Now, if the user runs _docker ps_, one can see that the conatiner has a name _"redis-older"_.


- **docker ps**: It shows a list of running conatiners. For example, after executing 'docker run -it --rm busybox' on the machine, it will be shown with a container id when _docker ps_ is executed. here, _-a_ flag, lists running as well as stopped containers.

- **docker images**: It is used to get a list of all images on the machine.

- **docker pull [image_name]**: This pulls the docker image from the _dockerhub or some private_ repository. For example, _docker pull busybox_

- **docker stop [container_id]**: This will stop the container. For example: _docker stop 7b601211ae47_

- **docker start [container_id]**: This will start the container. For example: _docker start 7b601211ae47_. Please note that _docker run_ works with _images_ whereas _docker start_ works with _containers_.

- **docker logs [container_id]**: This prints out the logs of the container. For example: _docker logs 7b601211ae47_
- By adding _-f_ , the logs are displayed continuously on the screen.

- **docker exec -it [container_id]**: This is used for starting and interactive terminal and browse inside a container. For example: by running _docker exec -it 54d0a544de2e /bin/bash_, the user lands inside the container and has root access to the file system.

- **docker network ls**: Prints out a list of auto generated docker network.

- **docker netwrok create [network_name]**: This creates a docker network with the given name. For example, _docker netwrok create mongo-network_.

- docker network create mongo-network 
- docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo    
- docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express   

- **docker rm [container_id]**: Removes the container from docker. Here, the __container_id__ can be fetched via _docker ps_.

- **docker rmi [image_id]**: Removes the docker image.  Here, the __image_id__ can be fetched via _docker images_.

- **docker build -t [image_name]:[version_numer]**: Used for building a docker image. Here, __image_name__ is mandatory but __version_number__ is optional.

- **docker build -t my-app:1.0**: Used for building a docker image. Here, instead of _my-app:1.0_, please replace it with the __[application_name]:[version_number]__.

- **docker run my-app:1.0**: Used for running a docker image. Here, instead of _my-app:1.0_, please replace it with the __[application_name]:[version_number]__.






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

For eaxmple: container has port: 3000 whereas host has port:3001. now, after port binding, if one writes command: some-app://localhost:3001, it will connect to port's 3000 port. In other wods, _3000:3000_ means that the port of the host machine (left side 3000) is connected to the port of the container(right side 3000).

In real world, the following command: docker run -p6000:6379 redis, means that _6000_ port of host machine is connected to the _6379_ port of the container.

# Docker Network

- **Docker network**:: Docker creates its own isolated network where the containers are running in. So, if two or more containers are deployed in the same docker network, they can talk to each other using just the container name as in, they do not need losthost or port number etc. Just the container name is enough as they are in the same network.

# Add missing parts of how to run the node js application once the tutorial is finished!--> Logs in the github readme of Nana.

# Docker Compose

- With docker compose, we can take dockers commands (with their configurations) and map it to a file so that we have structured commands.
- Note: The docker compose takes care of creating a common network for docker containers by itself.
- Note: indentation in yaml-file is important.

Command: **docker-compose -f** _[filename]_ **up**

Note: By default, the data ppresent in the docker container is lost once the docker compose file is shutdown and started up again. In order to persist data after shutdown of docker compose, **Docker volumes** can be used. **Docker Volumes** are used for _data persistence_.

Command: **docker-compose -f** _[filename]_ **down**
This command shutdolwns the docker container created from the _docker compose_ file and in addition, it will also shutdown the docker network that it created when _up_ command was executed.

# Docker File

- A docker file is blueprint for building docker images.
# Syntax of a Docker file
- **FROM**:Start by basing it on another image. For example, FROM node, which hsa the same affect as _docker pull node_.
- **ENV**: Used for configuring environment variable in a docker file.
- **RUN**: Used for executing any linux command. the directories created using _RUN_ command are created inside the docker container and NOT inside the host machine.
- **COPY**: Copies the file from the host machine to inside the container image.
- **CMD**: It acts as the entrypoint for the docker file. In concept, this is similar to **main()** in _Java_.

**Relationship between RUN and CMD command**:
- CMD is marked as an entrypoint command for the Docker file. In other words, you can run _multiple_ RUN commands but only _one_ CMD command.

**Note:**
- Whe we adjust the Dockerfile, we must **rebuild** the image. This is because the old image is not overwritten (so to say no hot deploy for the docker image).

# Private Docker Registry
- **Docker private repository**: In case of Amazon, one can use Amazon Elastic Container Services(Amazon ECS). It has one repository per image. Here, one saves and stores different tags (versions) of the same image.
- Registry options
- **Build and tag an image**:
- _Image nameing in docker registries_:registryDomain/imageName:tag
- docker tag = rename the image.
- **Docker login**: in case of AWS, the pre-requisite are:
- The AWS Cli needs to be installed.
- Credentials are configured.
- **Docker push**:
- One has to always login to the private repository i.e. _docker login_. 
- 






# What to do if?

- How to fix docker: Got permission denied issue
https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue
