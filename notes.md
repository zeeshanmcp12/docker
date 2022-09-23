# Docker Basics

## to search any tool / image on docker hub
docker search busybox

docker run -P -d
-P -> map the port of container with any port of our host
-d -> start the container in detach mode

docker run -p 80:80
-p -> (small letter): map the port 80(right side of colon) of container with port 80(left side of colon) of host

docker run -d <image_name>
this -d should always be at the very end of command (as a best practice)

### Docker commands
docker search <image>
docker run <image_name>
docker ps -> list containers
docker ps -a -> list all containers even they are exited
docker images -> list all images
docker rmi <image_name>
docker stop <container_id> -> stop container
docker start <container_id> -> start stopped container
docker rm <container_id> -> remove container
docker rm $(docker ps -aq) -> remove all exited containers
docker run -v "$PWD" -> mount current working directory as a volume in container
Note: we cannot type only ".(dot)" as we have to define absolute path in quotes
docker logs <container_name>
Note: when docker container starts it send error to standard out and standard error.
docker build -t <image_name> . -> (. dot) means current working directory
docker volume ls -> list the volumes (persistent storage)

docker inspect <container_name> -> to extract the details of containers for example, IP, port, service etc
docker exec -it <container_name> bash -> start container in interactive mode and execute "bash" command or run shell in the container.
    - exec -> execute the command
    - -it -> interactive mode and connect with teletype terminal
    - <container_name> -> container name
    - bash -> we want to execute bash command when connect/login with interactive mode. i.e.


### Verify if nginx/apache web server
curl localhost
curl -i localhost -> to add the headers in request

docker run -p 3080:80 -v "$PWD":/var/www/html -d php:apache-buster


### How container connects to another container. For example if php/apache container wants to connect with mysql.
In this case, container required a gateway to connect with another container. This gateway we can find out by executing docker inpect command. Since both containers will be in same network so a gateway IP is required.
Our local computer is connected to docker daemon(or docker client) using gateway.