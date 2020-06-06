---
title: 使用适用于 Linux 的 Windows 子系统的 VS Code 入门
description: 了解如何使用适用于 Linux 的 Windows 子系统设置 VS Code 来创作和调试代码。
keywords: wsl，windows，windowssubsystem，gnu，linux，bash，vs code，远程扩展，调试，路径，visual studio
ms.date: 05/28/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 416862201094ba28474918dca8e7d9ce316844cc
ms.sourcegitcommit: d95bdbc2fea991ba14a4c9ec53ee0ec19d6bbdb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84457779"
---
# <a name="get-started-using-visual-studio-code-with-windows-subsystem-for-linux"></a>使用适用于 Linux 的 Windows 子系统的 Visual Studio Code 入门

Visual Studio Code 与远程 WSL 扩展一起使用，你可以直接从 VS Code 使用 WSL 作为你的全时开发环境。 你可以：

* 在基于 Linux 的环境中进行开发
* 使用特定于 Linux 的工具链和实用工具
* 从 Windows 轻松运行和调试基于 Linux 的应用程序，同时保持对高效率工具（如 Outlook 和 Office）的访问
* 使用 VS Code 内置终端运行所选的 Linux 分发版
* 利用[Intellisense 代码完成](https://code.visualstudio.com/docs/editor/intellisense)、 [linting](https://code.visualstudio.com/docs/python/linting)、[调试支持](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)、[代码片段](https://code.visualstudio.com/docs/editor/userdefinedsnippets)和[单元测试](https://code.visualstudio.com/docs/python/testing)等 VS Code 功能
* 通过 VS Code 的内置[Git 支持](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)轻松管理版本控制
* 直接在 WSL 项目上运行命令和 VS Code 扩展
* 在 Linux 或已装载的 Windows filesystem 中编辑文件（例如/mnt/c），无需担心路径问题、二进制兼容性或其他跨操作系统挑战

## <a name="install-vs-code-and-the-remote-wsl-extension"></a>安装 VS Code 和远程 WSL 扩展

* 访问[VS Code 安装 "页](https://code.visualstudio.com/download)，然后选择32或64位安装程序。 在 Windows 上安装 Visual Studio Code （不在 WSL 文件系统中安装）。

* 当系统提示您在安装过程中**选择其他任务**时，请务必选中 "**添加到路径**" 选项，以便您可以使用代码命令轻松打开 WSL 中的文件夹。

* 安装[远程开发扩展包](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)。 除了远程 SSH 和远程容器扩展外，此扩展包还包括远程 WSL 扩展，使你能够打开容器、远程计算机或 WSL 中的任何文件夹。

> [!IMPORTANT]
> 若要安装 WSL 扩展，将需要[1.35 的发行](https://code.visualstudio.com/updates/v1_35)版本或更高版本 VS Code。 建议不要在不使用 WSL 扩展的 VS Code 中使用 WSL，因为将失去对自动完成、调试、linting 等的支持。有趣的事实：此 WSL 扩展安装在 $HOME/.vscode-server/extensions。

## <a name="update-your-linux-distribution"></a>更新 Linux 分发版

某些 WSL Linux 发行版缺少 VS Code 服务器启动所需的库。 可以通过使用包管理器将其他库添加到 Linux 分发中。

例如，若要更新 Debian 或 Ubuntu，请使用：

```bash
sudo apt-get update
```

若要添加 wget （从 web 服务器检索内容）和 ca 证书（以允许基于 SSL 的应用程序检查 SSL 连接的真实性），请输入：

```bash
sudo apt-get install wget ca-certificates
```

## <a name="open-a-wsl-project-in-visual-studio-code"></a>在 Visual Studio Code 中打开 WSL 项目

### <a name="from-the-command-line"></a>从命令行

若要从 WSL 分发打开项目，请打开分发的命令行并输入以下命令：`code .`

![VS Code 远程服务器打开 WSL 项目](../media/wsl-open-vs-code.gif)

### <a name="from-vs-code"></a>From VS Code

你还可以使用快捷方式访问更多 VS Code 远程选项： `CTRL+SHIFT+P` 在 VS Code 中打开命令面板。 如果随后键入，您 `VSCODE-REMOTE` 将看到所有可用的 VS Code 远程选项，允许您在远程会话中重新打开该文件夹，指定要在其中打开的分发，等等。

![VS Code 的命令面板](../media/vscode-remote-command-palette.png)

## <a name="extensions-inside-of-vs-code-remote"></a>VS Code 远程中的扩展

远程 WSL 扩展将 VS Code 拆分为 "客户端-服务器" 体系结构，并在 Windows 计算机上运行的客户端（用户界面）以及远程运行的服务器（你的代码、Git、插件等）运行客户端（用户界面）。

VS Code 远程运行时，选择 "扩展" 选项卡将显示本地计算机与 WSL 分发之间剥离的扩展的列表。

安装本地扩展（如[主题](https://marketplace.visualstudio.com/search?target=VSCode&category=Themes&sortBy=Installs)）只需安装一次。

某些扩展（如[Python 扩展](https://marketplace.visualstudio.com/items?itemName=ms-python.python)）或处理 linting 或调试等内容的任何内容必须在每个远程 WSL 分发上单独安装。 ⚠如果本地安装的扩展未安装在 WSL Remote 上，VS Code 将显示一个警告图标以及绿色的 "安装在 WSL" 按钮。

![VS Code 与 WSL extension vs local extension](../media/vscode-remote-wsl-extensions.png)

有关详细信息，请参阅 VS Code 文档：

* 在 WSL 中启动 VS Code Remote 时，将不运行任何 shell 启动脚本。 有关如何运行其他命令或修改环境的详细信息，请参阅此[高级环境安装脚本一文](https://code.visualstudio.com/docs/remote/wsl#_advanced-environment-setup-script)。

* 从 WSL 命令行启动 VS Code 时遇到问题？ 此[故障排除指南](https://code.visualstudio.com/docs/remote/troubleshooting#_fixing-problems-with-the-code-command-not-working)包含有关更改路径变量、解决有关缺失依赖项的扩展错误、解决 Git 行结束问题、在远程计算机上安装本地 VSIX、启动浏览器窗口、阻止 localhost 端口、web socket 不工作、存储扩展数据错误等的提示。

## <a name="install-git-optional"></a>安装 Git（可选）

如果计划与其他人协作，或是在开放源代码站点（如 GitHub）上托管项目，则 VS Code 支持[使用 Git 进行版本控制](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)。 VS Code 中的“源代码管理”选项卡可跟踪所有更改，并直接在 UI 中内置了常见 Git 命令（add、commit、push、pull）。

若要安装 Git，请参阅[设置 git 以使用适用于 Linux 的 Windows 子系统](./wsl-git.md)。

## <a name="install-windows-terminal-optional"></a>安装 Windows 终端（可选）

新的 Windows 终端启用多个选项卡（在命令提示符、PowerShell 或多个 Linux 分发之间快速切换）、自定义密钥绑定（创建自己的快捷键以打开或关闭选项卡、复制 + 粘贴等）、表情符号☺和自定义主题（配色方案、字体样式和大小、背景图像/模糊/透明度）。 在[Windows 终端文档](https://docs.microsoft.com/windows/terminal)中了解详细信息。

1. 获取[Microsoft Store 中的 Windows 终端](https://www.microsoft.com/store/apps/9n0dx20hk701)：通过应用商店进行安装，将自动处理更新。

2. 安装完成后，打开 Windows 终端并选择“设置”以使用 `profile.json` 文件自定义终端。

## <a name="additional-resources"></a>其他资源

* [VS Code 远程开发](https://code.visualstudio.com/docs/remote/remote-overview)
* [远程开发提示和技巧](https://code.visualstudio.com/docs/remote/troubleshooting)
* [通过 WSL 的远程开发教程](https://code.visualstudio.com/remote-tutorials/wsl/getting-started)
* [将 Docker 与 WSL 2 和 VS Code 一起使用](https://code.visualstudio.com/blogs/2020/03/02/docker-in-wsl2)
* [在 VS Code 中使用 c + + 和 WSL](https://code.visualstudio.com/docs/cpp/config-wsl)
* [适用于 Linux 的远程 R 服务](https://docs.microsoft.com/visualstudio/rtvs/setting-up-remote-r-service-on-linux?view=vs-2017)

可能需要考虑的几个附加扩展包括：

* [来自其他编辑器的键映射](https://marketplace.visualstudio.com/search?target=VSCode&category=Keymaps&sortBy=Downloads)：如果是从另一个文本编辑器（如 Atom、Sublime、Vim、eMacs、Notepad++ 等）进行转换，则这些扩展可帮助你的环境对此进行适应。
* [设置同步](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)：可以使用 GitHub 在不同安装之间同步 VS Code 设置。 如果在不同的计算机上工作，这有助于在它们之间保持一致的环境。
* [适用于 Chrome 的调试器](https://code.visualstudio.com/blogs/2016/02/23/introducing-chrome-debugger-for-vs-code)：在服务器端通过 Linux 进行开发后，需要开发并测试客户端。 此扩展将 VS Code 编辑器与 Chrome 浏览器调试服务进行集成，以提高工作效率。
