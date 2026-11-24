

\# Lab 02: Static NAT Configuration



\## Objective

Configure Static Network Address Translation (NAT)

to map an internal private IP address to a public

IP address, enabling external access to an internal device.



\## Concepts Covered

\- Static NAT

\- Inside Local and Inside Global Addresses

\- NAT Inside and Outside Interfaces

\- One-to-One Address Translation



\## Configuration

```cisco

interface g0/1

&#x20;ip nat inside



interface g0/0

&#x20;ip nat outside



ip nat inside source static 172.16.0.1 100.0.0.1 

ip nat inside source static 172.16.0.2 100.0.0.2 

ip nat inside source static 172.16.0.3 100.0.0.3 ```



\## Verification Commands

```cisco

show ip nat translations

show ip nat statistics

show running-config

```



\## Testing

\- Verify internal and external connectivity.

\- Check the static NAT mapping.

\- Confirm successful address translation.



\## Lab File

Static-NAT.pkt



