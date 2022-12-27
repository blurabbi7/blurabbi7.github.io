---
title: BDPU Guard
date: 2022-12-27
---

BPDU Guard is a security feature that prevents unauthorized switches from attaching to your network by disabling the port if a BPDU (Bridge Protocol Data Unit) is received on the port. 
In this blog post, we will go over the steps for configuring BPDU Guard on a Cisco switch.

Step 1: Enable BPDU Guard on the desired port.

To enable BPDU Guard on a particular port, enter the following command:
```
interface interface_name
spanning-tree bpduguard enable
```
For example, to enable BPDU Guard on interface `GigabitEthernet0/1`, you would enter the following command:
```
interface GigabitEthernet0/1
spanning-tree bpduguard enable
```
Step 2: Configure the BPDU Guard violation action.

When a BPDU is received on a port with BPDU Guard enabled, a violation occurs. 
You can specify the action that should be taken when a violation occurs by entering the following command:
```
interface interface_name
spanning-tree bpduguard {enable | disable}
```
Enable: The port is disabled when a violation occurs.
Disable: The port remains enabled when a violation occurs.
For example, to disable the port when a BPDU Guard violation occurs on interface `GigabitEthernet0/1`, you would enter the following command:
```
interface GigabitEthernet0/1
spanning-tree bpduguard enable
```
Step 3: Save the configuration.

To save the BPDU Guard configuration, enter the following command:
```
write memory
```
And that's it! You have successfully configured BPDU Guard on your Cisco switch. 
Be sure to regularly check the BPDU Guard status to ensure it is functioning properly and to update the enabled ports as needed.
