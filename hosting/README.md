#### Here is the architecture we are trying to make in AWS

![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/202f879b-92c5-4889-82ca-9e8fecb8e284)

This architecture allows us to create a secure RDS mariadb dataabse inside a private subnet, so only our website in the same VPC will be able to access our database.


#### We start by creating a VPC  
![Alt text](images/image.png)

#### Then we create two subnets: one public (for the ec2), one private (for the rds)
![Alt text](images/image-1.png)

#### Then we create an internet gateway  
![Alt text](images/image-2.png)

#### We then edit our automaticaly generated route to add our internet gateway
![Alt text](images/image-3.png)

#### Then, we create a Cloud9 development environnement, with an t2.micro ec2 instance, and we put it inside the public subnet of our VPC  
![Alt text](images/image-5.png)
![Alt text](images/image-4.png)

#### We run a bunch of commands on the ec2 instance to create the httpd and mariadb service.  
![images/image](https://github.com/Turdyo/aws-project-m1/assets/63463668/84c754a1-dd82-4a55-85dd-b0945185a615)

#### We can now edit the inboud rules of our newly created ec2 instance.
![Alt text](images/image-8.png)

#### Then, we can see the result on the internet.  
![Alt text](images/image-7.png)

#### We then create a NAT gateway to manage connections.  
![Alt text](images/image-6.png)

#### We also create a new route to target the nat gateway  
![Alt text](images/image-9.png)
![Alt text](images/image-12.png)

#### We modify our route subnet association to the private subnet.
![Alt text](images/image-10.png)

#### Then, we edit the subnet association for the route table to detect the private subnet  
![Alt text](images/image-10.png)

#### Now, let's focus on the RDS. First, we need to create a subnet group:
![Alt text](images/image-13.png)

#### After this, we create the RDS database inside of the private subnet. We link it directly to the ec2 ressource.
![Alt text](images/image-14.png)  
![Alt text](images/image-16.png)

#### Let's not forget to update inbound rules of our VPC in order to accept mysql
![Alt text](images/image-15.png)

#### we managed to connect to our database and looked for  the databases.
![Alt text](images/image-17.png)

#### We insert the data form the sql dump file into the database using our ec2 instance.  
![Alt text](images/image-18.png)  
![Alt text](images/image-19.png)

#### We can see that the private/public relation between our ec2 istance and RDS is workling, because we can't log into our database from another computer.  
![Alt text](images/image-22.png)

#### We can see that the code uses endpoints in order to retrieve information about the database. Let's create them using the Systems Manager
![Alt text](images/image-20.png)
![Alt text](images/image-21.png)

#### Then, we can observe that the data is read from our RDS database  
![Alt text](images/image-23.png)
