# Hotmail Multi-Checker

<div align="center">

![Version](https://img.shields.io/github/v/release/elkhailiissam/hotmail-multi-checker-releases?style=flat-square&color=3B82F6)
![Downloads](https://img.shields.io/github/downloads/elkhailiissam/hotmail-multi-checker-releases/total?style=flat-square&color=22c55e)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blue?style=flat-square)
![License](https://img.shields.io/badge/license-Educational-yellow?style=flat-square)

**A cross-platform desktop application for Outlook/Hotmail account analysis and linked service detection.**

Built with Electron. Runs natively on Windows, macOS, and Linux.

[Download Latest Release](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases/latest)

</div>

---

> **Disclaimer:** This software is provided strictly for **educational and research purposes only**. It is designed to demonstrate concepts in email API interaction, OAuth authentication flows, and desktop application development. The authors do not endorse or encourage any unauthorized access to accounts. Users are solely responsible for ensuring their use complies with all applicable laws and terms of service. See [LEGAL.md](LEGAL.md) for full details.

---

## Features

| Feature | Description |
|---------|-------------|
| **Multi-threaded Engine** | Configurable worker pool (1-200 threads) for concurrent processing |
| **Module Detection** | Detects linked PlayStation, Epic Games, and Instagram accounts via email analysis |
| **Proxy Support** | Rotating proxy integration — paste or upload `.txt` proxy lists |
| **Real-time Dashboard** | Live stats, progress bar, CPM counter, and activity log |
| **Hit Management** | Filter, search, sort, export, and copy results |
| **License System** | Secure activation with hardware ID binding |
| **Cross-platform** | Native builds for Windows (.exe), macOS (DMG), and Linux (AppImage) |
| **Native UI** | Dark theme with custom titlebar, smooth animations, no browser chrome |

## Screenshots

<img width="3360" height="2100" alt="image" src="https://github.com/user-attachments/assets/ac706154-c0bf-476a-a92e-5755dce89061" />


## Download

**Distribution policy:** Published builds are **only** under **Release assets** on the [Releases](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases) page. This repository holds documentation and legal text; it does **not** host binaries on `main`.

1. Open **Releases** and select the latest version.
2. Under **Assets**, download the file for your platform (same naming style as below).

| Platform | File | Architecture |
|----------|------|-------------|
| **Windows** | `Hotmail.Multi-Checker-x.x.x.exe` | x64 |
| **macOS** | `Hotmail.Multi-Checker-x.x.x.dmg` | Universal (Intel + Apple Silicon) |
| **Linux** | `Hotmail.Multi-Checker-x.x.x.AppImage` | x64 |

### Installation

**Windows:**
1. Download `Hotmail.Multi-Checker-x.x.x.exe` from **Releases → Assets**
2. Run it — Windows SmartScreen may prompt you; choose **More info**, then **Run anyway**

**macOS:**
1. Download the `.dmg` file
2. Open it and drag the app to your Applications folder
3. First launch: right-click the app, select "Open", then confirm (Gatekeeper unsigned app)

**Linux:**
1. Download the `.AppImage` file
2. Make it executable: `chmod +x Hotmail.Multi-Checker-*.AppImage`
3. Run it: `./Hotmail.Multi-Checker-*.AppImage`

## Getting Started

1. **Launch the app** — you'll see the activation screen
2. **Enter your license key** — purchase one via [Telegram](https://t.me/configbys)
3. **Load combos** — paste `email:password` lines or upload a `.txt` file
4. **Select modules** — choose which services to scan for (PSN, Epic, Instagram)
5. **Configure threads** — higher = faster, but more resource intensive
6. **Optionally load proxies** — recommended for large combo lists
7. **Click Start** — results stream in real-time to the dashboard

## Modules

| Module | What It Detects |
|--------|----------------|
| **PSN** | PlayStation Network emails, purchase orders, account region, date of birth |
| **Epic Games** | Epic/Fortnite account emails, purchase receipts, match history |
| **Instagram** | Instagram account emails, username, follower count, login alerts |

## System Requirements

| | Minimum | Recommended |
|---|---------|-------------|
| **OS** | Windows 10, macOS 11, Ubuntu 20.04 | Windows 11, macOS 14, Ubuntu 22.04 |
| **RAM** | 2 GB | 4 GB+ |
| **Disk** | 200 MB | 500 MB |
| **Network** | Broadband | Broadband + proxies |

## Technical Architecture

```
┌─────────────────────────────────────────────┐
│                 Electron Shell               │
│  ┌────────────────────────────────────────┐  │
│  │           Embedded Express Server      │  │
│  │  ┌──────────┐  ┌───────────────────┐   │  │
│  │  │ REST API │  │  SSE (real-time)  │   │  │
│  │  └────┬─────┘  └────────┬──────────┘   │  │
│  │       │                 │              │  │
│  │  ┌────┴─────────────────┴──────────┐   │  │
│  │  │       Async Worker Pool         │   │  │
│  │  │  ┌───────┐ ┌───────┐ ┌───────┐ │   │  │
│  │  │  │ Wkr 1 │ │ Wkr 2 │ │ Wkr N │ │   │  │
│  │  │  └───┬───┘ └───┬───┘ └───┬───┘ │   │  │
│  │  └──────┼─────────┼─────────┼──────┘   │  │
│  └─────────┼─────────┼─────────┼──────────┘  │
└────────────┼─────────┼─────────┼─────────────┘
             │         │         │
     ┌───────┴─────────┴─────────┴───────┐
     │        Microsoft OAuth PKCE       │
     │     Outlook Search API (REST)     │
     │      Module Data Extraction       │
     └───────────────────────────────────┘
```

**Stack:** Electron 41 | Express 5 | Undici (HTTP/2) | AES-256-GCM encryption

## FAQ

**Q: Is this free?**
A: The application requires a license key to operate. Contact [@configbys](https://t.me/configbys) on Telegram to purchase.

**Q: Can I use this on multiple devices?**
A: Each license is bound to a single hardware ID. Contact support to transfer your license to a new device.

**Q: My antivirus flags the installer. Is it safe?**
A: Unsigned Electron builds often trigger heuristic antivirus warnings. Download **only** from the official [Releases](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases) page for this repository. When checksums are listed in release notes, verify them before running the file.

**Q: The app says "Update required". What do I do?**
A: Download the latest version from the [Releases](https://github.com/elkhailiissam/hotmail-multi-checker-releases/releases/latest) page.

**Q: Proxies aren't working.**
A: Supported formats: `host:port`, `host:port:user:pass`, `user:pass@host:port`. HTTP/HTTPS proxies only.

## Support

- **Telegram:** [@configbys](https://t.me/configbys)
- **Issues:** [GitHub Issues](https://github.com/elkhailiissam/hotmail-multi-checker-releases/issues)

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

---

<div align="center">
<sub>Built by <a href="https://t.me/configbys">Mr Robot</a></sub>
</div>
