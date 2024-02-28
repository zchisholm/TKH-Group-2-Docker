# HOW TO DOWNLOAD AND INSTALL DOCKER ON WINDOWS

> _Authors: Ivan Castillo, Zedd Chisholm, Shantericka Greene_

![Group Banner](/assets/images/TKH-Group-2-Docker-Doc-Banner.jpg)

I. Complete Documentation of Download, Installation, and Configuration

## A. Introduction

**Purpose of the documentation**

The purpose of this documentation is to successfully download Docker for Windows/macOS
Overview of Docker and its significance.
Docker is a platform that allows you to packages, distribute, and run applications in a containerized environment, making it easier to deploy and manage applications across different environments.

## B. Downloading Docker
**Choosing the correct Docker version for your system (Desktop/Cloud)**

When choosing the correct Docker version for your system, it is important to consider the following factors: compatibility, system requirements, support and documentation, cloud, and stability versus cutting edge features.

**Navigating to the official Docker website.**

Downloading the Docker installer for the chosen platform.
Ensure you click on the download link for chosen platform (e.g., Windows, macOS, Linux).

## C. Installing Docker
**To download Docker desktop:**
1. click the link https://www.docker.com/
2. In the top left corner, go to the "Products" drop down button and click on "Docker Desktop"
3. Download either the Mac/Windows version by clicking the link and saving it 
4. Once software is downloaded, open Docker desktop
5. Accept "Docker Subscription Service Agreement"
6. Choose the "recommended settings" and click "Finish"
7. Access your terminal and enter command "docker version"

Following on-screen instructions to complete the installation.
Windows/Mac: Using Docker Desktop.
Linux: Installing Docker Engine.
Verifying Docker installation.
Opening a terminal or command prompt.
Running docker --version to check the installed version.

## D. Configuring Docker (Post-Installation Steps)

### Setting up Docker to Start on Boot (if required)

To ensure Docker runs automatically at system startup:

- **For Linux:**

  ```bash
  sudo systemctl enable docker

  ```

- **For Windows:**
  Docker Desktop will start automatically by default. You can adjust this setting in Docker Desktop's General settings.

- **For Windows:**
  Similar to Windows, Docker Desktop will automatically start. This can be adjusted in the Docker Desktop's Preferences.

### Adjusting Docker's resource allocation (optional)

- **Docker Desktop:**
  Go to Settings (or Preferences on macOS) > Resources to adjust CPUs, Memory, Swap, and Disk Image size as per your requirement.

- **For Docker Engine on Linux:**
  Edit the /etc/docker/daemon.json file and restart Docker to apply changes:
  ```json
  {
    "resources": {
      "cpus": "2",
      "memory": "4g"
    }
  }
  ```

### Configuring Docker for use without sudo (Linux specific)

To run Docker commands without sudo:

1. Add your user to the docker group:

```bash
sudo usermod -aG docker $USER
```

2. Log out and log back in for the group changes to take effect.

## E. Pulling Container Images

### Accessing Docker Hub from the command line

Ensure you have an active internet connection and Docker is running. Use the docker search command to find images on Docker Hub.

### Pulling Images for CentOS, Ubuntu Desktop/Server, and Kali

- **Pulling CentOS Image:**

```bash
docker pull centos
```

- **Pulling Ubuntu Desktop/Server Image:**

```bash
docker pull ubuntu
```

- **Pulling Kali Linux Image:**

```bash
docker pull kalilinux/kali-rolling
```

### Verifying the images are pulled successfully

To verify that the images have been pulled correctly, list all downloaded Docker images:

```bash
docker images
```

You should see the CentOS, Ubuntu, and Kali Linux images listed among your downloaded images.

![Screenshot of a 'docker images' command results with the three images in yellow.](/assets/images/Docker-Images-CMD.jpg)

## F. Running Containers

### Running a CentOS Container

To run a CentOS container and access its shell:

```bash
docker run -it --name my_centos centos /bin/bash
```

### Running an Ubuntu Desktop/Server Container

To run an Ubuntu container and access its shell:

```bash
docker run -it --name my_ubuntu ubuntu /bin/bash
```

### Running a Kali Container

To run a Kali Linux container and access its shell:

```bash
docker run -it --name my_kali kalilinux/kali-rolling /bin/bash
```

### Explanation of Common Options Used in docker run

