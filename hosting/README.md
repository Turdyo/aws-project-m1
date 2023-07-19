We start by creating a VPC  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/eeb3f137-5e02-4e0e-af4e-a53ac9342aba)

Then we create an internet gateway  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/b9c032aa-4da5-4c32-b68e-b5767acc8ee9)
  
We create route tables  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/f0a20dcb-65e1-4b27-b39e-6f2c7fa2c7a0)

Then, we create a Cloud9 development environnement, with an t2.micro ec2 instance, and we put it inside the public subnet of our VPC  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/2c2324a2-85ed-429e-a6c2-8992b26c30fd)

We have 2 subnets: one public for the ec2 instance, and one private for our database which is inside of RDS  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/f3b88d83-276a-4eff-8429-e4ccf0f7d52f)

We then create a NAT gateway to manage connections.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/285effb5-00f3-414f-844d-15dc61debdc3)

We also edit the routes to target the nat gateway  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/82d8c4c3-1a67-446c-9736-83a6c32a458c)

Then, we edit the subnet association for the rotue table to detect the private subnet  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/12521d90-347c-40fa-ac17-f03446b5140d)

After this, we create the RDS database inside of the private subnet.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/84fec1ec-8ab6-41d9-9d32-417b12003472)

We run a bunch of commands on the ec2 instance to create the httpd and mariadb service.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/84c754a1-dd82-4a55-85dd-b0945185a615)

Then, we can see the result on the internet.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/e0c5a05d-9862-4540-858e-db6b0f579a12)

We insert the data form the sql dump file into the database using our ec2 instance.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/439abc44-4764-4465-bd5c-af2ac46f250d)  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/db7c97f6-d23c-4c96-9582-afef6823b134)  

We can see that the private/public relation between our ec2 istance and RDS is workling, because we can't log into our database from another computer.  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/386d1acc-83bd-495d-95a4-29da4c901548)

Then, we can observe that the data is read from our RDS database  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/071bae5f-f676-41d8-ad97-bae7a461cc4d)

Here is our db using RDS mariadb free tier  
![image](https://github.com/Turdyo/aws-project-m1/assets/63463668/50876b02-e4aa-4061-9c16-8191b2bf0137)
