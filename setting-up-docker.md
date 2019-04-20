## For a normal centos/RHEL machine


	$ sudo yum install -y yum-utils
	$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
	$ sudo yum install docker
	$ sudo systemctl start docker


## For Amazon linux 2 - ec2 instances 
connect to ec2 instance through putty
	$ sudo su
	$ yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
	$ yum install docker
	$ service docker start

## To check whether it has worked correctly 
	$ docker run hello-world

	"""
	Unable to find image 'hello-world:latest' locally
	latest: Pulling from library/hello-world
	78445dd45222: Pull complete
	Digest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7
	Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

"""

For further help for other OS ... Visit official site:
https://docs.docker.com/engine/installation
