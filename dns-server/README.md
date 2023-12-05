# Setup DNS server on the debian 12 server
```
set static ip in the /etc/network/interfaces file
nano /etc/network/interfaces

# The primary network interface
allow-hotplug ens18
iface ens18 inet static
        address 10.0.2.3/24
        gateway 10.0.2.1
```
```
hostnamectl set-hostname dns1.example.com
nameserver 10.0.2.1 > /etc/resolv.conf
127.0.1.1   dns1.example.com dns1 > /etc/hosts
apt install bind9 bind9-doc dnsutils -y
systemctl status bind9
dig @127.0.0.1 . NS
nameserver 10.0.2.3 > /etc/resolv.conf
```
