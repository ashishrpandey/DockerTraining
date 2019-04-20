
Show images on this machine

	$docker images 

Pull images to local docker host from docker store

	$docker pull image_name:tag_name 

Show all images on this machine

	$docker images -a                               

Remove the specified image from this machine

	$docker rmi <imagename>            

Remove all images from this machine

	$docker rmi $(docker images -q)             

## Image Lifecycle development

Create image using this directory's Dockerfile

	$docker build -t dir_containing_dockerfile .

Create image from a container

	$docker commit container_name image_repo:tag 

Log in this CLI session using your Docker credentials

	$docker login             

Tag <image> for upload to registry
OR rename the image 

	$docker tag <image> username/repository:tag  

Upload tagged image to registry

	$docker push username/repository:tag            

Run image from a registry

	$docker run username/repository:tag            

