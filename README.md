# Mac Clean Scripts

安全、全面的 Mac 系统自动清理脚本集合

## ✨ 特性

- 🔒 **安全优先**：只删内容保留目录结构，运行中的应用自动跳过
- 🤖 **全自动**：支持定时任务（cron），无需人工干预
- 🎯 **精细管理**：交互式管理 Kimi CLI 会话
- 📊 **完整日志**：记录每次清理详情

## 📁 文件说明

| 脚本 | 用途 | 运行方式 |
|------|------|----------|
| `auto-clean-safe` | 全自动清理系统缓存、开发工具缓存、应用缓存等 | 定时自动运行 |
| `kimi-clean` | 交互式管理 Kimi CLI 有效会话 | 手动运行 |

## 🚀 快速开始

### 1. 安装

```bash
# 克隆仓库
git clone https://github.com/YOUR_USERNAME/mac-clean-scripts.git
cd mac-clean-scripts

# 复制到本地 bin 目录
chmod +x auto-clean-safe kimi-clean
cp auto-clean-safe kimi-clean ~/.local/bin/
```

### 2. 手动运行

```bash
# 全自动清理（安全，推荐每天运行）
auto-clean-safe

# 交互式管理 Kimi 会话
kimi-clean
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
6. **Kimi CLI**：空会话、空文件、临时图片、App 缓存
7. **容器应用**：微信、QQ、钉钉、飞书、Bob 翻译等
8. **VS Code 插件**：保留最新版本，删除旧版本

### kimi-clean 功能

- 查看有效 Kimi 会话列表（显示标题、大小、时间）
- 交互式选择删除特定会话
- 支持批量删除（输入 `all`）

## ⚙️ 配置

### 修改保留版本数

编辑 `auto-clean-safe`，修改第 374 行：

```bash
KEEP_COUNT=1  # 保留最新 N 个版本
```

### 自定义清理应用

编辑 `auto-clean-safe` 第 314-336 行的 `CONTAINER_CACHES` 数组：

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
