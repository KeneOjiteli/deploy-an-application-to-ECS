$docker -v (Checks the version of Docker)

$docker ps (To check images)

$docker ps -a (Checks all running and stopped images)

$docker images (Let's you see all the images available)

$docker pull image(Pulls a Parent image from Docker hub)

$docker run <imagename> (runs the image but can creates extra images)

$docker start image (To run the image without creating extra images)

$docker stop (Allows you to stop a running Container)

$docker run -d (The '-d' option runs the image in a detach mode)

$docker run -t (The -t flag is called a Tag, it allows you to name your image in running state)

$Docker run -p (The -p flag allows you to give a Port number and can also be used for port mapping)

$docker run --name (The --name flag allows you to rename your image)

$docker rm container <Container name> (Allow you to remove a Conatiner)

$docker rmi (Notice the additional option -i, it simply allows you to remove the image but you'll need to first remove the container)

$docker rmi -f (The -f flag allows you to forcefully remove an image without having to go through removing the Container first)

$ocker logs & Docker exec (Are both used for debugging purposes)

$docker build -t <directoryname> (Allows you to build a new image from a Parent image)
$docker-Compose -f <filename> (includesmy different containers) up(To start multiple services)

$docker-compose -f <filename> down (This command stops the running containers)