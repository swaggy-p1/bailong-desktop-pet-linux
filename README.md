# Bailong Desktop Pet Linux

Linux 适配版：透明动态桌宠，支持互动、拖动、托盘菜单、可选 Codex 对话和登录自启动。原项目作者为 GitHub 账号 `jingh12312-rgb`，原仓库见 https://github.com/jingh12312-rgb/bailong-desktop-pet。

## 快速部署

### 1. 安装系统依赖

Ubuntu/Debian：

```bash
sudo apt update
sudo apt install python3 python3-venv libxcb-cursor0 libxcb-xinerama0
```

### 2. 解压并安装

从 [v0.1.0 Release](https://github.com/swaggy-p1/bailong-desktop-pet-linux/releases/tag/v0.1.0) 下载 `bailong-desktop-pet-linux-x86_64-v0.1.0.tar.gz`，然后：

```bash
tar -xzf bailong-desktop-pet-linux-x86_64-v0.1.0.tar.gz
cd BailongPetLinux
./install-linux.sh
```

安装脚本会在项目目录创建 `.venv`，安装 PySide6/Pillow/psutil，并为当前用户开启登录自启动。首次安装需要网络访问 PyPI 镜像。

### 3. 手动启动

```bash
./run-bailong-pet.sh
```

启动后可以单击互动、双击查询额度、按住左键拖动，右键打开菜单。离线互动不需要 Codex 账号；对话和额度查询需要本机已登录 Codex。

## Codex 路径配置

如果 `codex` 不在登录会话的 `PATH` 中：

```bash
export BAILONG_CODEX=/absolute/path/to/codex
./run-bailong-pet.sh
```

## 关闭自启动和卸载

```bash
./uninstall-linux.sh
```

它只移除 `~/.config/autostart/BailongPet.desktop` 和应用菜单入口，不删除项目目录或本地历史文件。

## 常见问题

- Qt 报 `could not connect to display`：请在图形桌面会话中运行，不要在纯 SSH 终端中运行。
- Qt 报缺少 `xcb-cursor`：安装 `libxcb-cursor0 libxcb-xinerama0`。
- 找不到 Codex：检查 `command -v codex`，或设置 `BAILONG_CODEX`。
- 首次启动较慢：程序会预加载完整动画帧，并占用较多内存，这是正常现象。

## 归属和素材许可

详细说明见 [ATTRIBUTION.md](ATTRIBUTION.md)，完整部署细节见 [DEPLOYMENT.md](DEPLOYMENT.md)。原项目角色美术和源码授权以原作者发布说明为准，本适配不扩展其商用或再分发许可。
