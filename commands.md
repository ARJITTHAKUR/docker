
1. docker container run --detach --name "mysql" -p 3360:3360 --env MYSQL_RANDOM_ROOT_PASSWORD=yes  mysq
2. docker container logs mysql
    2024-01-14 10:45:53+00:00 [Note] [Entrypoint]: GENERATED ROOT PASSWORD: 71NjBu6gNj9xg2hjnMKljIui5553mYW3

3. docker container stats
4. docker container top mysql (show process inside a specific container)


# shell and interactivity

1. docker container run -it (start a new container interactivily)
2. doker container exec -it (run additional command in existing container)

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