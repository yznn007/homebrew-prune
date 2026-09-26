[English](README.md) | 简体中文

# Homebrew Prune

手动删除 Mac 上的 App 后，Homebrew 有时还会保留对应的 Cask 登记。之后执行 `brew upgrade`，可能会提示 `.app` 文件不存在。

这个 tap 只有一个小脚本，用来清理这类 Cask 登记残留。脚本会先列出候选项，等你确认后再让 Homebrew 卸载。一个脚本，一条清理命令：

```sh
brew prune
```

## 快速使用

首次使用时添加 tap，并信任其中的 `prune` 命令：

```sh
brew tap yznn007/prune
brew trust --command yznn007/prune/prune
```

这一步只信任此 tap 的 `prune` 命令。

之后运行：

```sh
brew prune
```

脚本会列出所有声明的 App 路径都已缺失的已安装 Cask。确认前请检查清单中的名称和路径。输入 `y` 或 `yes` 继续；直接按回车会取消。

确认后，脚本会对清单中的每个 Cask 运行 `brew uninstall --cask --force`。Homebrew 也可能执行该 Cask 声明的卸载动作。脚本不使用 `--zap`。

## 注意事项

如果 App 被移到了其他目录，或所在的外接磁盘暂时未连接，它也可能显示为缺失。确认前请检查候选清单。

## 运行要求

macOS、Homebrew 和 Python 3.9 或更新版本；无需安装额外 Python 包。

## 许可证

本项目采用 [MIT License](LICENSE)。
