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
# <a name="get-started-using-visual-studio-code-with-windows-subsystem-for-linux"></a><span data-ttu-id="c86ed-104">使用适用于 Linux 的 Windows 子系统的 Visual Studio Code 入门</span><span class="sxs-lookup"><span data-stu-id="c86ed-104">Get started using Visual Studio Code with Windows Subsystem for Linux</span></span>

<span data-ttu-id="c86ed-105">Visual Studio Code 与远程 WSL 扩展一起使用，你可以直接从 VS Code 使用 WSL 作为你的全时开发环境。</span><span class="sxs-lookup"><span data-stu-id="c86ed-105">Visual Studio Code, along with the Remote - WSL extension, enables you to use WSL as your full-time development environment directly from VS Code.</span></span> <span data-ttu-id="c86ed-106">你可以：</span><span class="sxs-lookup"><span data-stu-id="c86ed-106">You can:</span></span>

* <span data-ttu-id="c86ed-107">在基于 Linux 的环境中进行开发</span><span class="sxs-lookup"><span data-stu-id="c86ed-107">develop in a Linux-based environment</span></span>
* <span data-ttu-id="c86ed-108">使用特定于 Linux 的工具链和实用工具</span><span class="sxs-lookup"><span data-stu-id="c86ed-108">use Linux-specific toolchains and utilities</span></span>
* <span data-ttu-id="c86ed-109">从 Windows 轻松运行和调试基于 Linux 的应用程序，同时保持对高效率工具（如 Outlook 和 Office）的访问</span><span class="sxs-lookup"><span data-stu-id="c86ed-109">run and debug your Linux-based applications from the comfort of Windows while maintaining access to productivity tools like Outlook and Office</span></span>
* <span data-ttu-id="c86ed-110">使用 VS Code 内置终端运行所选的 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="c86ed-110">use the VS Code built-in terminal to run your Linux distribution of choice</span></span>
* <span data-ttu-id="c86ed-111">利用[Intellisense 代码完成](https://code.visualstudio.com/docs/editor/intellisense)、 [linting](https://code.visualstudio.com/docs/python/linting)、[调试支持](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)、[代码片段](https://code.visualstudio.com/docs/editor/userdefinedsnippets)和[单元测试](https://code.visualstudio.com/docs/python/testing)等 VS Code 功能</span><span class="sxs-lookup"><span data-stu-id="c86ed-111">take advantage of VS Code features like [Intellisense code completion](https://code.visualstudio.com/docs/editor/intellisense), [linting](https://code.visualstudio.com/docs/python/linting), [debug support](https://code.visualstudio.com/docs/nodejs/nodejs-debugging), [code snippets](https://code.visualstudio.com/docs/editor/userdefinedsnippets), and [unit testing](https://code.visualstudio.com/docs/python/testing)</span></span>
* <span data-ttu-id="c86ed-112">通过 VS Code 的内置[Git 支持](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)轻松管理版本控制</span><span class="sxs-lookup"><span data-stu-id="c86ed-112">easily manage your version control with VS Code's built-in [Git support](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)</span></span>
* <span data-ttu-id="c86ed-113">直接在 WSL 项目上运行命令和 VS Code 扩展</span><span class="sxs-lookup"><span data-stu-id="c86ed-113">run commands and VS Code extensions directly on your WSL projects</span></span>
* <span data-ttu-id="c86ed-114">在 Linux 或已装载的 Windows filesystem 中编辑文件（例如/mnt/c），无需担心路径问题、二进制兼容性或其他跨操作系统挑战</span><span class="sxs-lookup"><span data-stu-id="c86ed-114">edit files in your Linux or mounted Windows filesystem (for example /mnt/c) without worrying about pathing issues, binary compatibility, or other cross-OS challenges</span></span>

## <a name="install-vs-code-and-the-remote-wsl-extension"></a><span data-ttu-id="c86ed-115">安装 VS Code 和远程 WSL 扩展</span><span class="sxs-lookup"><span data-stu-id="c86ed-115">Install VS Code and the Remote WSL extension</span></span>

* <span data-ttu-id="c86ed-116">访问[VS Code 安装 "页](https://code.visualstudio.com/download)，然后选择32或64位安装程序。</span><span class="sxs-lookup"><span data-stu-id="c86ed-116">Visit the [VS Code install page](https://code.visualstudio.com/download) and select the 32 or 64 bit installer.</span></span> <span data-ttu-id="c86ed-117">在 Windows 上安装 Visual Studio Code （不在 WSL 文件系统中安装）。</span><span class="sxs-lookup"><span data-stu-id="c86ed-117">Install Visual Studio Code on Windows (not in your WSL file system).</span></span>

* <span data-ttu-id="c86ed-118">当系统提示您在安装过程中**选择其他任务**时，请务必选中 "**添加到路径**" 选项，以便您可以使用代码命令轻松打开 WSL 中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c86ed-118">When prompted to **Select Additional Tasks** during installation, be sure to check the **Add to PATH** option so you can easily open a folder in WSL using the code command.</span></span>

* <span data-ttu-id="c86ed-119">安装[远程开发扩展包](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)。</span><span class="sxs-lookup"><span data-stu-id="c86ed-119">Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).</span></span> <span data-ttu-id="c86ed-120">除了远程 SSH 和远程容器扩展外，此扩展包还包括远程 WSL 扩展，使你能够打开容器、远程计算机或 WSL 中的任何文件夹。</span><span class="sxs-lookup"><span data-stu-id="c86ed-120">This extension pack includes the Remote - WSL extension, in addition to the Remote - SSH, and Remote - Containers extensions, enabling you to open any folder in a container, on a remote machine, or in WSL.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c86ed-121">若要安装 WSL 扩展，将需要[1.35 的发行](https://code.visualstudio.com/updates/v1_35)版本或更高版本 VS Code。</span><span class="sxs-lookup"><span data-stu-id="c86ed-121">In order to install the Remote-WSL extension, you will need the [1.35 May release](https://code.visualstudio.com/updates/v1_35) version or later of VS Code.</span></span> <span data-ttu-id="c86ed-122">建议不要在不使用 WSL 扩展的 VS Code 中使用 WSL，因为将失去对自动完成、调试、linting 等的支持。有趣的事实：此 WSL 扩展安装在 $HOME/.vscode-server/extensions。</span><span class="sxs-lookup"><span data-stu-id="c86ed-122">We do not recommend using WSL in VS Code without the Remote-WSL extension as you will lose support for auto-complete, debugging, linting, etc. Fun fact: this WSL extension is installed in $HOME/.vscode-server/extensions.</span></span>

## <a name="update-your-linux-distribution"></a><span data-ttu-id="c86ed-123">更新 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="c86ed-123">Update your Linux distribution</span></span>

<span data-ttu-id="c86ed-124">某些 WSL Linux 发行版缺少 VS Code 服务器启动所需的库。</span><span class="sxs-lookup"><span data-stu-id="c86ed-124">Some WSL Linux distributions are lacking libraries that are required by the VS Code server to start up.</span></span> <span data-ttu-id="c86ed-125">可以通过使用包管理器将其他库添加到 Linux 分发中。</span><span class="sxs-lookup"><span data-stu-id="c86ed-125">You can add additional libraries into your Linux distribution by using its package manager.</span></span>

<span data-ttu-id="c86ed-126">例如，若要更新 Debian 或 Ubuntu，请使用：</span><span class="sxs-lookup"><span data-stu-id="c86ed-126">For example, to update Debian or Ubuntu, use:</span></span>

```bash
sudo apt-get update
```

<span data-ttu-id="c86ed-127">若要添加 wget （从 web 服务器检索内容）和 ca 证书（以允许基于 SSL 的应用程序检查 SSL 连接的真实性），请输入：</span><span class="sxs-lookup"><span data-stu-id="c86ed-127">To add wget (to retrieve content from web servers) and ca-certificates (to allow SSL-based applications to check for the authenticity of SSL connections), enter:</span></span>

```bash
sudo apt-get install wget ca-certificates
```

## <a name="open-a-wsl-project-in-visual-studio-code"></a><span data-ttu-id="c86ed-128">在 Visual Studio Code 中打开 WSL 项目</span><span class="sxs-lookup"><span data-stu-id="c86ed-128">Open a WSL project in Visual Studio Code</span></span>

### <a name="from-the-command-line"></a><span data-ttu-id="c86ed-129">从命令行</span><span class="sxs-lookup"><span data-stu-id="c86ed-129">From the command-line</span></span>

<span data-ttu-id="c86ed-130">若要从 WSL 分发打开项目，请打开分发的命令行并输入以下命令：`code .`</span><span class="sxs-lookup"><span data-stu-id="c86ed-130">To open a project from your WSL distribution, open the distribution's command line and enter: `code .`</span></span>

![VS Code 远程服务器打开 WSL 项目](../media/wsl-open-vs-code.gif)

### <a name="from-vs-code"></a><span data-ttu-id="c86ed-132">From VS Code</span><span class="sxs-lookup"><span data-stu-id="c86ed-132">From VS Code</span></span>

<span data-ttu-id="c86ed-133">你还可以使用快捷方式访问更多 VS Code 远程选项： `CTRL+SHIFT+P` 在 VS Code 中打开命令面板。</span><span class="sxs-lookup"><span data-stu-id="c86ed-133">You can also access more VS Code Remote options by using the shortcut: `CTRL+SHIFT+P` in VS Code to bring up the command palette.</span></span> <span data-ttu-id="c86ed-134">如果随后键入，您 `VSCODE-REMOTE` 将看到所有可用的 VS Code 远程选项，允许您在远程会话中重新打开该文件夹，指定要在其中打开的分发，等等。</span><span class="sxs-lookup"><span data-stu-id="c86ed-134">If you then type `VSCODE-REMOTE` you will see all of the VS Code Remote options available, allowing you to reopen the folder in a remote session, specify which distribution you want to open in, and more.</span></span>

![VS Code 的命令面板](../media/vscode-remote-command-palette.png)

## <a name="extensions-inside-of-vs-code-remote"></a><span data-ttu-id="c86ed-136">VS Code 远程中的扩展</span><span class="sxs-lookup"><span data-stu-id="c86ed-136">Extensions inside of VS Code Remote</span></span>

<span data-ttu-id="c86ed-137">远程 WSL 扩展将 VS Code 拆分为 "客户端-服务器" 体系结构，并在 Windows 计算机上运行的客户端（用户界面）以及远程运行的服务器（你的代码、Git、插件等）运行客户端（用户界面）。</span><span class="sxs-lookup"><span data-stu-id="c86ed-137">The Remote-WSL extension splits VS Code into a “client-server” architecture, with the client (the user interface) running on your Windows machine and the server (your code, Git, plugins, etc) running remotely.</span></span>

<span data-ttu-id="c86ed-138">VS Code 远程运行时，选择 "扩展" 选项卡将显示本地计算机与 WSL 分发之间剥离的扩展的列表。</span><span class="sxs-lookup"><span data-stu-id="c86ed-138">When running VS Code Remote, selecting the 'Extensions' tab will display a list of extensions split between your local machine and your WSL distribution.</span></span>

<span data-ttu-id="c86ed-139">安装本地扩展（如[主题](https://marketplace.visualstudio.com/search?target=VSCode&category=Themes&sortBy=Installs)）只需安装一次。</span><span class="sxs-lookup"><span data-stu-id="c86ed-139">Installing a local extension, like a [theme](https://marketplace.visualstudio.com/search?target=VSCode&category=Themes&sortBy=Installs),  only needs to be installed once.</span></span>

<span data-ttu-id="c86ed-140">某些扩展（如[Python 扩展](https://marketplace.visualstudio.com/items?itemName=ms-python.python)）或处理 linting 或调试等内容的任何内容必须在每个远程 WSL 分发上单独安装。</span><span class="sxs-lookup"><span data-stu-id="c86ed-140">Some extensions, like the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) or anything that handles things like linting or debugging, must be installed separately on each remote WSL distributions.</span></span> <span data-ttu-id="c86ed-141">⚠如果本地安装的扩展未安装在 WSL Remote 上，VS Code 将显示一个警告图标以及绿色的 "安装在 WSL" 按钮。</span><span class="sxs-lookup"><span data-stu-id="c86ed-141">VS Code will display a warning icon ⚠, along with a green "Install in WSL" button, if you have an extension locally installed that is not installed on your WSL Remote.</span></span>

![VS Code 与 WSL extension vs local extension](../media/vscode-remote-wsl-extensions.png)

<span data-ttu-id="c86ed-143">有关详细信息，请参阅 VS Code 文档：</span><span class="sxs-lookup"><span data-stu-id="c86ed-143">For further information, see the VS Code docs:</span></span>

* <span data-ttu-id="c86ed-144">在 WSL 中启动 VS Code Remote 时，将不运行任何 shell 启动脚本。</span><span class="sxs-lookup"><span data-stu-id="c86ed-144">When VS Code Remote is started in WSL, no shell startup scripts are run.</span></span> <span data-ttu-id="c86ed-145">有关如何运行其他命令或修改环境的详细信息，请参阅此[高级环境安装脚本一文](https://code.visualstudio.com/docs/remote/wsl#_advanced-environment-setup-script)。</span><span class="sxs-lookup"><span data-stu-id="c86ed-145">See this [advanced environment setup script article](https://code.visualstudio.com/docs/remote/wsl#_advanced-environment-setup-script) for more info on how to run additional commands or modify the environment.</span></span>

* <span data-ttu-id="c86ed-146">从 WSL 命令行启动 VS Code 时遇到问题？</span><span class="sxs-lookup"><span data-stu-id="c86ed-146">Having problems launching VS Code from your WSL command line?</span></span> <span data-ttu-id="c86ed-147">此[故障排除指南](https://code.visualstudio.com/docs/remote/troubleshooting#_fixing-problems-with-the-code-command-not-working)包含有关更改路径变量、解决有关缺失依赖项的扩展错误、解决 Git 行结束问题、在远程计算机上安装本地 VSIX、启动浏览器窗口、阻止 localhost 端口、web socket 不工作、存储扩展数据错误等的提示。</span><span class="sxs-lookup"><span data-stu-id="c86ed-147">This [troubleshooting guide](https://code.visualstudio.com/docs/remote/troubleshooting#_fixing-problems-with-the-code-command-not-working) includes tips on changing path variables, resolving extension errors about missing dependencies, resolving Git line ending issues, installing a local VSIX on a remote machine, launching a browser window, blocker localhost port, web sockets not working, errors storing extension data, and more.</span></span>

## <a name="install-git-optional"></a><span data-ttu-id="c86ed-148">安装 Git（可选）</span><span class="sxs-lookup"><span data-stu-id="c86ed-148">Install Git (optional)</span></span>

<span data-ttu-id="c86ed-149">如果计划与其他人协作，或是在开放源代码站点（如 GitHub）上托管项目，则 VS Code 支持[使用 Git 进行版本控制](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)。</span><span class="sxs-lookup"><span data-stu-id="c86ed-149">If you plan to collaborate with others, or host your project on an open-source site (like GitHub), VS Code supports [version control with Git](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).</span></span> <span data-ttu-id="c86ed-150">VS Code 中的“源代码管理”选项卡可跟踪所有更改，并直接在 UI 中内置了常见 Git 命令（add、commit、push、pull）。</span><span class="sxs-lookup"><span data-stu-id="c86ed-150">The Source Control tab in VS Code tracks all of your changes and has common Git commands (add, commit, push, pull) built right into the UI.</span></span>

<span data-ttu-id="c86ed-151">若要安装 Git，请参阅[设置 git 以使用适用于 Linux 的 Windows 子系统](./wsl-git.md)。</span><span class="sxs-lookup"><span data-stu-id="c86ed-151">To install Git, see [set up Git to work with Windows Subsystem for Linux](./wsl-git.md).</span></span>

## <a name="install-windows-terminal-optional"></a><span data-ttu-id="c86ed-152">安装 Windows 终端（可选）</span><span class="sxs-lookup"><span data-stu-id="c86ed-152">Install Windows Terminal (optional)</span></span>

<span data-ttu-id="c86ed-153">新的 Windows 终端启用多个选项卡（在命令提示符、PowerShell 或多个 Linux 分发之间快速切换）、自定义密钥绑定（创建自己的快捷键以打开或关闭选项卡、复制 + 粘贴等）、表情符号☺和自定义主题（配色方案、字体样式和大小、背景图像/模糊/透明度）。</span><span class="sxs-lookup"><span data-stu-id="c86ed-153">The new Windows Terminal enables multiple tabs (quickly switch between Command Prompt, PowerShell, or multiple Linux distributions), custom key bindings (create your own shortcut keys for opening or closing tabs, copy+paste, etc.), emojis ☺, and custom themes (color schemes, font styles and sizes, background image/blur/transparency).</span></span> <span data-ttu-id="c86ed-154">在[Windows 终端文档](https://docs.microsoft.com/windows/terminal)中了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="c86ed-154">Learn more in the [Windows Terminal docs](https://docs.microsoft.com/windows/terminal).</span></span>

1. <span data-ttu-id="c86ed-155">获取[Microsoft Store 中的 Windows 终端](https://www.microsoft.com/store/apps/9n0dx20hk701)：通过应用商店进行安装，将自动处理更新。</span><span class="sxs-lookup"><span data-stu-id="c86ed-155">Get [Windows Terminal in the Microsoft Store](https://www.microsoft.com/store/apps/9n0dx20hk701): By installing via the store, updates are handled automatically.</span></span>

2. <span data-ttu-id="c86ed-156">安装完成后，打开 Windows 终端并选择“设置”以使用 `profile.json` 文件自定义终端。</span><span class="sxs-lookup"><span data-stu-id="c86ed-156">Once installed, open Windows Terminal and select **Settings** to customize your terminal using the `profile.json` file.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c86ed-157">其他资源</span><span class="sxs-lookup"><span data-stu-id="c86ed-157">Additional Resources</span></span>

* [<span data-ttu-id="c86ed-158">VS Code 远程开发</span><span class="sxs-lookup"><span data-stu-id="c86ed-158">VS Code Remote Development</span></span>](https://code.visualstudio.com/docs/remote/remote-overview)
* [<span data-ttu-id="c86ed-159">远程开发提示和技巧</span><span class="sxs-lookup"><span data-stu-id="c86ed-159">Remote development tips and tricks</span></span>](https://code.visualstudio.com/docs/remote/troubleshooting)
* [<span data-ttu-id="c86ed-160">通过 WSL 的远程开发教程</span><span class="sxs-lookup"><span data-stu-id="c86ed-160">Remote development with WSL tutorial</span></span>](https://code.visualstudio.com/remote-tutorials/wsl/getting-started)
* [<span data-ttu-id="c86ed-161">将 Docker 与 WSL 2 和 VS Code 一起使用</span><span class="sxs-lookup"><span data-stu-id="c86ed-161">Using Docker with WSL 2 and VS Code</span></span>](https://code.visualstudio.com/blogs/2020/03/02/docker-in-wsl2)
* [<span data-ttu-id="c86ed-162">在 VS Code 中使用 c + + 和 WSL</span><span class="sxs-lookup"><span data-stu-id="c86ed-162">Using C++ and WSL in VS Code</span></span>](https://code.visualstudio.com/docs/cpp/config-wsl)
* [<span data-ttu-id="c86ed-163">适用于 Linux 的远程 R 服务</span><span class="sxs-lookup"><span data-stu-id="c86ed-163">Remote R Service for Linux</span></span>](https://docs.microsoft.com/visualstudio/rtvs/setting-up-remote-r-service-on-linux?view=vs-2017)

<span data-ttu-id="c86ed-164">可能需要考虑的几个附加扩展包括：</span><span class="sxs-lookup"><span data-stu-id="c86ed-164">A few additional extensions you may want to consider include:</span></span>

* <span data-ttu-id="c86ed-165">[来自其他编辑器的键映射](https://marketplace.visualstudio.com/search?target=VSCode&category=Keymaps&sortBy=Downloads)：如果是从另一个文本编辑器（如 Atom、Sublime、Vim、eMacs、Notepad++ 等）进行转换，则这些扩展可帮助你的环境对此进行适应。</span><span class="sxs-lookup"><span data-stu-id="c86ed-165">[Keymaps from other editors](https://marketplace.visualstudio.com/search?target=VSCode&category=Keymaps&sortBy=Downloads): These extensions can help your environment feel right at home if you're transitioning from another text editor (like Atom, Sublime, Vim, eMacs, Notepad++, etc).</span></span>
* <span data-ttu-id="c86ed-166">[设置同步](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)：可以使用 GitHub 在不同安装之间同步 VS Code 设置。</span><span class="sxs-lookup"><span data-stu-id="c86ed-166">[Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync): Enables you to synchronize your VS Code settings across different installations using GitHub.</span></span> <span data-ttu-id="c86ed-167">如果在不同的计算机上工作，这有助于在它们之间保持一致的环境。</span><span class="sxs-lookup"><span data-stu-id="c86ed-167">If you work on different machines, this helps keep your environment consistent across them.</span></span>
* <span data-ttu-id="c86ed-168">[适用于 Chrome 的调试器](https://code.visualstudio.com/blogs/2016/02/23/introducing-chrome-debugger-for-vs-code)：在服务器端通过 Linux 进行开发后，需要开发并测试客户端。</span><span class="sxs-lookup"><span data-stu-id="c86ed-168">[Debugger for Chrome](https://code.visualstudio.com/blogs/2016/02/23/introducing-chrome-debugger-for-vs-code): Once you finish developing on the server side with Linux, you'll need to develop and test the client side.</span></span> <span data-ttu-id="c86ed-169">此扩展将 VS Code 编辑器与 Chrome 浏览器调试服务进行集成，以提高工作效率。</span><span class="sxs-lookup"><span data-stu-id="c86ed-169">This extension integrates your VS Code editor with your Chrome browser debugging service, making things a bit more efficient.</span></span>
