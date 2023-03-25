# DEPLOYING A WEB APPLICATION TO AMAZON ECS USING EC2, DOCKER, ECR & LOAD BALANCER

__STEPS__

1. Login to AWS and navigate to EC2 to create an instance, not forgetting to attach a keypair to the instance.
![](img/docker.png)
2. Using the __SSH client__ option to connect remotely into the instance.
![](img/docker1.png)
3. Using Mobaxterm to connect remotely the instance via SSH by specifying public IPV4, username and path to the keypair.
![](img/docker2.png)
4. SSH is successful and tested using __whoami__ command.
![](img/docker3.png)
5. Install docker using root priviledges and yum.
![](img/docker4.png)
6. Docker installation is complete.
![](img/docker4-1.png)
7. Start docker using systemctl and ensure it is active.
![](img/docker4-2.png)
8. Create and directory and navigate to this directory, create a Dockerfile (a text document that contains all the commands a user could call on the command line to assemble an image) and input the command below using any preferred editor (I used vim editor)
![](img/docker5.png)
9. Create and edit an index.html file.
![](img/docker6.png)
10. Build the image using the docker build -t command (. means in the current directory)
![](img/docker7.png)
11. Build is complete, centos is the base image.
![](img/docker7-1.png)
12. Run the commands below to view docker images (docker images) and running containers (docker ps -a).
![](img/docker8.png)
13. Run app using public DNS.
![](img/docker9.png)
14. Navigate to ECR on AWS to create a private repo where built image will be pushed to.
![](img/docker10.png)
15. Create a role for IAM user (with programmatic access) for ECR.
![](img/docker11.png)
16. Configure credential (access key and secret access key of user) using __aws configure__
![](img/docker12.png)
17. Use __push commands__ from ecr repo to push my image to ECR.
![](img/docker13.png)
18. I had issues continuing as a non-root user while trying to login.
![](img/docker14.png)
19. I switched to root user using __sudo su__ command and login was successful.
![](img/docker14-1.png)
20. Using __docker images__ command to check my images and tagging my image before pushing to ECR.
![](img/docker14-2.png)
21. I pushed my image to my private repo on ECR.
![](img/docker14-3.png)
22. My image is visible on Amazon ECR (ECR is a registry for images).
![](img/docker14-4.png)
23. More details about my image.
![](img/docker14-5.png)
24. Create a target group to attach to an application load balancer (notice the target group is not associated to a LB yet).
![](img/docker15.png)
25. Create an application load balancer (summary of my ALB details).
![](img/docker15-1.png)
26. ALB is active with high availability (more than 1 AZ).
![](img/docker15-2.png)
27. Create a task execution role that grants the Amazon ECS container and Fargate agents permission to make AWS API calls on our behalf.
![](img/docker16.png)
28. Create a task definiton that describes the containers that forms our application.
![](img/docker17.png)
29. Create a cluster which is a group of ECS container instances.
![](img/docker18.png)
30. Create a service that defines the minimum and maximum task from a task definition.
![](img/docker18-1.png)
31. A list of tasks using fargate as launch type (a task is an instance of a task definition).
![](img/docker19.png)
32. This shows a deployment and events for ECS.
![](img/docker19-1.png)
33. Using ALB DNS to view my web app.
![](img/docker20.png)
