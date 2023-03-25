# DEPLOYING A WEB APPLICATION TO AMAZON ECS USING EC2, DOCKER, ECR & LOAD BALANCER

__STEPS__

1. Login to AWS and navigate to EC2 to create an instance, not forgetting to attach a keypair to the instance. <br><br>
![](img/docker.png) <br><br>
2. Using the __SSH client__ option to connect remotely into the instance. <br><br>
![](img/docker1.png) <br><br>
3. Using Mobaxterm to connect remotely the instance via SSH by specifying public IPV4, username and path to the keypair. <br><br>
![](img/docker2.png) <br><br>
4. SSH is successful and tested using __whoami__ command. <br><br>
![](img/docker3.png) <br><br>
5. Install docker using root priviledges and yum. <br><br>
![](img/docker4.png) <br><br>
6. Docker installation is complete. <br><br>
![](img/docker4-1.png) <br><br>
7. Start docker using systemctl and ensure it is active. <br><br>
![](img/docker4-2.png) <br><br>
8. Create and directory and navigate to this directory, create a Dockerfile (a text document that contains all the commands a user could call on the command line to assemble an image) and input the command below using any preferred editor (I used vim editor). <br><br>
![](img/docker5.png) <br><br>
9. Create and edit an index.html file. <br><br>
![](img/docker6.png) <br><br>
10. Build the image using the docker build -t command (. means in the current directory). <br><br>
![](img/docker7.png) <br><br>
11. Build is complete, centos is the base image. <br><br>
![](img/docker7-1.png) <br><br>
12. Run the commands below to view docker images (docker images) and running containers (docker ps -a). <br><br>
![](img/docker8.png) <br><br>
13. Run app using public DNS. <br><br>
![](img/docker9.png) <br><br>
14. Navigate to ECR on AWS to create a private repo where built image will be pushed to. <br><br>
![](img/docker10.png) <br><br>
15. Create a role for IAM user (with programmatic access) for ECR. <br><br>
![](img/docker11.png) <br><br>
16. Configure credential (access key and secret access key of user) using __aws configure__. <br><br>
![](img/docker12.png) <br><br>
17. Use __push commands__ from ecr repo to push my image to ECR. <br><br>
![](img/docker13.png) <br><br>
18. I had issues continuing as a non-root user while trying to login. <br><br>
![](img/docker14.png) <br><br>
19. I switched to root user using __sudo su__ command and login was successful. <br><br>
![](img/docker14-1.png) <br><br>
20. Using __docker images__ command to check my images and tagging my image before pushing to ECR. <br><br>
![](img/docker14-2.png) <br><br>
21. I pushed my image to my private repo on ECR. <br><br>
![](img/docker14-3.png) <br><br>
22. My image is visible on Amazon ECR (ECR is a registry for images). <br><br>
![](img/docker14-4.png) <br><br>
23. More details about my image. <br><br>
![](img/docker14-5.png) <br><br>
24. Create a target group to attach to an application load balancer (notice the target group is not associated to a LB yet). <br><br>
![](img/docker15.png) <br><br>
25. Create an application load balancer (summary of my ALB details). <br><br>
![](img/docker15-1.png) <br><br>
26. ALB is active with high availability (more than 1 AZ). <br><br>
![](img/docker15-2.png) <br><br>
27. Create a task execution role that grants the Amazon ECS container and Fargate agents permission to make AWS API calls on our behalf. <br><br>
![](img/docker16.png) <br><br>
28. Create a task definiton that describes the containers that forms our application.<br><br>
![](img/docker17.png) <br><br>
29. Create a cluster which is a group of ECS container instances. <br><br>
![](img/docker18.png) <br><br>
30. Create a service that defines the minimum and maximum task from a task definition. <br><br>
![](img/docker18-1.png) <br><br>
31. A list of tasks using fargate as launch type (a task is an instance of a task definition). <br><br>
![](img/docker19.png) <br><br>
32. This shows a deployment and events for ECS. <br><br>
![](img/docker19-1.png) <br><br>
33. Using ALB DNS to view my web app. <br><br>
![](img/docker20.png) <br><br>
34. To avoid being charged, I cleaned up my resources by terminating my instance and deleting other resources.
