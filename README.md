## TKH-Group-2-Docker
> _Authors: Zedd Chisholm, Shantericka Greene_


# HOW TO DOWNLOAD AND INSTALL DOCKER ON WINDOWS
I. Complete Documentation of Download, Installation, and Configuration

## A. Introduction
Purpose of the documentation.
Overview of Docker and its significance.

## B. Downloading Docker
Choosing the correct Docker version for your system (Desktop/Cloud).
Navigating to the official Docker website.
Downloading the Docker installer for the chosen platform.

## C. Installing Docker
Running the Docker installer.
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

- **Pulling Ubuntu Desktop/Server  Image:**
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
Running a CentOS container.
Command to initiate and access the container.
Running an Ubuntu Desktop/Server container.
Command to initiate and access the container.
Running a Kali container.
Command to initiate and access the container.
Explanation of common options used in docker run (e.g., -d, -it, --name).

## G. Verifying Container Functionality
Accessing each container via terminal or SSH (if applicable).
Performing basic operations inside the containers to ensure they are running correctly.
Updating package lists.
Installing software.
Navigating the filesystem.



### H. Docker Management Commands
$  docker build -t welcome-to-docker .
	tell Docker to package the application
	-t flag tags your image with the name ‘welcome-to-docker’. This tag identifies it.
	.  tells Docker to find our file in the current working directory

$  docker images
	show all images on this computer, and 5 detail columns. Runs globally from any directory. The columns are:
    * REPOSITORY  :  the name of the image. Is often the name of the directory the files are located in.  (Ex:  ubuntu-image)
    * TAG  :  the tag is the version of the image.  (Ex:  latest)
    * IMAGE ID  :  a unique identifier for each image.  (Ex:  91ecc778ac05)
    * CREATED  :  how long ago the image was created.  (Ex:  15 hours ago)
    * SIZE  :  the size of the image  (Ex:  139MB)

$  docker run <REPOSITORY_NAME>
	start a new Docker container from the image.  (Ex:  docker run hello-docker)

$  docker ps --all
	list all running Docker containers. Similar to listing running processes in Unix terminal.

$  docker stop <CONTAINER_ID>
	stop a running Docker container.  (Ex:  docker stop 91ecc778ac05)

$  docker rm <OPTION> <CONTAINER_ID>
	remove a Docker container. Options:
* -v or --volumes  :  also remove its volumes.  (Ex:  docker rm -v 91ecc778ac05)
* -f or --force  :  force remove if container is currently running.  (Ex:  docker rm -f 91ecc778ac05)

$  docker search <IMAGE_NAME>
	search for images in Docker Hub.  (Ex:  docker search ubuntu)

$  docker pull <IMAGE_NAME> <TAG>
	pulls the specified image from Docker Hub. Ommitting the tag pulls latest. (Ex:  docker pull neurodebian)



## I. Troubleshooting Common Issues
Docker daemon not starting.
Issues pulling images from Docker Hub.
Containers exiting immediately after starting.

## J. Conclusion
Summary of the tasks accomplished.
Reflection on the learning process and the utility of Docker.

## K. Appendices
Screenshots of the installation process, Docker running, and containers in operation.
Additional resources for further learning.

