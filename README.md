# AWS CloudFormation Template: EC2 Instance Creation

This CloudFormation Template (CFT) helps you launch an EC2 instance in a specified VPC with a security group and keypair.

---

##  **Template Version**
```yaml  AWSTemplateFormatVersion: 2010-09-09 ```

Specifies the CloudFormation template version. Here, 2010-09-09 is the current standard.
Description
Description: EC2 instance creation using the CFT 
Provides a short description of what this template does.
Parameters
Parameters allow you to pass dynamic values when creating a stack.
Parameters: VpcId: Type: AWS::EC2::VPC::Id Description: Select the VPC where you want to launch the EC2 Instance 
VpcId: Choose the VPC to launch the EC2 instance.
KeyName: Type: AWS::EC2::KeyPair::KeyName Description: Select the keypair name that you need to give to the EC2 Instance 
KeyName: The keypair used for SSH access to the EC2 instance.
AvailabilityZone: Type: AWS::EC2::AvailabilityZone::Name Description: Provide the AvailabilityZone where you want your EC2 Instance 
AvailabilityZone: Specify which AZ the EC2 instance should be in.
ImageId: Type: AWS::EC2::Image::Id Description: Provide the AMI ID 
ImageId: The AMI to use for the EC2 instance.
SubnetId: Type: AWS::EC2::Subnet::Id Description: Provide the Subnet Id where you want the EC2 Instance to launch 
SubnetId: The subnet in which to launch the EC2 instance.
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

