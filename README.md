# Vpc-project
# VPC Architecture
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/vpc-example-private-subnets.png)

Go to the VPC service in aws and click on create VPC
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%201.PNG).

Now click on vpc and more.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%201-1.PNG)

Select 1 nat gateway per AZ to ensure high availability and internet connectivity to two instances in the VPC
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%201-2.PNG)

Overview of the VPC.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Vpc%20overview.PNG)

Now let's create Auto scaling groups.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-1.PNG)

Give a name and create a new template.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-2.PNG)

now give a name to template then description.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-3.PNG)

Now select the AMI (amazon machine image) (Operating system) for your instances in Auto scaling groups.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-4.PNG)

Select instance type and key login pair.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-5.PNG)

Now select the Vpc for deployment of ASG.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-6.PNG)

Then create the template and use it to create Auto Scaling Group.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-7.PNG)

Now select the vpc for ASG.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-8.PNG)

Now select subnets, here we are selecting private subnets to ensure higher security.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%202-9.PNG)

See your instances are deployed.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%203-1.PNG)

Now lets launch an bastion instance inorder to ssh into our private instances we need bastion instance which should live in the same vpc as of the instances in private subnets.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%203-2.PNG)

select ami.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%203-3.PNG)

select the same vpc, public subnet and enable auto assign public ip
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%203-4.PNG)

Then create a new security group with ssh access and launch the instance.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Step%203-5.PNG)


Now ssh into the bastion instance using its public ip address then ssh into the private instances in private subnets using the private ip. Before that don't forget to scp the key used while creating the bastion instance.

Then after ssh into the private instance, create an index.html file with any basic example.

Now use this command to run a python server on the instance "python3 -m http.server 8000". we are using port 8000 here

Now lets setup a load balancer to distribute the traffic. We need an application load balancer.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/load-balancer-setup.PNG)

Select the Vpc and public subnets
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Load-balancer-jd.PNG)

Configure the load balancer to be accessed by port 8000. Also make sure that the security group allows http traffic.

now just use the url provided at the load balancer.

Finally we can get the application.
![](https://github.com/AbdulR431/Vpc-project/blob/main/images/Project%20REsult.PNG)
