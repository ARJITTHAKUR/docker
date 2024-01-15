
1. docker container run --detach --name "mysql" -p 3360:3360 --env MYSQL_RANDOM_ROOT_PASSWORD=yes  mysq
2. docker container logs mysql
    2024-01-14 10:45:53+00:00 [Note] [Entrypoint]: GENERATED ROOT PASSWORD: 71NjBu6gNj9xg2hjnMKljIui5553mYW3

3. docker container stats
4. docker container top mysql (show process inside a specific container)


# shell and interactivity

1. docker container run -it (start a new container interactivily)
2. docker container exec -it (run additional command in existing container)
        i.e : docker container exec -it container_name sh

 i.e :  docker container run -it --name proxy nginx bash


## starting an existing container

1. docker container start -ai ubuntu

docker image ls (lists size of all the images present on the system)

## important to note 
1.  You can only run things in the container that already exsists in it's image when you started it

that is why when we start an alpine image with
    - docker container run -it alpine bash (this fails as bash is not present in the alpine image)
    but,
    - docker container run -it alpine sh (this runs, because sh is present in bash image)


## Virtual networks
 (default driver is bridge)
1. docker inspect bridge
2. docker network ls
3. docker network create --driver
4. docker network connect id1 id2
5. docker network disconnect id1 id2

### important to remember
1. id1 network was created using docker network create and id2 was already running


# DNS

(here we are setting creating and running a new container on a preivously created network my_app_net that we created using docker create network create "network_name")

1. docker container run -d --name another_nginx --network my_app_net nginx 

(now if try to ping from another_nginx(our newly created container running on network my_app_net) to our previously created container which is also running on my_app_net)
(we see that they are able to communicate with each other since they are on same network)
2. docker container exec -it another_nginx ping new_nginx

## create a new network instead of manually creating link between containers

### important points for DNS
1. Containers shouldn't rely on IP's for inter-communication
2. DNS for friendly names is built-in if you use custom networks

