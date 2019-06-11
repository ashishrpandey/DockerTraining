Create a volume:

      docker volume create my-vol

List and inspect volumes:
      
      docker volume ls
      docker volume inspect my-vol
      
Remove a volume:

      docker volume rm my-vol
      
      
Start a container with a volume

       docker run -d -p 80:80  --name=nginxtest --mount source=nginx-vol,destination=/usr/share/nginx/html  nginx:latest

Check the data in volume
       
       docker volume inspect nginx-yvol
       cd /var/lib/docker/volumes/nginx-vol/_data

Stop and remove the container , volume should still exist

       docker container stop nginxtest
 
Remove the volume
 
       docker volume rm nginx-vol
       


## bind mount

         docker run -d \
        -it   --name devtest \
        --mount type=bind,source="$(pwd)"/target,target=/app \
        nginx:latest
        
        
docker inspect devtest
      
    
  
  
       
