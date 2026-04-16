GNS3 Static Routing Assignment

Name: Shila Sunar
Student ID:12298064
Date:14 April 2026


Aim

The aim of this assignment is to design and configure a small routed network in GNS3.
This includes setting up static IP addresses, enabling routing between networks, and verifying connectivity.

Network Overview

This network consists of:

 2 LANs (Left and Right)
 2 Routers (Router1 & Router2)
 2 Switches
 8 Linux Hosts

 Network Topology

Left Network: `10.10.10.0/24`
Right Network: `10.10.20.0/24`
Router Link:`10.10.30.0/24`


IP Addressing Table

Left LAN (10.10.10.0/24)

| Device | IP Address  | Gateway    |
| ------ | ----------- | ---------- |
| HostA  | 10.10.10.10 | 10.10.10.1 |
| HostB  | 10.10.10.20 | 10.10.10.1 |
| HostC  | 10.10.10.30 | 10.10.10.1 |
| HostD  | 10.10.10.40 | 10.10.10.1 |

 Right LAN (10.10.20.0/24)

| Device | IP Address  | Gateway    |
| ------ | ----------- | ---------- |
| Host1  | 10.10.20.10 | 10.10.20.1 |
| Host5  | 10.10.20.20 | 10.10.20.1 |
| Host2  | 10.10.20.30 | 10.10.20.1 |
| Host4  | 10.10.20.40 | 10.10.20.1 |

 Routers

| Router  | Interface | IP Address |
| ------- | --------- | ---------- |
| Router1 | eth0      | 10.10.10.1 |
| Router1 | eth1      | 10.10.30.1 |
| Router2 | eth0      | 10.10.30.2 |
| Router2 | eth1      | 10.10.20.1 |

Configuration

Host Configuration Example

auto eth0
iface eth0 inet static
    address 10.10.10.10
    netmask 255.255.255.0
    gateway 10.10.10.1

(All hosts follow the same format with different IPs.)

 Router Configuration

 Router1

auto eth0
iface eth0 inet static
    address 10.10.10.1
    netmask 255.255.255.0

auto eth1
iface eth1 inet static
    address 10.10.30.1
    netmask 255.255.255.0


Router2

auto eth0
iface eth0 inet static
    address 10.10.30.2
    netmask 255.255.255.0

auto eth1
iface eth1 inet static
    address 10.10.20.1
    netmask 255.255.255.0


 Enable IP Forwarding

Run on both routers:


sysctl -w net.ipv4.ip_forward=1

Static Routing

Router1


ip route add 10.10.20.0/24 via 10.10.30.2

 Router2


ip route add 10.10.10.0/24 via 10.10.30.1




Testing & Verification

 Same Network Test


ping 10.10.10.20
ping 10.10.20.30


 Gateway Test


ping 10.10.10.1
ping 10.10.20.1


 Cross Network Test

ping 10.10.20.10
ping 10.10.10.30

All tests were successful with 0% packet loss




<img width="452" height="295" alt="image" src="https://github.com/user-attachments/assets/2cf7fd00-b350-410c-b93a-ef6d81fb0c8a" />

<img width="342" height="445" alt="image" src="https://github.com/user-attachments/assets/48ecb94c-dacd-4c98-b6ba-122fd46bc9d9" />

<img width="337" height="447" alt="image" src="https://github.com/user-attachments/assets/6024108f-ea95-4162-a66b-ec23d896a110" />

<img width="350" height="451" alt="image" src="https://github.com/user-attachments/assets/0001aae7-ffe2-4c72-8be2-7a4be691ea4c" />

<img width="353" height="447" alt="image" src="https://github.com/user-attachments/assets/201bf58f-5ecc-4ea8-bbe0-9b5b8d877517" />

<img width="338" height="419" alt="image" src="https://github.com/user-attachments/assets/1f5627de-9639-4b1b-8702-6cb396ab6818" />

<img width="346" height="426" alt="image" src="https://github.com/user-attachments/assets/78c3dd04-1287-43dd-b4f2-baaec567748e" />

<img width="345" height="423" alt="image" src="https://github.com/user-attachments/assets/25951a3c-2e0b-4cee-a0f4-d2b182826ed6" />

<img width="333" height="426" alt="image" src="https://github.com/user-attachments/assets/edb941f1-5b49-4fed-a4d5-943b11bf37f5" />

<img width="328" height="450" alt="image" src="https://github.com/user-attachments/assets/01f33b2a-c261-4c5c-8654-4cd2914cc826" />

<img width="292" height="439" alt="image" src="https://github.com/user-attachments/assets/9532615f-38c0-4430-8b6f-ade1339190fc" />

<img width="294" height="433" alt="image" src="https://github.com/user-attachments/assets/4c125ab4-b623-400a-b938-4a56c13b7273" />

 Result

Hosts within the same LAN communicate successfully
Routers forward traffic correctly
Cross-network communication works


Conclusion

This assignment helped in understanding:

Static IP configuration
Default gateway setup
Router configuration
IP forwarding
Static routing
Network troubleshooting using ping

The network was successfully implemented and tested in GNS3.

Author