- `-d`: Run container in detached mode (in the background).
- `-it`: Allocate a pseudo-TTY connected to the container’s stdin; creating an interactive bash shell in the container.
- `--name`: Assign a name to the container. If you don't specify a name, Docker will generate a random one for you.
- `/bin/bash`: Runs the Bash shell in the container, providing you with interactive shell access.

After running these commands, you will have active containers for CentOS, Ubuntu, and Kali Linux. You can interact with each container's shell, allowing you to execute commands within the container as if you were logged into a CentOS, Ubuntu, or Kali Linux system directly.

Remember, when you are finished with a container, you can exit the bash shell by typing exit. This will stop the container. You can restart it anytime with docker start <container_name> and attach to it again using docker attach <container_name> or docker exec -it <container_name> /bin/bash for a new shell session.

## G. Verifying Container Functionality

Accessing each container via terminal or SSH (if applicable).
Performing basic operations inside the containers to ensure they are running correctly.
Updating package lists.
Installing software.
Navigating the filesystem.

## H. Docker Management Commands

**Package Application**
Tell Docker to package the application

```bash
$  docker build -t welcome-to-docker .
```

- `-t` flag tags your image with the name ‘welcome-to-docker’. This tag identifies it.
- `.` tells Docker to find our file in the current working directory

**Show Images**
Show all image on this computer, and 5 detail columns. Runs globally from any directory.

```bash
$  docker images
```

The columns are:

- REPOSITORY : the name of the image. Is often the name of the directory the files are located in. (Ex: ubuntu-image)
- TAG : the tag is the version of the image. (Ex: latest)
- IMAGE ID : a unique identifier for each image. (Ex: 91ecc778ac05)
- CREATED : how long ago the image was created. (Ex: 15 hours ago)
- SIZE : the size of the image (Ex: 139MB)

**Run an Image**

Start a new Docker container from the image.

```
$  docker run <REPOSITORY_NAME>
```

**List Running Containers**

List all running Docker containers. Similar to listing running processes in Unix terminal.

```
$  docker ps --all
```

**Stop a Container**

Stop a running Docker container. (Ex: docker stop 91ecc778ac05)

```
$  docker stop <CONTAINER_ID>
```

**Remove a Container**

Remove a Docker container.

```
$  docker rm <OPTION> <CONTAINER_ID>
```

    Options:
        - -v or --volumes  :  also remove its volumes.  (Ex:  docker rm -v 91ecc778ac05)
        - -f or --force  :  force remove if container is currently running.  (Ex:  docker rm -f 91ecc778ac05)

**Search for Images**

Search for images in Docker Hub. (Ex: docker search ubuntu)

```
$  docker search <IMAGE_NAME>
```

**Pull an Image**

Pulls the specified image from Docker Hub. Ommitting the tag pulls latest. (Ex: docker pull neurodebian)

```
$  docker pull <IMAGE_NAME> <TAG>
```

## I. Troubleshooting Common Issues

### Docker daemon not starting

- **On Linux:**
  - Ensure the Docker service is enabled to start at boot:
    ```bash
    sudo systemctl enable docker
    ```
  - Try starting the Docker service manually:
    ```bash
    sudo systemctl start docker
    ```
  - Check the Docker daemon logs for errors:
    ```bash
    journalctl -u docker.service
    ```

- **On Windows and macOS:**
  - Restart Docker Desktop.
  - Check Docker Desktop settings to ensure it's allocated enough resources.
  - Reinstall Docker Desktop if the issue persists, ensuring you download the latest

### Issues pulling images from Docker Hub
- Ensure you have a stable internet connection.
- Check if Docker Hub is experiencing downtime or operational issues by visiting their status page.
- If you're behind a proxy, configure Docker to use the proxy settings:
  - On Docker Desktop, you can set this in the network settings.
  - On Linux, configure the proxy settings in the Docker daemon configuration file.


### Containers exiting immediately after starting
- Containers usually exit immediately if the main process fails to start or encounters an error. To diagnose:
  - Check the container logs:
    ```bash
    docker logs <container_name_or_id>
    ```
  - Ensure the command you're trying to run inside the container is correct. For instance, using an incorrect base image tag might not include the binaries you're trying to execute.
  - Some applications require a foreground process. Ensure your Dockerfile CMD or ENTRYPOINT instructions are correctly configured to keep the container running.

## J. Conclusion
Summary of the tasks accomplished.
Reflection on the learning process and the utility of Docker.
