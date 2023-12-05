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
