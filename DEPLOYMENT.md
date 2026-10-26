# Linux 部署说明

## 1. 安装系统依赖

Ubuntu/Debian 可执行：

```bash
sudo apt install python3 python3-venv libxcb-cursor0 libxcb-xinerama0
```

桌宠使用 PySide6、Pillow 和 psutil。安装脚本会在项目目录创建隔离的 `.venv`，不替换系统 Python。

## 2. 安装并开启登录自启动

解压 Release 包后运行：

```bash
cd BailongPetLinux
./install-linux.sh
```

脚本会安装 Linux 依赖、创建应用菜单入口，并写入当前用户的：

```text
~/.config/autostart/BailongPet.desktop
```

## 3. 手动启动

```bash
./run-bailong-pet.sh
```

桌宠支持透明动画、互动、拖动、托盘菜单和可选 Codex 对话。对话和额度查询需要本机可用并已登录的 Codex；离线互动不需要账号。

## 4. 关闭自启动和卸载

```bash
./uninstall-linux.sh
```

该命令只移除用户级自启动和应用菜单入口，不删除项目目录或本地历史文件。

## 5. 指定 Codex 路径

如果 `codex` 不在登录会话的 `PATH` 中，可在启动前设置：

```bash
export BAILONG_CODEX=/absolute/path/to/codex
./run-bailong-pet.sh
```
