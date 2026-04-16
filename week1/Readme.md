GNS3 Introduction Assignment

Project Name: GNS3-Intro-12298064
Name: Shila Sunar
Student ID: 12298064
Date: 9 March 2026

1. Aim

The aim of this task is to understand basic GNS3 operations including creating a project, configuring IP addresses, and testing connectivity between devices.

2. Network Topology

The network consists of:

2 Linux Hosts (Host1 and Host2)
1 Switch

Host1 is connected to the switch via eth0, and Host2 is also connected to the switch.

3. IP Configuration
Device	Interface	IP Address
Host1	eth0	10.10.10.1
Host2	eth0	10.10.10.2

All devices are configured in the same subnet: 10.10.10.0/24

4. Configuration Steps
Step 1: Project Creation

A new project named GNS3-Intro-12298064 was created.

Step 2: Add Devices

Two Linux hosts and one switch were added and connected.

Step 3: Configure IP Address

The IP address was configured using:

vi /etc/network/interfaces

Then verified using:

ip address show
Step 4: Verify Configuration

From the console output:

Host1 IP: 10.10.10.1/24
Interface: eth0 is active
Step 5: Connectivity Test

Ping command can be used:

ping 10.10.10.2

This confirms successful communication between hosts.

5. Output
Screenshot 1: Network Topology
<img width="452" height="273" alt="image" src="https://github.com/user-attachments/assets/f7413a54-4f0b-44f0-bf1a-b79b9728900c" />

Screenshot 2: IP Configuration

<img width="452" height="305" alt="image" src="https://github.com/user-attachments/assets/ad804096-599e-486b-834f-0d630590df35" />

6. Conclusion

This task helped in understanding basic GNS3 setup, IP configuration, and connectivity testing. It demonstrated how devices communicate within the same subnet using a switch.

