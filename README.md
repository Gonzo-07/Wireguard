# 🔒 Proxmox WireGuard VPN
A self-hosted WireGuard VPN setup to securely access a Proxmox homelab server from anywhere, without exposing any services directly to the internet.
> Built as a personal side project to replace risky port-forwarding of the Proxmox GUI with a proper, encrypted VPN tunnel.

## 📦 Tech Stack
- Proxmox VE (Host)
- WireGuard / wireguard-tools
- iptables / sysctl (IP forwarding & NAT)
- Vodafone Router (Port Forwarding)

## 🦄 Features
- Encrypted point-to-point VPN tunnel (WireGuard)
- Full access to the home LAN, not just the Proxmox host
- No open web ports on the router — only one UDP port for the VPN
- Persistent keepalive for stable connections behind NAT
- Easy to extend with additional clients (phone, laptop, etc.)
- Works from any network — home, mobile data, public WiFi

## 🎯 Architecture
Internet → Vodafone Router (UDP 51820) → Proxmox Host (WireGuard Server) → LAN (192.168.1.0/24) → Proxmox GUI / other LAN devices

External Client (WireGuard App) → 10.10.10.0/24 (WG Tunnel) → 10.10.10.1 (Server)

## 📚 What I Learned
- Setting up a WireGuard server and generating key pairs
- Configuring IP forwarding and NAT on a Linux host
- Difference between full-tunnel and split-tunnel (LAN-only) VPN setups
- Port forwarding and firewall configuration on a consumer router
- Debugging VPN connectivity using `wg show` and ping tests
- Network fundamentals: subnets, interfaces, and routing in a homelab environment

## 💭 How can it be improved?
- Add multiple client profiles (phone, laptop, work PC)
- Automate config generation with a script
- Add a dynamic DNS service in case the public IP changes
- Add monitoring/alerting for tunnel status

## 🚦 Requirements
- Proxmox Server with a public-facing router
- Root/Shell access to the Proxmox host
- A router that supports UDP port forwarding
- WireGuard client app on the external device

## 📖 Full Setup Guide (in German)
See [Dokumentation](https://app.notion.com/p/VPN-Tunnel-anlegen-2f2c8d95942180b58316c4806bfadde7?source=copy_link)
