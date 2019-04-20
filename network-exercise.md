## Without custom network
Using only default bridge 

Show current networks

	$ docker network ls

Run 2 containers with default bridge network

	$ docker run -dit --name alpine1 alpine ash

	$ docker run -dit --name alpine2 alpine ash

	$ docker container ls

Get more info about the default network 

	$ docker network inspect bridge

Attach to a running container

	$ docker attach alpine1

	$ip addr show

	$ping -c 2 google.com
	Success


	$ping -c 2 <ipaddr of alpine2>
	Success


	$ping -c 2 alpine2
	Fails

// Remove all the containers

	$ docker container stop alpine1 alpine2

	$ docker container rm alpine1 alpine2


# With custom bridge network 


	$ docker network create --driver bridge alpine-net 		// create a user defined network alpine-net

	$ docker network ls

	$ docker network inspect alpine-net

## Run container with custom brisge network alpine-net 

	$ docker run -dit --name alpine1 --network alpine-net alpine ash

	$ docker run -dit --name alpine2 --network alpine-net alpine ash

	$ docker run -dit --name alpine3 alpine ash  		//alpine3 only connected to bridge not to alpine-net

	$ docker run -dit --name alpine4 --network alpine-net alpine ash

	$ docker network connect bridge alpine4  		//alpine4 connect to bridge as well


	$ docker network inspect bridge

	$ docker network inspect alpine-net


Ping from one container to others by name and see the connectivity
ping from alpine4 which is connected to both

