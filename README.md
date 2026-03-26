# Mac Clean Scripts

中文 | [English](README_EN.md)

安全、全面的 Mac 系统自动清理脚本

## ✨ 特性

- 🔒 **安全优先**：只删内容保留目录结构，运行中的应用自动跳过
- 🤖 **全自动**：支持定时任务（cron），无需人工干预
- 📊 **完整日志**：记录每次清理详情

## 📁 文件说明

| 脚本 | 用途 | 运行方式 |
|------|------|----------|
| `auto-clean-safe` | 全自动清理系统缓存、开发工具缓存、应用缓存等 | 定时自动运行 |

## 🚀 快速开始

### 1. 安装

```bash
# 克隆仓库
git clone https://github.com/jacobyao0/mac-clean-scripts.git
cd mac-clean-scripts

# 复制到本地 bin 目录
chmod +x auto-clean-safe
cp auto-clean-safe ~/.local/bin/
```

### 2. 手动运行

```bash
# 全自动清理（安全，推荐每天运行）
auto-clean-safe
```

### 3. 设置定时任务（推荐）

```bash
# 编辑 crontab
crontab -e

# 添加每天凌晨 3 点自动运行
0 3 * * * /Users/$USER/.local/bin/auto-clean-safe >> /Users/$USER/.cache/auto-clean.log 2>&1
```

## 📋 清理内容

### auto-clean-safe 清理项

1. **开发工具缓存**：Homebrew、uv、npm、yarn、pnpm、CocoaPods、Gem
2. **系统临时文件**：3天以上的临时文件
3. **应用缓存**：Chrome、Safari、Firefox、VS Code、Spotify 等（不在运行时）
4. **开发环境**：Xcode DerivedData、Python `__pycache__`、Gradle
5. **日志文件**：30天以上的日志
6. **容器应用**：微信、QQ、钉钉、飞书、Bob 翻译等
7. **VS Code 插件**：保留最新版本，删除旧版本

## ⚙️ 配置

### 修改保留版本数

编辑 `auto-clean-safe`，修改 `KEEP_COUNT` 变量：

```bash
KEEP_COUNT=1  # 保留最新 N 个版本
```

### 自定义清理应用

编辑 `auto-clean-safe` 中的 `CONTAINER_CACHES` 数组，添加你想清理的应用：

```bash
CONTAINER_CACHES=(
    "bundle.id" "应用名称"
    # 添加你的应用
)
```

## 📝 日志位置

```
~/.cache/auto-clean.log
```

## 🛡️ 安全原则

1. **只删内容，保留目录结构**
2. **运行中的应用自动跳过**
3. **优先使用官方清理命令**
4. **保留登录状态**（Cookies）

## 📄 License

MIT License - 详见 [LICENSE](LICENSE) 文件

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！
