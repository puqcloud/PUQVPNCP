# PUQVPNCP — Documentation v2.3.0


## Table of Contents

### Release Notes

| # | Chapter | Description |
|---|---------|-------------|
| 0 | [Changelog](00-changelog.md) | What's new in v2.3.0 — full release notes |

### Getting Started

| # | Chapter | Description |
|---|---------|-------------|
| 1 | [Description](01-description.md) | Product overview, features, and architecture |
| 2 | [Installation](02-installation.md) | System requirements and installation guide |
| 3 | [Initial Setup](03-initial-setup.md) | System config, SSL, firewall, DNS, license |
| 4 | [Dashboard](04-dashboard.md) | Main dashboard overview |

### Core Concepts

| # | Chapter | Description |
|---|---------|-------------|
| 5 | [WireGuard](07-wireguard.md) | WireGuard protocol configuration |
| 6 | [AmneziaWG](22-amneziawg.md) | AmneziaWG anti-censorship protocol configuration |
| 7 | [OpenVPN](09-openvpn.md) | OpenVPN protocol configuration |
| 8 | [IKEv2](08-ikev2.md) | IKEv2/IPsec protocol configuration |
| 9 | [Upstreams (WireGuard Tunnels)](10-upstreams.md) | Upstream VPN tunnels, use cases, geo-routing |
| 10 | [Networks](05-networks.md) | Creating and managing VPN networks |
| 11 | [Clients](06-clients.md) | Client accounts, bandwidth, traffic |
| 12 | [Network Peering](11-peering.md) | Inter-network communication |

### Advanced Features

| # | Chapter | Description |
|---|---------|-------------|
| 13 | [Firewall](12-firewall.md) | iptables rules, ipset, NAT |
| 14 | [DNS](13-dns.md) | Built-in DNS server (bind9), ad blocking |
| 15 | [One-Time Links](14-one-time-links.md) | Self-service client configuration links |

### Operations

| # | Chapter | Description |
|---|---------|-------------|
| 16 | [Diagnostics](21-diagnostics.md) | Real-time diagnostics, logs, integrity check |
| 17 | [Monitoring](15-monitoring.md) | Traffic logging, InfluxDB, Grafana |
| 18 | [Backups](16-backups.md) | Backup, restore, FTP sync |
| 19 | [System Settings](17-system-settings.md) | Users, permissions, API tokens, environment |
| 20 | [REST API](18-api.md) | Full REST API with OpenAPI/Swagger |
| 21 | [Use Cases](19-use-cases.md) | Real-world deployment scenarios |
| 22 | [Troubleshooting](20-troubleshooting.md) | Password reset, common issues, diagnostics |

---

## Key Highlights

- **4 VPN protocols** in one panel: WireGuard, AmneziaWG (anti-censorship), OpenVPN, IKEv2/IPsec
- **DPI Bypass** — obfuscated WireGuard headers and junk packet padding
- **Upstream tunnels** — route client traffic through external VPN servers
- **Per-network configuration** — each network has its own subnet, protocols, firewall, bandwidth
- **Role-based access control** — permission groups, API tokens, multi-user
- **DNS ad blocking** — block ads and trackers for all VPN clients at the DNS level
- **Full REST API** — 170+ endpoints with OpenAPI 3.0 documentation
- **Built-in monitoring** — traffic stats, InfluxDB, Grafana integration
- **One-time links** — self-service VPN configuration for end users
- **Network peering** — allow communication between VPN networks

---

## Commercial Automation & WHMCS

Selling VPN services or integrating with web hosting billing?
- **[Official PUQVPNCP WHMCS Provisioning Module](https://puqcloud.com/whmcs-module-puqvpncp.php)** — Turnkey billing module that automates client provisioning upon payment, manages suspensions, synchronizes bandwidth shaping and traffic quotas, and delivers config files (WireGuard, AmneziaWG, OpenVPN, IKEv2) directly inside the WHMCS client portal.

---

*Documentation for PUQVPNCP v2.3.0 | [puqcloud.com](https://puqcloud.com)*
