# Proxmox nat network establishing
```
iface lo inet loopback

iface eno1 inet manual

iface eno2 inet manual

iface eno3 inet manual

iface eno4 inet manual

iface enp68s0f0 inet manual

iface enp68s0f1 inet manual

auto vmbr0
iface vmbr0 inet static
        address 192.168.0.100/24
        gateway 192.168.0.1
        bridge-ports eno1
        bridge-stp off
        bridge-fd 0

auto vmbr1
iface vmbr1 inet static
        address 10.0.2.1/24
        bridge-ports none
        bridge-stp off
        bridge-fd 0

#Nat settings
post-up echo 1 > /proc/sys/net/ipv4/ip-forward
post-up iptables -t nat -A POSTROUTING -s '10.0.2.0/24' -o vmbr0 -j MASQUERADE
post-down iptables -t nat -D POSTROUTING -S '10.0.2.0/24' -o vmbr0 -j MASQUERADE
```
# Client linux machine network settings
nano /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.2.10/24
gateway 10.0.2.1
nameserver 8.8.8.8
```
