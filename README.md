# ⚡ Premium VPS Setup Script

A lightweight, high-performance, and secure script to install and manage SSH services on Ubuntu VPS servers. Fully optimized to bypass client rate limits and optimized for fast tunneling connection speeds.

[![Supported OS](https://img.shields.io/badge/OS-Ubuntu%2020.04%20%7C%2022.04%20%7C%2024.04-orange.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](#)

---

## ✨ Features

- 🔒 **Multi-Service SSH**: Clean installation of OpenSSH, Dropbear, WebSocket SSH, and Stunnel.
- 🚀 **BBR & TCP Optimizations**: Enables Google BBR congestion control and optimizes TCP window buffers for faster tunneling speeds.
- 🛡️ **Zero Rate-Limiting**: Configures Go WebSocket-SSH and Stunnel to proxy through OpenSSH (port 22) with custom `MaxStartups` settings to prevent dropped connections.
- 🔌 **Dynamic Port Management**: Quickly modify service ports dynamically from the CLI menu without reinstalling.
- 🌐 **Acme.sh SSL Certificate integration**: Seamless Let's Encrypt SSL certificate issuance and installation.
- 🎮 **BadVPN UDP Gateway**: BadVPN compilation and installation on UDP ports 7300, 7400, and 7500 for gaming and UDP-based connections.
- 🖥️ **SSH-UI Web Panel**: A premium Flask-based web panel to create, delete, monitor, and manage SSH users via a clean browser UI.
- 📝 **SSH Banner Manager**: Easily change, restore, or clear the HTML/Text welcome banner displayed during login.

---

## 🔌 Port Configuration (Defaults)

| Service | Port | Protocol | Description | Forwarding Target |
| :--- | :--- | :--- | :--- | :--- |
| **OpenSSH** | `22` | TCP | Raw SSH connection | Local system shell |
| **Dropbear** | `109, 144, 50000` | TCP | Lightweight SSH daemon | Local system shell |
| **WebSocket SSH** | `143` | TCP | Go WebSocket SSH bridge | `127.0.0.1:22` (OpenSSH) |
| **Stunnel (SSH-SSL)** | `443` | TCP / TLS | SSL Tunnel wrapper | `127.0.0.1:22` (OpenSSH) |
| **Stunnel (WS-SSL)** | `2083` | TCP / TLS | SSL WebSocket wrapper | `127.0.0.1:143` (ws-ssh) |
| **BadVPN** | `7300, 7400, 7500` | UDP | BadVPN UDP gateway | Game/UDP traffic |
| **SSH-UI Panel** | `40460` | TCP | Flask Web Management Panel | Browser UI |

---

## 🚀 One-Line Installation

Run the following command as **root** on a fresh Ubuntu VPS:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/anewgmail26-stack/vps-setup/main/vps-setup.sh)"
```

---

## 🎮 CLI Management Menu

After installation, simply run the script to access the management panel:

```bash
./vps-setup.sh
```

```text
  ╭─────────────────────────────────────────────────────────╮
  │                      MAIN MENU                          │
  ├─────────────────────────────────────────────────────────┤
  │
  │  [1]  SSH Server Setup (Dropbear + WS + Stunnel)
  │  [2]  BadVPN UDP Gateway
  │  [3]  SSL Certificate (acme.sh)
  │  [4]  3X-UI Panel (Xray/V2Ray)
  │
  ├─────────────────────────────────────────────────────────┤
  │  [5]  SSH User Management
  │  [6]  Domain / Hostname Setup
  │  [7]  SSH Web Panel Management (SSH-UI)
  │  [8]  Show Service Status
  │  [9]  Restart All Services
  │
  ├─────────────────────────────────────────────────────────┤
  │  [10] Install ALL (SSH + BadVPN + 3X-UI + SSH-UI)
  │  [11] Change Service Ports
  │  [12] Change SSH Banner
  │  [0]  Exit
  │
  ╰─────────────────────────────────────────────────────────╯
```

---

## 🖥️ SSH-UI Web Panel Screenshots

Manage SSH accounts easily using the responsive Flask web panel listening on port **40460**:

- **Default Username**: `admin`
- **Default Password**: `admin123`

*(Change these default credentials inside the panel immediately after logging in)*

---

## 🛡️ License

This project is licensed under the MIT License. Feel free to clone, edit, and share!
