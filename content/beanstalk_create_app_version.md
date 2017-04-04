+++
date = "2017-04-04"
draft = false
title = "Creating a version for AWS Elastic Beanstalk"
section = "5.3.2"
page = 134

+++

Ensuring PowerShell compatibility. 

Replace ...

```
$ aws elasticbeanstalk create-application-version --application-name etherpad --version-label 1.5.2 --source-bundle S3Bucket=awsinaction,S3Key=chapter5/etherpad.zip
```

with ...

```
aws elasticbeanstalk create-application-version --application-name etherpad --version-label 1.5.2 --source-bundle "S3Bucket=awsinaction,S3Key=chapter5/etherpad.zip"
```

Note: `\` as line separator needs to be removed from all code listings as well.