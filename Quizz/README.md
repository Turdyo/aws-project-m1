# Quizz

## IAM

1. What actions are allowed for EC2 instances and S3 objects based on this policy? What specific resources are included?

> We can see in the **Action list** that the rules allow some actions on ec2 and s3. The actions are **Running and Terminate Instances in ec2** and **Get and Put objects on the s3**. It specifies that it can only be on ec2 instances located in the **us-east-1** region or on **every s3 bucket named `example-bucket`**.

2. Under what condition does this policy allow access to VPC-related information? Which AWS region is specified?

> This rule allow access to VPC-related information in condition that the user accessing it is conected on the `us-west-2` region.

3. What actions are allowed on the "example-bucket" and its objects based on this policy? What specific prefixes are specified in the condition?

> We can see on the **Action list** that any IAM user with this rule can either get or put an object, or access to the list objetcs inside the bucket. The prefixes are `documents/*` and `images/*`, meaning that this rule only apply to the files in the `images` and `documents` folders of `example-bucket`.

4. What actions are allowed for IAM users based on this policy? How are the resource ARNs constructed?

> So, the IAM users can create and delete IAM users/ The resource ARNs are constructed as an IAM ressource with the part: `arn:aws:iam::123456789012:user/`. Then we have a placeholder `${aws:username}` that precise the username of the IAM user making the creation/deletion request.

5. **Questions**
- Which AWS service does this policy grant you access to?
> the policity grants an access to the IAM policies.
- Does it allow you to create an IAM user, group, policy, or role?
> No, actually, we only can access information about one policy or list every policies, as indicated with `"Ressource": "*"`.
- Go to https://docs.aws.amazon.com/IAM/latest/UserGuide/ and in the left navigation expand Reference > Policy Reference > Actions, Resources, and Condition Keys. Choose Identity And Access Management. Scroll to the Actions Defined by Identity And Access Management list.��Name at least three specific actions that the iam:Get* action allows.

> So, the `iam/Get*` action is a set of actions that permits to acces to a lot of data. Let's check the most basics ones:
> - `iam/Getuser` Grants permission to retrieve information about the specified IAM user, including the user's creation date, path, unique ID, and ARN
> - `iam/GetRole` Grants permission to retrieve information about the specified IAM user, including the user's creation date, path, unique ID, and ARN
> - `iam/GetPolicy`Grants permission to retrieve information about the specified managed policy, including the policy's default version and the total number of identities to which the policy is attached

> Of course there is a lot more, this is only a small fraction of what is possible with the `iam/Get*` action.

6. **Questions:**
- What actions does the policy allow?
> This policy deny the possibily to run and start instances of ec2 `t2.micro` or `t2.small`. So it means that it allows everything except this.
- How would the policy restrict the access granted to you by this additional statement?
> The restriction would remain the same. In this case, we are just precising that we allow everything on ec2 with this new statement, so it doesn't change anything.
- If the policy included both the statement on the left and the statement in question 2, could you terminate an m3.xlarge instance that existed in the account?
> If the policy included all the statements, we would be able to terminate an `m3.xlarge` instance, since there is no restriction on this kind of instance.

## Network

### IMPORTANT

The corrects answer are indicated with a [x] and are written in **bold**. They are followed by a `(C)` that stands for **Correct**.
_________________
1. Which definition Describes a virtual private cloud (VPC)?

- [ ] A virtual private network (VPN) in the AWS Cloud
- [ ] An extension of an on-premises network into Amazon Web Serices (AWS)
- [x] **A logically isolated vitural network that you define in the aws Cloud** `(C)`
- [ ] A fully managed service that extends the AWS Cloud to customer premises
_________________
2. A company's VPC has the CIDR block `172.16.0.0/21` (2048 addresses). It has two subnets (A and B). Each subnet **must support 100 usable addresses now**, but this number is exptected to **rise to at most 254 soon**. Wich subnet addressing scheme meets the requirement and follows AWS best practices?
- [ ] *Subnet A*:  172.16.0.0/25 (128 addresses) *Subnet B*: 172.16.0.128/25 (1024 addresses)
- [ ] *Subnet A*: 172.16.0.0/25 (128 addresses) *Subnet B*: 172.16.0.128/25
- [x] ***Subnet A*: 172.0.0/23 (512 addresses) *Subnet B*: 172.16.2.0/22 (512 addresses)** `(C)`
- [ ] *Subnet A*: 172.16.0.0/22 (1024 addresses) *Subnet B*: 172.16.4.0/22 (128 addresses)
_________________
3. Which combination of actions enables direct internet access for IPv4 hosts in a VPC? (Select THREE).
- [ ] Creating a default route that points to the virtual private gateway
- [ ] Enabling Domain Name System (DNS) resolution for the VPC
- [x] **Configuring hosts to have or obtain an internet-routable address** `(C)`
- [ ] Configuring the VPC domain name in a Dynamic host Configuration Protocol (DHCP) options set
- [x] **Creating a route for 0.0.0.0/0 that points to the internet gateway** `(C)`
- [x] **Configuring security groups and network access control lists (network ACLs) to permit internet traffic** `(C)`
_________________
4.Several EC2 instances launch in a VPC that has internet access. These instances should not be accessible from the internet, but they must be able to download updates from the internet. How should the instances launch?
- [ ] With Elastic IP addresses, in a subnet with a default route to an internet gateway
- [ ] With public IP addresses, in a subnet with a default route to an internet gateway
- [ ] Without public IP addresses, in a subnet with a default route to an internet gateway
- [x] **Without public IP addresses, in a subnet with a default route to a network address translation (NAT) gateway** `(C)`