# configuration-client
Spring boot cloud config that can run on docker container
create your own network


docker network create --subnet=172.18.0.0/16 mynet123
Server



sudo docker run --net mynet123 --ip 172.18.0.22 -p 0.0.0.0:8888:8888 --name cloudserver  -t springio/configuration-service --hostname cloudserver

use server static ip in client bootstrap.yml and/or bootstrap.properties

client 

sudo docker run --net mynet123 -p 0.0.0.0:8080:8080 -t springio/configuration-client -h 0.0.0.0:8080 --bind 0.0.0.0:8080 --link cloudserver:cloudserver

