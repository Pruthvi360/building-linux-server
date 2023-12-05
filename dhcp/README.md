# Static IP for the DHCP server
```
nmcli con modify 'Wired connection 2' ipv4.method manual ipv4.address 10.0.1.2/24 ipv4.gateway 10.0.1.1
nmcli con down 'Wired connection 2'
nmcli con up 'Wired connection 2'
```

# Installing the DHCP server using ISC kea 2.4
```
curl -1sLf \
  'https://dl.cloudsmith.io/public/isc/kea-2-4/setup.deb.sh' \
  | sudo -E distro=some-distro codename=some-codename arch=some-arch bash
```
# Install common kea utilites
```
apt install isc-kea-common
```

# Install ISC kea DHCP4 
```
apt install isc-kea-dhcp4-server
```
# check status ISC kea DHCP4 
```
systemctl status isc-kea-dhcp4-server
```
# set domain name
```
hostnamectl set-hostname dhcp.example.com
```
# Download kea-dhcp4.conf file form git
```
apt install git
cd /home
git clone https://github.com/Pruthvi360/building-linux-server.git
cd building-linux-server/dhcp
cp kea-dhcp4.conf /etc/kea
```
# check the syntax error in kea-dhcp4.conf file and check the status of the dhcp4 service
```
kea-dhcp4 -t kea-dhcp4.conf
systemctl status isc-kea-dhcp4-server
```
# Check for logs
```
journalctl -u isc-kea-dhcp4-server
```
# Check for open ports
```
ss -tulw
ss -tulwn
```
