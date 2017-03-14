+++
date = "2016-03-12"
draft = false
title = "Creating an environment to execute Etherpad with Elastic Beanstalk"
section = "5.3.2"
page = 134

+++

Code format is broken.

Replace ...

```
$ aws elasticbeanstalk list-available-solution-stacks --output text \
--query "SolutionStacks[?contains(@, 'running Node.js')] | [0]"\
64bit Amazon Linux 2015.03 v1.4.6 running Node.js
```

with ...

```
$ aws elasticbeanstalk list-available-solution-stacks --output text \
--query "SolutionStacks[?contains(@, 'running Node.js')] | [0]"
```
