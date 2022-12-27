---
title: "port Security"
date: 2022-12-27
---

Port security is a security feature that allows you to specify the MAC addresses that are allowed to access a particular port on a Cisco switch. 
This can be useful in preventing unauthorized access to your network and mitigating security risks. In this blog post, we will go over the steps for configuring port security on a Cisco switch.

Step 1: Enable port security on the desired port.

To enable port security on a particular port, enter the following command:
```
interface interface_name
switchport port-security
```
For example, to enable port security on interface GigabitEthernet0/1, you would enter the following command:
```
interface GigabitEthernet0/1
switchport port-security
```
Step 2: Specify the maximum number of MAC addresses allowed on the port.

By default, port security allows only one MAC address on a port. However, you can specify a higher number if needed. To do this, enter the following command:

switchport port-security maximum number_of_addresses

For example, to allow up to three MAC addresses on interface GigabitEthernet0/1, you would enter the following command:

switchport port-security maximum 3

Step 3: Specify the MAC addresses that are allowed on the port.

You can specify the MAC addresses that are allowed on the port by entering the following command:

switchport port-security mac-address MAC_address

For example, to allow the MAC addresses 00:00:00:00:00:01 and 00:00:00:00:00:02 on interface GigabitEthernet0/1, you would enter the following commands:
```
switchport port-security mac-address 00:00:00:00:00:01
switchport port-security mac-address 00:00:00:00:00:02
```
Step 4: Configure the port security violation action.

When a device with an unauthorized MAC address attempts to access the port, a port security violation occurs. 
You can specify the action that should be taken when a violation occurs by entering the following command:

`switchport port-security violation {shutdown | restrict | protect}`

Shutdown: The port is shut down and all traffic is blocked.
Restrict: The port remains up, but only traffic from authorized MAC addresses is allowed.
Protect: The port remains up, but a log message is generated and an SNMP trap is sent to indicate a violation has occurred.
For example, to shut down the port when a violation occurs on interface GigabitEthernet0/1, you would enter the following command:

`switchport port-security violation shutdown`

Step 5: Save the configuration.

To save the port security configuration, enter the following command:

`write memory`

And that's it! You have successfully configured port security on your Cisco switch. 
Be sure to regularly check the port security status to ensure it is functioning properly and to update the allowed MAC addresses as needed.
