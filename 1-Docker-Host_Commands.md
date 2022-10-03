
# Docker composer basics

## Lets make folders

    mkdir -p c:\docker\weptop
    mkdir -p c:\docker\mount
    mkdir -p c:\docker\traefik
    mkdir -p c:\docker\logs


## Create a Docker composer file

    nano docker-compose.yml

    OR

    code docker-compose.yml

    OR

    cd c:\docker\traefik

    Invoke-WebRequest -Uri https://gist.githubusercontent.com/TeroKeso/19ca6d54a3811cb22ada4c1ca477b8b2/raw/0fcd5c830ad69d65aad3905d144a7efb844e3508/traefik.yml -OutFile docker-compose.yml -UseBasicParsing


# Start a docker composer prosess by reading docker-compose.yml

    docker-compose up -d

# Let's read docker-composer log and docker prosess 
  
    docker-compose logs
    docker ps
    docker inspect CONTAINER_NAMEs

# Docker-compose up and scale

    docker-compose up -d
    docker-compose up --scale whoami=2
    docker-compose up --scale whoami=3
 
 # Docker stop and remove container

    docker ps 
    docker stop CONTAINERNAME / ID
    docker remove CONTAINERNAME / ID


# Update docker Composer image

    docker-compose pull
    docker-compose up -d

# Clean all non used images, containers and networks
  
    docker system prune 
   

# *Extra* voluntary docker network practices. This will need to done on your own linux computer and network

You cant do this in HAMK network because you don't know network range and ALL ip are being given out with DHCP server. 

[How to use macvlan networks](https://docs.docker.com/network/macvlan/)

## Docker network commands

    docker network ls
    docker network create -d macvlan-subnet 192.168.0.0/24 -gateway 192.168.0.1 -ip-range 192.168.0.253/32 -o parent=eth0 custommacvlannetworkwemade

    
