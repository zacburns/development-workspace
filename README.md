# What is the Development Workspace?

[Development Workspace](https://github.com/ambitus/linux-containers/tree/master/examples/development-image) is a ubuntu based development tool that is intended to consolidate a number of commonly used compilers and build tools along with other development utilities to faciliate the creation of Docker images in zCX. From within a running development container a user should be able to download their source repositories, compile source on the s390x architecture and create a Dockerfile that executes the compiled resource alongside any other necessary resources. Due to the size of this image it should **NEVER** be used as a base image for production images.

### Applications contained within:

- bash 4.4.19
- Docker  18.06.0
- SSH/SFTP
- GIT
- vim
- curl
- gcc  8.3  
- Ant  1.10.3
- IBMJava  1.8.0_sr6fp10 
- Maven  3.6.0 
- Go  1.13.12 
- Gradle  6.5 
- Python  3.7


# How to use this image
By default this image is stateless, any artifacts built within will not persist. Use docker volumes to provide persistence as needed.

## Usage
The development workspace image can be started like any other container in interactive mode:  
`docker run --rm -it  quay.io/ibmz/development-workspace:1.0`
  
If you intend to use docker commands from within the development workspace then you should make sure to mount the parent docker socket when starting the image:  
`docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock:ro  quay.io/ibmz/development-workspace:1.0`
