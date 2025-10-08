# AWS CloudFormation Template: EC2 Instance Creation

This CloudFormation Template (CFT) helps you launch an EC2 instance in a specified VPC with a security group and keypair.


##  **Template Version**
`AWSTemplateFormatVersion: 2010-09-09`

Specifies the CloudFormation template version. Here, 2010-09-09 is the current standard.

## **Description**
`Description: EC2 instance creation using the CFT `

Provides a short description of what this template does.

## **Parameters**
Parameters allow you to pass dynamic values when creating a stack on AWS console.

## **Resources**
Resources define the AWS resources to create.
1. Security Group

```yaml
MySecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Security Group for EC2
      VpcId: !Ref VpcId
      SecurityGroupIngress: 
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
```
Here we are creating a security group for EC2 Instance by allowing traffic with port 22 (SSH) from the World.

2. Creating the EC2 Instance

``` yaml
Ec2Instance:
    Type: AWS::EC2::Instance
    Properties:
      AvailabilityZone: !Ref AvailabilityZone
      ImageId: !Ref ImageId
      InstanceType: t2.micro
      KeyName: !Ref KeyName
      NetworkInterfaces:
        - AssociatePublicIpAddress: true
          DeviceIndex: 0
          SubnetId: !Ref SubnetId
          GroupSet:
            - !Ref MySecurityGroup
```
creating the EC2 instance on the selected Availability Zone, AMI ID, key pair and the subnet which will be available at the parameter feature of the CFT Stack 
