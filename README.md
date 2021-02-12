# ansible-wireguard-vpn

Ansible + WireGuard = VPN

## Introduction

This Ansible playbook will set up a point-to-point VPN network.

Tested  on Ubuntu.

To customize installation, see roles/wireguard/vars/main.yml and roles/wireguard/defaults/main.yml.

## Prerequisites

- Ansible
- SSH
- Root account

## Usage

First, list all VPN servers, fill in hosts.txt, for example:

```
server-1 ansible_ssh_host=212.x.x.x vpn_ip=192.168.0.1 public_ip=212.x.x.x
client  ansible_ssh_host=212.x.x.x vpn_ip=192.168.0.2 public_ip=212.x.x.x

[vpn-servers]
server-1
client
```

Next, install the VPN network:

```
$ ansible-playbook wireguard.yml -i hosts -u root
```

## WireGuard cheat sheet

Show WireGuard configuration:

```bash
# wg
```

Stop/Start WireGuard:

```bash
# wg-quick down wg0
# wg-quick up wg0
```

Start the WireGuard service:

```bash
# systemctl start wg-quick@wg0
```

Check WireGuard status:

```bash
# systemctl status wg-quick@wg0
```

Configure WireGuard to start up at boot:

```bash
# systemctl enable wg-quick@wg0
```
