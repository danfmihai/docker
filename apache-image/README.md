# Building an apache server Dockerfile

use in terminal the command to begin the image creation
```
docker build -t img_apache .
```
Run the image:
```
docker run -itd --name cont_apache -p 8080:80 img_apache
```