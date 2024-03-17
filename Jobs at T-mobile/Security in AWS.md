The importance of security
![[Pasted image 20240316235719.png]]
Security of the underlying physical infrastructure
- Number of data centers
	- Physical servers
	- Network devices 
- We have data center access, so only approved employees are allowed to get access. But the access to the data center is granted based on the principle of least privilege
	- also based on time period, not infinitive
- All physical access to the AWS data centers is logged and monitored
	- also to detect and alert in case of any security incidents
	- Need authentication

Tools available for security
- Identity and Access Management (IAM) - This service allows you to manage users and encryption keys in AWS
- Amazon Cognito - This can be used for managing users for your applications
- Amazon GuardDuty - This can be used for managing threats to your AWS environment
- Amazon Inspector - This can be used to check for vulnerabilities to your underlying infrastructure 
- Amazon Macie - This helps to discover, classify and protect the data
- AWS Key Management Service - Here you can create and manage your encryption keys
- AWS Artifact - Here you can get access to AWS compliance reports
- AWS Certificate Manager - This can be used to provision, manage and deploy SSL and TLS based certificates
- AWS Secrets Manager - This can be used to manage your secrets
- AWS Shield - This can be used to protect your environment against DDoS attacks
- AWS WAF - This is used to filter malicious web traffic

Shared responsibility
![[Pasted image 20240317101529.png]]
- AWS is responbile for
	- The underlying physical infrastructure
	- Ensure the infrastructure is up and running
	- Ensuring physical security of the underlying infrastructure
	- Ensuring security against attacks on their own infrastructure
	- Configuration of the physical devices
	- Replacing physical devices that have reached end of life
- The customer is responsible for
	- Patch management for the underlying resources. When looking at EC2 (Elastic Compute Cloud service), the customer has to ensure that the underlying instances are patched on a regular basis.
	- Customers have to use the available security controls in AWS to protect their resources.
	- Configuring their own operating systems
	- Training their own employees on how to work with AWS resources

Incident Response
- The principles of Incident Response
	- Educate
		- Customers
		- IT support staff on the Incident Response Plan
	- Prepare
		- Show the plan to respond to an incident, or right mitigation plans
	- Simulate
		- Try to simulate an incident and see if the plan works
	- Iterate
		- Keep on reviewing your incident response plan on a regular basis to make sure that it adheres to changes in your environment. Make the generalized solution
- What you consider?
	- Objectives
		- Do you need to carry out any sort mitigation plans, preserve data for forensics
	- Understand the data you have and what you need - ensure to have logs, snapshots and other data in place for investigative purposes.
		- AWS Cloudwatch
		- Cloudtrail
		- Amazon S3 access logs
		- VPC flow logs
	- See if you can automate responses to incidents, so that the incidents can be resolved faster.
	- Ensure to have scalable solutions. This helps reduce the time between the detection and response to the incident.
	- Keep on improving your incident response process.
	- You should use AWS Cloud tools as your disposal. Or you can use third party tools for threat intelligence, host intrusion and detection systems
		- AWS Support can also call you if they suspect any abusive or malicious activity
- Response plan
	- If an event has occurred in an affected account in place to investigate the event
		- We should have at least 1 separated account just to investigate incidents
		- Use CloudInformation templates to provision resources in out isolated account.
	- Ensure that IAM policies are in place to allow the response team to have read only permission to the data
		- Sometimes your response team might need to copy the EBS snapshots of EBS volumes which are attached to an affected instance. They want to understand how the instance has been impacted or affected
		- Ensure that the response team has permission to copy the EBS snapshots onto the isolated account
	- Ensure to isolate resources that have been affected
	- Look at creating forensic workstations
		- Create and EC2 Instance from a base AMI image
			- EC2 is the service in AWS, offers businesses the ability to run applications on the public cloud.
			- An EC2 instance is simply a virtual server in Amazon Web Services terminology. With an EC2 instance, AWS subscribers can request and provision a computer server within the AWS cloud. With EC2, you can quickly scale compute resources up or down as needed, paying only for the capacity you actually use. These instances can run various operating systems, including Linux and Windows, and offer a wide range of instance types optimized for different workloads, such as compute-optimized, memory-optimized, storage-optimized, and more.
			- When you launch an EC2 instance, you can choose the Region and the specific Availability Zone where you want your instance to be deployed.
			- EC2 vs S3
				- Where EC2 is like a remote computer running Windows or Linux, S3 is simply a storage service for storing large binary files.
			- EC2 vs EBS
				- [Amazon Elastic Block Store](https://aws.amazon.com/ebs/) (Amazon EBS) provides block-level storage volumes for an EC2 instance.
			- EC2 vs AWS Lambda
				- [AWS Lambda](https://www.sumologic.com/glossary/aws-lambda/) can be considered an EC2 Container Service (ECS) framework that uses containers to run a piece of code representing your application.
			- EC2 vs Cloudwatch
				- The CloudWatch agent collects metrics and logs from Amazon EC2 instances and on-premises servers.
			- EC2 vs AMI
				- The [Amazon Linux AMI](https://aws.amazon.com/amazon-linux-ami/) is a supported and maintained Linux image provided by Amazon Web Services for use on Amazon Elastic Compute Cloud (Amazon EC2).
		- Harden the underlying operating system
		- Install the preferred forensic tools on the system
		- Create an AMI out of the EC2 Instance
		- Ensure to rebuild the AMI on a regular basis with the latest software patches

AWS IAM (Identity and Access Management)
- This service allows you to manage users and encryption keys in AWS
- We want to deal with compromised users
	- It is the account that a threat actor gains access to a user's credentials or finds another way to act on their behalf.
- If the user has been assigned Access Keys, consider making them inactive (applied for compromised users)
- Do not consider deleting them directly or access keys. Because if the keys are being used in an application, that application could be impacted
- Review all policies that have been assigned to the user
- Check Cloudtrail events
- After that, you can delete the user account and recreate it again
	- If the user has long term access credentials, consider using IAM roles. Roles tend to use short term credentials which is much safer.
- When using this service on AWS, you can see the details about users: Permission, Groups, Tags, Security credentials, Access Advisor
	- In security credentials, there is access key ID, status. The user has the ability to log in via the console with a password. If the user is compromised, you need to mark the access key as inactive as first. 
	- After there is no impact based on the access key, you can go ahead and delete the access key. And create new access key.
	- In Access advisor, you can see how often the user has used the permissions (Last accessed related to service name and policy type). Now we need to detach policy assigned to the user in Permissions tab.

AWS EC2 (Elastic Block) Instances
- 