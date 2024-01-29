# PiHole DNS

**An Ansible playbook to configure a PiHole DNS server.**

I used to use a modified version of [geerlingguy/internet-pi](https://github.com/geerlingguy/internet-pi) but want different things from my Pi than that project provides.

## Components

**PiHole**: Install and configure [PiHole](pi-hole.net) to do network-wide DNS blackholing of ads.

**Unbound**: Install and configure [Unbound](https://www.nlnetlabs.nl/projects/unbound/about/) as a recursive DNS server.
Unbound has a number of features that help increase your online privacy, especially when compared to using Google DNS (`8.8.8.8`) as your upstream DNS provider for PiHole including DNS-over-TLS and DNS-over-HTTPS.

If you configure DNS-over-TLS (`unbound_enable_dot: yes`), the default DoT provider is [CloudFlare](https://developers.cloudflare.com/1.1.1.1/encryption/dns-over-tls/).
You can change this by setting `unbound_dot_providers` in `config.yml`.
If you are using CloudFlare as your DoT provider, you can verify DNS-over-TLS is enabled by visiting https://1.1.1.1/help.

## Setup

1. Install Ansible
2. `git clone git@github.com:5donuts/pihole-dns.git`
3. `ansible-galaxy collection install -r requirements.yml`
4. Modify `inventory.ini` to match your setup (i.e., set your Pi's IP address or configure a local connection)
5. `cp config.defaults.yml config.yml`, then modify `config.yml` to suit your needs (i.e., change the Pi password, enable & disable components)
6. `cp inventory.example.ini inventory.ini`, then modify `inventory.ini` to suit your needs (e.g., set the actual IP address of the Pi on your network, configure connection variables)
7. `ansible-playbook -i inventory.ini main.yml`

## License

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
