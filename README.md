# Catppuccin-Glass 

> A sleek, glassy YASB status bar theme built on Catppuccin Mocha — featuring Komorebi workspace integration, live media controls, CPU temperature, while keeping it minimal with a pill based design.

![Preview](https://i.imgur.com/KRRoCua.png)

---
#IMPORTANT - HOW TO GET THE CPU TEMP WIDGET WORKING 

### CPU Temperature (Right) — Requires LibreHardwareMonitor

This widget reads your CPU temperature via LibreHardwareMonitor's local web server.

**First time setup:**

1. Download [LibreHardwareMonitor](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor/releases)
2. Extract and run `LibreHardwareMonitor.exe` as **Administrator**
3. In the menu bar go to **Options → Web Server → Run**
4. Check that `http://localhost:8085` loads in your browser
5. To make it start minimized to tray on boot:
   - Go to **Options → Start Minimized** ✓
   - Go to **Options → Minimize To Tray** ✓
   - Go to **Options → Run On Windows Startup** ✓

**Finding your sensor ID:**

Open `http://localhost:8085` in your browser and look for your CPU temperature sensor path. Common examples:
```
Intel: /intelcpu/0/temperature/12
AMD:   /amdcpu/0/temperature/0
```

Update it in `config.yaml`:
```yaml
cpu_temp:
  options:
    sensor_id: "/intelcpu/0/temperature/12"  # replace with yours
```

---

## Bar Layout

```
[ ⊞  ○ ━━━ ○ ○ ○  App Name ]   [ Date · Media Controls · Apps ]   [ RAM · Temp · WiFi · Vol · Bat · 🔔 ]
  ↑        ↑          ↑                ↑          ↑            ↑                ↑      ↑      ↑
Power   Workspaces  Active          Clock      Media        Center            Memory  CPU   WiFi
Menu               Window                     Player       Grouper           Widget  Temp  Menu
```

---

## Widgets — What Each Does

### ⊞ Power Menu (Left)
Click the Windows icon on the far left to open the power menu.

<img width="1919" height="1069" alt="Screenshot 2026-04-25 223239" src="https://github.com/user-attachments/assets/cbdec2d2-c0d8-4392-bc8d-33cbfe9d4007" />


Options: Shut Down · Restart · Lock · Sign Out · Hibernate · Sleep · Cancel

Uptime is shown at the bottom of the power menu.

---

### ○ ━━━ ○ ○ ○ Komorebi Workspaces (Left)
Shows your active Komorebi tiling window manager workspaces. The active workspace appears as a wider filled pill. Populated workspaces show a small dot.

**Don't use Komorebi?** Remove it from your config:

In `config.yaml`, find this line under `widgets > left`:
```yaml
left: ["power_menu", "komorebi_workspaces", "active_window"]
```
Change it to:
```yaml
left: ["power_menu", "active_window"]
```
Then remove the `komorebi_workspaces` widget block entirely from the widgets section.it will finally look something like this.

<img width="1920" height="58" alt="no_komorebi" src="https://github.com/user-attachments/assets/e9d69533-ccaf-43c1-9351-c6908720e35d" />


---

### Media Controls (Center)
Shows currently playing track from Spotify, Apple Music, or any media source.Apple music doesnt allow playback time rest everything works.

- **Left click** — opens media popup with album art, progress bar and volume
- **Right click** — toggles between `Song - Artist` and `Artist - Song` display

<img width="1919" height="1021" alt="Screenshot 2026-04-25 222032" src="https://github.com/user-attachments/assets/d7448717-df06-46ef-8f88-15e5079ae647" />


---

### Center Grouper — App Shortcuts (Center)
The pill-shaped group in the center contains quick launch icons:

| Icon | Action |
|------|--------|
| 🔔 | Opens Windows Notification Center |
| 🔍 | Dont get confused this search Opens Windows Settings search — I personally use flow launcher nstead of windows search so this is why this is here i recommended to use in
| ⋮⋮⋮ | Opens Komorebi Control menu — start, stop, or reload Komorebi |
| 🏞️ | Opens Wallpaper Gallery — browse and set wallpapers from your folder |
| >_ | Opens terminal in ADMINSTRATOR MODE (Be Careful while using it)
| 🎚️ | Opens Windows Quick Settings |

**Komorebi Control popup:**

<img width="1919" height="1010" alt="Screenshot 2026-04-25 222628" src="https://github.com/user-attachments/assets/31220426-895a-401a-9cc8-1c0773dca3a3" />


Komorebi starts automatically on boot via `komorebic start --whkd`. Use this menu if you need to manually restart or stop it.

---

### Wallpaper Gallery
Click the wallpaper icon in the center grouper to browse your wallpaper collection in a glassy gallery popup.

**Setting your wallpaper folder:**

In `config.yaml`, find the wallpapers widget and update the path:
```yaml
wallpapers:
  options:
    image_path: "C:\\Users\\YourName\\YourWallpaperFolder"
```
Replace `YourName` with your Windows username and `YourWallpaperFolder` with your folder name.

---

### WiFi Widget (Right)
Shows WiFi signal strength percentage. **Left click** opens the WiFi network menu.

<img width="1919" height="1011" alt="Screenshot 2026-04-25 223055" src="https://github.com/user-attachments/assets/73648a9c-183e-4223-a6d4-575c01b6e92c" />


**Right click** toggles between signal percentage and network name.

---

# Final Note


You can use it however you may like but i personally use it with a modded taskbar. Everything you need — app switching, system stats, media, workspaces — is right here at the top. For launching apps, [Flow Launcher] is recommended as a keyboard-driven app launcher.Combine it **with a  windhawk modded minimal Windows taskbar** it looks great and improves functionality as this bar doesnt have a system tray or taskbar built into it. 

For a complete setup, i  personally use [Windhawk] with the Squircle taskbar mod for a minimal-style taskbar at the bottom — keeping the YASB bar clean and distraction-free at the top.


<img width="1919" height="1077" alt="Screenshot 2026-04-25 233735" src="https://github.com/user-attachments/assets/282259d8-5af2-4d63-b54c-0b5330446c04" />


---


## Requirements

| Komorebi | Tiling window manager | [github.com/LGUG2Z/komorebi](https://github.com/LGUG2Z/komorebi) |
| whkd | Hotkey daemon for Komorebi | [github.com/LGUG2Z/whkd](https://github.com/LGUG2Z/whkd) |
| JetBrainsMono NFP | Nerd Font for icons | [nerdfonts.com](https://www.nerdfonts.com/font-downloads) |
| LibreHardwareMonitor | CPU temp readings | [GitHub Releases](https://github.com/LibreHardwareMonitor/LibreHardwareMonitor/releases) |


---

## Credits

Built with [YASB](https://github.com/amnweb/yasb) by amnweb.Inspired by design of Yasb-OO4
Catppuccin color palette by [catppuccin](https://github.com/catppuccin/catppuccin).
Theme by PRABUDDHA1x1
