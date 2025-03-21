# Installation asterisk serveur (machine virtuelle debian bookworm)

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
make menuselect # channel drivers cocher chan_sip
make -j$(nproc)
make install
ldconfig
make basic-pbx
rm /etc/asterisk/pjsip*
cd /etc/asterisk
rm modules.conf extensions.conf
wget https://raw.githubusercontent.com/bbaranoff/tp_asterisk/refs/heads/main/sip.conf
wget https://raw.githubusercontent.com/bbaranoff/tp_asterisk/refs/heads/main/modules.conf
wget https://raw.githubusercontent.com/bbaranoff/tp_asterisk/refs/heads/main/extensions.conf
# Lancer asterisk :
asterisk -cvvvvvvvv
```

# Installer le Softphone (sur l'hôte Windows)
```
1 - Ajouter un compte 
2 - nom : myuser / pass: tester
3 - desaticer dans l'onglet Préférences -> Réseau port d'écoute tcp 5060/ port d'écoute udp 5060
4 - effectuer un test d'echo en appelant le 600
``
