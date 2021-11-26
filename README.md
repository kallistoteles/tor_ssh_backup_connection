## TOR SSH backup connection
Whenever your usual way to connect to a server or a device fails for whatever reason, it's great to have another easy way to connect.

## Concept
Fall back to a slow but existing ssh connection through a tor hidden service for emergency use to any device.

## Setup
* Install tor and add the lines found in the torrc file in this reposetory in /etc/tor/torrc
* Create the directory /var/lib/tor/ssh and it should be owned by tor and tor group with mode 700.
sudo mkdir /var/lib/tor/ssh
sudo chown tor:tor /var/lib/tor/ssh
sudo chmod 700 /var/lib/tor/ssh
* Once you start the tor service you hidden service address will be found in the file /var/lib/tor/ssh/hostname

## Usage examples
You can use torsocks to connect to it using the given hidden service address.
torsocks ssh verylonghostnameexamplelkjklhadljkjlkjlflkja.onion

If the device you are trying to access does not have public ip, if it is on a cellular network or behind a firewall for exmaple, this setup would work as well.

I'm using mosh and tmux so my connection string look like this:
mosh device_name_or_ip -- tmux attach torsocks ssh verylonghostnameexamplelkjklhadljkjlkjlflkja.onion

## Dependencies
* tor
