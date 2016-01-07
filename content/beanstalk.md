+++
date = "2015-12-21"
draft = false
title = "Ceating an environment to execute Etherpad with Elastic Beanstalk"
section = "5.3.2"

+++

The Node.js version must be pinned to `0.12.6` otherwise Etherpad will not work.

```
$ aws elasticbeanstalk create-environment --environment-name etherpad --application-name etherpad --option-settings Namespace=aws:elasticbeanstalk:environment,OptionName=EnvironmentType,Value=SingleInstance --solution-stack-name "$SolutionStackName" --version-label 1.5.2
```

is not correct. It should be:

```
$ aws elasticbeanstalk create-environment --environment-name etherpad --application-name etherpad --option-settings Namespace=aws:elasticbeanstalk:environment,OptionName=EnvironmentType,Value=SingleInstance Namespace=aws:elasticbeanstalk:container:nodejs,OptionName=NodeVersion,Value=0.12.6 --solution-stack-name "$SolutionStackName" --version-label 1.5.2
```