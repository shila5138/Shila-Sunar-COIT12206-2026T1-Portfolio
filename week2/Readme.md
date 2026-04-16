
Project Name: Setting-IP-12298064

Student Name: Shila Sunar
Student ID: 12298064
Date: 9 March 2026

1. Aim

The aim of this task is to learn how to configure static IP addresses on Linux hosts in GNS3 and verify network connectivity between devices in the same subnet.

2. Introduction

GNS3 is a network simulation tool used to design and test network configurations. In this task, multiple Linux hosts are connected through a switch, and each host is assigned a static IP address. This allows communication between devices within the same network.

3. Network Topology

The network consists of:

4 Linux Hosts (Host1, Host2, Host3, Host4)
1 Switch

Each host is connected to the switch using interface eth0.

<img width="452" height="305" alt="image" src="https://github.com/user-attachments/assets/41d1bcbb-4030-420a-a832-c3f6eb28fc3b" />


4. IP Addressing Table
Device	Interface	IP Address	Subnet Mask
Host1	eth0	10.10.10.1	255.255.255.0
Host2	eth0	10.10.10.2	255.255.255.0
Host3	eth0	10.10.10.3	255.255.255.0
Host4	eth0	10.10.10.4	255.255.255.0

All devices are in the same network: 10.10.10.0/24

5. Configuration Steps
Step 1: Create Project

A new project named Setting-IP-12298064 was created in GNS3.

Step 2: Add Devices
Four Linux hosts were added
One switch was added
All hosts were connected to the switch
Step 3: Configure Static IP Address

The IP addresses were configured by editing:

vi /etc/network/interfaces

Example configuration:

auto eth0
iface eth0 inet static
address 10.10.10.X
netmask 255.255.255.0
Step 4: Apply Configuration
ifdown eth0
ifup eth0
Step 5: Verify IP Address
ip address show

Host 1:

<img width="452" height="476" alt="image" src="https://github.com/user-attachments/assets/058921fb-2424-43e4-97e1-da273ecd3b2e" />

Host 2:

<img width="452" height="305" alt="image" src="https://github.com/user-attachments/assets/058bde57-9be4-4216-b142-7a49055653ae" />

Host 3:

<img width="452" height="247" alt="image" src="https://github.com/user-attachments/assets/301695df-6e6e-4867-b1da-ed92ff115c3a" />

Host 3:

<img width="452" height="196" alt="image" src="https://github.com/user-attachments/assets/ba5c6d2f-d6a4-4ef0-b802-fae6a3bc9acc" />

6. Connectivity Testing
Ping Test

Ping command used:

ping 10.10.10.2
Result
Successful communication between hosts
0% packet loss observed

Example output:

Replies received from destination
Time delay shown in milliseconds

Ping-Basics-12298064-simple.png

<img width="452" height="160" alt="image" src="https://github.com/user-attachments/assets/006b456c-e9ec-4b75-97f6-a07b74c81bbe" />


Invalid Network Test

When pinging an unreachable IP (e.g., 10.1.1.99):

Result:

Network unreachable error

Ping-Basics-12298064-error.png

<img width="436" height="99" alt="image" src="https://github.com/user-attachments/assets/1b5e38fd-f1bd-46ed-be1f-f1e28fce93e8" />


Ping-Basics-12298064-options.png

<img width="438" height="189" alt="image" src="https://github.com/user-attachments/assets/20e8b2e6-45af-4de0-a8dd-debb2aee4598" />




7. Results

All hosts were successfully assigned IP addresses
Devices in the same subnet communicated successfully
Invalid IP addresses resulted in errors

8. Conclusion

This experiment demonstrated how to configure static IP addresses and test connectivity in a simulated network. It showed that devices in the same subnet can communicate effectively, while incorrect network configurations result in communication failure.
