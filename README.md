### Malware Boys 
# 🐍 Honeypot: A Beginner-Friendly Cybersecurity Trap

A lightweight and educational honeypot designed to simulate vulnerable services, capture attacker behavior, and explore how intrusions occur in real-world environments. This project emphasizes **isolation, observability, and secure deployment.**

---

## 🔍 Project Overview

A **honeypot** is a decoy system intended to attract malicious traffic so that attacker behaviour can be safely observed and analyzed without risking real production systems. 

This honeypot emulates common network services (e.g. SSH, HTTP, FTP), logs interaction data, and run in an isolated Linux environment to ensure containment and safety.

---

## 👤 My Contributions (Important)

This project was developed as a **group security project.**
My primary contributions focus on **system isolation, networking, and containment.**


### 🔧 My work includes
- Designing **Docker-based service isolation** to safely run the honeypot on Linux.
- Creating a **custom Docker bridge network** to segment honeypot traffic.
- Implementing **firewall rules and IP-blocking logic** to contain and limit malicious activity.
- Ensuring the honeypot could run continuously with minimal risk to the host system.

### 📌 Note:
My contributions live on the **isolation-docker branch.** Please review that branch to see the Docker networking, firewall configuration, and isolation logic.

---

## 🛠️ Features

### ✅ Basic Features
- **Service Emulation**: Fake SSH/HTTP/FTP services to mimic real systems.
- **Logging & Monitoring**: Captures IPs, timestamps, commands, and full request data.
- **Deception**: Includes dummy files like `/etc/passwd`, fake credentials, and time delays to appear real.
- **Isolation**: Runs in a container or virtual machine to protect your host system.
- **Alerting**: Notifies on suspicious activity (console-based or optional integrations).
- **Persistence**: Secure logging to local or remote systems for later analysis.

---

## 🧰 Tech Stack

| Feature              | Tool/Language     |
|----------------------|------------------|
| Service Emulation    | Python (`socket`, `http.server`) |
| Logging              | Python `logging` module |
| Containerization     | Docker |
| Monitoring           | JSON log files |
| Isolation            | iptables / Docker networking |

---

## 🗂️ Project Structure

```
honeypot/
│
├── honeypot/                  # Core package
│   ├── __init__.py
│   ├── main.py                # Entry point
│   ├── config.py              # Config loader (ports, services, flags)
│   ├── logger.py              # Logging setup
│   ├── alert.py               # Alerting logic (email, webhook)
│   │
│   ├── services/              # Each protocol honeypot in its own module
│   │   ├── __init__.py
│   │   ├── ssh.py             # Fake SSH server
│   │   ├── http.py            # Fake HTTP server
│   │   └── ftp.py             # Fake FTP server
│   │   
│   └── utils/
│       ├── isolation.py       # Docker/VPN/firewall helpers
│       └── geoip.py           # IP geolocation
│
├── logs/                      # Structured logs stored here
│   └── ...
│
├── data/                      # Dummy payloads, fake files (e.g. /etc/passwd)
│   └── fake_passwd.txt
│
├── Dockerfile                 # Containerized deployment
├── requirements.txt           # Dependencies
├── README.md                  # Project overview
└── run.py                     # Thin wrapper for CLI entry

```

---

## ⚠️ Security Notice

**⚠️ Never run a honeypot on a production or personal machine.**  
Always isolate it in a **VM**, **container**, or behind strict **firewall rules**. Honeypots attract real attackers.

---

## 🏁 Getting Started

```bash
# Clone this repo
git clone https://github.com/shadmanh123/honeypot.git
cd honeypot

# Switch to branch with isolation work
git checkout isolation-docker

# Build and run
docker build -t honeypot .
docker run --rm honeypot
```

---

## 🧠 Future Improvements

- 🌍 Geolocate attacker IPs
- 📁 Trap malicious file uploads
- 🐚 Detect reverse shell attempts
- 🔒 Encrypt and ship logs to S3 or remote servers
- 🚫 Auto-block repeated intrusions by IP
