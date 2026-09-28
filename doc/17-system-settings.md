# System Settings


## System Users

Navigate to **Settings > System users**.

![Users list](img/system-users/01-users-list.png)
*System users list*

PUQVPNCP supports multiple administrator accounts with role-based access control.

### Adding a User

![Add user](img/system-users/02-user-add.png)
*Add a new system user*

| Field | Description |
|-------|-------------|
| **Username** | Unique login name |
| **Email** | User email |
| **Password** | Account password |
| **Groups** | Permission groups assigned to this user |

### Editing a User

![Edit user](img/system-users/03-user-edit.png)
*Edit system user*

---

## Permission Groups

Navigate to **Settings > Permission groups**.

![Groups list](img/permission-groups/01-groups-list.png)
*Permission groups list*

Permission groups define what actions a user can perform. PUQVPNCP includes 36+ granular permissions across 17 resource categories.

### Default Groups

| Group | Access Level |
|-------|-------------|
| **admin** | Full access to everything |
| **operator** | All operations except system settings |
| **viewer** | Read-only access to all pages |

### Creating a Custom Group

![Add group](img/permission-groups/02-group-add.png)
*Create a new permission group*

![Edit group](img/permission-groups/03-group-edit.png)
*Edit permission group — select permissions by resource*

Permissions are organized by resource:

| Resource | Permissions |
|----------|-------------|
| **system_config** | read, write |
| **wireguard** | read, write |
| **amneziawg** | read, write |
| **network** | read, write |
| **client** | read, write |
| **peering** | read, write |
| **account** | read, write |
| **openvpn** | read, write |
| **ikev2** | read, write |
| **diagnostics** | read, write |
| **firewall** | read, write |
| **dns** | read, write |
| **otl** | read, write |
| **traffic (Monitoring)** | read, write |
| **backups** | read, write |
| **license** | read, write |
| **api_tokens** | read, write |
| **system_users** | read, write |
| **permission_groups** | read, write |

---

## API Tokens

Navigate to **Settings > API Tokens**.

![Tokens list](img/api-tokens/01-tokens-list.png)
*API tokens list*

API tokens provide programmatic access to the REST API without using session cookies.

### Creating a Token

![Create token](img/api-tokens/02-token-create.png)
*Create a new API token*

| Field | Description |
|-------|-------------|
| **Name** | Token description |
| **Username** | The user this token belongs to (inherits permissions) |
| **Allowed IP** | Restrict token to a specific IP (empty = any) |
| **Expires At** | Token expiration date (empty = never) |

![Token created](img/api-tokens/03-token-created.png)
*Token created — copy the token now, it won't be shown again*

> **Important:** The token value is shown only once. Copy it immediately after creation.

### Usage

Include the token in the `Authorization` header:

```bash
curl -sk https://vpn.example.com/api/v1/system/status \
  -H "Authorization: Bearer YOUR_TOKEN_HERE"
```

---

## Environment Check

Navigate to **Settings > Environment**.

![Environment check](img/system-environment/01-environment-check-vpn.png)
*Environment check — verify all required packages*

The Environment page scans for all required and optional system packages:

- **VPN Protocols** — wireguard, amneziawg, openvpn, easy-rsa, strongswan
- **Network & Firewall** — iproute2, iptables, ipset
- **DNS** — bind9, bind9-utils
- **Monitoring** — rsyslog, telegraf
- **Security** — openssl
- **System Utilities** — procps, uuid-runtime, bash, grep, gawk
- **Network Configuration** — ifupdown2 (Debian) or netplan.io (Ubuntu)

![Environment bottom](img/system-environment/02-environment-check-dns-monitoring.png)
*Environment check — DNS, Monitoring, Security, System Utilities*

![Environment networking](img/system-environment/03-environment-check-network-config.png)
*Environment check — Network Configuration (ifupdown2 / netplan.io)*

Missing packages are highlighted and can be installed via the system package manager.

---

## About Us & Project Support

Navigate to **About us** in the top navigation bar.

![About Us and Support](img/other/06-about-us.png)
*About Us — licensing information, WHMCS provisioning module integration, and support links*

The About page displays project license limits (up to 50 VPN clients without license, unlimited with license from puqcloud.com), integration options including the official WHMCS provisioning module, and links to documentation and support.

