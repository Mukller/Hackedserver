<div align="center">

**English** • [Русский](README.md)

</div>

# HackedServer — Anti-Cheat Protection for Minecraft

[![Version](https://img.shields.io/badge/version-3.16.1-blue.svg)](https://github.com/Mukller/Hackedserver-)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE.md)
[![Status](https://img.shields.io/badge/status-Active-brightgreen.svg)]()

**HackedServer** is a premium plugin for Minecraft servers that protects against cheats and unauthorized modifications through data-packet analysis.

## 🎯 Key Features

- **Real-time packet analysis** — detects suspicious activity as players connect
- **Cheat protection** — blocks popular cheating tools
- **Mod detection** — identifies unauthorized client modifications
- **Automatic responses** — configurable actions on detected violations
- **Event logging** — detailed records of all suspicious actions
- **Optimized performance** — minimal impact on server performance

## 📦 Requirements

- **Minecraft version:** 1.8 - 1.21.x
- **Server Software:** Spigot, Paper, Purpur, or compatible
- **Java version:** Java 8 or higher

## 🚀 Installation

1. Download the latest `hackedserver-3.16.1.jar`
2. Place it into your server's `plugins/` folder
3. Reload the server with `/reload`
4. The plugin is ready to go!

```bash
# Command to reload the server
/reload
```

## ⚙️ Configuration

On first launch the plugin creates `config.yml` in `plugins/HackedServer/`.

### Main parameters:

```yaml
# Enable the plugin
enabled: true

# Detection mode (STRICT, NORMAL, PERMISSIVE)
detection-mode: NORMAL

# Log events to file
log-events: true

# Notify administrators about suspicious activity
notify-admins: true

# Action on cheat detection (KICK, BAN, WARN)
action-on-detect: KICK
```

## 🎮 Commands

| Command | Description | Permission |
|---------|---------|-----------|
| `/hs reload` | Reload the plugin configuration | `hackedserver.admin` |
| `/hs status` | Show plugin status | `hackedserver.status` |
| `/hs check <player>` | Check a specific player | `hackedserver.check` |
| `/hs logs` | View the event log | `hackedserver.logs` |

## 📋 Permissions

```
hackedserver.admin        # Full access to admin commands
hackedserver.status       # View plugin status
hackedserver.check        # Check players
hackedserver.logs         # View logs
hackedserver.bypass       # Bypass detection protection
```

## 🐛 Detected cheats

- Aimbot and auto-aim
- Speed hack (movement acceleration)
- Fly hack
- Noclip (passing through blocks)
- Damage hack (damage modification)
- Killaura and ranged attacks
- Reach hack (extended attack range)
- Anti-knockback

## 📊 Statistics and logging

All events are logged to `plugins/HackedServer/logs/events.log` for later analysis:

```
[2024-05-14 10:30:45] Player: Steve | Detection: Aimbot | Action: KICKED
[2024-05-14 10:31:12] Player: Alex | Detection: Speed Hack | Action: WARNED
```

## 🔧 Technical support

If you run into problems:

1. Check Minecraft version compatibility
2. Make sure the configuration file is valid
3. Look at the server logs in `logs/latest.log`
4. Create an issue in the repository describing the problem

## 📈 Updates and versions

Current version: **3.16.1**

To follow updates:
- See [CHANGELOG.md](CHANGELOG.md)
- Watch the releases on GitHub
- Join our community

## 📜 License

This project is protected by a proprietary license. See [LICENSE.md](LICENSE.md) for details.

## 🤝 Contributing

We welcome bug reports and improvement suggestions. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 📝 Code of Conduct

When participating in the project community, please follow our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)

## 📞 Contacts

- **Developer:** Mukller
- **GitHub:** [@Mukller](https://github.com/Mukller)
- **Issues:** [Create an issue](https://github.com/Mukller/Hackedserver-/issues)

---

**Thanks for using HackedServer! 🛡️**
