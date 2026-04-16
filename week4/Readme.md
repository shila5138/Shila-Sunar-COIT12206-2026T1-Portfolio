Project Name: View-Routes-12298064

Student Name: Shila Sunar
Student ID: 12298064
Date: 30 March 2026

1. Aim

The aim of this task is to configure IP addressing and routing in a network using GNS3, and to verify communication between different subnets through a router.

2. Introduction

In networking, routers are used to connect different networks and allow communication between them. In this experiment, multiple hosts are connected through a switch and a router, with each network assigned a different IP range. Routing is configured to enable communication across these networks.

3. Network Topology

The network consists of:

3 Linux Hosts (Host1, Host2, Host3)
1 Switch
1 Router
Host1 and Host2 are in network: 10.10.1.0/24
Host3 is in network: 10.10.2.0/24
Router connects both networks

<img width="452" height="260" alt="image" src="https://github.com/user-attachments/assets/0d1f83ed-e34d-44fc-9316-9fb4d3c5c779" />


4. IP Addressing Table

| Device  | Interface | IP Address  | Subnet Mask   | Gateway   |
| ------- | --------- | ----------- | ------------- | --------- |
| Host1   | eth0      | 10.10.1.101 | 255.255.255.0 | 10.10.1.1 |
| Host2   | eth0      | 10.10.1.102 | 255.255.255.0 | 10.10.1.1 |
| Router1 | eth0      | 10.10.1.1   | 255.255.255.0 | —         |
| Router1 | eth1      | 10.10.2.1   | 255.255.255.0 | —         |
| Host3   | eth0      | 10.10.2.103 | 255.255.255.0 | 10.10.2.1 |


5. Configuration Steps


Step 1: Create Project

Created a project named:
View-Routes-12298064

Step 2: Add Devices

Added 3 Linux hosts
Added 1 switch
Added 1 router
Connected all devices properly

Step 3: Configure Host IP Addresses

Command used:

vi /etc/network/interfaces

Example configuration (Host1):

auto eth0
iface eth0 inet static
address 10.10.1.101
netmask 255.255.255.0
gateway 10.10.1.1

Same method used for Host2 and Host3.

Step 4: Configure Router

Router configuration:

auto eth0
iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 10.10.2.1
netmask 255.255.255.0


Step 5: Enable IP Forwarding

sysctl net.ipv4.ip_forward=1

This allows the router to forward packets between networks.


Step 6: Apply Configuration
ifdown eth0
ifup eth0


Step 7: Verify IP Address
ip address show

<img width="452" height="122" alt="image" src="https://github.com/user-attachments/assets/8aa7e12d-c0e5-48e7-8587-cb21b6fcee27" />



6. Connectivity Testing

Ping Tests Performed
Host → Router
ping 10.10.1.1
Host1 → Host2
ping 10.10.1.102
Host1 → Host3 (different network)
ping 10.10.2.103
Results
All pings were successful 
0% packet loss observed
Communication between different networks worked correctly

<img width="397" height="346" alt="image" src="https://github.com/user-attachments/assets/a848753f-9943-4419-a9ed-6ee9530c8202" />

7. Results

IP addresses were successfully configured
Router successfully connected two networks
Devices communicated across different subnets

8. Conclusion

This experiment demonstrated how routing enables communication between different networks. By configuring a router and enabling IP forwarding, devices in separate subnets were able to communicate successfully.
