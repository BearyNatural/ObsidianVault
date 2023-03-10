# Task 1: Complete Labs

Before beginning this assessment, you need to demonstrate the existing skills and knowledge you’ve developed through the course - this also establishes you are ready for the task.  Here is an example screenshot showing:

·       Module 3 Guided Lab and Capstone Project are **complete** (100%).

·       Module 2 Knowledge Check and Module 3 Challenge Lab are **not complete** (0%)  
![Graphical user interface, text, application
Description automatically generated](file:///C:/Users/kayhowe/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

1.1 Every week, you’ve been completing Knowledge Checks and Labs in AWS Academy.  Below, insert screenshots of your **AWS Academy gradebook** showing your score for the following activities:

·       All Knowledge checks (score: **minimum** of 80%, each module)

·       All Guided Labs (score: **minimum** of 70% for each lab)

·       Challenge Labs from Modules 6, 8, and 9 (**score**: 100% for each lab)  
Note: You may need more than one screenshot.  Doing **all** the challenge labs is highly recommended but only these specific challenge labs are required.

  

# Task 2: Design a secure, scalable, highly available solution

Note: At the end of this document, you’ll see a point-in-time copy of the instructions of the Capstone Project for your convenience.  The Capstone instructions are created by and hosted in AWS Academy - any changes or updates are published there first, so use those notes as your primary guide.  To begin the activity:

·       Log into the AWS Academy account you’ve been using throughout the unit.

·       Click on the AWS Architecting class

·       Click on Modules, scroll to the end (Module 15) and click on **Capstone Project** activity.

·       Read through every part of the activity.

2.1 Before beginning your design, read and review the Capstone project customer requirements.  After you’ve read the scenario, brainstorm AWS services/resources that would satisfy each customer requirement.

**Solution requirement  
(from case study)**

**Ideal AWS services/resources to satisfy the requirement**

**Sub-optimal AWS services/ resources**

_Database connection credentials are secured through AWS Systems Manager Store_

_e.g. AWS Systems Manager Parameter Store (required by scenario)_

_e.g. Storing the username and password on the ec2 instance_

Highly available, fault tolerant, secure MySQL-compatible database

Secure website (written in PHP) for anonymous web users

Website is highly available through the use of a load balancer

Access to AWS admin user is secured

Automated EC2 scaling using a template

2.2 For at least three of the requirements above, **briefly describe** why your chosen service is **ideal** and why the other services were **sub-optimal**. _(e.g. Using DynamoDB for the database isn’t optimal because while it’s fully managed, serverless, highly available, and automatically scales, it is a NoSQL database service and the customer requires a MySQL relational database.  Redesigning/rebuilding to use a NoSQL data store requires significant effort.)_

2.3 **Briefly describe** AWS best practices for securing the **AWS root account**. (Note: because we’re using the AWS Academy/Vocareum you likely won’t be able to **do** each action, but you are required to **know** what to do)

2.4 You were given a partly built environment and a network diagram of the current “as-is” state. Before attempting the project, **create a new network diagram** showing the completed solution.  It must show:

·       The AWS service/resource you used to distribute traffic amongst resources

·       The AWS service/resource you used to automatically scale resources

·       All AWS other service/resources used in this solution (instances, buckets, etc)

·       Subnet details (availability zones and IP address ranges)

·       All security group rules and ACLs (you don’t need to document default allow/deny, just the rules you added)

  

# Task 3: Implement your Solution

With your design completed, now you can implement it.  

·       Make sure tasks 1 and 2 above are complete before implementing your solution.

·       With the Capstone lab running and 5+ minutes remaining, click on the **Submit** button.  This will begin automated checks of your solution to ensure you completed all requirements successfully. 

o   These are simple, basic checks - you must score 100% here.  This doesn’t mean you pass the assessment as you must also complete all the tasks in this document.

o   The automated submission checks take up to 30 seconds.

3.1 Click on the **Submit** button. Paste screenshot(s) of your **successful submission** in the AWS Academy lab, showing:

·       Lab Submission Report showing all checks were complete and successful. It should look similar to the below:  
![Text
Description automatically generated with medium confidence](file:///C:/Users/kayhowe/AppData/Local/Temp/msohtmlclip1/01/clip_image004.gif) ![Graphical user interface, text, application
Description automatically generated](file:///C:/Users/kayhowe/AppData/Local/Temp/msohtmlclip1/01/clip_image006.gif) 

·       The credit remaining and time elapsed to complete this lab  
![](file:///C:/Users/kayhowe/AppData/Local/Temp/msohtmlclip1/01/clip_image008.gif)

3.2 In your browser, browse to the URL of the application to view the website.  **Provide screenshots showing**:

·       The load balancer’s **URL** (you can get this from your browser or the AWS load balancer configuration screen)

·       The main _Example Social Research_ web site page is **working** (i.e. you can see the website in your browser)

·       The web site’s “**Query**” page is working  
(e.g. click on it, then click on any of the queries/reports.  If your website is fully working, you’ll see reports such as Country-level data about lifespans.  If your website is not fully working, you’ll get a blank page.

URL:

Screenshot:

  

Appendix: Task instructions

This is a **copy** of the scenario instructions. Remember: the AWS Academy Capstone Project page always has the most up-to-date version of these instructions. This is only provided for convenience.

# AWS Academy Cloud Architecting - Capstone Project

## Environment Overview

**Important note: Do NOT use the Sandbox for this activity as all your work is deleted when the timer hits 0:00.** 

**Click on Capstone Project in Module 15.**  This environment is **long-lived**. Your data will not be deleted at 0:00 but your resources will be turned off, so turn them back on next time.

When the session timer runs to 0:00, the session will end, **but any data and resources that you created in the AWS account will be retained**. Running EC2 instances will be stopped for you if you did not already stop them before the session ends.

If you later launch a new session (for example, the next day), you will find that your work is still in the lab environment. Any existing EC2 instances may be started up again when you start the new session, but may be assigned new IPv4 public IP addresses.

You can continue to develop your solution as you progress through the course materials.

## Project overview

This project provides you with an opportunity to demonstrate the solution design skills that you develop throughout this course. Your assignment is to design and deploy a solution for the following case.

 By the end of this project, you should be able to apply the architectural design principles that you learned in this course to:

-   Deploy a PHP application that runs on an Amazon Elastic Compute Cloud (Amazon EC2) instance
-   Create a database instance that the PHP application can query
-   Create a MySQL database from a structured query language (SQL) dump file
-   Update application parameters in an AWS Systems Manager Parameter Store
-   Secure the application to prevent public access to backend systems

## Introducing the Example Social Research Organization

Example Social Research Organization is a (fictitious) nonprofit organization that provides a website for social science researchers to obtain global development statistics. For example, visitors to the site can look up various data, such as the life expectancy for any country in the world over the past 10 years.

Shirley Rodriguez, a researcher at the organization, developed the website. She thought it would be valuable to share the data that she had gathered with other researchers. Shirley stores the data in a MySQL database, and the data is available through a PHP website that she built. She initially published the site through a commercial hosting company that provides limited support for technical issues and security.

Over the past year, Shirley’s website has grown in popularity. As a result of increased traffic, she started receiving complaints that the site is not as responsive as it used to be. She also experienced an attempted ransomware security breach. The security breach was unsuccessful, but her supervisor, Mateo Jackson, suggested that Shirley investigate new ways to host the website.

Shirley heard about Amazon Web Services (AWS), and initially moved her website and database to an EC2 instance that runs in a public subnet. She also runs an instance of MySQL on the same EC2 instance.

Shirley approached your team to make sure that her current design follows best practices. She wants to make sure that she has a robust and secure website. One of your colleagues started the process of migrating the site to a more secure implementation, but they were reassigned to another project. Your tasks are to complete the implementation, make sure that the website is secure, and confirm that the website returns data from the query page.

The following summary lists the solution requirements, and provides a diagram of the current environment.

![Text
Description automatically generated](file:///C:/Users/kayhowe/AppData/Local/Temp/msohtmlclip1/01/clip_image010.gif)

### Solution requirements

·       Provide secure hosting of the MySQL database

·       Provide secure access for an administrative user

·       Provide anonymous access to web users

·       Run the website on a t2.micro EC2 instance, and provide Secure Shell (SSH) access to administrators

·       Provide high availability to the website through a load balancer

·       Store database connection information in the AWS Systems Manager Parameter Store

·       Provide automatic scaling that uses a launch template

The following parameters are used by the PHP application to connect to the database:

-   /example/endpoint
-   /example/username
-   /example/password
-   /example/database

**These parameter values are case sensitive**.

## Project deliverables

To complete this assignment, you must:

-   Deploy a PHP application that meets the system requirements outlined above
-   Submit a diagram that illustrates your solution
-   Submit a written summary of the design decisions that you made to achieve the result

## Assets for completing the project

You can use the following assets for this project:

-   [A SQL dump file that contains sample data](https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/ILT-TF-200-ACACAD-20-EN/capstone-project/Countrydatadump.sql)
-   [A .zip file that contains the PHP and image files for the Example Social Research Organization website](https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/ILT-TF-200-ACACAD-20-EN/capstone-project/Example.zip) **Note**: An EC2 launch template named Example-LT is provided in the AWS account. It already has both the SQL dump file and the unzipped PHP application resources built into it.