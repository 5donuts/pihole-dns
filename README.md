# PiHole DNS

Ansible playbooks to configure [PiHole](https://pi-hole.net/) as a recursive DNS server.

## Pi Prereqs

At minimum, you need the following to configure your Pi with these playbooks:
* A static IP address on the network
* A running SSH daemon, with access allowed on the current network

You will need to copy your public SSH key to the Pi to connect:

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub pi@${pi-ip-addr}
```
