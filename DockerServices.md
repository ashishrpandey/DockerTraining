Create a service with nginx image

    $ docker service create nginx

Create nginx service with a name
  
    $ docker service create --name my_web nginx
    
List services:

    $ docker service ls

Login to a private registry 

    $ docker login registry.example.com
    $ docker service  create   --with-registry-auth   --name my_service registry.example.com/acme/my_image:latest

Update a service 

    $ docker service update --publish-add 80 my_zekelabs      ## Adding a port 80 with the service for outside world

Create a service with various options 

    $ docker service create --name  zekeCalling   --env MYVAR=myvalue   --workdir /tmp   --user my_user   alpine ping docker.com

Create a service with 3 containers with port forwarding 

    $ docker service create --name my_web --replicas 3 --publish published=8080, target=80 nginx
