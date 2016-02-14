+++
date = "2016-02-14"
draft = false
title = "Missing DependsOn for AWS::EC2::VPCGatewayAttachment in various CloudFormation templates"
section = "all"
page = 0

+++

Every CloudFormation template containing a ``AWS::EC2::VPCGatewayAttachment`` attaching an Internet Gateway to a VPC requires a ``DependsOn`` attribute for every resource with a public IP address.

* Auto Scaling Group
* EC2 Instance
* ELB
* Elastic IP
* VPC routes including the Internet Gateway

See http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-dependson.html#gatewayattachment for more details.

Example templates from various chapters have been improved accordingly:

```
chapter2/template.json
chapter6/vpc.json
chapter9/template-multiaz.json
chapter9/template-snapshot.json
chapter9/template.json
chapter11/multiaz-ebs.json
chapter11/multiaz-elasticip.json
chapter11/multiaz.json
chapter12/loadbalancer.json
chapter14/url2png-loadtest.json
chapter14/url2png.json
chapter14/wordpress.json
```

Example from chapter 2 ``chapter2/template.json``:

```
...
"LoadBalancer": {
	"Type": "AWS::ElasticLoadBalancing::LoadBalancer",
	"Properties": {
		"Subnets": [{"Ref": "SubnetA"}, {"Ref": "SubnetB"}],
		"LoadBalancerName": "awsinaction-elb",
		"Listeners": [{
			"InstancePort": "80",
			"InstanceProtocol": "HTTP",
			"LoadBalancerPort": "80",
			"Protocol": "HTTP"
		}],
		"HealthCheck": {
			"HealthyThreshold": "2",
			"Interval": "5",
			"Target": "TCP:80",
			"Timeout": "3",
			"UnhealthyThreshold": "2"
		},
		"SecurityGroups": [{"Ref": "LoadBalancerSecurityGroup"}],
		"Scheme": "internet-facing"
	},
	"DependsOn": "VPCGatewayAttachment"
}
...
```