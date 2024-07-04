# docker

Video Link: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana
Timestamp: 23:53

# Container
- A container is a way to **package** an application with **all** the necessary **dependencies** and **configuration**.

- It creates a _portable artifact_ which can be easily shared and moved around.

# Where do containers live?
- In a _container repository_, this is of two types:
- - **Private repository**: This belongs to a company as in a company has there own private repository.
- - **Public repository**: DockerHub is a public repository which anayone can access.

# Docker commands
- **docker run [image_name]:[specific_version_number_if_needed]**: For example, docker pull busybox

- **docker ps**: It shows the running conatiners. For example, after executing 'docker run -it --rm busybox' on the machine, it will be shown with a container id when _docker ps_ is executed.

# Docker Image
- This is the actual image. In simple words, this is the artifactg which is shipped around and it contains the configuration, application and the start script.
- It is not running on the machine.

# Docker Container
- It actually start the application.
- A container environment is created.
- It is running on the machine.

# Docker vs Virtual Machine
- All operating systems are made up of the following layers:
- - Application
- - OS Kernel
- - Hardware

- Docker virtualizes _only the Application layer_ whereas Virtual Machine virtualizes _both Application and OS Kernel_ layers.
- Size of docker images is much smaller comapred to virtal machine.
- Speed: Docker containers start and run much faster.
- Compatibility: VM of any OS can run on any OS host.That is not true for Docker and due to this , in th eolder versions of OS, one needs to install Docker Toolbox.




# What to do if?

- How to fix docker: Got permission denied issue
https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue
