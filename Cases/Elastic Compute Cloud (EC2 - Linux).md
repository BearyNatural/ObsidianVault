https://command-center.support.aws.a2z.com/case-console#/cases/11144921721/correspondences/ekko:us-east-1:63273696-4976-4445-9b75-662a4552144f
11144921721

To summarize, we could see that there were many requests from Bots which would increase the number of calls to database.  As you might already know, WordPress database includes posts, pages, comments, categories, tags, custom fields, users, and other WordPress settings are stored in Database(in this case RDS database). When bots, accesses different pages in the website, wordpress creates connections to database. I suggested contacting your team who enabled bots and disable bots for now. 

As part of the investigation, I went ahead and checked the Classic Load Balancer LBDiario-1359243828.us-east-1.elb.amazonaws.com  and could see that SurgeQueueLength[1] is high. This is the total number of requests (HTTP listener) or connections (TCP listener) that are pending routing to a healthy instance. While there was surge queue, the apache was still processing requests from CLB. To confirm this, we checked the apache logs and could see that there were around 187k calls from bots in past ~15 hours. Each of these calls can initiate database connection which in turn increases db load. 

While on SSH session, we checked the following:
--
1. Checked the connections to mysql port 3306
sudo ss -plan| grep :3306

2. Checked connections to wordpress
sudo ss -plan| grep :80

3. To check how many connections are there:
sudo ss -plan| grep :80 | wc -l

4. Check number calls with word "bot":
cd /var/log/apache2/
cat access.log | grep -i bot | wc -l

5. See when the access.log was started (it gets rotated based on size or per day):
head -10 access.log

# In the above output, you can see the date

6. Check current date:
date 

7. Check apache version
apache2 -v

8. Reload apache:
sudo /etc/init.d/apache2 restart

9. Restart apache:
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

or
sudo /etc/init.d/apache2 restart
--

We tried adding logging for apache to log remote IP, but since the apache version is less that 2.4.31, this didn't work. We used the steps mentioned in [2]. You can look for the steps mentioned in "Classic Load Balancers with TCP/SSL Listeners (Apache)". 

We also tried to add robot.txt to deny bots access to the website as per [3], but unfortunately, it didn't work. So you'll contact your development team and try to make changes in code as per [4]. 

As mentioned over chat, please note that support EC2-classic has been deprecated on August 15, 2022. Please follow [5] for preparing for migration. You can consider migrating your instance to a bigger and better instance type after migrations. Recommended migration path for m3 instance type is to m5 instance types. Following is a comparison between m3 and m5:
--
M5 instances provide the latest Intel Xeon processors paired with the new Nitro Hypervisor which delivers practically all of the compute and memory resources of the host hardware to your instances. With M5, you get a higher performing CPU with support for AVX-512 instructions, up to 384 GiB of RAM, and up to 25 Gbps of networking bandwidth, all at a lower price point then our previous generation instances.

M3	         Feature 	                                  M5
----------------------------------------------------------------
No	         Latest Intel Xeon Processor	      Yes
No	         Lightweight Nitro Hypervisor	      Yes
High         Network Performance	              25 Gbps
No	         Enhanced Networking	              Yes (ENA-only)
Yes           SSD Storage	                                      No (EBS optimized by default)
Better      Price per Compute Performance      Best
--

Details about pricing is available in [5].

I hope this helps. It was a pleasure chatting with you. Please feel free to contact me if you have any further questions. Thanks!  


References:
[1] https://us-east-1.console.aws.amazon.com/cloudwatch/home?region=us-east-1#metricsV2:graph=~(metrics~(~(~'AWS*2fELB~'SurgeQueueLength~'LoadBalancerName~'LBDiario))~view~'timeSeries~stacked~false~region~'us-east-1~start~'-PT12H~end~'P0D~stat~'Sum~period~300);query=~'*7bAWS*2fELB*2cLoadBalancerName*7d 
[2] https://aws.amazon.com/premiumsupport/knowledge-center/elb-capture-client-ip-addresses/ 
[3] https://www.searchenginejournal.com/prevent-bot-crawling/450430/ 
[4] https://support.google.com/news/publisher-center/answer/9605477?hl=en#:~:text=%2C%20nofollow%22%3E.-,Prevent%20specific%20articles%20on%20your%20site%20from%20appearing%20in%20Google,%22noindex%2C%20nofollow%22%3E 
[5] https://aws.amazon.com/ec2/pricing/on-demand/ 

