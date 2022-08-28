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
- php with apache


docker pull php:7.4-apache-buster
docker pull mysql:5.7