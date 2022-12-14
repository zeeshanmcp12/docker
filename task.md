# Task

## Setup Wordpress
### Pre-requisite
- php with apache (php version 7.4)
- mysql (version 5.7)



### Steps to complete the task
- Start database service




### Related information
- mysql
    - mysql port 3306
    - We need to set mysql password when running mysql container
    - -e (environment variable) MYSQL_ROOT_PASSWORD='password'
    - mysql -h localhost -u root -p password -> : if mysql is installed on local system
    - Start mysql container and execute below command to log into container
    - docker exec -it mysql bash
    - netstat -antp -> to verify the port is listening on 3306
    - create database wordpressdb;
    - grant all on wordpressdb.* to wordpressuser identified by 'wordpresspass';
        - this 'secret' will be the password for db
    - flush privileges;
        - don't exit untill above command otherwise mysql won't apply changes
    - docker inspect <container_name> -> to see more about container like ip address, network etc
- php with apache


docker pull php:7.4-apache-buster
docker pull mysql:5.7


### Create file in php/apache container
cat > index.html << EOF

### download wordpress
curl -# -LO latest.tar.gz -> -# shows progress bar

### Untar zip file
tar xzf latest.tar.gz

mv wordpress/* .
rm  wordpress/* -fr


### To list the loaded module (for php)
apachectl -M

a2enmod -> to list the modules available to php
a2enmod <module_name> which we want to load/enable
a2enmode rewrite -> then restart apache server (service apache2 restart)...but if we are running this in a container for apache then docker will kill the container because in an image we define an entry point which docker continously monitor either it is live or not. When it see the entry point is not live then it kills the container.

### To check the owner of the process
ps aux -> to check the process running in server and their users
id www-data -> to see the id of user
ls -ln -> list numeric user and group IDs -> output -> drwxrwxrwx 1 33 33 4096 Sep 17 06:32 html

### When working with volume
docker run -p <port:port> -v <volume>:<path_in_container> -d <image_name>
For example:
docker run -p 80:80 -v site-data:/var/www/html -d wordpress-site