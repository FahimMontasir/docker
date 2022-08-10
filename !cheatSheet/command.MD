# All docker commands

## images

Images: like blueprints for containers -> runtime env, application code,
dependencies.

1. docker build -t [tag-name] [folder-name]
2. docker images //to see all images
3. docker image rm [image-name] -f //remove image with fore flag
4. docker build -t [image-name]:v1 . //build image with tag v1

## container

runnable instance of a image, runs our application, isolated process

1. docker run [image-name]
2. docker ps //see running container
3. docker run --name [my-app_1] [image-name] //with a name attached
4. docker stop [container-name]
5. docker run --name [my-app_2] -p 4000:4000 -d [image-name] //run in detached mode and port map
6. docker ps -a //all container
7. docker start [container-name] //to start existing container
8. docker container rm [container-name] //remove container
9. docker system prune -a //to remove all containers
10. docker run --name [container-name] -p 4000:4000 [image]:[tag] //run myapp_c1 container with myapp:v1 image

## volumes

if we want to change something instantly from dev mode

## docker compose

1. docker-compose up
2. docker-compose down --rmi all -v //stop and remove all

## docker hub

where we store our containers

1. docker login //give user name and password
2. docker tag [image-id] [username/repo-name]
3. docker push [repo-name]
4. docker pull [repo-name]
