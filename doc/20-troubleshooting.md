# Troubleshooting


## Reset Admin Password

If you have lost access to the web panel or forgotten the admin password, you can reset it using the recovery mode.

### Step 1: Stop the Service

```bash
systemctl stop puqvpncp
```

### Step 2: Run Recovery

```bash
puqvpncp --recover
```

This will:

```
=== PUQVPNCP Recovery Mode ===
[OK] Admin group reset to full access (*)
[OK] Admin user: already in admin group
[OK] Admin password reset to 'admin' (password change will be required)

Recovery complete. Login as admin / admin.
You will be prompted to change the password on first login.
```

The recovery command performs the following:
- Resets the `admin` permission group to full access (`*`)
- If the `admin` user does not exist — creates it with password `admin`
- If the `admin` user exists — resets password to `admin` and ensures the user is in the `admin` group
- Sets the `ForcePasswordChange` flag — you will be prompted to change the password on first login
- Recreates default permission groups (`operator`, `viewer`) if they are missing

### Step 3: Start the Service

```bash
systemctl start puqvpncp
```

### Step 4: Login

Open the web panel and login with:

| Field | Value |
|-------|-------|
| **Username** | `admin` |
| **Password** | `admin` |

You will be prompted to set a new password immediately.

---

## Service Won't Start

### Check the service status

```bash
systemctl status puqvpncp
```

### Check the logs

```bash
tail -100 /var/log/puqvpncp/puqvpncp.log
```

### Common causes

| Problem | Solution |
|---------|----------|
| Port already in use | Check `WebPort` in `/etc/puqvpncp/puqvpncp.conf`, or stop the conflicting service |
| SSL certificate error | Verify that `Domain` resolves to this server's IP and port 443 is not in use |
| Permission denied | Ensure the binary is at `/usr/sbin/puqvpncp` and has execute permissions |
| Missing dependencies | Run **Settings > Environment** check, or install missing packages manually |

---

## Web Panel Not Accessible

### Check if the service is running

```bash
systemctl is-active puqvpncp
```

### Check which port is in use

```bash
ss -tlnp | grep puqvpncp
```

### Common causes

| Problem | Solution |
|---------|----------|
| Firewall blocking the port | Allow the port: `iptables -I INPUT -p tcp --dport 8098 -j ACCEPT` |
| Wrong listen address | Check `WebIP` in `/etc/puqvpncp/puqvpncp.conf` (default: `0.0.0.0`) |
| IP restriction active | Check `AllowedWebIP` — set to `0.0.0.0` to allow all IPs |
| SSL enabled but accessing HTTP | With `LetsEncrypSSL=yes`, use `https://` on port 443, not HTTP |

---

## Binary Cannot Be Updated

If you get "Text file busy" error when trying to copy a new binary:

```bash
systemctl stop puqvpncp
cp puqvpncp /usr/sbin/puqvpncp
systemctl start puqvpncp
```

> The service **must** be stopped before replacing the binary. The running process locks the file.

---

## WireGuard Interface Not Created

### Check if WireGuard kernel module is loaded

```bash
modprobe wireguard
lsmod | grep wireguard
```

### Check WireGuard tools

```bash
wg --version
```

If missing, install:

```bash
apt install wireguard wireguard-tools
```

---

## AmneziaWG Interface Not Created or Module Not Loaded

### 1. Check DKMS status and kernel module

```bash
# Check DKMS compilation status
dkms status
# Should show: amneziawg/..., ...: installed

# Check if the kernel module is currently loaded
lsmod | grep amneziawg

# Try loading the module manually
modprobe amneziawg
```

### 2. Module build failed or missing (Debian / Ubuntu)

On **Debian**, DKMS compilation fails if `linux-headers-$(uname -r)` and build tools are missing. To fix:

```bash
# Install kernel headers and build tools for the running kernel
apt-get update && apt-get install -y build-essential dkms linux-headers-$(uname -r)

# Reconfigure and recompile the DKMS module
dpkg-reconfigure amneziawg-dkms

# Load the compiled module into the kernel
modprobe amneziawg

# Verify
lsmod | grep amneziawg
```

### 3. Missing repository or packages

**Debian (11 / 12 / 13):**
```bash
apt-get update && apt-get install -y build-essential dkms linux-headers-$(uname -r)
mkdir -p /etc/apt/keyrings && curl -fsSL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x75C9DD72C799870E310542E24166F2C257290828" | gpg --dearmor --yes -o /etc/apt/keyrings/amnezia.gpg
echo "deb [signed-by=/etc/apt/keyrings/amnezia.gpg] https://ppa.launchpadcontent.net/amnezia/ppa/ubuntu noble main" > /etc/apt/sources.list.d/amnezia.list
apt-get update && apt-get install -y amneziawg-dkms amneziawg-tools
modprobe amneziawg
```

**Ubuntu (22.04 / 24.04 LTS):**
```bash
add-apt-repository -y ppa:amnezia/ppa
apt-get update && apt-get install -y amneziawg-dkms amneziawg-tools
modprobe amneziawg
```

### 4. Check AmneziaWG tools

```bash
awg --version
```

### 5. DNS resolution error when using awg-quick manually

If `awg-quick up awg0` fails with `resolvconf: command not found` on Debian:
```bash
apt-get install -y openresolv
```

---

## Getting Help

- **Documentation**: [https://puqvpncp.com/doc/](https://puqvpncp.com/doc/)
- **Community**: [https://community.puqcloud.com](https://community.puqcloud.com)
- **Support**: [https://puqcloud.com/submitticket.php](https://puqcloud.com/submitticket.php)
