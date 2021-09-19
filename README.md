# Docker Introduction

## Docker Introduction
- What problems we have with Traditional Infra?
- Why do we need to use Docker? 
- What are advantages of using Docker?
-  For introduction slides refer the [presentation slides](/otherfiles/presentation/Docker-Fundamentals-v1.pdf). 


# Docker Architecture

## Understand Docker Architecture & Docker Terminology
- What is Docker Daemon? 
- What is Docker Client?
- What are Docker Images?
- What are Docker Containers?
- What is Docker Registry or Docker Hub?
-  Refer the [presentation slides](/otherfiles/presentation/Docker-Fundamentals-v1.pdf). 


## Docker Installations
- https://docs.docker.com/install/

## Docker Desktop on Windows
- https://docs.docker.com/docker-for-windows/

## Docker Desktop on MAC
- https://docs.docker.com/docker-for-mac/

### Troubleshooting Docker Desktop issues on MAC
- Docker Desktop on mac has an issue with MAC **osxkeychain**
- To fix it perform the below steps.
- **Pre-requisite:** Refer below link for additional understanding
	- https://medium.com/@dakshika/error-creating-the-docker-image-on-macos-wso2-enterprise-integrator-tooling-dfb5b537b44e
- **Step-1:** Docker Desktop changes
	- Open Docker Desktop --> Preferences
	- Uncheck the option named **Securely store Docker logins in macOS keychain**
- **Step-2:** Go to **config.json** file in **.docker** folder		
	- Sample Reference Location: 
		- /Users/<userid>/.docker/config.json
		- ~/.docker/config.json
	- Remove the line **“credSstore” : “osxkeychain”,** in config.json


 
