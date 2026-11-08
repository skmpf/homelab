# Homelab

Homelab aims to provide a turnkey solution for self-hosting essential infrastructure services for your home network.

## Table of Contents

- [Homelab](#homelab)
  - [Table of Contents](#table-of-contents)
  - [Quickstart](#quickstart)
  - [Notes](#notes)
  - [Services](#services)
    - [Cloudflared Tunnel](#cloudflared-tunnel)
    - [Dockhand](#dockhand)
    - [Uptime Kuma](#uptime-kuma)
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
   - Dockhand: http://localhost:3004
   - Uptime Kuma: http://localhost:3001

## Notes

- ZeroTier also runs in host network mode and requires NET_ADMIN capabilities
- Cloudflared requires a tunnel token from Cloudflare
- Make sure to create the directories specified for `DOCKERCONFDIR` before starting the services
- All services use the non-root PUID for better security

## Services

### Cloudflared Tunnel

A tunneling service by Cloudflare that securely exposes local servers to the internet without needing a public IP or port forwarding. Great for remote access to your services. [More information](https://github.com/cloudflare/cloudflared)

### Dockhand

A modern, efficient Docker management application providing real-time container management, Compose stack orchestration, and multi-environment support. [More information](https://github.com/Finsys/dockhand)

### Uptime Kuma

A self-hosted monitoring tool that keeps track of the uptime status of your services and websites. Features include status pages, notifications, and detailed metrics. [More information](https://github.com/louislam/uptime-kuma)

### ZeroTier

A virtual network service that creates secure, encrypted networks between devices, regardless of location or network configuration. Allows for easy remote access to your home network. [More information](https://github.com/zerotier/ZeroTierOne)
