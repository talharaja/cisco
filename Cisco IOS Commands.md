## Router configuration

|     |     |
| --- | --- |
| ?   | explore the command |
| enable | privileged executive mode |
| disable | user exec mode |
| configure terminal | global configuration mode |
| exit | drop down / go back one level |
| end | drop down back to privileged exec mode |
| interface <interface> | configure interface/port on device |
| ip address <address>  <subnet> | configure ip address |
| duplex auto | auto full duplex mode enabled |
| speed auto | auto speed setting |
| no shutdown | configure port status up |
| show ip interface brief | show interfaces details |
| show ip <protocol> interface brief | e.g  show ip ospf interface brief |
| show ip <protocol> neighbor | e.g. show ip ospf neighbor |
| show ip route | show routes in routing tables |
| hostname <name> | create router name |
| ip route <network> <subnet> <next hop> | create static route |
| no ip route <network>  <subnet> <address> |     |
| enable password <password> | creating  password |
| show running-config   (do show run) | view password/configuration |
| show run \| begin hostname | view details starting from hostname |
| show run \| include/exclude interface | view details with line include/exclude |
| service password-encryption | create and encrypt password - Type 7 |
| no service password-encyrption | decrypt future password |
| enable secret <password> | create and encrypt password -Type 5 |
| copy running-config start-up config  (write) | save configuration of router |
| show startup-config | view configuration |
| reload | reboot |
| no router <protocol> | remove/delete protocol from router |
| debug ip rip |     |
| show run int <int> | to check bandwidth |
| default-information originate | router connected to internet to avoid configuring each router for public internet access |

## Switch configuration

