+++
date = "2017-03-14"
draft = false
title = "Creating an environment to execute Etherpad with Elastic Beanstalk"
section = "5.3.2"
page = 134

+++

The Node.js version `0.12.*` is no longer supported and fails with an error: ConfigurationValidationException Value is not one of the allowed values: [4.6.1, 4.8.0, 5.12.0, 6.9.1, 6.10.0, 7.6.0] 

```
$ aws elasticbeanstalk create-environment --environment-name etherpad --application-name etherpad --option-settings Namespace=aws:elasticbeanstalk:environment,OptionName=EnvironmentType,Value=SingleInstance Namespace=aws:elasticbeanstalk:container:nodejs,OptionName=NodeVersion,Value=0.12.15 --solution-stack-name "$SolutionStackName" --version-label 1.5.2
```

is not correct. It should be:

```
$ aws elasticbeanstalk create-environment --environment-name etherpad --application-name etherpad --option-settings "Namespace=aws:elasticbeanstalk:environment,OptionName=EnvironmentType,Value=SingleInstance" --solution-stack-name "$SolutionStackName" --version-label 1.5.2
```
