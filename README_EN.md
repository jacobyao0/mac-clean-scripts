# Mac Clean Scripts

[中文](README.md) | English

A safe and comprehensive automatic cleaning script for macOS.

## ✨ Features

- 🔒 **Safety First**: Only deletes contents, preserves directory structures; skips running applications
- 🤖 **Fully Automatic**: Supports cron jobs, no manual intervention needed
- 📊 **Complete Logs**: Records every cleanup session

## 📁 Files

| Script | Purpose | Run Mode |
|--------|---------|----------|
| `auto-clean-safe` | Automatically cleans system cache, dev tools cache, app cache, etc. | Scheduled/Automatic |

## 🚀 Quick Start

### 1. Installation

```bash
# Clone the repository
git clone https://github.com/jacobyao0/mac-clean-scripts.git
cd mac-clean-scripts

# Copy to local bin directory
chmod +x auto-clean-safe
cp auto-clean-safe ~/.local/bin/
```

### 2. Manual Run

```bash
# Full automatic cleanup (safe, recommended for daily use)
auto-clean-safe
```

### 3. Setup Cron Job (Recommended)

```bash
# Edit crontab
crontab -e

# Add this line to run daily at 3 AM
0 3 * * * /Users/$USER/.local/bin/auto-clean-safe >> /Users/$USER/.cache/auto-clean.log 2>&1
```

## 📋 What Gets Cleaned

### auto-clean-safe

1. **Dev Tools Cache**: Homebrew, uv, npm, yarn, pnpm, CocoaPods, Gem
2. **System Temp Files**: Files older than 3 days
3. **App Cache**: Chrome, Safari, Firefox, VS Code, Spotify (skipped if running)
4. **Dev Environment**: Xcode DerivedData, Python `__pycache__`, Gradle
5. **Log Files**: Logs older than 30 days
6. **Container Apps**: WeChat, QQ, DingTalk, Feishu, Bob Translate, etc.
7. **VS Code Extensions**: Keeps latest version, removes old ones

## ⚙️ Configuration

### Change Keep Version Count

Edit `KEEP_COUNT` in `auto-clean-safe`:

```bash
KEEP_COUNT=1  # Keep latest N versions
```

### Add Custom Apps

Edit `CONTAINER_CACHES` array in `auto-clean-safe`:

```bash
CONTAINER_CACHES=(
    "bundle.id" "App Name"
    # Add your apps
)
```

## 📝 Log Location

```
~/.cache/auto-clean.log
```

## 🛡️ Safety Principles

1. **Only delete contents, preserve directory structure**
2. **Skip running applications automatically**
3. **Prefer official cleanup commands**
4. **Preserve login state** (Cookies)

## 📄 License

MIT License - See [LICENSE](LICENSE) file

## 🤝 Contributing

Issues and Pull Requests are welcome!
