<h1 align="center">Lab diagram</h1>

_This repository shows a test infrastructure in the AWS cloud._

---

![Image diagram](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/VPC-Test-project28.drawio.png)

# Creating a VPC


We will create VPC, 4 Subnets and place the EC-2 instance inside the subnet.

We will also install a webserver on the EC-2 instance and access it using a web browser.

### Quick Check

  1\. Create the VPC with the CIDR Block Range 10.0.0.0/16 (65000 Hosts)

  2.Create an Internet Gateway and attach it to the newly created VPC

  3.Create Public Subnet-1 in Availability Zone-1 with the CIDR 10.0.0.0/24

  4.Create Private Subnet-1 in Availability Zone-1 with CIDR of 10.0.1.0/24

  5.Create an Elastic IP.

  6.Create a NAT Gateway using the Elastic IP and Public Subnet -1 as base

  7.Create Public Subnet-2 in Availability Zone-2 with the CIDR 10.0.2.0/24

  8.Create Private Subnet-2 in Availability Zone-2 with the CIDR 10.0.3.0/24

  9.Update Route Configurations for present Route Table and name it Private Route Table

  10.Create Public Route Table and update Route Configurations

  11.Create VPC Security Group to allow inbound HTTP,HTTPS and SSH

  12.Create EC-2 Instances using the VPC Created as base and the Public Subnet-1 as EC-2 Location.

  13.Enable Public IP for the EC-2 

  14.Associate the VPC Security Group for the EC-2

  15.Update User Data for the EC-2

  16.Launch EC-2

  17.Test Webserver running on EC-2 using a browser.

After completing the above steps, you can successfully complete this work using the following guide:


### Step by Step Review

  1\. Create the VPC with the CIDR Block Range 10.0.0.0/16 (65000 Hosts).

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo1.png)

  2\. Create an Internet Gateway and attach it to the newly created VPC

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo2.png)

  3\. Create Public Subnet -1 in Availability zone -1 with the CIDR 10.0.0.0/24

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo3.png)

  4\. Create Private Subnet -1 in Availability Zone -1 with CIDR of 10.0.1.0/24

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo4.png)

  5\. Create an Elastic IP.

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo5.png)

  6\. Create a NAT Gateway using the Elastic IP using the Public Subnet -1 as base

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo6.png)

  7\. Create Public Subnet -2 in Availability zone -2 with the CIDR 10.0.2.0/24

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo7.png)

  8\. Create Private Subnet -2 in Availability Zone -2 with the CIDR 10.0.3.0/24

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo8.png)



![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo9.png)

  9\. Update Route Configurations for present Route Table and name it Private Route Table

Update Private Route Table Route’s as follows

| Destination |   Target    |
| ----------- | ----------- |
| 10.0.0.0/16 |    Local    |
| 0.0.0.0/0   | NAT Gateway |




![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo10.png)

  Create Public Route Table and update Route Configurations.

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo11.png)

  10\. Create Public Route Table and update Route Configurations.


![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo12.png)

  11\. Create VPC Security Group to allow inbound HTTP,HTTPS and SSH


![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo13.png)


12. Create EC-2 Instances using the VPC Created as Base and the Public Subnet-1 as EC-2 Location.

13. Enable Public IP for the EC-2 

14. Associate the VPC Security Group for the EC-2

15. Update User Data for the EC-2 (Check paragraph 17)




![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo14.png)


  Doublececk our Public Routes:

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo18.png)

  Doublececk our Private Routes:

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo19.png)

  15\. Launch EC-2

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo15.png)


16. Connect by SSH:

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo16.png)

17. Follow these commands after a successful connection:

  (Or make a .sh file give chmod and run)((Or use like User data))


```bash
#!/bin/bash

sudo su

yum update

# Install Apache Web Server and PHP

yum install -y httpd

yum install -y mysql

yum install -y php

# Download Lab files

wget https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/lab-app-san.zip

unzip lab-app-san.zip -d /var/www/html/

# Turn on web server

chkconfig httpd on

service httpd start

```


  Enter to our WEB page:

``` http://<our_instance_ip>```

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo21.png)

  Enter the magic command in terminal, just for fun, to load our one CPU core of the instance to 100%

  (# -- mean root user)((For remove this load make # killall yes ))

```# yes > /dev/null &```

  Voila, BOOM!

![DevOps-Project-photo](https://github.com/san-vivt/VPC-DevOps-project/raw/main/src/DevOps-Project-photo23.png)


<h1 align="center">Congratulations!!!</h1>