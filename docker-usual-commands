$ docker images                    ##lists all images available locally

$ docker search <keyword>         ## search the repository docker-hub for all the images containg <keyword>
$ docker search centos    

$ docker pull hello-world         ## Download hello-world image to local host machine from docker-hub repo
$ docker images                   
$ docker run hello-world:latest   ## Run latest version of hello-world
OR 
$ docker run <Image-id>           

other examples
$ docker pull centos:centos6          ##centos6 is the version tag
'''
Hello-world is an ephemeral container. Ran and exited.
In images it can have multiple layers/snapshot over that image e.g. 
base layer: package layer: configuration layer
''' 

## To look about details of image
$ docker inspect <image name/image-id>

$ docker pull docker/whalesay       ## Download docker/whalesay image to local host machine from docker-hub repo
$ docker run docker/whalesay cowsay IAMWHALE     ## run container 
 __________
< IAMWHALE >
 ----------
    \
     \
      \
                    ##        .
              ## ## ##       ==
           ## ## ## ##      ===
       /""""""""""""""""___/ ===
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~
       \______ o          __/
        \    \        __/
          \____\______/
        


$ docker ps                         ## lists the containers running
$ docker ps -a                      ## gives all the containers that ran in the past
$ docker inspect <container_name>   ## Gives jason object enumerating details of the running container

$ docker run -it centos:latest /bin/bash        ## -I  iteractive mode , -t on terminal; create a bash shell
                                                ## It will instantly login to the container and launch a bash 
                                                ##shell. On exiting bash shell the container will also terminate.

## to avoid that run with -d command:
$ docker run -d centos:latest /bin/bash         ## it shall return a container id only
                                                  ## and container will be exited 

$ docker stop container id                      ### will kill the container
$ docker ps                                     ## check it with "docker ps" command
$ docker ps -a                                  ## will show killed containers

$ docker run -d --name=mycontainername imagename:imageversion     ## Give container a name
$ docker inspect mycontainername

$ docker attach container_name/id                 ## control will attach to the container and exitig from their will bring down the container itself

$ docker exec -it containername /bin/bash       ## it will launch a bash shell and jump to this bash shell running in the container. exiting from here will just exit from bash shell

$ docker restart container_name                   ## restart the container

###   Image and container management:

$ docker rmi centos:centos6           ## remove images only if no containers are running on it.

$ docker rm container_id              ### removes the container
$ docker rm `docker ps -a -q `          ### removes all the containers 

## if we do now 
$ docker rmi <image_name>           ## it will remove the image
                                    ## use -f option to forcefully remove the image even if containers are runnning


