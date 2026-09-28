<div align="center">

# PUQVPNCP
### Multi-Protocol VPN Server Control Panel

[![License](https://img.shields.io/badge/license-Proprietary-blue.svg)](https://puqvpncp.com)
[![Version](https://img.shields.io/badge/version-2.3.0-brightgreen.svg)](https://puqvpncp.com)
[![Protocols](https://img.shields.io/badge/protocols-WireGuard%20%7C%20AmneziaWG%20%7C%20OpenVPN%20%7C%20IKEv2-blueviolet.svg)](https://puqvpncp.com/#protocols)
[![Free Tier](https://img.shields.io/badge/free%20tier-Up%20to%2050%20users-orange.svg)](https://puqvpncp.com/#pricing)
[![API](https://img.shields.io/badge/REST%20API-170%2B%20endpoints-informational.svg)](https://puqvpncp.com/api/)

**A high-performance Linux VPN management panel featuring stealth anti-censorship protocols, granular traffic shaping, built-in DNS ad blocking, and complete REST API automation.**

[Official Website](https://puqvpncp.com) • [Documentation](https://puqvpncp.com/doc/) • [API Reference](https://puqvpncp.com/api/) • [Download](https://puqvpncp.com/download/) • [Community Forum](https://community.puqcloud.com/)

---

<img src="doc/img/dashboard/01-dashboard-overview.png" alt="PUQVPNCP Dashboard" width="900">

</div>

## Key Capabilities

- **4 VPN Protocols in One Panel**:
  - **WireGuard**: Modern, high-speed, kernel-accelerated cryptography.
  - **AmneziaWG (New in v2.3)**: Anti-censorship obfuscated WireGuard with custom magic packet headers (`H1`–`H4`) and junk padding (`Jc`, `Jmin`, `Jmax`) to defeat Deep Packet Inspection (DPI).
  - **OpenVPN**: Enterprise TCP and UDP tunnels with automated internal PKI.
  - **IKEv2 / IPsec**: High-security, mobile-friendly strongSwan daemon with certificate management.
- **Hierarchical Network Architecture**: Create networks (`10.0.0.0/24`), provision client accounts, and enable any combination of protocols per client.
- **WireGuard Upstream Tunnels**: Route client VPN traffic through external commercial WireGuard servers for geo-relocation.
- **Built-in DNS Ad Blocking**: Local Bind9 DNS server with pre-configured blocklists (Steven Black Unified, OISD, AdGuard) and custom records.
- **Traffic Control & Quotas**: Real-time HTB bandwidth shaping (Kbps / Mbps) and traffic quotas.
- **Centralized Firewall**: Visual iptables rule builder with pre/post chains and ipset IP lists.
- **170+ REST API Endpoints**: Full OpenAPI 3.0 specification for automated provisioning, WHMCS billing integration, and custom dashboards.
- **Self-Service One-Time Links (OTL)**: Distribute QR codes and client profiles with password and expiration controls.

---

## Quick Installation

PUQVPNCP is distributed as a lightweight Debian package for **Debian 11/12** and **Ubuntu 20.04/22.04/24.04** (amd64).

```bash
# 1. Download the latest release package
wget https://puqvpncp.com/download/puqvpncp_latest_amd64.deb

# 2. Install package
sudo dpkg -i puqvpncp_latest_amd64.deb

# 3. Open your browser
# https://<YOUR_SERVER_IP>:8098 (or https://your-domain)
# Default login: admin / admin
```

> **Note**: PUQVPNCP is free for up to 50 active VPN users with complete access to all features and the full REST API.

---

## Documentation

Full documentation is included in the [`doc/`](doc/) directory and available online at [puqvpncp.com/doc](https://puqvpncp.com/doc/):

| # | Chapter | Description |
|---|---|---|
| 00 | [Changelog](doc/00-changelog.md) | Release notes for v2.3.0 and past versions |
| 01 | [Description](doc/01-description.md) | Product overview, features, and architecture |
| 02 | [Installation](doc/02-installation.md) | System requirements and step-by-step setup |
| 03 | [Initial Setup](doc/03-initial-setup.md) | System config, Let's Encrypt SSL, license |
| 04 | [Dashboard](doc/04-dashboard.md) | Main dashboard widgets and navigation |
| 05 | [Networks](doc/05-networks.md) | Creating subnets, routes, and IP pools |
| 06 | [Clients](doc/06-clients.md) | Client accounts, bandwidth shaping, and quotas |
| 07 | [WireGuard](doc/07-wireguard.md) | WireGuard server and peer configuration |
| 08 | [IKEv2](doc/08-ikev2.md) | strongSwan setup, CA certificates, and clients |
| 09 | [OpenVPN](doc/09-openvpn.md) | OpenVPN server, port, cipher, and PKI settings |
| 10 | [Upstreams](doc/10-upstreams.md) | WireGuard external upstream tunnel routing |
| 11 | [Peering](doc/11-peering.md) | Inter-network communication rules |
| 12 | [Firewall](doc/12-firewall.md) | Global iptables pre/post network filtering |
| 13 | [DNS & Ad Blocking](doc/13-dns.md) | Built-in bind9 DNS with ad blocking |
| 14 | [One-Time Links](doc/14-one-time-links.md) | Self-service web links for configuration download |
| 15 | [Monitoring](doc/15-monitoring.md) | Traffic logging, rsyslog, and InfluxDB metrics |
| 16 | [Backups](doc/16-backups.md) | Automatic scheduled backups and FTP sync |
| 17 | [System Settings](doc/17-system-settings.md) | Users, RBAC permissions, and API tokens |
| 18 | [REST API](doc/18-api.md) | 170+ endpoints with interactive Swagger UI |
| 19 | [Use Cases](doc/19-use-cases.md) | Real-world architectures and configurations |
| 20 | [Troubleshooting](doc/20-troubleshooting.md) | Diagnostics, repair tools, and password recovery |
| 21 | [Diagnostics](doc/21-diagnostics.md) | Real-time logs and system health checks |
| 22 | [AmneziaWG](doc/22-amneziawg.md) | Anti-censorship stealth configuration & DPI bypass |

---

## Official WHMCS Provisioning Module

Selling VPN access through WHMCS? Use the official module:
- [PUQVPNCP WHMCS Provisioning Module](https://puqcloud.com/whmcs-module-puqvpncp.php)
- Automates client provisioning, suspension, traffic quota enforcement, and delivers config files directly inside the client area.

---

## Support & Links

- **Website**: [https://puqvpncp.com](https://puqvpncp.com)
- **Downloads**: [https://puqvpncp.com/download/](https://puqvpncp.com/download/)
- **Documentation**: [https://puqvpncp.com/doc/](https://puqvpncp.com/doc/)
- **API Reference**: [https://puqvpncp.com/api/](https://puqvpncp.com/api/)
- **Community Forum**: [https://community.puqcloud.com/](https://community.puqcloud.com/)
- **Support Tickets**: [https://puqcloud.com/submitticket.php](https://puqcloud.com/submitticket.php)
- **Author**: Ruslan Polovyi ([PUQ sp. z o.o.](https://puqcloud.com))

---

&copy; 2024–2026 PUQ sp. z o.o. All rights reserved.
