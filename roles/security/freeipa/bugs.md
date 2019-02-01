
## For Error `Unable to find 'admin' user with 'getent passwd admin@charcoaleats.com'!`
Make Sure below code present in `/etc/nsswitch.conf`

`passwd:         compat systemd ss
group:          compat systemd ss
shadow:         compat ss
gshadow:        files

hosts:          files dns myhostname
networks:       files

protocols:      db files
services:       db files ss
ethers:         db files
rpc:            db files

netgroup:       nis ss




sudoers: files sss`