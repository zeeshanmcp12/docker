## Docker Basics

# to search any tool / image on docker hub
docker search busybox

docker run -P -d
-P -> map the port of container with any port of our host
-d -> start the container in detach mode

docker run -p 80:80
-p -> (small letter): map the port 80(right side of colon) of container with port 80(left side of colon) of host