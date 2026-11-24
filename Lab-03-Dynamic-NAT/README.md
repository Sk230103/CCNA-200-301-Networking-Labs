

\# Lab 03: Dynamic NAT and PAT Configuration



\## Objective

Configure Dynamic NAT and Port Address Translation (PAT)

to translate private IPv4 addresses into public addresses

and allow multiple internal devices to access external networks.



\## Concepts Covered



\### Dynamic NAT

\- NAT address pools

\- Standard Access Control Lists

\- Dynamic inside-to-outside translation

\- Inside Local and Inside Global addresses



\### Port Address Translation (PAT)

\- NAT Overload

\- Port-based address translation

\- Multiple internal hosts sharing a public IP address

\- Translation using TCP/UDP port numbers



\## Configuration

The Packet Tracer lab contains separate Dynamic NAT

and PAT configurations. Refer to the device configurations

in the attached Packet Tracer file.



!

interface GigabitEthernet0/0

&#x20;ip address 203.0.113.1 255.255.255.252

&#x20;ip nat outside

&#x20;duplex auto

&#x20;speed auto

!

interface GigabitEthernet0/1

&#x20;ip address 172.16.0.254 255.255.255.0

&#x20;ip nat inside

&#x20;duplex auto

&#x20;speed auto

!

interface GigabitEthernet0/2

&#x20;no ip address

&#x20;duplex auto

&#x20;speed auto

&#x20;shutdown

!

interface Vlan1

&#x20;no ip address

&#x20;shutdown

!

ip nat pool POOL1 100.0.0.1 100.0.0.2 netmask 255.255.255.0

ip nat inside source list 1 interface GigabitEthernet0/0 overload

ip classless

ip route 0.0.0.0 0.0.0.0 203.0.113.2 

!

ip flow-export version 9

!

!

access-list 1 permit 172.16.0.0 0.0.0.255



\## Verification Commands

```cisco

show ip nat translations

show ip nat statistics

show access-lists

show running-config

```



\## Testing

\- Generate traffic from internal devices.

\- Verify dynamic NAT address allocation.

\- Verify PAT translations for multiple internal hosts.

\- Inspect translated IP addresses and port numbers.

\- Confirm external connectivity.



\## Lab File

Dynamic-NAT-and-PAT.pkt



