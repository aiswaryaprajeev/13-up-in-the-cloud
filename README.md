# 13-up-in-the-cloud
TASK 13 – Up in the Clouds (AWS VM Setup)
## INTRODUCTION
This task involves launching a free-tier virtual machine (VM) on AWS, checking its network connectivity, connecting via SSH, and hosting a simple webpage. The goal is to practice cloud VM deployment, basic network testing, and web hosting in a safe way while staying within the AWS Free Tier.
## STEPS PERFORMED
1. Cloud Provider and Region
  - For the task I’ve used Amazon Web Services (AWS) to launch a virtual machine. The region selected was Asia Pacific (Mumbai) –ap–south-1.
2.	VM OS and size-tier
  - The virtual machine was created by using the following configurations :
  - Operating System : Ubuntu Server 22.04 LTS
  - Instance Type : t3.micro
  - Storage : 8 GB General Purpose SSD (default)
    The t3.micro instance is eligible for the AWS Free Tier, which allows up to 750 hours per month for free usage during the free-tier period.
 3. Network / Security Rules
  - For secure authentication to the VM, I used SSH key authentication.
    - Created a new key pair named task13-key.
    -	Selected TSA key type.
    -	Downloaded the .pem private key file.
    -	Stored it securely in Kali Linux.
    -	Before connecting I changed the permission of the key file : chmod 400 task13-key.pem
  -	A security group was configured to control inbound traffic to the VM.
  -	The following rules were added :
     SL.No  Type	Protocol	Port	Source
      1.    SSH	  TCP      	22	  My IP
      2.    HTTP	TCP	      80	  Anywhere
      3.    ICMP	ICMP	    All	  Anywhere
  -	SSH connection from my system.
  -	Ping requests for connectivity testing.
  -	HTTP traffic for hosting the webpage.
4.	VM Public IP 
  -	After launching the instance, AWS assigned a public IPv4 address which was used for ping, SSH connection and accessing the hosted webpage.
    -	Public IP : 13.60.56.101
5.	Shutdown and Termination
  -	After completing the task, I stopped and terminated the instance to avoid unnecessary resource usage.
  -	Steps performed :
    -	Opened EC2 Dashboard.
    -	Selected the Instance.
    -	Clicked Instance state
    -	Chose Terminate Instance.
  -	This permanently deleted the VM and ensured no additional cloud resources remained active.
6.	Ping Public IP from the VM
  -	The ping confirmed that the VM had outbound internet connectivity which means that it could communicate with the external networks.
7.	Hosted a webpage on port 80 and accessed it from my browser
  -	To install a webpage, I installed the Apache web server on the VM
  -	Commands used :
    -	sudo apt update
    -	sudo apt install apache2  -y
  -	After installation, the Apache service started automatically.
  -	I verified it by opening the following address in my browser : http://13.60.56.101
  -	To allow access to the webpage from the internet, the following rule was added to AWS security group :
    -	HTTP (TCP) – Port 80 – Source : Anywhere (0.0.0.0/0)
  -	This allowed the external users to access the webpage hosted on the VM.
## CONCLUSION
The AWS free-tier VM was successfully launched, network connectivity tested, SSH access verified, a webpage hosted, and the VM terminated. This task helped practice cloud VM setup, networking, and basic web hosting safely and efficiently.

