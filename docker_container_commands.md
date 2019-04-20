
Run container  mapping port 4000 to 80

	$docker run -p 4000:80 container_name 

Run detached container  mapping port 4000 to 80 

	$docker run -d -p 4000:80 container_name

See a list of all running containers

	$docker ps                                 

See a list of all containers, even the ones not running

	$docker ps -a

Gracefully stop a container

	$docker stop container_name               

Force shutdown of the specified container

	$docker kill <hash>                  

Remove the specified container from this machine

	$docker rm <hash>              

Remove all containers from this machine

	$docker rm $(docker ps -a -q)   
        
Run image from a registry

	$docker run username/repository:tag            

