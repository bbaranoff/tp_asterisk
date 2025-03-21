#Installation asterisk

```bash
apt update
apt upgrade
apt install curl
systemctl stop apparmor
apt remove apparmor
cd /usr/src
wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-20-current.tar.gz
tar zxvf asterisk-20-current.tar.gz
rm -rf asterisk-20-current.tar.gz
cd asterisk-20*/
contrib/scripts/install_prereq install
./configure
make -j$(nproc)
make install
ldconfig
```
