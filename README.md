# 🔥 Douyin Spark Auto-Sender

自动发送抖音好友消息，维持火花。支持多账号、Web管理面板、定时发送、一键更新。

![Version](https://img.shields.io/badge/version-V1.0.3-brightgreen)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-green)
![Python](https://img.shields.io/badge/python-3.8+-yellow)

---

## ✨ 功能

- **多账号管理** — 无限账号，各自独立好友列表和定时
- **Web管理面板** — 浏览器控制一切（手机/电脑都行）
- **定时发送** — 全局定时或每账号独立定时
- **扫码登录** — 扫码登录，重启不掉线
- **好友同步** — 自动抓取好友列表和火花天数（🔥）
- **实时画面** — 任务运行时实时看浏览器
- **远程登录控制** — 手机上输验证码/密码
- **一键更新** — 面板里直接检查并安装更新
- **省电模式** — 自动关后台进程降CPU/内存
- **黑屏** — 一键关显示器电源
- **远程访问** — 内网穿透，外网也能访问
- **毛玻璃UI** — iOS风格界面

---

## 📥 下载

| 平台 | 下载地址 |
|------|----------|
| **Windows 10/11** | [douyin-spark-v1.0.3-windows.zip](https://github.com/huiyao0908/douyin-spark-updates/raw/main/douyin-spark-v1.0.3-windows.zip) |
| **Linux / WSL** | [douyin-spark-v1.0.3-linux.zip](https://github.com/huiyao0908/douyin-spark-updates/raw/main/douyin-spark-v1.0.3-linux.zip) |

---

## 🚀 快速开始

### Windows
1. 下载上面的 Windows zip，解压
2. 双击 **`一键部署.bat`**
3. 等它装完依赖，自动打开面板 `http://127.0.0.1:5000`

### Linux / WSL
```bash
# 解压
unzip douyin-spark-v1.0.3-linux.zip
cd douyin-spark

# 装依赖
pip3 install -r requirements.txt
playwright install chromium

# 启动
python3 app.py

# 后台常驻（systemd）
# 参考下方 systemd 配置
```

WSL 一键部署：
```bash
sudo cp douyin-spark.service /etc/systemd/system/
sudo systemctl enable --now douyin-spark
```

---

## 📖 使用

### 1. 加账号
- 点 **"+ 加账号"**
- 点 **"扫码登录"**，用抖音扫码
- 二次验证用远程控制面板输验证码/密码

### 2. 同步好友
- 点 **"同步好友"**
- 选要续火花的好友，点 **"导入所选"**

### 3. 设消息
- 点 **"编辑"**，输入自定义消息
- 自动带时间戳和火花计数

### 4. 设定时
- 点 **"定时设置"**
- 全局时间（如 00:30）或每账号独立时间

### 5. 测试发送
- 点 **"发送"** 测试单个账号
- 点 **"全部发送"** 发所有启用账号

### 6. 检查更新
- 点 **"更多工具" → "检查更新"**
- 有新版点 **"立即更新"**
- 账号、登录态、设置都保留

---

## 🔄 自动更新

工具自动从以下地址检查更新（三源轮询，国内可用）：
1. jsDelivr CDN
2. GitHub raw
3. ghproxy 镜像

更新时自动保留：
- `config.json`（配置）
- `storage/`（登录态）
- `stats.json`（统计）
- `logs/`（日志）

Windows 更新包和 Linux 更新包分开，自动识别平台下载对应版本。

---

## 🌐 远程访问

### 同一WiFi
手机访问 `http://<电脑IP>:5000`

### 外网
面板里点 **"更多工具" → "手机连接"**，启用内网穿透。

---

## ⚠️ 注意

- 本工具仅供个人使用
- 自动化发消息可能违反抖音条款，风险自负
- 不要用于刷屏或商业用途
- 尊重频率限制，合理间隔

---

## 👤 开发者

**@HuiYao_Digital**
- 抖音: [63799276514](https://www.douyin.com/user/MS4wLjABAAAAgYlwGrGUroyYL79iPEbVDKRVi-bBOieIYt2NyLz2x-y80ZIUrY3XT51s7cdSRaHV)
- GitHub: [huiyao0908](https://github.com/huiyao0908)
