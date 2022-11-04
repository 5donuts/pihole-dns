# PiHole DNS

Ansible playbooks to configure [PiHole](https://pi-hole.net/) as a recursive DNS server.
## Using this playbook

Before running this playbook, you should:
* assign the Pi a static IP address on your network,
* ensure an SSH daemon is running on the Pi
* copy your public SSH key to the Pi (e.g., `ssh-copy-id -i ~/.ssh/id_rsa.pub pi@${pi-ip-addr}`), and
* modify `roles/install_pihole/default/main.yml` with an admin password of your choosing

Additionally, you should modify `inventory.yml` with:
* the IP address(es) of the Pi(s) to configure, and
* add hosts to groups depending on if you want them to also be DNS and/or DHCP server(s)

After running this playbook, you should:
* set the Pi as your DNS server in your router settings (if applicable), and
* remove (or modify) any custom DNS configuration in your network clients so they use the PiHole
