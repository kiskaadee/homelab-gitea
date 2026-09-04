# 🐙 Homelab Gitea (Git Service)

Self-hosted lightweight Git service, code repository, and issue tracker.

---

## 🏗️ Architecture & Requirements

- **Proxy Network**: Attached to external `proxy-net`
- **Domain**: `gitea.roadtotech.me`
- **Target Port**: `3000` (HTTP Web), `2222` (SSH)

---

## ⚙️ Configuration & Metadata (`app.yaml`)

```yaml
name: "gitea"
aliases:
  - "git"
domain: "gitea.roadtotech.me"
description: "Self-Hosted Git Service & Code Repository"
visible: true
auth: false
networks:
  - proxy-net
env:
  SSH_DOMAIN: "gitea.roadtotech.me"
homepage:
  title: "Gitea"
  group: "Development & AI"
  icon: "gitea.png"
  container: "gitea"
  weight: 10
```

---

## 🚀 Deployment

### Via Orchestrator (`appctl`)
```bash
appctl up gitea
```

### Manual Deployment
```bash
docker compose up -d
```

---

## 📄 License
This repository is released into the public domain under the [Unlicense](LICENSE).
