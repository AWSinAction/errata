+++
date = "2015-10-16"
draft = false
title = "Elastic IP flip causes short downtime"
section = "3.6"

+++

> Requests using the Elastic IP address will now be routed to virtual server B without interruption

is not correct. It should be:

> Requests using the Elastic IP address will now be routed to virtual server B with a short interruption while moving the Elastic IP
