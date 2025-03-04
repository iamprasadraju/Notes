# What is Docker ?


Docker is an open-sourec platform taht enables developers to automate the deployment, scaling and management of applications using **containerization**. Containers are lightweight, portable, and efficient environments that include everything needed to run an application code, runtime, libraries, and dependencies

### Key Features of Docker:

- **Lightweight**: Containers share thehost OS Kernel, making them more efficient than virtual machines (VMs)

- **Portability**: Containers run consistently across different environments (local, testing, production).

- **Scalability**: Easily scale applications by spinning up multiple containers.

- **Isolation**: Each Container runs independently, preventing conflicts between dependencies.

- **Fast Deployments**: Containers start up quickly comparred to VMs.


### Why Use Docker ?

- Eliminates: "IT works on machine" problems

- Simplifies software deployment and version control

- Works seamlessly with CI/CD pipeliners.

- Optimizes resource usage compared to VMs.


# Docker Architecture

Docker follows a client-server architecture, consisting of the following key components:


### 1.Docker Client 

The Docker Client (docker CLI) is the command-line tool used to interact with the Docker Daemon.

- Commands like ```docker run```, ``` docker build```, ``` docker ps ``` are sent to the daemon.

- The client communicates with the deamon via **REST API**, **UNIX socket**, or ***network interface***.


### 2. Docker Daemon (dockerd)

The Docker Daemon runs in the background and manages Docker objects like containers, images, networks, and volumes.

- It listens for client requests and handles container lifecycle (start, stop, remove).

- It communicates with the Docker Registry to fetch or store container images.


### 3. Docker Objects 

Docker users various Objects to manage applications efficiently:

- **Containers:** Runnimg instances of Docker images.
- **Images:**  Read-only templates with application code and dependencies.
- **Volumes:** Persistent storage for containers.
- **Networks:** Isolated environments for containers for container communication.

### 4. Docker Registry (Docker Hub or Private Registry)

The Docker Registry stores and distributes container images.

- **Docker Hub**(public) provides pre-built images.
- **Private registries** allow enterpries to store custom images securely.

### 5. Docker Engine

Docker Engine is the core component that runs on the host system and includes:

- Docker Daemon(dockerd)
- REST API for communication
- CLI (Command-Line Interface)

### How it works (Flow):

1. The Docker Client sends a request to Daemon (docker run hello-world)

2. The Daemon checks if the required image exists locally. if not, it pulls from Docker Hub.

3. The Daemon creates and runs the container using the image.

4. The application runs inside the container in an isolated environment.



![Docker Architecture](https://docs.docker.com/get-started/images/docker-architecture.webp)


Key components - **Dockerfile**, **Docker Image**, and **Docker Container**


## 1. Dockefile

A Dockerfile is a script conatining a set of instructions to build a Docker image. it defines the base image, dependencies, environment setup, and the appliction to run.

Example Dockerfile:

```
# Use an official Python image as the base
FROM python:3.9  

# Set the working directory inside the container
WORKDIR /app  

# Copy files from the local system to the container
COPY . /app  

# Install dependencies
RUN pip install -r requirements.txt  

# Define the command to run the application
CMD ["python", "app.py"]  

```

Key Instructions in a Dockerfile:

- **FROM** → Defines the base image (e.g., ```python:3.9```).
- **WORKDIR** → Sets the working directory inside the container.
- **COPY** → Copies files from the local machine to the container.
- **RUN** → Executes commands during the image build process.
- **CMD** → Defines the default command to run when the container starts.

## 2. Docker image

A docker Image is a lightweight, standalone, and executable package that includes everything needed to run a container: code, runtime, libaries, and dependencies.

**How to Build a Docker Image?**

Run the following command inside the directory containing the ```Dockerfile```:
```
docker built -t myapp .
```
- ```-t myapp``` → Tags the image with the name "myapp".
- ```.``` → Refers to the current directory (where the Dockerfile is located).

**List All Docker Images on Host machine:**

```
docker images
```

## 3. Docker Conatiner:

A **Docker Container** is a running instance of a Docker Image. Containers are lightweight, isolated environments that execute applictaions.

**How to Run a Container?**
```
docker run -d -p 5000:5000 myapp
```

- ```-d``` → Runs the container in detached mode (background).

- ```-p 5000:5000``` → Maps port 5000 of the container to port 5000 on the host.

- ```myapp``` → Name of the image to run.

**Check Runninf Containers:**

```
docker ps
```

**Stop and Remove a Container:**

```
docker stop <container_id>
docker rm <container_id>
```
