docker pull nginx 

docker images

docker run -d -p 80:80 -v ${PWD}/html:/usr/share/nginx/html nginx