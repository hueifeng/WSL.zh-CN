---
title: 在 Windows Server 上安装 Linux 子系统
description: Windows Server 上的 Linux 子系统的安装说明。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, windows server
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 805b7d266020c62e0c6f58889541517d44db3726
ms.sourcegitcommit: 90f7caeefe886bf6c0ba2b90c1b56b5f9795ad1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84153080"
---
# <a name="windows-server-installation-guide"></a><span data-ttu-id="e924c-104">Windows Server 安装指南</span><span class="sxs-lookup"><span data-stu-id="e924c-104">Windows Server Installation Guide</span></span>

<span data-ttu-id="e924c-105">适用于 Linux 的 Windows 子系统可供在 Windows Server 2019（版本 1709）和更高版本上安装。</span><span class="sxs-lookup"><span data-stu-id="e924c-105">The Windows Subsystem for Linux is available for installation on Windows Server 2019 (version 1709) and later.</span></span> <span data-ttu-id="e924c-106">本指南将指导你完成在计算机上启用 WSL 的步骤。</span><span class="sxs-lookup"><span data-stu-id="e924c-106">This guide will walk through the steps of enabling WSL on your machine.</span></span>

## <a name="enable-the-windows-subsystem-for-linux"></a><span data-ttu-id="e924c-107">启用适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="e924c-107">Enable the Windows Subsystem for Linux</span></span>

<span data-ttu-id="e924c-108">必须启用“适用于 Linux 的 Windows 子系统”可选功能并重启，然后才能在 Windows 上运行 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="e924c-108">Before you can run Linux distros on Windows, you must enable the "Windows Subsystem for Linux" optional feature and reboot.</span></span>

<span data-ttu-id="e924c-109">以管理员身份打开 PowerShell 并运行：</span><span class="sxs-lookup"><span data-stu-id="e924c-109">Open PowerShell as Administrator and run:</span></span>

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

