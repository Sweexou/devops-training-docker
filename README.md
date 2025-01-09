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

#installation of mysql and phpmyadmin images
docker pull mysql
docker pull phpmyadmin/phpmyadmin

#creation of network for the containers
docker network create test_docker
id : b35f4490d5f1ab74e3f09ca68608f543bf3e35c04bd3b9780be3307cfe2ea498

#creation of a network to link the containers
docker network create test_docker

#creation of mysql container
docker run -d --name=mysql-container --network test_docker -e MYSQL_ROOT_PASSWORD=root mysql
id : 24252e796d4817ddaa4dd04384e1c7b24687e61e0e07a5af2745af194bee72d0

#creation of phpmyadmin container
docker run -d --name phpmyadmin-container --network test_docker -e PMA_HOST=mysql-container -p 8080:80 phpmyadmin/phpmyadmin
id : 5f04b9b947b00910543779d8e35b4719c57ed1549715e5f8b3cc9dd8f374687c