+++
date = "2016-04-07"
draft = false
title = "Using OpsWorks to deploy an IRC chat application"
section = "5.4.2"
page = 140

+++

OpsWorks added a new version of Chef as the new default for the service. To be able to follow the example from 5.4.2 you need to use a Chef 11 stack.

Therefore the 12 steps described in *CREATING A NEW OPSWORKS STACK* need to be replaced with:

1. Click Add Stack under Select Stack or Add Your First Stack.
1. Select Chef 11 stack
1. For Name, type in irc.
1. For Region, choose US East (N. Virginia).
1. The default VPC is the only one available. Select it.
1. For Default Subnet, select us-east-1a.
1. For Default Operating System, choose Ubuntu 14.04 LTS.
1. Select your SSH key, mykey, for Default SSH Key.
1. Select Chef version 11.10
1. Click Add Stack to create the stack.