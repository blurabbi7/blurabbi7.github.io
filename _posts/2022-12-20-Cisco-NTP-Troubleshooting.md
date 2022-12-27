## Network Time Protocol

---

NTP (Network Time Protocol) is a protocol used to synchronize the clocks of computers and other devices over a network. It is important for security because accurate time synchronization is essential for a wide range of applications, including event logging, digital certificate expiration, and network communication.

Lets say, if two devices are communicating with each other and their clocks are not synchronized, it may be difficult to determine the order in which events occurred. This can make it difficult to accurately diagnose problems or detect security breaches. Additionally, if the clock on a device is set to a time that is significantly different from the actual time, it can cause issues with digital certificates, which are used to authenticate the identity of devices and users.

Moreover, accurate time synchronization is also important for security because it can help to prevent attacks that rely on manipulating the clock or other time-related information. For example, an attacker might try to "spoof" the time on a device in order to bypass security measures or to make it appear that an event occurred at a different time.

Overall, NTP is an important tool for ensuring the accurate and secure operation of networks and devices.


## NTP Troubleshooting on Cisco Network Devices

---
Troubleshooting NTP on Cisco IOS can be a daunting task, but with the right set of commands and a bit of patience, you can resolve most issues. 
In this blog post, we will go over some common NTP issues and the steps you can take to troubleshoot them.

Step 1: Verify NTP is enabled on your device.

To do this, enter the following command:

`show ntp status`

If NTP is enabled, you should see output similar to this:
```
Clock is synchronized, stratum 3, reference is 10.1.1.1
nominal freq is 250.0000 Hz, actual freq is 250.0000 Hz, precision is 2**18
reference time is D5D5F5E5.6AC5A5A5 (15:48:53.128 CDT Mon Jul 13 2020)
clock offset is -3.3621 ms, root delay is 4.72 ms
root dispersion is 12.53 ms, peer dispersion is 2.91 ms
```
If NTP is not enabled, you will see output similar to this:
```
Clock is unsynchronized, stratum 16, reference is 0.0.0.0
nominal freq is 250.0000 Hz, actual freq is 250.0000 Hz, precision is 2**18
reference time is 00000000.00000000 (00:00:00.000 UTC Fri Dec 31 1999)
clock offset is 0.0000 ms, root delay is 0.00 ms
root dispersion is 0.00 ms, peer dispersion is 0.00 ms
```

Precision is determined automatically and is measured as a power of two. In the example, 2**18 means 2^(-18), or 3.8 microseconds.

Loss of synchronization between NTP peers or between a master and client can be due to a variety of causes. NTP avoids synchronization with a machine whose time might be ambiguous in these ways:

1. NTP never synchronizes to a machine that is not synchronized itself.
2. NTP compares the time that is reported by several machines and does not synchronize to a machine whose time is significantly different from the others, even if its stratum is lower.


If NTP is not enabled, you can enable it by entering the following command:

`ntp enable`

Step 2: Check the status of your NTP peers.

To do this, enter the following command:

`show ntp associations`

This will display a list of your NTP peers, along with their status. If a peer is not in the "reachable" state, it may be experiencing issues and causing your NTP issues.

Step 3: Check for NTP-related errors in the log.

To check for NTP-related errors in the log, enter the following command:

`show logging`

This will display a list of log messages, including any NTP-related errors. If you see any errors, try to troubleshoot the issue based on the error message.

Step 4: Check the status of your network connectivity.

If you are experiencing issues with your NTP peers, it may be due to connectivity issues on your network. 
To check the status of your network connectivity, enter the following command:

`show interface`

This will display a list of your interfaces and their status. If an interface is down or experiencing errors, it may be causing issues with your NTP connectivity.

Step 5: Check the status of your NTP server.

If you are using an external NTP server, you may want to check the status of the server to ensure it is functioning properly. 
To do this, you can use an external tool such as `ping` or `traceroute` to check the server's connectivity.


Some of the most common causes of NTP issues are:

+ NTP packets are not received.
+ NTP packets are received, but are not processed by the NTP process on the IOS.
+ NTP packets are processed, but erroneous factors or packet data causes the loss of synchronization.
+ NTP clock-period is manually set.

Important debug commands that help isolate the cause of these issues include:
```
debug ip packets <acl>
debug ntp packets
debug ntp validity
debug ntp sync
debug ntp events
```
For Cisco Unified Communication appliances use `utils ntp status` as in image below:

![This is an image](https://community.cisco.com/t5/image/serverpage/image-id/6177iAE585E872DCBAD36/image-size/large?v=v2&px=999)

By following these steps, you should be able to troubleshoot most NTP issues on Cisco IOS devices. 
If you are still experiencing issues after trying these steps, you may want to seek further assistance from your network administrator or a technical support representative.

REFERENCE:
https://www.cisco.com/c/en/us/support/docs/ip/network-time-protocol-ntp/116161-trouble-ntp-00.html
