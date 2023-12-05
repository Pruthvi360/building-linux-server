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
