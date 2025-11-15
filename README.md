# Homelab

Homelab aims to provide a turnkey solution for self-hosting essential infrastructure services for your home network.

## Table of Contents

- [Homelab](#homelab)
  - [Table of Contents](#table-of-contents)
  - [Quickstart](#quickstart)
  - [Notes](#notes)
  - [Services](#services)
    - [AdGuardHome](#adguardhome)
    - [Cloudflared Tunnel](#cloudflared-tunnel)
    - [Portainer](#portainer)
    - [Uptime Kuma](#uptime-kuma)
    - [WUD (What's Up Docker)](#wud-whats-up-docker)
    - [ZeroTier](#zerotier)

## Quickstart

1. Clone the repository and `cd` into it

```bash
git clone https://github.com/skmpf/homelab
cd homelab
```

2. Copy the `.env` template

```bash
cp .env.template .env
```

3. Fill in the required values in the `.env` file:

   - `DOCKERCONFDIR`: Directory for container configuration files
   - `DOCKERSTORAGEDIR`: Directory for storage (if needed)
   - `PUID`: Your user's ID (run `id -u` to find it)
   - `TZ`: Your timezone (e.g., Europe/Paris)
   - `TUNNEL_TOKEN`: Cloudflare tunnel token

4. Start the stack

```bash
docker-compose up -d
```

5. Access the web interfaces for each service:
   - AdGuardHome: http://localhost:3000
   - Portainer: http://localhost:9000
   - Uptime Kuma: http://localhost:3001

## Notes

- AdGuardHome runs in host network mode for DNS server functionality
- ZeroTier also runs in host network mode and requires NET_ADMIN capabilities
- Cloudflared requires a tunnel token from Cloudflare
- Watchtower is configured to automatically update all containers at 4 AM daily
- Make sure to create the directories specified for `DOCKERCONFDIR` before starting the services
- All services use the non-root PUID for better security

## Services

### AdGuardHome

A network-wide software for blocking ads and tracking, enhancing privacy and security on your home network. Runs as your own private DNS server. [More information](https://github.com/AdguardTeam/AdGuardHome)

### Cloudflared Tunnel

A tunneling service by Cloudflare that securely exposes local servers to the internet without needing a public IP or port forwarding. Great for remote access to your services. [More information](https://github.com/cloudflare/cloudflared)

### Portainer

A web-based interface for managing Docker environments, making it easier to deploy, manage, and troubleshoot containerized applications. Perfect for monitoring and controlling all your Docker containers. [More information](https://github.com/portainer/portainer)

### Uptime Kuma

A self-hosted monitoring tool that keeps track of the uptime status of your services and websites. Features include status pages, notifications, and detailed metrics. [More information](https://github.com/louislam/uptime-kuma)

### WUD (What's Up Docker)

A web dashboard that monitors your Docker containers for available image updates and notifies you when new versions are released. [More information](https://github.com/fmartinou/whats-up-docker)

### ZeroTier

A virtual network service that creates secure, encrypted networks between devices, regardless of location or network configuration. Allows for easy remote access to your home network. [More information](https://github.com/zerotier/ZeroTierOne)
