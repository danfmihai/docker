# Docker HUB
docker list images on local machine
```
docker images
```
Get a image from docker hub (ex. nginx)
```
docker image pull nginx:latest
```
Docker Search with filters
```
docker search --filter "is-official=true" registry
```
or
```
docker search --format "table {{.Name}}\t{{.Description}}"\t{{.IsOfficial}}" registry
```
Login in cli to docker hub
```
docker login
```
Create identical copy of an image with you own name (tag) 
```
docker tag nginx:latest accountname/repo-name:yournewtagname
```
Push image to docker hub
```
docker push accountname/repo-name:yournewtagname
```
Get information about an image (json format)
```
docker image inspect ubuntu:12.04
docker image inspect --format " {{.RepoTags}} : {{.RepoDigests}} " ubuntu:12.04
docker image inspect --format " {{json .Config}}" ubuntu:12.04 > inspect_report.txt
```
Get history of the image
```
docker image history ubuntu
```
Remove image (by name or by ID)
```
docker image rm nginx:alpine
docker image rmi 7d0cdcc60a96
```
docker create
```
docker container create -it --name test-busybox-A busybox:latest
```
docker run (--rm to remove the container after finishing running)
```
docker container run -itd --rm --name test-busybox-B busybox:latest
```
Rename, Start, Restart, Stop container 
```
docker container rename test-busybox-A my-busybox
docker container start cont_apache
docker container restart cont_apache
docker container stop cont_apache
```
docker attach ( attach the std io to terminal) after execution of exit command the container will stop
```
docker attach my-busybox
```
Exec stdout without stopping the container
```
docker exec -it my-busybox ls
```
Port mapping
```
docker container run -itd --name cont_nginx -p 8181:80/tcp img_apache
# let docker expose ports with -P
docker container run -itd --name cont_apache_A -P img_apache
```
Erasing containers
```
docker container rm my-busybox
```
Remove all stopped containers
```
docker container prune
```
### DOCKER NETWORK

```
docker network create --driver bridge my-bridge
docker network create --driver bridge --subnet=192.168.0.0/16 --ip-range=192.168.5.0/24 my-bridge-1
docker network ls
docker network ls --filter driver=bridge

docker network connect my-bridge-1 ubuntu
docker inspect ubuntu

docker container run -itd --network host --name cont_nginx nginx:latest
docker container port cont_nginx
```
Inspect Network
````
docker inspect bridge my-bridge-1
docker network inspect --format "{{.Scope}}" bridge
docker network inspect --format "{{.ID}}: {{.Name}}" bridge
```
Disconnect Bridge
```
docker network disconnect my-bridge-1 cyberpower 
```
### VOLUMES
Create volumes
```
docker volume create vol-busybox
docker run -d --volume vol-ubuntu:/tmp ubuntu:18.04
```
List volumes
```
docker volume ls --filter "dangling=true"
```
Remove volume
```
docker volume rm vol-ubuntu
```




