# 🚀 Raspberry Pi OS Setup Guide

[![License: GPL-3.0](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
![Stars](https://img.shields.io/github/stars/Aryan-136/raspberry-pi-os-setup?style=social)
![Forks](https://img.shields.io/github/forks/Aryan-136/raspberry-pi-os-setup?style=social)
![Last Commit](https://img.shields.io/github/last-commit/Aryan-136/raspberry-pi-os-setup)
![Issues](https://img.shields.io/github/issues/Aryan-136/raspberry-pi-os-setup)
![Pull Requests](https://img.shields.io/github/issues-pr/Aryan-136/raspberry-pi-os-setup)

> **A modern, minimal, and advanced guide to install Raspberry Pi OS on SD card or SSD. Includes automation, troubleshooting, security, headless setup, project ideas, and more.**

---

## 🚦 Quick Start

```bash
# 1. Download and install Raspberry Pi Imager from https://www.raspberrypi.com/software/
# 2. Insert SD card or SSD
# 3. Flash Raspberry Pi OS using Imager (configure WiFi/SSH if needed)
# 4. Insert into Pi, power on, and follow setup wizard
```
[Full instructions below ⬇️](#installation-steps)

---

## 🎬 Video Walkthrough

[![Watch the setup video](https://img.youtube.com/vi/VIDEO_ID_HERE/0.jpg)](https://www.youtube.com/watch?v=VIDEO_ID_HERE)
> _Replace with your own video or a recommended YouTube tutorial!_
>  
> Or see [animated GIFs in the `/screenshots` folder](./screenshots/).

---

## 🧰 What You'll Need

| Item                   | Description                                 |
| ---------------------- | ------------------------------------------- |
| 🧠 Raspberry Pi        | Any model (Pi 3, 4, 5, Zero, etc.)          |
| 💾 SD Card             | 16GB+ (Class 10/UHS-1, A1/A2 recommended)   |
| 💽 SSD (Optional)      | For faster performance (USB 3.0 enclosure)  |
| 🔌 Power Supply        | Official or high-quality USB power source   |
| 📶 Internet            | WiFi or Ethernet (for updates/headless)     |
| 🖥️ Monitor & Keyboard | Optional for desktop setup                  |
| 🖱️ Mouse              | Optional for desktop setup                  |
| 📲 Raspberry Pi Imager | Official tool to flash OS                   |
| 🛠️ Card Reader/Adapter| For SD card/SSD connection to PC            |

---

## 📦 Installation Steps

### 1️⃣ Download Raspberry Pi Imager

- [Raspberry Pi Imager Download Page](https://www.raspberrypi.com/software/)
- 🪟 [Windows](https://downloads.raspberrypi.org/imager/imager_latest.exe)
- 🍎 [macOS](https://downloads.raspberrypi.org/imager/imager_latest.dmg)
- 🐧 [Ubuntu x86](https://downloads.raspberrypi.org/imager/imager_latest_amd64.deb)
- 🧠 On Raspberry Pi OS:
  ```bash
  sudo apt install rpi-imager
  ```
- 💡 [Manual OS Images](https://www.raspberrypi.com/software/operating-systems/)

<img src="screenshots/step1_imager.png" alt="Step 1 - Imager Download" width="700" />

---

### 2️⃣ Insert Your SD Card or SSD

- Insert microSD card via card reader **OR** connect SSD via USB 3.0 adapter.
- Confirm it's detected as a removable drive.

<img src="screenshots/step2_storage.png" alt="Step 2 - Storage Detected" width="700" />

---

### 3️⃣ Flash Raspberry Pi OS

1. **Open Raspberry Pi Imager**
2. **Select Device** → Choose your Pi model
3. **Select OS** → Pick your preferred OS (32/64-bit, Lite, Desktop, etc.)
4. **Select Storage** → Choose SD card or SSD
5. **Advanced Options:** (⚙️) Pre-configure hostname, SSH, WiFi, locale, timezone, user/password

**Configuration Prompt:**
- **Edit Configure: Yes** → Set custom options
- **Edit Configure: No** → Use defaults

⚠️ **Warning:** This will format your drive. Backup important data!

**Process:**
- Imager will **download**, **verify**, and **write** the image
- Progress bar and popup on completion
- ✅ Safely eject your SD card or SSD

<img src="screenshots/step3_flash.png" alt="Step 3 - Flashing Process" width="700" />

---

### 4️⃣ Boot Your Raspberry Pi

- Insert SD card/SSD into your Pi
- Connect monitor, keyboard, mouse (or use headless SSH)
- Plug in power
- Wait for first boot/setup wizard

<img src="screenshots/step4_boot.png" alt="Step 4 - Pi Boot" width="700" />

---

## 🛰️ Headless WiFi-Only Setup

1. In Imager, click ⚙️ and:
   - Set hostname
   - Enable SSH
   - Enter WiFi SSID, password, and country
2. Flash as usual, insert SD/SSD, power on Pi
3. Find Pi’s IP (check router or use `raspberrypi.local`)
4. SSH in:
   ```bash
   ssh pi@raspberrypi.local
   ```
5. Complete setup via terminal

---

## 🛡️ Advanced Security Hardening

- Change default password: `passwd`
- Create a new user, disable `pi` if not needed
- Enable UFW firewall:
  ```bash
  sudo ufw allow OpenSSH
  sudo ufw --force enable
  ```
- Enable automatic security updates:
  ```bash
  sudo apt install unattended-upgrades
  sudo dpkg-reconfigure --priority=low unattended-upgrades
  ```
- Disable unused interfaces in `raspi-config`
- Use SSH keys instead of passwords
- Disable password login for SSH (edit `/etc/ssh/sshd_config`)

---

## 🛠️ First-Time Setup

```bash
sudo apt update && sudo apt full-upgrade -y
sudo raspi-config
```
- Change password, expand filesystem, set locale/timezone, enable interfaces (I2C, SPI, Camera, SSH, VNC)

---

## 💡 Tips & Tricks

- 🏎️ **SSD boot:** Faster and more reliable than SD cards
- 🛜 **Headless setup:** Pre-configure WiFi & SSH in Imager
- 🧠 **Default login:**  
  - Username: `pi`  
  - Password: `raspberry`
- 🎯 **SSH access:** Use `raspberrypi.local` or your custom hostname
- 🖥️ **Remote desktop:** Enable VNC in `raspi-config`

---

## 🛠️ Customization & Tweaks

- **Overclocking:**  
  Edit `/boot/config.txt` to safely overclock your Pi for better performance.
- **Custom Splash Screen:**  
  Replace `/usr/share/plymouth/themes/pix/splash.png` with your own image.
- **Kiosk Mode:**  
  Set up Chromium in kiosk mode for digital signage or dashboards.
- **Auto-login:**  
  Enable/disable auto-login for desktop or CLI in `raspi-config`.
- **Custom Hostname:**  
  Change your Pi's hostname for easier network identification.

---

## 🧩 Advanced Projects & Use Cases

- **AI/ML on Pi:** Run TensorFlow Lite or PyTorch for edge AI projects.
- **Network Security Monitor:** Use Pi as a network sniffer or IDS.
- **Weather Station:** Connect sensors and visualize data.
- **Home Assistant:** Smart home automation hub.
- **Pi-hole:** Network-wide ad blocker.
- **RetroPie:** Retro gaming console.
- **Media Center:** Kodi, Plex, Jellyfin.
- **Personal web server:** Host your own site or blog.
- **Network-attached storage (NAS):** Central file storage.
- **IoT sensor hub:** Collect and visualize sensor data.
- **VPN server:** Secure remote access to your network.
- **MagicMirror:** Smart mirror display.
- **AdGuard Home:** Alternative to Pi-hole for network-wide ad blocking.
- **OctoPrint:** 3D printer server.
- **Minecraft Server:** Host your own Minecraft world.
- **PiVPN:** Simple OpenVPN/WireGuard server.

---

## 🗃️ FAQ

**Q: My Pi won’t boot, what should I check?**  
A: Check power supply, SD/SSD, cables, and try re-flashing the OS.

**Q: How do I enable SSH if I forgot?**  
A: Place a file named `ssh` (no extension) in the boot partition.

**Q: WiFi won’t connect?**  
A: Use 2.4GHz, check country code, and re-enter credentials.

**Q: How do I expand storage?**  
A: Run `sudo raspi-config` → Advanced Options → Expand Filesystem.

**Q: How do I check my Pi's IP address?**  
A: Run `hostname -I` or check your router's device list.

**Q: How do I update Raspberry Pi OS?**  
A: Run `sudo apt update && sudo apt full-upgrade -y`.

**Q: How do I backup my SD card?**  
A: Use `Win32 Disk Imager` (Windows) or `dd` (Linux/macOS) to create an image.

---

## 🏆 Hall of Fame / Showcase

> Have you built something cool with this guide?  
> Share your project, photo, or repo link here!  
> _Open a PR or Issue to be featured._

---

## 📚 Resources & Further Reading

- [Official Raspberry Pi Documentation](https://www.raspberrypi.com/documentation/)
- [Raspberry Pi Forums](https://forums.raspberrypi.com/)
- [Raspberry Pi Stack Exchange](https://raspberrypi.stackexchange.com/)
- [Jeff Geerling’s YouTube Channel](https://www.youtube.com/c/JeffGeerling)
- [The MagPi Magazine](https://magpi.raspberrypi.com/)
- [Raspberry Pi Tips & Tricks](https://www.raspberrypi.com/news/)

---

## 🌐 Community & Chat

- [Raspberry Pi Discord](https://discord.gg/raspberrypi)
- [Reddit r/raspberry_pi](https://www.reddit.com/r/raspberry_pi/)
- [Telegram Group (unofficial)](https://t.me/raspberrypi)
- [Matrix Chat](https://matrix.to/#/#raspberrypi:matrix.org)

---

## 🤝 Contribution

We welcome contributions to improve this guide!  
Feel free to fork the repository, create a branch, and submit a pull request.

- Open Issues or PRs to improve the guide
- Add translations, scripts, or troubleshooting steps
- Share your own automation scripts!

---

## 💖 Support

If you find this project helpful, consider supporting us! Your support helps us continue improving and adding new features.

**Ways to Support:**
- [![☕ Buy Me a Coffee](https://img.shields.io/badge/☕-Buy%20Me%20a%20Coffee-orange?style=for-the-badge)](https://buymeacoffee.com/Aryan_13.6)  
  Show your appreciation by buying us a coffee!
- ⭐ **Star the repository on GitHub**  
  Help us gain visibility by starring the project.
- 🗣️ **Share the project**  
  Spread the word about this guide to your network.

Every contribution, whether big or small, makes a difference. Thank you for your support! 🙌

---

## 📧 Contact

For inquiries, feedback, or support, feel free to reach out:

- **📧 Email:** [pandyaaryanp348@gmail.com](mailto:pandyaaryanp348@gmail.com)
- **🌐 GitHub:** [Aryan-136](https://github.com/Aryan-136)

We value your input and are here to assist you with any questions or issues. Don't hesitate to get in touch!

---

## 📜 License

This project is licensed under the **GPL-3.0 License**. See the `LICENSE` file for details.

---
