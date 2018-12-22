# Lab 04 - Docker - Kopp Olivier, Piller Florent

## Task 0 : Identify issues and install the tools 

### M1

This infrastructure can't be deployed on production. The main reasons for this is that it' pretty weak against crashes. If on of the server crash and we have to relaunch it, we also have to relaunch the HAproxy which cause an indisponibility of the web app. The same process need to be done if we want to add another server.

### M2

In order to add another webapp container, we have to build it (with the same files as the two previous containers), to modify the haproxy config file (adding the third server to the load balancing configuration)  and the run.sh script (adding the line `sed -i 's/<s3>/$S3_PORT_3000_TCP_ADDR/g' /usr/local/etc/haproxy/haproxy.cfg`). 

Next to that, we have to rebuild the haproxy image, and to run it with `docker run -d -p 80:80 -p 1936:1936 -p 9999:9999 --link s1 --link s2 --link s3 --name ha softengheigvd/ha` .

We can also modify the provision script to allows restart of the systems (adding a remove of the third webapp container and modifying the run command by the one we executed just before).

### M3

A better approach would be to detect changes on runtime and to be able to add node to the haproxy without having to relaunch to whole infrastructure each time.

### M4

### M5

### M6

Stats page : 

![](./images/T0_stats_page.PNG)

repository at https://github.com/olivierKopp/Teaching-HEIGVD-AIT-2016-Labo-Docker.git

## Task 1 : Add a process supervisor to run several processes

Stats page at the end of the manipulations : 

![](./images/T1_stats_page.PNG)

We didn't have particular difficulties in this task.

During this task, we modified the configuration of the docker images in order to installed a process supervisor which will allow us to run multiple process within the same container easily. The process supervisor will help us to manage the processes inside the docker containers. For example, if a web application crashes, it can restart it for us.

## Task 2 : Add a tool to manage membership in the web server cluster

#### Problem with the current solution : 



#### Give an explanation on how `Serf` is working. Try to find other solutions that can be used to solve similar situations where we need some auto-discovery mechanism.



## Task 3 : React to membership changes

## Task 4 : Use a template engine to easily generate configuration files

## Task 5 : Generate a new load balancer configuration when membership changes

## Task 6 : Make the load balancer automatically reload the new configuration










#### Pedagogical objectives
