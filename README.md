# Docker Installation

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


 
 # Flow-1: Create a new Docker Image, Run as Container and Push to Docker Hub

## Pre-requisite Step
- Create your Docker hub account. 
- https://hub.docker.com/
- **Important Note**: In the below listed commands wherever you see **stacksimplify** you can replace with your docker hub account id. 


## Step-1: Run the base Nginx container
- Access the URL http://localhost
```
docker run --name mynginxdefault -p 80:80 -d nginx
docker ps
docker stop mynginxdefault
```

## Step-2: Create Dockerfile and copy our customized index.html
- **Dockerfile**
```
FROM nginx
COPY index.html /usr/share/nginx/html
```

## Step-3: Build Docker Image & run it
```
docker build -t stacksimplify/mynginx_image1:v1 .
docker run --name mynginx1 -p 80:80 -d stacksimplify/mynginx_image1:v1

Replace your docker hub account Id
docker build -t <your-docker-hub-id>/mynginx_image1:v1 .
docker run --name mynginx1 -p 80:80 -d <your-docker-hub-id>/mynginx_image1:v1
```

## Step-4: Tag & push the Docker image to docker hub
```
docker images
docker tag stacksimplify/mynginx_image1:v1 stacksimplify/mynginx_image1:v1-release
docker push stacksimplify/mynginx_image1:v1-release

Replace your docker hub account Id
docker tag <your-docker-hub-id>/mynginx_image1:v1 <your-docker-hub-id>/mynginx_image1:v1-release
docker push <your-docker-hub-id>/mynginx_image1:v1-release
```
## Step-5: Verify the same on docker hub
- Login to docker hub and verify the image we have pushed
- Url: https://hub.docker.com/repositories

 # Flow-2: Pull Docker Image from Docker Hub and Run it

## Step-1: Verify Docker version and also login to Docker Hub
```
docker version
docker login
```

## Step-2: Pull Image from Docker Hub
```
docker pull stacksimplify/dockerintro-springboot-helloworld-rest-api:1.0.0-RELEASE
```

## Step-3: Run the downloaded Docker Image & Access the Application
- Copy the docker image name from Docker Hub
```
docker run --name app1 -p 80:8080 -d stacksimplify/dockerintro-springboot-helloworld-rest-api:1.0.0-RELEASE
http://localhost/hello

# For Mac with Apple Chips (use different application)
Step-1: Install Docker with Apple Chips binary (https://docs.docker.com/desktop/mac/install/) on your mac machine

Step-2: Run the simple Nginx Application container. 
docker run --name kube1 -p 80:80 --platform linux/amd64 -d  stacksimplify/kubenginx:1.0.0
http://localhost

## Sample Output
kalyanreddy@Kalyans-Mac-mini-2 ~ % docker run --name kube1 -p 80:80 --platform linux/amd64 -d  stacksimplify/kubenginx:1.0.0
370f238d97556813a4978572d24983d6aaf80d4300828a57f27cda3d3d8f0fec
kalyanreddy@Kalyans-Mac-mini-2 ~ % curl http://localhost
<!DOCTYPE html>
<html>
   <body style="background-color:lightgoldenrodyellow;">
      <h1>Welcome to Stack Simplify</h1>
      <p>Kubernetes Fundamentals Demo</p>
      <p>Application Version: V1</p>
   </body>
</html>%
kalyanreddy@Kalyans-Mac-mini-2 ~ % 

```

## Step-4: List Running Containers
```
docker ps
docker ps -a
docker ps -a -q
```

## Step-5: Connect to Container Terminal
```
docker exec -it <container-name> /bin/sh
```

## Step-6: Container Stop, Start 
```
docker stop <container-name>
docker start  <container-name>
```

## Step-7: Remove Container 
```
docker stop <container-name> 
docker rm <container-name>
```

## Step-8: Remove Image
```
docker images
docker rmi  <image-id>
docker rm $(docker ps -a -q)
```




# Docker - Essential Commands
- The below are the list of essential commands we are in need 

|     Commands                 |    Description                                  |
| ------------------------------- | --------------------------------------------- |
| docker ps | List all running containers |
| docker ps -a | List all containers stopped, running |
| docker stop container-id | Stop the container which is running |
| docker start container-id | Start the container which is stopped |
| docker restart container-id | Restart the container which is running |
| docker port container-id | List port mappings of a specific container |
| docker rm container-id or name | Remove the stopped container |
| docker rm -f container-id or name| Remove the running container forcefully |
| docker pull image-info | Pull the image from docker hub repository |
| docker pull stacksimplify/springboot-helloworld-rest-api:2.0.0-RELEASE | Pull the image from docker hub repository |
| docker exec -it container-name /bin/sh | Connect to linux container and execute commands in container |
| docker rmi image-id | Remove the docker image |
| docker logout | Logout from docker hub |
| docker login -u username -p password | Login to docker hub |
| docker stats | Display a live stream of container(s) resource usage statistics |
| docker top container-id or name | Display the running processes of a container |
| docker version | Show the Docker version information |
