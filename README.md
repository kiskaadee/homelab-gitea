# 🫖 Homelab Gitea (Git Service)

Self-hosted lightweight Git service, code repository, and issue tracker.

---

## 🏗️ Architecture & Requirements

- **Proxy Network**: Attached to external `proxy-net`
- **Domain**: `gitea.roadtotech.me`
- **Target Port**: `3000` (HTTP Web), `2223` (SSH Host Port)

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
  SSH_PORT: "2223"
homepage:
  title: "Gitea"
  group: "Development & AI"
  icon: "gitea.png"
  container: "gitea"
  weight: 10
```

---

## 🔑 SSH Access

Gitea exposes its SSH service on host port **`2223`** to avoid collision with the host OS SSH daemon.

### Client `~/.ssh/config`
To use standard `git clone git@gitea.roadtotech.me:...` without specifying `-p 2223`:

```ssh-config
Host gitea.roadtotech.me
    User git
    Port 2223
    IdentityFile ~/.ssh/id_ed25519
```

Test connection:
```bash
ssh -T git@gitea.roadtotech.me
# or explicitly: ssh -T -p 2223 git@gitea.roadtotech.me
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
This repository is released into the public domain under the [Unlicense](UNLICENSE).
