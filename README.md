# Challenge: Dockerized Tomcat Deployment

This repository contains a Dockerfile and with the supporting files to deploy a sample web app (sample.war) in a Tomcat container using SSL/TLS.

## Requirements
- Docker must expose port 4041;
- Tomcat version is 8.5
- The docker base image is centos:7
- No manual commands should be required after the docker run command is executed in order to start and make the Sample App available.
- SSL/TLS is enabled at the 4041 endpoint.

## Steps 

### 1. Clone Repository
Clone this repository with the command: ``git clone https://github.com/EmaTavares/Challenge.git``

### 2. Generate SSL Certificates
You can generate a private key and its certificate using the command: ``openssl req -newkey rsa:2048 -nodes -keyout privateKey.key -x509 -days 365 -out certificate.crt -subj "/C=PT/ST=Lisbon/L=Lisbon/O=Challenge/OU=Challenge/CN=localhost``
> Note that this pair is only available for 365 days.

### 3. Build the Docker Container
You can build the container in the project directory with the command: ``docker build -t <yourDockerName> .``

### 4. Run the Docker Container 
To run the container you can use the command: ``docker run -d -p 4041:4041 <yourDockerName>``
> Note that the command ``docker run -p 4041:4041 <yourDockerName>`` is also valid, but will display its output in the terminal

### 5. Access the WAR
Open your web browser and go to https://localhost:4041/sample
> In some instances the connection may not be secure because the SSL certificate is self-signed.

### 6. Extra Steps
The following steps are not mandatory to execute the Dockerfile!

#### a) Check If the Container Is Running
Use the command: ``docker ps``
#### b) Explore the Container's File System
Use the commad ``docker exec -it <containerId> bash`` and the commands ``ls`` and ``cd <pathOfYourChoice>`` to explore inside the container
#### c) Check If Tomcat was successfully installed
Go to your web browser and go to https://localhost:4041
#### d) Stop Container 
Use the commad ``docker stop <containerId>``

## Files Delivered
- Dockerfile
- README.md
- certificate.crt (CA public certificate)
- privateKey.key (CA private key)



