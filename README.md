# Learning-Amazon-AWS
This captures my journey on learning Amazon AWS.

Hi, I'm Ayoge, an aspiring Data Scientist. This repository is started to document my learning journey with Amazon AWS.
You're welcome to journey with me. 

Today, we're going to launch an instance.

First step is to go the website https://aws.amazon.com/education/awseducate/ and sign in with your credentials.
Click on "My Classrooms", and then click on "Go to Classrooms". This brings you to the page https://labs.vocareum.com/main/main.php?m=editor&nav=1&asnid=133937&stepid=133938
Find and click on the link "AWS Console" to arrive at the page https://console.aws.amazon.com/console/home?region=us-east-1#
Under services, click on "EC2" and we arrive at https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Home:. To launch an instance, we need a VPC (Virtual Private Cloud).
DO NOT USE THE DEFAULT VPCs!!! Using them might pose a difficulty later on, escpecially as it concerns debugging. So, we will create and configure our own VPCs in our areas.
Click on Services. In the search bar on this page, type and search for VPC (You will have this suggestion as you type VPC Isolated Cloud Resources)
Click on Launch VPC Wizard. Here, we are to select a VPC configuration (4 options are given on the leftside of the page).
At this stage, we're only interested in the first 2 options- a. VPC with a Single Public Subnet b. VPC with a Public & Private Subnet.
Return to the page https://console.aws.amazon.com/vpc/home?region=us-east-1#
In the VPC Dashboard to the left, click on "Your VPCs". ANd then cick on "Create VPCs"
Enter details for Name Tag & IPv4 CIDR block* (You may choose to use IPv6 CIDR block) and click on Create

After creating VPC, next we create SubNets. Click on Subnet in the VPC Dashboard, and at the top, click on "Create SubNet".
Enter SubNet name (we wnat to create a Public Subnet this time)
Select the VPC you just created to assign the Subnet to it.
There are a possibility of Availability Zones, select one of them.
Enter a valid IP address (one that belongs to the family previously selected when creating VPCs). Click Create.
Create another SubNet (a Private one this time) in the same way. You ay choose the same AZ. Take note to have a unique IP address.

Creating & attaching a IGW
A Public subnet routes its data through an Internet Gateway (IGW). So, we have to create a IGW.
On "VPC Dashboard", click on Internet Gateway, and then Create Internet Gateway. 
Upon creation, the IGW is detached, so we're going to attach it to the VPC
At top right of page, click on "Actions" and go to "Attach VPC". Select the right VPC and attach. This though, does not automatically route dat from the SubNet.

Route data from the Public SubNet via the IGW
Now, we need to route the data from the Public SubNet via the IGW
Click on SubNet. Select the Public SubNet we just created. Click on Route Table and then on the Route Table link provided.
In bottom table, click on Route Table, and then Edit routes.
This concludes the setup of the Public SubNet

Route data from the Private SubNet
You may notice that automatically, the Private Subnet assumes the same route table as the Public Subnet which we just set.
To change this, click on Route Tables in your VPC Dashboard. Create route table. Enter name tag, select VPC, and click "Create". 
Select Private SubNet, edit route table associations, and select the correct route table from the options.


Launching an instance
Go to Services. Click on EC2, and Launch Instance.
Choose an Amazon Machine Image (AMI)
Choose an Instance Type and click on Next: Configure Instance Details
To configure, choose the correct VPC under Network, Enable Auto-assign Public IP. Click Next: Add Storage
Update Storage if required. Click Next: add Tags. Edit tags and click Next: Configure Security Group
A security group is a set of firewall rules that control the traffic for your instance.
Create a new Security Group and Edit rules as required.

Click on Review & Launch. At this point, you may review and edit all previously entered details.
Click Launch if details entered correctly.
A dialogue box for selecting/ creating a Key Pair pops up. Make sure to download your Key Pair at this point, otherwise you will not be able to download at another time and thus will be unable to connect to your instance. If this happens, you will have to shut down this instance and create a brand new one.
Key Pair is a private key file that allows you to connect to your instance.
After download of Key Pair, click on Launch.
Your instance is now ready.
