---
title: 在 Windows Server 上安装 Linux 子系统
description: Windows Server 上的 Linux 子系统的安装说明。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, windows server
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: ebcd7f6b10d2b734b1f2a66f64a5e3292855bcf4
ms.sourcegitcommit: 5d3898772851e6ac9a310f219cc0d71278f95d22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671017"
---
# <a name="windows-server-installation-guide"></a><span data-ttu-id="d0a1d-104">Windows Server 安装指南</span><span class="sxs-lookup"><span data-stu-id="d0a1d-104">Windows Server Installation Guide</span></span>

<span data-ttu-id="d0a1d-105">适用于 Linux 的 Windows 子系统可供在 Windows Server 2019（版本 1709）和更高版本上安装。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-105">The Windows Subsystem for Linux is available for installation on Windows Server 2019 (version 1709) and later.</span></span> <span data-ttu-id="d0a1d-106">本指南将指导你完成在计算机上启用 WSL 的步骤。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-106">This guide will walk through the steps of enabling WSL on your machine.</span></span>

## <a name="enable-the-windows-subsystem-for-linux"></a><span data-ttu-id="d0a1d-107">启用适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="d0a1d-107">Enable the Windows Subsystem for Linux</span></span>

<span data-ttu-id="d0a1d-108">必须启用“适用于 Linux 的 Windows 子系统”可选功能并重启，然后才能在 Windows 上运行 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-108">Before you can run Linux distros on Windows, you must enable the "Windows Subsystem for Linux" optional feature and reboot.</span></span>

<span data-ttu-id="d0a1d-109">以管理员身份打开 PowerShell 并运行：</span><span class="sxs-lookup"><span data-stu-id="d0a1d-109">Open PowerShell as Administrator and run:</span></span>

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

```

## <a name="download-a-linux-distribution"></a><span data-ttu-id="d0a1d-110">下载 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="d0a1d-110">Download a Linux distribution</span></span>

<span data-ttu-id="d0a1d-111">按照[这些说明](install-manual.md)下载你最喜爱的 Linux 发行版。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-111">Follow [these instructions](install-manual.md) to download your favorite Linux distribution.</span></span>

## <a name="extract-and-install-a-linux-distribution"></a><span data-ttu-id="d0a1d-112">提取并安装 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="d0a1d-112">Extract and install a Linux distribution</span></span>

<span data-ttu-id="d0a1d-113">下载 Linux 分发版后，若要提取其内容并进行手动安装，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="d0a1d-113">Now that you've downloaded a Linux distribution, in order to extract its contents and manually install, follow these steps:</span></span>

1. <span data-ttu-id="d0a1d-114">使用 PowerShell 提取 `<distro>.appx` 包的内容：</span><span class="sxs-lookup"><span data-stu-id="d0a1d-114">Extract the `<distro>.appx` package's contents, using PowerShell:</span></span>

    ```powershell
    Rename-Item .\Ubuntu.appx .\Ubuntu.zip
    Expand-Archive .\Ubuntu.zip .\Ubuntu
    ```

2. <span data-ttu-id="d0a1d-115">在目标文件夹中运行分发版启动器应用程序。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-115">Run the distribution launcher application in the target folder.</span></span> <span data-ttu-id="d0a1d-116">启动器通常命名为 `<distro>.exe`（例如，`ubuntu.exe`）。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-116">The launcher is typically named `<distro>.exe` (for example, `ubuntu.exe`).</span></span>

    ![Windows Server 上展开的 Ubuntu 发行版](media/server-appx-expand.png)

> [!CAUTION]
> <span data-ttu-id="d0a1d-118">**安装失败并出现错误 0x8007007e**：如果收到此错误，则表明系统不支持 WSL。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-118">**Installation failed with error 0x8007007e**: If you receive this error, then your system doesn't support WSL.</span></span> <span data-ttu-id="d0a1d-119">请确保运行的是 Windows 版本 16215 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-119">Ensure that you're running Windows build 16215 or later.</span></span> <span data-ttu-id="d0a1d-120">[检查内部版本](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-120">[Check your build](troubleshooting.md#check-your-build-number).</span></span> <span data-ttu-id="d0a1d-121">另外，请进行检查以[确认 WSL 已启用](troubleshooting.md#confirm-wsl-is-enabled)，并且在启用此功能后重新启动了计算机。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-121">Also check to [confirm that WSL is enabled](troubleshooting.md#confirm-wsl-is-enabled) and your computer was restarted after the feature was enabled.</span></span>  

<span data-ttu-id="d0a1d-122">3. 使用 PowerShell 将你的分发版路径添加到 Windows 环境路径（在本例中为 `C:\Users\Administrator\Ubuntu`）：</span><span class="sxs-lookup"><span data-stu-id="d0a1d-122">3.Add your distro path to the Windows environment PATH (`C:\Users\Administrator\Ubuntu` in this example), using PowerShell:</span></span>

```powershell
$userenv = [System.Environment]::GetEnvironmentVariable("Path", "User")
[System.Environment]::SetEnvironmentVariable("PATH", $userenv + ";C:\Users\Administrator\Ubuntu", "User")
```

<span data-ttu-id="d0a1d-123">现在，可以通过键入 `<distro>.exe` 从任何路径启动你的分发版。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-123">You can now launch your distribution from any path by typing `<distro>.exe`.</span></span> <span data-ttu-id="d0a1d-124">例如： `ubuntu.exe`。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-124">For example: `ubuntu.exe`.</span></span>

<span data-ttu-id="d0a1d-125">安装了分发版后，必须先[初始化新的分发版实例](initialize-distro.md)，然后才能使用它。</span><span class="sxs-lookup"><span data-stu-id="d0a1d-125">Now that it is installed, you must [initialize your new distribution instance](initialize-distro.md) before using it.</span></span>
