# become user netdata
sudo -su netdata

# run python plugin for apache
/usr/libexec/netdata/plugins.d/python.d.plugin debug 1 apache