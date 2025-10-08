# AWS CloudFormation Template: EC2 Instance Creation

This CloudFormation Template (CFT) helps you launch an EC2 instance in a specified VPC with a security group and keypair.

---

##  **Template Version**
```AWSTemplateFormatVersion: 2010-09-09 ```
Specifies the CloudFormation template version. Here, 2010-09-09 is the current standard.

## **Description**
```Description: EC2 instance creation using the CFT ```
Provides a short description of what this template does.

## **Parameters** ##
Parameters allow you to pass dynamic values when creating a stack on AWS console.

Resources
Resources define the AWS resources to create.
1. Security Group
MySecurityGroup: Type: AWS::EC2::SecurityGroup Properties: GroupDescription: Security Group for EC2 VpcId: !Ref VpcId SecurityGroupIngress: - IpProtocol: tcp FromPort: 80 ToPort: 80 CidrIp: 0.0.0.0/0 
Creates a Security Group for the EC2 instance.
Opens port 80 (HTTP) to the world.
2. EC2 Instance
Ec2Instance: Type: AWS::EC2::Instance Properties: AvailabilityZone: !Ref AvailabilityZone ImageId: !Ref ImageId InstanceType: t2.micro KeyName: !Ref KeyName NetworkInterfaces: - AssociatePublicIpAddress: true DeviceIndex: 0 SubnetId: !Ref SubnetId GroupSet: - !Ref MySecurityGroup 
Launches an EC2 instance with:
The specified AMI and instance type (t2.micro).
The keypair for SSH access.
Attached to the subnet with a public IP.
Associated with the previously created security group.
Summary
This template allows you to quickly deploy an EC2 instance with:
Custom VPC and subnet
Security group allowing HTTP access
Public IP and SSH keypair
Specified AMI and availability zone
--- If you want, I can also make a super-short version of this Markdown suitable for a LinkedIn post so you can share it as a neat snippet. Do you want me to do that?