|     |     |
| --- | --- |
| interface vlan 1 |     |
| ip address 192.168.0.10 255.255.255.0 |     |
| no shutdown |     |
| exit |     |
| ip default-gateway [192.168.0.1](http://192.168.0.1) |     |
| interface <interface> |     |
| description <comment or describe> |     |

## Interface speed and duplex

|     |     |
| --- | --- |
| interface <interface> |     |
| duplex full |     |
| speed 100 |     |

## Verification Commands

|     |     |
| --- | --- |
| show running-config |     |
| show ip interface brief |     |
| show run interface vlan 1 | show manually configured configuration |
| show interface vlan 1 | show all details of interface e.g Mac Address, IP etc |
| show version | show IOS version running |

## CDP Cisco Discovery Protocol (Cisco Properietry)

|     |     |
| --- | --- |
| cdp run | enabled by default on cisco devices |
| no cdp run | stops cdp for neighbours on all ports of switch or router |
| no cdp enable | stops particular port on cisco devices |
| show cdp neighbors | show neighbors |
| show cdp neighbors detail | show neighbors details |

## LLDP Link Layer Discovery (Open Standard)

|     |     |
| --- | --- |
| lldp run | enabled or disabled by default on devices |
| no lldp run |     |
| no lldp transmit |     |
| no lldp receive |     |
| show lldp |     |
| show lldp neighbors |     |
| show lldp neighbors detail |     |

## Factory Reset

|     |     |
| --- | --- |
| write erase |     |

## Dynamic Routing Protocol (RIP)

|     |     |
| --- | --- |
| show ip protocols |     |
| show run \| section rip |     |
| show run \| begin rip |     |
| show ip  rip database |     |
| show ip route |     |

## **EIGRP Protocol**

|     |     |
| --- | --- |
| router eigrp 100 | '100' is autonomous system and should be same to peer with each other |
| network <network address> <wildcard mask> |     |
| eigrp router-id <router-id number> |     |
| show run \| section eigrp | router configuration |
| show ip eigrp neighbors |     |
| show ip protocols |     |
| show ip eigrp interface |     |
| show ip route | ##  |

## Dynamic Routing Protocol (OSPF)

|     |     |
| --- | --- |
| router ospf 1 | 1 is process ID |
| network <address> <wildcard mask> area 0 | look interfaces with network and activate OSPF on specified interfaces |
| passive-interface <interface> | Loop back address and other devices etc |
| passive-interface default | only use if there are more passive interfaces to configure |
| no passive-interface <interface> | only use if last command used to remove passive interfaces default |
| default-information originate | to avoid configuring each router for public internet access |
| auto-cost reference-bandwidth 100000 | change default bandwidth of 100 (router ospf 1) |
| ip ospf cost <cost> | changing interface bandwidth only (manipulating path) |
| area <area num> range <network> <subnet> | manual summation required for ABRs |
| ip ospf priority <priority number> | setting ospf priority at interface level (default priority =1 ) |
|     |     |
| show ip protocols |     |
| show ip ospf neighbor |     |
| show ip ospf interface br |     |
| show ip ospf interface <int> | show ospf metric cost |
| show  ip ospf database |     |
| debug ip ospf adj | show whole process of OSPF adjancy |

## ABR

Manual Summarization

|     |     |
| --- | --- |
| router ospf 1 |     |
| network [10.1.0.0](http://10.1.0.0) [0.0.255.255](http://0.0.255.255) area 0 |     |
| network [10.0.0.0](http://10.0.0.0) [0.0.255.255](http://0.0.255.255) area 1 |     |
| area 0 range [10.1.0.0](http://10.1.0.0) 255.255.0.0 |     |
| area 1 range [10.0.0.0](http://10.0.0.0) 255.255.0.0 |     |

![[50_Studies/Networking/_resources/Cisco_IOS_Commands.resources/image.png]]

## 

## Copy Paste Router Commands

|     |
| --- |
| enable |
| config terminal |
| int g0/0 |
| ip address 10.0.3.2 255.255.255.0 |
| no shutdown |
| int g0/1 |
| ip address 10.1.3.2 255.255.255.0 |
| no shutdown |
| exit |
| do copy running-config startup-config |

## RIP Protocol

config t
router rip
version 2
no auto-summary
network 10.0.0.0

## EIGRP Protocol

config t
router eigrp 100
no auto-summary
network 10.0.0.0

## OSPF Protocol

|     |     |
| --- | --- |
| config t<br>router ospf <process id><br>router-id <router id> (optional as automatically set by router)<br>network 10.0.0.0 0.255.255.255 area 0<br><br>passive-interface <interface>  (where we have no router e.g PC connected)<br><br>show ip ospf interface<br>show ip ospf neighbor<br>show ip ospf database<br>show ip route | en<br>conf t<br>router ospf 100<br>network 10.2.0.0 0.255.255.255 area 0<br>network 10.3.0.0 0.255.255.255 area 0<br><br>auto-cost reference-bandwidth 100000 |

## Configure IS-IS Protocol

config t
router isis
 net 49.0001.0000.0000.0001.00
!
interface f0/0
 ip router isis
!
interface f1/0
 ip router isis
!
interface f2/0
 ip router isis
!
interface f3/0
 ip router isis

## Troubleshooting

|     |
| --- |
| ping |
| traceroute |

## DHCP using Cisco Router

|     |     |
| --- | --- |
| ip dhcp excluded-address 10.10.10.1 10.10.10.10 | exclude dhcp IP, printers etc which requires static IP |
| service dhcp | start dhcp |
| ip dhcp pool <pool name> | pool name e.g Main or 10.10.10.0 \_Clients etc |
| network <network address> <subnet mask> | network 10.10.10.0 255.255.255.0 |
| dns-server <IP address> | dns-server 10.10.20.10 (routers own address) |
| default-router <Ip address> | default gateway e.g 10.10.10.1 or router own address |
| show ip dhcp pool | show dhcp details |
| show ip dhcp bindings | all leased ip and mac addresses |

## DHCP using External DHCP Server

**Configure Router to forward Request to DHCP Server**

|     |
| --- |
| int <interface> |
| ip helper-address <DNS-Server> |

## Router DNS Commands

### DNS Client

|     |     |
| --- | --- |
| ip domain-lookup | will look for router which needs to resolve DNS |
| ip name-server <router-itself-ip> | router which is resolving DNS |
| ip domain-name flackboxA.lab | primary domain name |
| ip domain-name flackboxB.lab | additional DNS suffixes to search |

### DNS Server

|     |     |
| --- | --- |
| ip dns server | router resolving DNS |
| ip host <name> <address> | router adding DNS list |

## VLAN

**Configure VLANs**

|     |
| --- |
| vlan <VLAN ID> |
| name <Name> |

**Assigning Interfaces**

|     |     |
| --- | --- |
| configure terminal |     |
| interface <interface> |     |
| switchport mode access |     |
| switchport access vlan <VLAN ID> |     |
| int <interface> | select to delete |
| no switchport access vlan <vlan-id> | delete port from vlan |
| show vlan brief |     |

## Trunk

|     |
| --- |
| interface <interface> |
| description Trunk to SW2 |
| switchport mode trunk |
| switchport trunk encapsulation dot1q |
| switchport trunk allowed vlan {VLAN IDS} |

## Voice VLAN Configuration

|     |
| --- |
| interface <interface> |
| description IP Phone |
| switchport mode access |
| switchport access vlan 10 |
| switchport voice vlan 20 |

## Native VLAN

|     |
| --- |
| vlan 199 |
| name Native |
| interface <interface> |
| switchport trunk encapsulation dot1q |
| switchport mode trunk |
| switchport trunk native vlan 199 |
| show interface <interface> switchport |

## **Limiting Allowed VLANs**

|     |
| --- |
| int <interface> |
| switchport trunk allowed vlan 10,30 |

## Dynamic Trunking Protocol - DTP

|     |     |
| --- | --- |
| switchport mode dynamic auto |     |
| switchport mode dynamic desirable |     |
| switchport nonegotiate | disable DTP |

## VLAN Trunking Protocol - VTP

|     |     |
| --- | --- |
| vtp domain Flackbox |     |
| vtp mode server OR vtp mode server OR vtp mode transparent |     |
|     |     |

## Inter-VLAN Routing

### Option 2: Router on a stick

|     |
| --- |
| interface <interface> |
| no ip address |
| no shutdown |
| interface <interface.any logical number\> |
| encapsulation dot1q 10 |
| ip address <gateway> <subnet> |
| int <interface> |
| switchport mode trunk |

### Option 3:

|     |     |
| --- | --- |
| ip routing |     |
| interface vlan 10 |     |
| ip address <gateway> <subnet> |     |
| interface vlan 20 |     |
| ip address <gateway> <subnet> |     |
| int <interface on switch requires routing> | Switch requires routing cofiguration |
| ip  address <address> <subnet> |     |
| R # int <interface> AND ip address <address> <subnet> |     |

|     |     |
| --- | --- |
| SW: int <int> |     |
| no switchport |     |
| ip address [192.168.100.1](http://192.168.100.1) [255.255.255.0](http://255.255.255.0) |     |
| ip route [0.0.0.0](http://0.0.0.0) [0.0.0.0](http://0.0.0.0) [10.10.100.2](http://10.10.100.2) |     |
|     |     |
| Router: int <int> |     |
| ip address [192.168.100.2](http://192.168.100.2) [255.255.255.0](http://255.255.255.0) |     |
| int <int> |     |
| ip address 203.0.113.2 255.255.255.0 | ip address [203.0.113.1](http://203.0.113.1) 255.255.240.0 |
| ip route [0.0.0.0](http://0.0.0.0) [0.0.0.0](http://0.0.0.0) [203.0.113.2](http://203.0.113.2) |     |
| ip route [192.168.0.0](http://192.168.0.0) [255.255.0.0](http://255.255.0.0) 192.168.100.1 |     |

## 

## 

## Floating Static Route

**Configure FSR**

|     |
| --- |
| conf t |
| ip route <dst address> <dst subnet mask> <next hop> <AD value> |

**Show Routing table**
show ip route

## First Hop Redundancy Protocol - FHRP

**HSRP - Cisco**

|     |     |
| --- | --- |
| configure terminal |     |
| interface <interface ID> |     |
| ip address <IP address> <subnet mask> |     |
| no shutdown |     |
| standby version <version> |     |
| standby <group number> ip <virtual IP> | standby 1 ip 10.10.10.1 |
| show standby |     |
| show standby brief |     |
| standby 1 priority 110 | Priority and Pre-emption - default value is 100 |
| standby 1 preempt | only on one router |

## Network Time Protocol - NTP

|     |
| --- |
| configure terminal |
| ntp server <NTP IP address/domain> |
| show clock |
| show ntp associations |
| show ntp status |

## Network Time Protocol - NTP Server (Cisco Router)

|     |     |
| --- | --- |
| configure terminal |     |
| clock timezone GMT  <hours> |     |
| clock summer-time BST recurring last Sun Mar 1:00 last Sun Oct 2:00 | CertBro UK time zone command |
| ip name-server 8.8.8.8 | google DNS server |
| ntp server pool.ntp.org | one of famous time server |
| show ntp status |     |
| show ntp associations |     |
| show clock |     |

## Port Security

|     |     |
| --- | --- |
| configure terminal |     |
| interface range <start interface> - <end interface> |     |
| switchport mode access |     |
| switchport port-security |     |
| switchport port-security mac-address <sticky/H.H.H> |     |
| swtichport port-security violation <protect/restrict/shutdown> |     |
| show ip int br |     |
| show port-security |     |
| show port-security interface <Interface> |     |

## ACL

|     |     |
| --- | --- |
| configure terminal |     |
| access-list <List number> <permit/deny> <protocol> <Source> <Destination> <Port> |     |
| interface <interface> |     |
| ip access-group <List number> <in/out> |     |
| show access-lists |     |

## **Spanning Tree**

|     |     |
| --- | --- |
| show spanning-tree |     |
| show spanning-tree vlan  1 |     |
| show mac  address -table |     |
| spanning-tree vlan 1 root primary | core switch primary |
| spanning-tree vlan 1 root secondary | core switch secondary (backup) |
| interface <interface> AND THEN spanning-tree portfast | for hosts to quickly do port transition |
| spanning-tree portfast default | if there are too many hosts connected to switch but then reconfigure switch connected ports back to avoid loops |
| interface <interface> AND THEN spanning-tree bpduguard enable | use this after portfast to avoid any loop due to someone changing ports or switches |
| spanning-tree portfast bpduguard default | same like portfast default |
| interface <interface> AND THEN spanning-tree guard root |     |

## EtherChannel/PortChannel/LAG

### LACP Configuration

|     |     |
| --- | --- |
| Create port-channel 1 |     |
| interface range <interface/ports> |     |
| channel-group 1 mode **active/passive** | active on one side or both |
| Configure interface settings on the port channel |     |
| interface port-channel 1 |     |
| switchport mode trunk |     |

### **PAgP Configuration**

|     |     |
| --- | --- |
| Create port-channel 1 |     |
| interface range <interface/ports> |     |
| channel-group 1 mode **desirable/auto** | desirable on one side or both |
| Configure interface settings on the port channel |     |
| interface port-channel 1 |     |
| switchport mode trunk |     |

### Static Configuration

|     |
| --- |
| Create port-channel 1 |
| interface range <interface/ports> |
| channel-group 1 mode **on** |
| Configure interface settings on the port channel |
| interface port-channel 1 |
| switchport mode trunk |

### EtherChannel Verification

show etherchannel summary

## Layer 3 EtherChannel

|     |     |
| --- | --- |
| Create port-channel 1 |     |
| interface range <interface/ports> |     |
| no switchport |     |
| channel-group 1 mode **active/desirable/on** |     |
| Configure interface settings on the port channel |     |
| interface port-channel 1 |     |
| ip address <address> <subnet> | ip address [192.168.0.1](http://192.168.0.1) 255.255.255.252 |
| no shutdown |     |

## DHCP Snooping

|     |     |
| --- | --- |
| ip dhcp snooping |     |
| ip dhcp snooping vlan 10 |     |
| interface <interface> |     |
| ip dhcp snooping trust |     |

## ARP DAI Configuration

|     |     |
| --- | --- |
| int <interface> |     |
| ip arp inspection trust |     |
| ip arp inspection vlan 10 |     |

## PORT Security

|     |     |
| --- | --- |
| show port security int <int> |     |
|     |     |
|     |     |

### Manually Adding Mac-Addresses

|     |     |
| --- | --- |
| interface <interface> |     |
| switchport port-security |     |
| switchport port-security mac-address <mac-address> |     |
| switchport port-security maximum 1 |     |

MAC Address Learning

|     |     |
| --- | --- |
| interface <interface> |     |
| switchport port-security |     |
| switchport port-security mac-address sticky |     |
| show port-security address |     |
| show port-security |     |

## Access List

### Standard Access List

|     |     |
| --- | --- |
| access-list 1 deny 10.10.10.10 0.0.0.0 |     |
| access-list 1 permit 10.10.10.0 0.0.0.255 |     |
|     |     |
|     |     |

### Extended Access List

### For Application

|     |
| --- |
| access-list 100 deny tcp 10.10.30.0 0.0.0.255 gt 49151 10.10.20.1 0.0.0.0 eq 23 |
| access-list <ACL number> <action> <protocol> <Source -IP> <wildcard> <Qual> <Port> <Dest.-IP> <wildcard> <Qual.> <Port> |

### For IP

|     |
| --- |
| access-list 100 deny ip 10.10.30.0 0.0.0.255 10.10.20.1 0.0.0.0 |
| access-list <ACL number> <action> <protocol> <Source -IP> <wildcard> <Dest.-IP> <wildcard> |

### Named ACLs

|     |
| --- |
| ip access list standard <name> |
| deny <address> <wildcard> |
| permit <address> <wildcard> |

### **Verification**

show access-lists 100

### Access Group Configuration

|     |
| --- |
| interface <interface> |
| ip access-group 100 out |
| ip access-group 101 in |
| show ip int <int> \| include access list |
|     |

Injecting ACEs in existing ACL

|     |
| --- |
| ip access-list extended 110 |
| 15 deny tcp host 10.10.10.11 host 10.10.50.10 eq telnet |
| sh access-lists 110 |

### Implicit Deny All, Explicit Deny All and Explicit Permit All

* Implicit deny all is by default going to block all traffic except allowed in ACL as it runs deny command at end
* Explicit deny all is run just to get logs for any illegal traffic and commands are as below
* Explicit Permit all will allow all traffic except denied above

|     |     |
| --- | --- |
| access-list 1 deny any log | explicit deny all |
| access-list 1 permit any | explicit permit all |

## Cisco Device Security

### Console Password

|     |     |
| --- | --- |
| line console 0 | always 0 as only one person can connect on console |
| password <password> |     |
| login |     |

### Creating username with password

|     |
| --- |
| username <username> password <password> |
| line console 0 |
| login local |

### Virtual Terminal (VTY) Configuration

|     |
| --- |
| line vty 0 15 |
| login local |

### Encrypt all passwords

|     |     |
| --- | --- |
| service password-encryption | encrypt all passwords |

### Exec Timeout

|     |     |
| --- | --- |
| line con 0 |     |
| exec-timeout <minutes> | exec-timeout 15 |
| line vty 0 15 |     |
| exec-timeout <minutes> <seconds> | exec-timeout 5 30 |

Securing VTY Lines with Access Lists

|     |     |
| --- | --- |
| access-list 1 permit host [10.0.0.10](http://10.0.0.10) |     |
|     |     |
| line vty 0 15 |     |
| login |     |
| password <password> |     |
| access-class 1 in |     |

### Configuring command privilege levels

|     |     |
| --- | --- |
| username <username> privilege <0-15> secret <password> |     |
| privilege exec level <5> show running-config | changing show run command privilege from 15 to 5 |
| enable secret level 5 secret <password> | set password for privilege level 5 |

### Enable SSH

|     |     |
| --- | --- |
| ip domain-name <domain name> | ip domain-name [flackbox.com](http://flackbox.com) |
| crypto key generate rsa |     |
| 768 |     |

### Disable Telnet

|     |     |
| --- | --- |
| username <username> password <password> |     |
| line vty 0 15 |     |
| transport input ssh | only allow ssh and disables telnet |
| login local |     |
| exit |     |
| ip ssh version 2 |     |

## AAA Configuration

### **Old RADIUS Configuration**

|     |     |
| --- | --- |
| username <BackupAdmin> secret <Flackbox1> | configure a local user in case of connectivity to the AAA server |
| aaa new-model |     |
| radius-server host 10.10.10.10 key <Flackbox1> |     |
| radius-server host 10.10.10.11 key <Flackbox2> |     |
| aaa authentication login default group radius local | user all RADIUS servers |
| aaa authentication login default group FB-RG local | user servers in specified group |

### **New RADIUS Configuration**

|     |     |
| --- | --- |
| aaa new-model |     |
| radius-server host <Server1> |     |
| address ipv4 10.10.10.10 |     |
| key Flackbox1 |     |
| radius-server host <Server2> |     |
| address ipv4 10.10.10.11 |     |
| key Flackbox2 |     |
| aaa group server radius FB-RG |     |
| server name Server1 |     |
| server name Server2 |     |
| aaa authentication login default group FB-RG local |     |

### **Old TACACS+ Configuration**

|     |     |
| --- | --- |
| username <BackupAdmin> secret <Flackbox1> |     |
| aaa new-model |     |
| tacacs-server host 10.10.10.10 key <Flackbox1> |     |
| tacacs-server host 10.10.10.11 key <Flackbox2> |     |
| aaa group server tacacs+ FB-TG |     |
| server 10.10.10.10 |     |
| server 10.10.10.11 |     |
| aaa authentication login default group FB-TG local |     |

### **New TACACS+ Configuration**

|     |     |
| --- | --- |
| tacacs-server host 10.10.10.10 |     |
| username <BackupAdmin> secret <Flackbox1> |     |
| aaa new-model |     |
| tacacs-server <Server1> |     |
| address ipv4 10.10.10.10 |     |
| key Flackbox1 |     |
| tacacs-server <Server2> |     |
| address ipv4 10.10.10.11 |     |
| key Flackbox2 |     |
| aaa group server tacacs+ FB-TG |     |
| server name Server1 |     |
| server name Server2 |     |
| aaa authentication login default group FB-TG local |     |

## Global security Best practices

### Login and Exec Banners

|     |     |
| --- | --- |
| banner login " |     |
| banner exec " |     |
| no ip http server |     |
| no cdp run | only disable in highly secure environments like banks |

### NTP Configuration

|     |     |
| --- | --- |
| clock timezone PST -8 |     |
| ntp server 10.0.1.100 | configures router to be NTP client |
| ntp master | configures router to be NTP server |
| show clock |     |
| show ntp status |     |

## Configuration on VTY line for SysLog

|     |     |
| --- | --- |
| no logging console |     |
| logging monitor 5 |     |
| end |     |
| terminal monitor |     |
| logging buffer 7 |     |
|     |     |
|     |     |

## IPv6

|     |     |
| --- | --- |
| ipv6 unicast-routing | router will not forward ipv6 without this command |
| int <int> |     |
| ipv6 add 2001:db8:0:1::1/64 |     |
| int <int> |     |
| ipv6 add 2001:db8:0:0::1/64 |     |

### EUI-64 Address Configuration

|     |     |
| --- | --- |
| int <int> |     |
| ipv6 address <ipv6 address> eui-64 |     |

## NAT

### Static NAT Configuration

|     |     |
| --- | --- |
| int <int> |     |
| ip nat outside |     |
| int <int> |     |
| ip nat inside |     |
| ip nat inside source static <inside ip address> <outside ip address> |     |
| sh ip nat translation |     |

