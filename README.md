# docker

Video Link: https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana
Timestamp: 16:08

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


# What to do if?

- How to fix docker: Got permission denied issue
https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue
