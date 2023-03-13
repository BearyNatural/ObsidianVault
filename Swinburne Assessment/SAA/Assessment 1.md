# Task 1: Design a solution for the cloud

You will use the knowledge you have developed across the AWS Academy Cloud Foundations (ACF – all modules) and AWS Academy Cloud Architecting (ACA – modules 1-8) to complete this assessment.  Read through the following scenario and respond to the questions below.

**Scenario**: A new, small business requires your help to design a solution that will be implemented in the AWS Cloud.

The small business runs a website and a Windows application server that they currently host on a PC in their office.  This solution has worked poorly for them: cleaners have unplugged the PC while cleaning, the office internet connection is slow, and one day a staff member was so angry (their country’s soccer team lost a World Cup game) that they threw the PC in the rubbish bin.

To put it mildly, the website and application server’s availability has been poor.  Management have decided to pursue a solution in the AWS cloud (and anger management classes for employees).  
  
Details about their current environment:

·       Public web server public with static content.  This website typically has little traffic, but occasionally will receive a flood of requests.  You can use any web page for now (a sample is provided)

·       Application server: A Windows server that will eventually run Microsoft Office - for staff only.  Staff will log in to the server from the office, use Word, Excel, Outlook etc., then log off.  

Customer requirements:

·       If two or more AWS services satisfy a requirement, the customer prefers the option that requires **less operational effort/overhead** (e.g. no responsibility for updates/security patching) and a **lower cost**.

o   i.e. S3, EBS, and EFS all provide storage and S3 is generally the cheapest.  But if many EC2 instances need to modify data simultaneously, S3 wouldn’t typically satisfy this requirement (EFS might).

[
- S3 is highly available, fast and inexpensive storage
	- can be public bucket
	- with versioning & delete protection on files
	- is serverless
- EC2 - windows instance
	- secure it with SG's to prevent anyone who isn't at the office from accessing
	- NACLs can block smtp port?



·       The **public website**

o   Must be highly available.  Even if an entire AWS availability zone fails, this website must work. 

o   Will only contain static, non-sensitive resources and must be available to anyone around the world. 

o   Must have its resources protected against deletion or modification.

o   Must not run on a server (i.e. serverless) as the company wants to reduce their operating costs.
[
Amazon Simple Storage Service (S3) would satisfy the requirements for Public web server, as it is an object storage, built to store and retrieve any amount of data from anywhere, which is perfect for a static website.  It is a simple storage service that offers industry leading durability, availablility, preformance, security and virtually unlimited scalability at very low costs.  It is also a serverless application that is a regional service, therefore if an availability zone were to go down, it would be unaffected.  S3 has features such as object versioning and object lock, which prevents an object version from being deleted or overwritten for a fixed amount of time or indefinitely, depending on your retention policies. Utilisation of limited bucket policies will ensure security of your objects unauthorised. https://aws.amazon.com/s3/]

·       The **Windows application server**

o   Is a useful tool that staff _sometimes_ use.  If it isn’t working, staff have other software they can use on their computer – so availability requirements aren’t as strict as the website.

o   Must only be accessible from the office. No one else on the internet should be able to connect to it.

o   Must have access to the internet to download applications, security updates, etc.

o   Must run Windows so staff can use Microsoft Office desktop apps.

o   Should cost as little as possible

·       The AWS environment must **prevent all subnets from sending email** (SMTP).  
(A recent malware incident on a staff PC sent millions of spam emails, causing reputation damage)
[ site to site vpn; workspaces; ec2 windows terminal; smtp secured port, block port 25; Port 587 Port 587: The standard secure SMTP port Modern email servers use port 587 for the secure submission of email for delivery. For example, if you use an email client software like Outlook or Apple Mail, it most likely is configured to use this port to send your messages. hybrid setup;

[
Amazon Elastic Compute Cloud (EC2) using Remote Desktop Protocol (RDP) would satisfy the requirements for a Windows application server, as it can run on Windows with Microsoft products and services applications.  A RDP license will be required however if more than 2 staff members will be accessing the service at one time.  Utilisation of NACLs on the subnets will prevent emails being sent externally i.e. internal email will still be allowed.  Security Groups will ensure the server is only accessible from the office.  However the server will have access to the internet for updates, downloads etc.  EC2 can be reasonably cheap depending on the size that is required and further savings are available if on a savings plan and/or scheduled reserved instances.  https://aws.amazon.com/ec2/]

Other notes:

·       For now, the “only available from the office” requirement can be satisfied by limiting traffic to your own IP. 

·       For the web servers, only HTTP traffic is required.

ASG & ELB scaling using sticky sessions (asg distribution method to spread across the AZs; EFS for all the user storage, set up across multiple azs;)
  

Complete the following questions about your design:

1. Demonstrate your cloud design knowledge by **briefly describing** the AWS Well Architected Framework pillars:

2. **Prepare a network diagram** which outlines your solution design.  You must use AWS-specific icons in your diagram.  You may use any application you like (PowerPoint, draw.io, LucidChart, etc.) to make the diagram.   Your diagram must include Security Group and Network Access Control List rules illustrated in the diagram.

3. Part of the AWS Well Architected Framework includes the **Security** and **Cost Optimisation** pillars.   
Describe how your design **specifically** **addresses these pillars**.

4. For the public website, you had many different choices of AWS services that were suitable (EC2 instance running a webserver, S3, Lightsail, etc).  **Answer the questions** below:

·       What were the primary reasons you chose those AWS service(s)?  
(i.e. describe its strengths in terms of the customer’s requirements)

·       Provide the reasons you _did not choose_ another AWS service in your design.  
(e.g. if you chose EC2, describe _specifically_ why Lightsail was inferior option)

  
5. A key requirement of the website was that it must be available even if an entire availability zone becomes unavailable.  **Briefly describe** how your design satisfies this customer availability requirement.

  
6. **Briefly describe** how you could perform backups for each of the AWS services you chose to use in your design.

Optional (challenging) questions – these are not required

7. The customer is curious about how to make their website even more reliable – even if an entire AWS region goes offline.  Describe some possible design changes that would allow the website to **tolerate the failure of a region**.

8. If the customer suddenly decided that the application server was a critical service that needed to be highly available and fault tolerant, **briefly describe** (2-3 sentences) at least one way you could achieve this.

 

# Task 2: Implement your cloud design.

For this task, implement your design.  You may use your own personal AWS account or the AWS Academy Sandbox. If you use the AWS Academy sandbox to implement this solution, remember:

·       Your environment is **terminated and erased** at the lab timer runs down to 0:00.   
Until 0:01, you can click Start Lab to add more time. **Everything is deleted at 0:00 and can’t be recovered.**

o   Make sure you have lots of time left on your timer!

·       Sandbox allows you to use many AWS services but not all (E.g. Workspaces).  If your design uses a service Sandbox doesn’t allow, don’t change your design.  Just use a similar service (e.g. EC2 Linux instance) and write a note below saying you’ve substituted it.

You also can use your work/personal AWS account to implement this, however using your own account may incur costs.  The AWS Academy Sandbox has no costs.

If you need a webpage to make sure the web server is working, use this file: [http://example.com/index.html](http://example.com/index.html)

If you need a _Userdata script_ to install and run a webserver on an EC2 instance running AWS Linux, use this script  
(it updates the operating system, downloads and installs the web server, then installs a sample web page)  
  
#!/bin/bash  
yum update -y  
yum install -y httpd.x86_64  
systemctl start httpd.service  
systemctl enable httpd.service  
wget http://www.example.com/index.html  
mv index.html /var/www/html  
chmod a+r /var/www/html/index.html  
  

Implement your cloud design and collect evidence as described below:

For the **public website**, **paste 2 or more screenshots** below showing: That the website is working correctly, and key configuration details of the AWS service.  (You will need several screenshots)

For the **Windows server**, **paste 3 or more screenshots** showing: You are logged into the Windows server, the instance has appropriate security to block unauthorised connections, and a screenshot with configuration details of the instance (e.g. IP, subnet).

  

# Task 3: Research more advanced cloud designs

Now that you’ve completed the design and implementation, the company would like to know more about future improvements they could make.  They’ve listed a number of use cases below and would like to know more about AWS services that could:

1.       Improve the performance of their public website for global users

2.       Automate backups of the AWS resources/services you chose

3.       Securely connect AWS services to the company’s Windows file server at their office

4.       Protect a future PHP-based web server against common attacks like SQL injection and XSS attacks

5.       Provide a managed database service for a globally distributed application

6.       Automatically add more servers/resources during busy times, and reduce servers/resources during idle times

Choose **three** of the use cases above.  Research and identify 1-2 AWS services that are designed for this use case

**Use case #**

**AWS service(s)**

  