```

<span data-ttu-id="e924c-110">**如果你正在寻求 100% 的系统调用兼容性和更快的 IO 性能，请阅读下文以安装 WSL 2！**</span><span class="sxs-lookup"><span data-stu-id="e924c-110">**If you're looking for 100% system call compatibility and faster IO performance, read below to install WSL 2!**</span></span>

<span data-ttu-id="e924c-111">只有 Windows 10 版本 2004 的内部版本 19041 或更高版本中才提供 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="e924c-111">WSL 2 is only available in Windows 10, Version 2004, Build 19041 or higher.</span></span> <span data-ttu-id="e924c-112">你可能需要[更新 Windows 版本](ms-settings:windowsupdate)。</span><span class="sxs-lookup"><span data-stu-id="e924c-112">You may need to [update your Windows version](ms-settings:windowsupdate).</span></span>

<span data-ttu-id="e924c-113">**如果要继续安装 WSL 1，请在系统提示时重新启动计算机，并访问[此处](./install-on-server.md#download-a-linux-distribution)继续安装**</span><span class="sxs-lookup"><span data-stu-id="e924c-113">**If continuing with WSL 1, restart your machine when prompted and continue with installation [here](./install-on-server.md#download-a-linux-distribution)**</span></span>

## <a name="enable-the-virtual-machine-platform-optional-component"></a><span data-ttu-id="e924c-114">启用“虚拟机平台”可选组件</span><span class="sxs-lookup"><span data-stu-id="e924c-114">Enable the Virtual Machine Platform optional component</span></span>

<span data-ttu-id="e924c-115">确保安装了“虚拟机平台”可选组件。</span><span class="sxs-lookup"><span data-stu-id="e924c-115">Ensure the 'Virtual Machine Platform' optional component is installed.</span></span> <span data-ttu-id="e924c-116">可以通过在 PowerShell 中运行以下命令来执行该操作：</span><span class="sxs-lookup"><span data-stu-id="e924c-116">You can do that by running the following command in PowerShell:</span></span>

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

## <a name="download-a-linux-distribution"></a><span data-ttu-id="e924c-117">下载 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="e924c-117">Download a Linux distribution</span></span>

<span data-ttu-id="e924c-118">按照[这些说明](install-manual.md)下载你最喜爱的 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="e924c-118">Follow [these instructions](install-manual.md) to download your favorite Linux distribution.</span></span>

## <a name="extract-and-install-a-linux-distribution"></a><span data-ttu-id="e924c-119">提取并安装 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="e924c-119">Extract and install a Linux distribution</span></span>

<span data-ttu-id="e924c-120">下载 Linux 分发版后，若要提取其内容并进行手动安装，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="e924c-120">Now that you've downloaded a Linux distribution, in order to extract its contents and manually install, follow these steps:</span></span>

1. <span data-ttu-id="e924c-121">使用 PowerShell 提取 `<distro>.appx` 包的内容：</span><span class="sxs-lookup"><span data-stu-id="e924c-121">Extract the `<distro>.appx` package's contents, using PowerShell:</span></span>

    ```powershell
    Rename-Item .\Ubuntu.appx .\Ubuntu.zip
    Expand-Archive .\Ubuntu.zip .\Ubuntu
    ```

2. <span data-ttu-id="e924c-122">在目标文件夹中运行分发版启动器应用程序。</span><span class="sxs-lookup"><span data-stu-id="e924c-122">Run the distribution launcher application in the target folder.</span></span> <span data-ttu-id="e924c-123">启动器通常命名为 `<distro>.exe`（例如，`ubuntu.exe`）。</span><span class="sxs-lookup"><span data-stu-id="e924c-123">The launcher is typically named `<distro>.exe` (for example, `ubuntu.exe`).</span></span>

    ![Windows Server 上展开的 Ubuntu 发行版](media/server-appx-expand.png)

> [!CAUTION]
> <span data-ttu-id="e924c-125">**安装失败并出现错误 0x8007007e**：如果收到此错误，则表明系统不支持 WSL。</span><span class="sxs-lookup"><span data-stu-id="e924c-125">**Installation failed with error 0x8007007e**: If you receive this error, then your system doesn't support WSL.</span></span> <span data-ttu-id="e924c-126">请确保运行的是 Windows 版本 16215 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e924c-126">Ensure that you're running Windows build 16215 or later.</span></span> <span data-ttu-id="e924c-127">[检查内部版本](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="e924c-127">[Check your build](troubleshooting.md#check-your-build-number).</span></span> <span data-ttu-id="e924c-128">另外，请进行检查以[确认 WSL 已启用](troubleshooting.md#confirm-wsl-is-enabled)，并且在启用此功能后重新启动了计算机。</span><span class="sxs-lookup"><span data-stu-id="e924c-128">Also check to [confirm that WSL is enabled](troubleshooting.md#confirm-wsl-is-enabled) and your computer was restarted after the feature was enabled.</span></span>  

<span data-ttu-id="e924c-129">3. 使用 PowerShell 将你的分发版路径添加到 Windows 环境路径（在本例中为 `C:\Users\Administrator\Ubuntu`）：</span><span class="sxs-lookup"><span data-stu-id="e924c-129">3.Add your distro path to the Windows environment PATH (`C:\Users\Administrator\Ubuntu` in this example), using PowerShell:</span></span>

```powershell
$userenv = [System.Environment]::GetEnvironmentVariable("Path", "User")
[System.Environment]::SetEnvironmentVariable("PATH", $userenv + ";C:\Users\Administrator\Ubuntu", "User")
```

<span data-ttu-id="e924c-130">现在，可以通过键入 `<distro>.exe` 从任何路径启动你的分发版。</span><span class="sxs-lookup"><span data-stu-id="e924c-130">You can now launch your distribution from any path by typing `<distro>.exe`.</span></span> <span data-ttu-id="e924c-131">例如： `ubuntu.exe`。</span><span class="sxs-lookup"><span data-stu-id="e924c-131">For example: `ubuntu.exe`.</span></span>

<span data-ttu-id="e924c-132">安装了分发版后，必须先[初始化新的分发版实例](initialize-distro.md)，然后才能使用它。</span><span class="sxs-lookup"><span data-stu-id="e924c-132">Now that it is installed, you must [initialize your new distribution instance](initialize-distro.md) before using it.</span></span>
