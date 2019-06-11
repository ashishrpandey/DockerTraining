# Run an ubuntu container

        docker pull ubuntu
        docker run -it -d -p 80:80 ubuntu:latest
        docker attach <container_id>

## in the container -->
        apt update
        apt-get install apache2 -y
        apt-get install vim -y
        service apache2 start
        apt-get install elinks -y
        
        elinks http://localhost:80/index.html   ## this will show the website on command line interface itself

## copy your web content in /var/www/html directory

