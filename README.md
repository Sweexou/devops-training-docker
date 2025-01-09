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

#execute dockerfile
docker build -t mynginx .

#run the docker image creater from the dockerfile
docker run mynginx

la différence entre la 3 et la 4 est que la premiere est réalisé entierement en ligne de commande alors que la deuxieme est réalisé a partir d'un fichier.
La procédure mount volume permet de réaliser des actions quand le container est allumé, alors que le copy est réaliser seulement lors du build.
La copy permet de garder un container immutable contrairement au volume.
