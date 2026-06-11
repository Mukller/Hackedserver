# HackedServer — Anti-Cheat Protection for Minecraft

<div align="center">

[![Version](https://img.shields.io/badge/version-3.16.1-blue.svg)](https://github.com/Mukller/Hackedserver-)
[![License: MIT](https://img.shields.io/badge/License-MIT-purple?style=flat-square)](LICENSE.md)
[![Minecraft](https://img.shields.io/badge/Minecraft-1.8%2B-green?style=flat-square)](https://minecraft.net)
[![maintained](https://img.shields.io/badge/maintained%3F-yes-green?style=flat-square)](https://github.com/Mukller/Hackedserver-)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen?style=flat-square)](CONTRIBUTING.md)
[![Status](https://img.shields.io/badge/status-Active-brightgreen.svg)]()

Русский • [English](README_EN.md)

</div>

**HackedServer** is a premium plugin for Minecraft servers that provides protection against cheats and unauthorized modifications through packet-based analysis.

## 🎯 Key Features

- **Real-time Packet Analysis** — Detects suspicious activity when players connect
- **Anti-Cheat Protection** — Blocks popular cheating software
- **Mod Detection** — Identifies unauthorized client modifications
- **Automated Responses** — Customizable actions upon violation detection
- **Event Logging** — Comprehensive recording of all suspicious activities
- **Optimized Performance** — Minimal server performance impact

## 📦 Requirements

- **Minecraft Version:** 1.8 - 1.21.x
- **Server Software:** Spigot, Paper, Purpur or compatible
- **Java Version:** Java 8 and above

## 🚀 Installation

1. Download the latest `hackedserver-3.16.1.jar` file
2. Place it in your server's `plugins/` folder
3. Restart your server using `/reload` command
4. Plugin is ready to use!

```bash
# Server reload command
/reload
```

## ⚙️ Configuration

After the first run, the plugin creates a `config.yml` file in `plugins/HackedServer/`.

### Main Parameters:

```yaml
# Enable the plugin
enabled: true

# Detection mode (STRICT, NORMAL, PERMISSIVE)
detection-mode: NORMAL

# Log events to file
log-events: true

# Notify admins about suspicious activity
notify-admins: true

# Action on cheat detection (KICK, BAN, WARN)
action-on-detect: KICK
```

## 🎮 Commands

| Command | Description | Permission |
|---------|-------------|-----------|
| `/hs reload` | Reload plugin configuration | `hackedserver.admin` |
| `/hs status` | Display plugin status | `hackedserver.status` |
| `/hs check <player>` | Check specific player | `hackedserver.check` |
| `/hs logs` | View event logs | `hackedserver.logs` |

## 📋 Permissions

```
hackedserver.admin        # Full access to admin commands
hackedserver.status       # View plugin status
hackedserver.check        # Check players
hackedserver.logs         # View logs
hackedserver.bypass       # Bypass cheat detection
```

## 🐛 Detected Cheats

- Aimbot and aim assistance
- Speed hack (movement acceleration)
- Fly hack (flying)
- Noclip (phase through blocks)
- Damage hack (damage modification)
- Killaura and extended range attacks
- Reach hack (increased attack radius)
- Anti-knockback

## 📊 Statistics and Logging

All events are logged to `plugins/HackedServer/logs/events.log` for analysis:

```
[2024-05-14 10:30:45] Player: Steve | Detection: Aimbot | Action: KICKED
[2024-05-14 10:31:12] Player: Alex | Detection: Speed Hack | Action: WARNED
```

## 🔧 Technical Support

If you encounter issues:

1. Check Minecraft version compatibility
2. Verify configuration file validity
3. Check server logs in `logs/latest.log`
4. Create an issue with detailed description

## 📈 Updates and Versions

Current Version: **3.16.1**

To stay updated:
- Review [CHANGELOG.md](CHANGELOG.md)
- Watch releases on GitHub
- Join our community

## 📜 License

This project is protected by a proprietary license. See [LICENSE.md](LICENSE.md) for details.

## 🤝 Contributing

We welcome bug reports and improvement suggestions. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 📝 Code of Conduct

When participating in this project, please follow our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)

## 📞 Contacts

- **Developer:** Mukller
- **GitHub:** [@Mukller](https://github.com/Mukller)
- **Issues:** [Create Issue](https://github.com/Mukller/Hackedserver-/issues)

---

**Thank you for using HackedServer! 🛡️**
