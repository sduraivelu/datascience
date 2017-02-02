
#### [Moving hosting from GoDaddy to AWS](http://serverfault.com/questions/611805/switching-hosting-from-godaddy-to-aws)
* "In order to move from GoDaddy to AWS, you can a) **just move your code to AWS** (if you have a static website, move it to S3 instead of EC2), **and point your GoDaddy DNS records at your new host** (e.g. your EC2 instance's IP address). In EC2, your instance's IP address will change when the instance reboots, etc. As such it is a dynamic IP address, not well suited for hosting a website. Instead, **you need to allocate a static IP address, once that can be assigned to an instance - AWS call this an 'Elastic IP'. This is what you will use for your A record. (The same holds true whether you use GoDaddy's DNS or Route53** - you need an A record that points to the IP address of your server - but **there is no requirement to use Route53 just because you are using AWS to host** your site - there are some exceptions - e.g. using an elastic load balancer)."
* You don't get to choose your elastic IP. You allocate one, and then associate it with the instance you want to use it with (you can move it between instances if needed). It remains the same until you release the IP address (even it is not associated with an instance). *Just ensure you allocate an IP address in the same region (e.g. US East) and scope (i.e. EC2 or VPC) as the instance you want to associate it with*.