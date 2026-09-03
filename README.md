# 🐙 Homelab Gitea

Self-hosted Git service providing repository management, webhooks, and issue tracking.

Part of the [homelab-core](https://github.com/kiskaadee/homelab-core) cluster ecosystem.

---

## 🏗️ Architecture & Storage

- **Container Image**: `gitea/gitea:latest`
- **Proxy**: Traefik (attached to `proxy-net`)
- **Persistent Data**: `./data` (gitignored, bind-mounted to `/data`)
- **SSH Port**: `222` (Host SSH passthrough)
- **Web Port**: `3000` (Traefik ingress)

---

## ⚙️ Environment Variables

| Variable | Description | Default / Example |
| :--- | :--- | :--- |
| `GITEA_DOMAIN` | Web UI FQDN | `gitea.arch-services.mywire.org` |
| `GITEA_SSH_DOMAIN` | SSH clone domain | `gitea.arch-services.mywire.org` |

---

## 🚀 Deployment

### Via Orchestrator (`appctl`)
```bash
appctl up homelab-gitea
```

### Manual Deployment
```bash
docker compose up -d
```
