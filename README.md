#install nginx images
docker pull nginx 

#check local images
docker images

#run docker container nginx on port 80 and serv index.html
docker run -d -p 80:80 -v ${PWD}/html:/usr/share/nginx/html nginx

#stop and delete docker container
docker stop {container_id}
docker rm {container_id}

#run container without serving the index.html 
docker run -d -p 80:80 nginx

#move a file from local to container html
docker cp ./html/index.html {container_id}:/usr/share/nginx/html