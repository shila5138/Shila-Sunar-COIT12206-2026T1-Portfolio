VLAN Configuration in GNS3

Name: Shila Sunar
Student ID: 12298064
Date: 7 April 2026

Aim

The purpose of this assignment is to configure VLANs on an Open vSwitch in GNS3 and verify communication between hosts in the same VLAN and isolation between different VLANs.


Topology

The network consists of one Open vSwitch and four hosts.

Host1 → VLAN 838
Host2 → VLAN 838
Host3 → VLAN 839
Host4 → VLAN 839


Network Diagram


IP Addressing

| Host  | IP Address  | VLAN |
| ----- | ----------- | ---- |
| Host1 | 10.10.1.101 | 838  |
| Host2 | 10.10.1.102 | 838  |
| Host3 | 10.10.1.103 | 839  |
| Host4 | 10.10.1.104 | 839  |

Subnet mask: 255.255.255.0


Switch Initialization

The Open vSwitch service was started using:


sh /etc/openvswitch/init.sh

VLAN Configuration

The VLANs were configured on switch ports using:

ovs-vsctl set port eth1 tag=838
ovs-vsctl set port eth2 tag=838
ovs-vsctl set port eth3 tag=839
ovs-vsctl set port eth4 tag=839


Verification

The configuration was verified using:


ovs-vsctl show

Connectivity Testing

Successful Communication (Same VLAN)


ping 10.10.1.102


Host1 successfully communicated with Host2 because both are in VLAN 838.



Failed Communication (Different VLAN)


ping 10.10.1.103
ping 10.10.1.104


Host1 could not reach Host3 and Host4 because they are in VLAN 839.

ARP / Neighbor Table


ip neigh show


The output shows that only Host2 is reachable, while Host3 and Host4 are marked as FAILED.


Result

Hosts in the same VLAN can communicate successfully.
Hosts in different VLANs cannot communicate.


Conclusion

This experiment demonstrates how VLANs logically separate network traffic on a single switch. Devices within the same VLAN communicate normally, while devices in different VLANs are isolated, even though they share the same physical infrastructure.


Screenshots:

<img width="410" height="258" alt="image" src="https://github.com/user-attachments/assets/e8072be6-dd2f-4c96-9faf-951149dba602" />


Host1:
<img width="411" height="267" alt="image" src="https://github.com/user-attachments/assets/388ec8ed-219b-4bd7-81ea-5b60d0f03a15" />

<img width="400" height="311" alt="image" src="https://github.com/user-attachments/assets/c4b53ac8-c03e-4fc9-9089-cd44cdecfb3e" />

<img width="429" height="289" alt="image" src="https://github.com/user-attachments/assets/e23b23cd-da06-4a0f-b8ed-b73104d85322" />

Pinging host2 from host 1:

<img width="366" height="260" alt="image" src="https://github.com/user-attachments/assets/4801b006-d7ea-412a-8647-4b3f03695706" />


Pinging host3 from host1:


<img width="441" height="299" alt="image" src="https://github.com/user-attachments/assets/5f5c1022-9564-4211-be0d-71a3d2449099" />


<img width="452" height="305" alt="image" src="https://github.com/user-attachments/assets/34fca12a-270c-451a-a2c5-b59628f55d6d" />


<img width="413" height="343" alt="image" src="https://github.com/user-attachments/assets/513f2778-3c13-48cc-9607-f2bfa87ef369" />



<img width="399" height="283" alt="image" src="https://github.com/user-attachments/assets/37500b17-65ff-40a1-8513-8d3e219085e5" />



<img width="344" height="95" alt="image" src="https://github.com/user-attachments/assets/24ebe38e-6a79-4e1d-873a-94c80ee8022f" />



