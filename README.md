# Creating EC2-instance, VPC, Subnets, Security-group using Cloud-formation service in AWS

------------
### Description
- By using yaml-file you could create a VPC, subnets, security-group and EC2 instance using cloud-formation service in AWS.
- Benefit of that project: 
	You save time by automating the creation of your infrastructure using cloudFormation service  
	
## :warning:  NOTICE:
-  Here I used **Paris Region** and the availability zones in, so if you use another Region you must change **AvailabilityZone propereties** in the Subnet section.
- Also in the EC2 section, I used **operating system image in that Region also** so if you changed the Region you must set an image of that region .


------------


#### 📝 The Resources section:
-Here are the resources that cloudFormation will create.
- **VPC :**
  - VPC is the virtual network within a subnet 192.168.101.0/24 .
- **PublicSubnetA :**
	-  a public subnet within a subnet 192.168.101.0/28 will be created in AvailabilityZone "eu-west-3a"
	- **MapPublicIpOnLaunch properety** Indicates whether instances launched in this subnet receive a public IPv4 address
	- **VpcId: !Ref VPC** means that subnet will be created in the VPC will be created above.
- **SecurityGroup :**
	- VpcId: !Ref VPC it also will be in the same VPC.
	- This security group allow to  SSH, HTTP inbound traffic and all outbound traffic from any IP address. 
	-  you can* **allow to another inbound/outbound traffic*** by **adding IpProtocol, FromPort, ToPort, CidrIp** in the SecurityGroupIngress/SecurityGroupEgress.
- **EC2Instance :**
	 - ImageId is the operating system image id, ***you must be sure that the image is in the same region you use***. 
	 - KeyName must be the keyPair you use or you can create a new one.
	 - SecurityGroupIds here you assign to the EC2 instance the security groups you want, 
I assigned the Security group i created above.
	 -  SubnetId in which subnet you want the instance be assigned.
   
------------
### How to use the Project

1. Enter to your AWS account
2. Choose *CloudFormation* service
3. press Create new stack with new resources button
4. in template source section choose *Upload a template file* option
5.  press on  *Choose file* so you can upload your yaml file
6. then press next and Enter *Stack name* then *Submit*.

------------
