# Docker HUB
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