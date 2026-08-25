# 🔥 Douyin Spark Auto-Sender

Automatically send daily messages to maintain your Douyin (TikTok China) chat streaks (火花). Supports multiple accounts, web management panel, scheduled sending, and one-click updates.

![Version](https://img.shields.io/badge/version-V1.0.0-blue)
![Platform](https://img.shields.io/badge/platform-Windows-green)
![Python](https://img.shields.io/badge/python-3.8+-yellow)

---

## ✨ Features

- **Multiple Accounts** — Manage unlimited Douyin accounts, each with independent friend lists and schedules
- **Web Management Panel** — Control everything from your browser (desktop or mobile)
- **Scheduled Sending** — Set a global schedule or per-account schedules, runs automatically every day
- **QR Code Login** — Scan to log in, session persists across restarts
- **Friend Sync** — Auto-scrape friend list with streak days (🔥), select which friends to auto-send
- **Live Screen View** — Watch the browser in real-time while tasks run
- **Remote Login Control** — Enter verification codes and passwords from your phone during login
- **One-Click Updates** — Check for and install updates directly from the panel (no re-download needed)
- **Power Save Mode** — Automatically close background processes to reduce CPU/memory usage
- **Screen Blackout** — One-click screen off for unattended operation
- **Remote Access** — Built-in cpolar integration for external network access
- **Apple-style Glass UI** — Beautiful frosted glass interface with iOS wallpapers
- **First-Run Guide** — Interactive tutorial for new users

---

## 📋 Requirements

- **Windows 10/11** (64-bit)
- **Python 3.8+** (auto-installed by the setup script if missing)
- **Microsoft Edge** (pre-installed on Windows, used as the browser engine)
- **Internet connection**

> No Chrome or Chromium download needed — uses your system Edge browser.

---

## 🚀 Quick Start

### Method 1: One-Click Deployment (Recommended)

1. Download the latest release ZIP from [Releases](https://github.com/huiyao0908/douyin-spark-updates/releases)
2. Extract to any folder (e.g., `D:\DouyinSpark`)
3. Double-click **`一键部署.bat`** (One-Click Setup)
4. Wait for the setup to complete (installs Python dependencies, creates config)
5. The web panel opens automatically at `http://127.0.0.1:5000`

### Method 2: Manual Setup

```bash
# 1. Clone or download
git clone https://github.com/huiyao0908/douyin-spark-updates.git
cd douyin-spark-updates

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run
python app.py
```

Then open `http://127.0.0.1:5000` in your browser.

---

## 📖 Usage Guide

### 1. Add an Account

- Click **"+ Add Account"** in the top toolbar
- Enter a name (or leave blank for auto-naming)
- Click **"Scan QR Login"** on the account card
- Scan the QR code with your Douyin app
- Complete any secondary verification (SMS code or password) using the remote control panel
- Account name and friend list sync automatically after login

### 2. Sync Friends

- Click **"Sync Friends"** on the account card
- The tool scrapes your chat list with streak days (🔥)
- Select the friends you want to auto-send to
- Click **"Import Selected"**

### 3. Set Message

- Click **"Edit"** on the account card
- Enter your custom message (supports multi-line)
- The message format automatically includes:
  - Current timestamp
  - Your custom message
  - Streak count and runtime duration

### 4. Set Schedule

- Click **"Schedule Settings"** in the top toolbar
- Set a global send time (e.g., 00:30)
- Or enable per-account schedules for different times
- Toggle schedule on/off as needed

### 5. Test Send

- Click **"Send"** on any account card to test immediately
- Click **"Send All"** to send for all enabled accounts
- Watch the live screen view to monitor progress

### 6. Check for Updates

- Click **"More Tools" → "Check Update"**
- If an update is available, click **"Update Now"**
- All accounts, login sessions, and settings are preserved during update

---

## 🎛️ Management Panel

### Top Toolbar
| Button | Function |
|--------|----------|
| + Add Account | Add a new Douyin account |
| Send All | Send messages to all enabled accounts |
| Cancel Send | Stop all ongoing send tasks |
| Schedule Settings | Configure global and per-account schedules |
| Refresh Sparks | Refresh streak days for all friends |
| Check Login | Verify login status of all accounts |
| Live View | Open real-time browser screen |
| More Tools | Tutorial, phone connection, wallpaper, power save, screen off, clear history, check update |
| Refresh | Reload the page |

### Account Card
| Button | Function |
|--------|----------|
| Send | Send to this account's friends |
| Sync Friends | Scrape friend list with streak days |
| Verify Login | Check if login is still valid |
| Live View | Open browser screen |
| Scan QR Login / Logout | Login or logout |
| Edit | Edit account name, message, friends |
| Delete | Remove this account |
| Enable Toggle | Enable/disable this account |
| Keep-Alive Toggle | Keep browser open between tasks |
| Schedule | Set per-account send time |

---

## 🌐 Remote Access (cpolar)

1. Click **"More Tools" → "Phone Connection"**
2. Click **"Enable Remote Access"**
3. Sign up at cpolar.com (free tier available)
4. Paste your cpolar authtoken
5. Get your public URL and access the panel from anywhere

### Mobile Connection
- **Same WiFi**: Use `http://<your-computer-ip>:5000`
- **External**: Use the cpolar public URL
- Add to home screen on iOS/Android for an app-like experience (PWA support)

---

## ⚙️ Configuration

Config file: `config.json`

```json
{
  "accounts": [],
  "browser": {
    "headless": false,
    "slow_mo": 50
  },
  "schedule": {
    "enabled": true,
    "hour": 0,
    "minute": 30,
    "per_account": {}
  },
  "power_save": false,
  "live_view_enabled": true,
  "low_performance_mode": false,
  "background": "",
  "update_source": "https://raw.githubusercontent.com/huiyao0908/douyin-spark-updates/main/version.json"
}
```

---

## 🔧 Troubleshooting

### "Service won't start"
- Make sure port 5000 is not in use
- Run `启动服务.bat` (Start Service) manually
- Check `logs/app.log` for errors

### "Login expired"
- Click "Verify Login" to check status
- Click "Scan QR Login" to re-authenticate
- Sessions typically last 7-30 days

### "Sync friends finds 0 friends"
- Make sure you're logged in (check login status)
- Try again — sometimes the page loads slowly
- Enable "Low Performance Mode" for slower computers

### "Sending is slow"
- This is normal — Douyin rate-limits message sending
- Enable "Browser Keep-Alive" to avoid re-opening browser each time
- Use "Low Performance Mode" on older computers

### "Page shakes every few seconds"
- Update to V1.0.0 or later — this bug was fixed
- If it persists, clear browser cache and reload

### "Update fails"
- Check your internet connection
- Try manual update: download ZIP, use "Upload Update Package" in the update panel
- Make sure the tool has write permission to its folder

---

## 📁 Project Structure

```
douyin-spark/
├── app.py              # Flask web server + API endpoints
├── douyin_bot.py       # Playwright browser automation core
├── scheduler.py        # APScheduler for scheduled sending
├── requirements.txt    # Python dependencies
├── config.json         # User configuration (auto-created)
├── stats.json          # Send statistics
├── version.json        # Version info for auto-update
├── templates/
│   └── index.html      # Web management panel (single-page app)
├── static/
│   ├── wallpapers/     # iOS 26/27 default wallpapers
│   ├── manifest.json   # PWA manifest
│   ├── sw.js           # Service worker
│   └── icon-*.png      # App icons
├── storage/            # Browser login states (per account)
├── logs/               # Application logs
├── screenshots/        # Temporary screenshots (auto-cleaned)
├── 一键部署.bat          # One-click setup script
├── 启动服务.bat          # Start service
├── 停止服务.bat          # Stop service
├── 卸载工具.bat          # Uninstall tool
├── 省电模式开关.bat       # Power save toggle
├── 一键黑屏.bat          # Screen blackout
├── 远程访问一键开启.bat    # Remote access setup
├── monitor_off.ps1     # Screen off script
├── monitor_on.ps1      # Screen on script
├── power_save.ps1      # Power save script
├── 使用教程.txt          # Chinese usage tutorial
└── 更新日志.txt          # Chinese changelog
```

---

## 🔄 Auto-Update System

The tool checks for updates from:
```
https://raw.githubusercontent.com/huiyao0908/douyin-spark-updates/main/version.json
```

`version.json` format:
```json
{
  "latest_version": "V1.0.0",
  "release_date": "2026-08-26",
  "download_url": "https://raw.githubusercontent.com/huiyao0908/douyin-spark-updates/main/douyin-spark-v1.0.0.zip",
  "changelog": {
    "features": ["..."],
    "bugfixes": ["..."]
  }
}
```

When an update is applied:
1. New ZIP is downloaded and extracted to a temp folder
2. User data (`config.json`, `storage/`, `stats.json`, `logs/`) is copied over
3. Service restarts automatically
4. Page refreshes after ~10 seconds

---

## 📝 Changelog

### V1.0.0 (2026-08-26)
**Initial Public Release**

Features:
- Multi-account management with independent friend lists
- Web-based management panel with Apple-style glass UI
- Scheduled sending (global + per-account)
- QR code login with session persistence
- Friend list sync with streak days (🔥)
- Real-time browser screen view
- Remote login control (SMS/password from phone)
- One-click online update from GitHub
- Power save mode
- Screen blackout
- cpolar remote access integration
- iOS 26/27 wallpapers with device detection
- PWA support (add to home screen)
- First-run interactive tutorial
- Low performance mode for older computers

Bugfixes:
- Page shaking caused by DOM rebuild every 5 seconds
- Login verification taking 30+ seconds (now ~2 seconds)
- Sync friends not reporting login expiration
- Send message not reporting login expiration
- Log performance issues with innerHTML+=

---

## ⚠️ Disclaimer

- This tool is for personal use only
- Use at your own risk — automated messaging may violate Douyin's terms of service
- Do not use for spam or commercial purposes
- The developer is not responsible for any account bans or penalties
- Respect rate limits and use reasonable send intervals

---

## 👤 Developer

**@HuiYao_Digital**
- Douyin: [63799276514](https://www.douyin.com/user/MS4wLjABAAAAgYlwGrGUroyYL79iPEbVDKRVi-bBOieIYt2NyLz2x-y80ZIUrY3XT51s7cdSRaHV)
- GitHub: [huiyao0908](https://github.com/huiyao0908)

---

## 📄 License

This project is provided as-is for personal use. All rights reserved.
