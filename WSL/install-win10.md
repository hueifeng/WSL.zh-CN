---
title: 在 Windows 10 上安装适用于 Linux 的 Windows 子系统 (WSL)
description: 有关在 Windows 10 上安装适用于 Linux 的 Windows 子系统的说明。
keywords: BashOnWindows, bash, wsl, Windows, 适用于 Linux 的 Windows 子系统, windows 子系统, ubuntu, debian, suse, Windows 10, 安装, 启用, WSL2, 版本 2
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 0f59fda8aa093487f09c1817acf47bd88eaae8cc
ms.sourcegitcommit: f1b049a1276782d4f2754f46a8d2025b598a0784
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85336090"
---
# <a name="windows-subsystem-for-linux-installation-guide-for-windows-10"></a><span data-ttu-id="e56c5-104">适用于 Linux 的 Windows 子系统安装指南 (Windows 10)</span><span class="sxs-lookup"><span data-stu-id="e56c5-104">Windows Subsystem for Linux Installation Guide for Windows 10</span></span>

## <a name="install-the-windows-subsystem-for-linux"></a><span data-ttu-id="e56c5-105">安装适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="e56c5-105">Install the Windows Subsystem for Linux</span></span>

<span data-ttu-id="e56c5-106">必须先启用“适用于 Linux 的 Windows 子系统”可选功能，然后才能在 Windows 上安装 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="e56c5-106">Before installing any Linux distributions on Windows, you must enable the "Windows Subsystem for Linux" optional feature.</span></span>

<span data-ttu-id="e56c5-107">以管理员身份打开 PowerShell 并运行：</span><span class="sxs-lookup"><span data-stu-id="e56c5-107">Open PowerShell as Administrator and run:</span></span>

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

<span data-ttu-id="e56c5-108">若要仅安装 WSL 1，现在应重启计算机并继续[安装所选的 Linux 分发版](./install-win10.md#install-your-linux-distribution-of-choice)，否则请等待重启并继续更新到 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="e56c5-108">To only install WSL 1, you should now restart your machine and move on to [Install your Linux distribution of choice](./install-win10.md#install-your-linux-distribution-of-choice), otherwise wait to restart and move on to update to WSL 2.</span></span> <span data-ttu-id="e56c5-109">阅读有关[比较 WSL 2 和 WSL 1](./compare-versions.md) 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e56c5-109">Read more about [Comparing WSL 2 and WSL 1](./compare-versions.md).</span></span>

## <a name="update-to-wsl-2"></a><span data-ttu-id="e56c5-110">更新到 WSL 2</span><span class="sxs-lookup"><span data-stu-id="e56c5-110">Update to WSL 2</span></span>

<span data-ttu-id="e56c5-111">若要更新到 WSL 2，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="e56c5-111">To update to WSL 2, you must meet the following criteria:</span></span>

- <span data-ttu-id="e56c5-112">运行 Windows 10（[已更新到版本 2004](ms-settings:windowsupdate) 的**内部版本 19041** 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="e56c5-112">Running Windows 10, [updated to version 2004](ms-settings:windowsupdate), **Build 19041** or higher.</span></span>

- <span data-ttu-id="e56c5-113">通过按 Windows 徽标键 + R，检查你的 Windows 版本，然后键入 **winver**，选择“确定”。</span><span class="sxs-lookup"><span data-stu-id="e56c5-113">Check your Windows version by selecting the **Windows logo key + R**, type **winver**, select **OK**.</span></span> <span data-ttu-id="e56c5-114">（或者在 Windows 命令提示符下输入 `ver` 命令）。</span><span class="sxs-lookup"><span data-stu-id="e56c5-114">(Or enter the `ver` command in Windows Command Prompt).</span></span> <span data-ttu-id="e56c5-115">如果内部版本低于 19041，请[更新到最新的 Windows 版本](ms-settings:windowsupdate)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-115">Please [update to the latest Windows version](ms-settings:windowsupdate) if your build is lower than 19041.</span></span> <span data-ttu-id="e56c5-116">[获取 Windows 更新助手](https://www.microsoft.com/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-116">[Get Windows Update Assistant](https://www.microsoft.com/software-download/windows10).</span></span>

### <a name="enable-the-virtual-machine-platform-optional-component"></a><span data-ttu-id="e56c5-117">启用“虚拟机平台”可选组件</span><span class="sxs-lookup"><span data-stu-id="e56c5-117">Enable the 'Virtual Machine Platform' optional component</span></span>

<span data-ttu-id="e56c5-118">安装 WSL 2 之前，必须启用“虚拟机平台”可选功能。</span><span class="sxs-lookup"><span data-stu-id="e56c5-118">Before installing WSL 2, you must enable the "Virtual Machine Platform" optional feature.</span></span>

<span data-ttu-id="e56c5-119">以管理员身份打开 PowerShell 并运行：</span><span class="sxs-lookup"><span data-stu-id="e56c5-119">Open PowerShell as Administrator and run:</span></span>

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

<span data-ttu-id="e56c5-120">**重新启动**计算机，以完成 WSL 安装并更新到 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="e56c5-120">**Restart** your machine to complete the WSL install and update to WSL 2.</span></span>

### <a name="set-wsl-2-as-your-default-version"></a><span data-ttu-id="e56c5-121">将 WSL 2 设置为默认版本</span><span class="sxs-lookup"><span data-stu-id="e56c5-121">Set WSL 2 as your default version</span></span>

<span data-ttu-id="e56c5-122">安装新的 Linux 分发版时，请在 PowerShell 中运行以下命令，以将 WSL 2 设置为默认版本：</span><span class="sxs-lookup"><span data-stu-id="e56c5-122">Run the following command in PowerShell to set WSL 2 as the default version when installing a new Linux distribution:</span></span>

```powershell
wsl --set-default-version 2
```

<span data-ttu-id="e56c5-123">运行该命令后，你可能会看到此消息：`WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`。</span><span class="sxs-lookup"><span data-stu-id="e56c5-123">You might see this message after running that command: `WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`.</span></span> <span data-ttu-id="e56c5-124">跟随链接（[https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)），在文档中安装来自该页面的 MSI，以便在计算机上安装 Linux 内核供 WSL 2 使用。</span><span class="sxs-lookup"><span data-stu-id="e56c5-124">Please follow the link ([https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)) and install the MSI from that page on our documentation to install a Linux kernel on your machine for WSL 2 to use.</span></span> <span data-ttu-id="e56c5-125">安装内核后，请再次运行该命令，该命令应会成功完成而不显示消息。</span><span class="sxs-lookup"><span data-stu-id="e56c5-125">Once you have the kernel installed, please run the command again and it should complete successfully without showing the message.</span></span> 

> [!NOTE]
> <span data-ttu-id="e56c5-126">从 WSL 1 更新到 WSL 2 可能需要几分钟才能完成，具体取决于目标分发版的大小。</span><span class="sxs-lookup"><span data-stu-id="e56c5-126">The update from WSL 1 to WSL 2 may take several minutes to complete depending on the size of your targeted distribution.</span></span> <span data-ttu-id="e56c5-127">如果从 Windows 10 周年更新或创意者更新运行 WSL 1 的旧（历史）安装，可能会遇到更新错误。</span><span class="sxs-lookup"><span data-stu-id="e56c5-127">If you are running an older (legacy) installation of WSL 1 from Windows 10 Anniversary Update or Creators Update, you may encounter an update error.</span></span> <span data-ttu-id="e56c5-128">按照这些说明[卸载并删除任何旧分发](https://docs.microsoft.com/windows/wsl/install-legacy#uninstallingremoving-the-legacy-distro)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-128">Follow these instructions to [uninstall and remove any legacy distributions](https://docs.microsoft.com/windows/wsl/install-legacy#uninstallingremoving-the-legacy-distro).</span></span>

## <a name="install-your-linux-distribution-of-choice"></a><span data-ttu-id="e56c5-129">安装所选的 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="e56c5-129">Install your Linux distribution of choice</span></span>

1. <span data-ttu-id="e56c5-130">打开 [Microsoft Store](https://aka.ms/wslstore)，并选择你偏好的 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="e56c5-130">Open the [Microsoft Store](https://aka.ms/wslstore) and select your favorite Linux distribution.</span></span>

    ![Microsoft Store 中的 Linux 分发版的视图](media/store.png)

    <span data-ttu-id="e56c5-132">单击以下链接会打开每个分发版的 Microsoft Store 页面：</span><span class="sxs-lookup"><span data-stu-id="e56c5-132">The following links will open the Microsoft store page for each distribution:</span></span>

    - [<span data-ttu-id="e56c5-133">Ubuntu 16.04 LTS</span><span class="sxs-lookup"><span data-stu-id="e56c5-133">Ubuntu 16.04 LTS</span></span>](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    - [<span data-ttu-id="e56c5-134">Ubuntu 18.04 LTS</span><span class="sxs-lookup"><span data-stu-id="e56c5-134">Ubuntu 18.04 LTS</span></span>](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    - [<span data-ttu-id="e56c5-135">Ubuntu 20.04 LTS</span><span class="sxs-lookup"><span data-stu-id="e56c5-135">Ubuntu 20.04 LTS</span></span>](https://www.microsoft.com/store/apps/9n6svws3rx71)
    - [<span data-ttu-id="e56c5-136">openSUSE Leap 15.1</span><span class="sxs-lookup"><span data-stu-id="e56c5-136">openSUSE Leap 15.1</span></span>](https://www.microsoft.com/store/apps/9NJFZK00FGKV)
    - [<span data-ttu-id="e56c5-137">SUSE Linux Enterprise Server 12 SP5</span><span class="sxs-lookup"><span data-stu-id="e56c5-137">SUSE Linux Enterprise Server 12 SP5</span></span>](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1)
    - [<span data-ttu-id="e56c5-138">SUSE Linux Enterprise Server 15 SP1</span><span class="sxs-lookup"><span data-stu-id="e56c5-138">SUSE Linux Enterprise Server 15 SP1</span></span>](https://www.microsoft.com/store/apps/9PN498VPMF3Z)
    - [<span data-ttu-id="e56c5-139">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="e56c5-139">Kali Linux</span></span>](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    - [<span data-ttu-id="e56c5-140">Debian GNU/Linux</span><span class="sxs-lookup"><span data-stu-id="e56c5-140">Debian GNU/Linux</span></span>](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    - [<span data-ttu-id="e56c5-141">Fedora Remix for WSL</span><span class="sxs-lookup"><span data-stu-id="e56c5-141">Fedora Remix for WSL</span></span>](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    - [<span data-ttu-id="e56c5-142">Pengwin</span><span class="sxs-lookup"><span data-stu-id="e56c5-142">Pengwin</span></span>](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    - [<span data-ttu-id="e56c5-143">Pengwin Enterprise</span><span class="sxs-lookup"><span data-stu-id="e56c5-143">Pengwin Enterprise</span></span>](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    - [<span data-ttu-id="e56c5-144">Alpine WSL</span><span class="sxs-lookup"><span data-stu-id="e56c5-144">Alpine WSL</span></span>](https://www.microsoft.com/store/apps/9p804crf0395)

2. <span data-ttu-id="e56c5-145">在分发版的页面中，选择“获取”。</span><span class="sxs-lookup"><span data-stu-id="e56c5-145">From the distribution's page, select "Get".</span></span>

    ![Microsoft Store 中的 Linux 分发版](media/UbuntuStore.png)

## <a name="set-up-a-new-distribution"></a><span data-ttu-id="e56c5-147">设置新分发版</span><span class="sxs-lookup"><span data-stu-id="e56c5-147">Set up a new distribution</span></span>

<span data-ttu-id="e56c5-148">首次启动新安装的 Linux 分发版时，将打开一个控制台窗口，系统会要求你等待一分钟或两分钟，以便文件解压缩并存储到电脑上。</span><span class="sxs-lookup"><span data-stu-id="e56c5-148">The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for a minute or two for files to de-compress and be stored on your PC.</span></span> <span data-ttu-id="e56c5-149">未来的所有启动时间应不到一秒。</span><span class="sxs-lookup"><span data-stu-id="e56c5-149">All future launches should take less than a second.</span></span>

<span data-ttu-id="e56c5-150">然后，需要[为新的 Linux 分发版创建用户帐户和密码](./user-support.md)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-150">You will then need to [create a user account and password for your new Linux distribution](./user-support.md).</span></span>

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

## <a name="set-your-distribution-version-to-wsl-1-or-wsl-2"></a><span data-ttu-id="e56c5-152">将分发版版本设置为 WSL 1 或 WSL 2</span><span class="sxs-lookup"><span data-stu-id="e56c5-152">Set your distribution version to WSL 1 or WSL 2</span></span>

<span data-ttu-id="e56c5-153">可以打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 19041 或更高版本](ms-settings:windowsupdate)中可用），来检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`</span><span class="sxs-lookup"><span data-stu-id="e56c5-153">You can check the WSL version assigned to each of the Linux distributions you have installed by opening the PowerShell command line and entering the command (only available in [Windows Build 19041 or higher](ms-settings:windowsupdate)): `wsl -l -v`</span></span>

```powershell
wsl --list --verbose
```

<span data-ttu-id="e56c5-154">若要将分发版设置为受某一 WSL 版本支持，请运行：</span><span class="sxs-lookup"><span data-stu-id="e56c5-154">To set a distribution to be backed by either version of WSL please run:</span></span>

```powershell
wsl --set-version <distribution name> <versionNumber>
```

<span data-ttu-id="e56c5-155">请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字“1”或“2”。</span><span class="sxs-lookup"><span data-stu-id="e56c5-155">Make sure to replace `<distribution name>` with the actual name of your distribution and `<versionNumber>` with the number '1' or '2'.</span></span> <span data-ttu-id="e56c5-156">可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将“2”替换为“1”。</span><span class="sxs-lookup"><span data-stu-id="e56c5-156">You can change back to WSL 1 at anytime by running the same command as above but replacing the '2' with a '1'.</span></span>

<span data-ttu-id="e56c5-157">此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：</span><span class="sxs-lookup"><span data-stu-id="e56c5-157">Additionally, if you want to make WSL 2 your default architecture you can do so with this command:</span></span>

```powershell
wsl --set-default-version 2
```

<span data-ttu-id="e56c5-158">这会将安装的任何新分发版的版本设置为 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="e56c5-158">This will set the version of any new distribution installed to WSL 2.</span></span>

## <a name="troubleshooting-installation"></a><span data-ttu-id="e56c5-159">排查安装问题</span><span class="sxs-lookup"><span data-stu-id="e56c5-159">Troubleshooting installation</span></span>

<span data-ttu-id="e56c5-160">下面是相关的错误和建议的修复措施。</span><span class="sxs-lookup"><span data-stu-id="e56c5-160">Below are related errors and suggested fixes.</span></span> <span data-ttu-id="e56c5-161">有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-161">Refer to the [WSL troubleshooting page](troubleshooting.md) for other common errors and their solutions.</span></span>

- <span data-ttu-id="e56c5-162">**安装失败并出现错误 0x80070003**</span><span class="sxs-lookup"><span data-stu-id="e56c5-162">**Installation failed with error 0x80070003**</span></span>
  - <span data-ttu-id="e56c5-163">适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。</span><span class="sxs-lookup"><span data-stu-id="e56c5-163">The Windows Subsystem for Linux only runs on your system drive (usually this is your `C:` drive).</span></span> <span data-ttu-id="e56c5-164">请确保分发版存储在系统驱动器上：</span><span class="sxs-lookup"><span data-stu-id="e56c5-164">Make sure that distributions are stored on your system drive:</span></span>  
  - <span data-ttu-id="e56c5-165">打开“设置”->“存储”->“更多存储设置：  更改新内容的保存位置”
    ![用于在 C: 驱动器中安装应用的系统设置屏幕截图](media/AppStorage.png)</span><span class="sxs-lookup"><span data-stu-id="e56c5-165">Open **Settings** -> **Storage** -> **More Storage Settings: Change where new content is saved**
![Picture of system settings to install apps on C: drive](media/AppStorage.png)</span></span>

- <span data-ttu-id="e56c5-166">**WslRegisterDistribution 失败并出现错误 0x8007019e**</span><span class="sxs-lookup"><span data-stu-id="e56c5-166">**WslRegisterDistribution failed with error 0x8007019e**</span></span>
  - <span data-ttu-id="e56c5-167">未启用“适用于 Linux 的 Windows 子系统”可选组件：</span><span class="sxs-lookup"><span data-stu-id="e56c5-167">The Windows Subsystem for Linux optional component is not enabled:</span></span>
  - <span data-ttu-id="e56c5-168">打开“控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中“适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。   </span><span class="sxs-lookup"><span data-stu-id="e56c5-168">Open **Control Panel** -> **Programs and Features** -> **Turn Windows Feature on or off** -> Check **Windows Subsystem for Linux** or using the PowerShell cmdlet mentioned at the beginning of this article.</span></span>

- <span data-ttu-id="e56c5-169">**安装失败，出现错误 0x80070003 或错误 0x80370102**</span><span class="sxs-lookup"><span data-stu-id="e56c5-169">**Installation failed with error 0x80070003 or error 0x80370102**</span></span>
  - <span data-ttu-id="e56c5-170">请确保在计算机的 BIOS 内已启用虚拟化。</span><span class="sxs-lookup"><span data-stu-id="e56c5-170">Please make sure that virtualization is enabled inside of your computer's BIOS.</span></span> <span data-ttu-id="e56c5-171">有关如何执行此操作的说明因计算机而异，并且很可能在 CPU 相关选项下。</span><span class="sxs-lookup"><span data-stu-id="e56c5-171">The instructions on how to do this will vary from computer to computer, and will most likely be under CPU related options.</span></span>

- <span data-ttu-id="e56c5-172">**尝试升级时出错：`Invalid command line option: wsl --set-version Ubuntu 2`**</span><span class="sxs-lookup"><span data-stu-id="e56c5-172">**Error when trying to upgrade: `Invalid command line option: wsl --set-version Ubuntu 2`**</span></span>
  - <span data-ttu-id="e56c5-173">请确保已启用适用于 Linux 的 Windows 子系统，并且你使用的是 Windows 内部版本 19041 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e56c5-173">Please make sure that you have the Windows Subsystem for Linux enabled, and that you're using Windows Build version 19041 or higher.</span></span> <span data-ttu-id="e56c5-174">若要启用 WSL，请在 PowerShell 提示符下以具有管理员权限的身份运行此命令：`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`。</span><span class="sxs-lookup"><span data-stu-id="e56c5-174">To enable WSL run this command in a PowerShell prompt with admin privileges: `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`.</span></span> <span data-ttu-id="e56c5-175">可在[此处](./install-win10.md)找到完整的 WSL 安装说明。</span><span class="sxs-lookup"><span data-stu-id="e56c5-175">You can find the full WSL install instructions [here](./install-win10.md).</span></span>

- <span data-ttu-id="e56c5-176">**由于虚拟磁盘系统的某个限制，无法完成所请求的操作。虚拟硬盘文件必须是解压缩的且未加密的，并且不能是稀疏的。**</span><span class="sxs-lookup"><span data-stu-id="e56c5-176">**The requested operation could not be completed due to a virtual disk system limitation. Virtual hard disk files must be uncompressed and unencrypted and must not be sparse.**</span></span>
  - <span data-ttu-id="e56c5-177">请检查 [WSL GitHub 主题 #4103](https://github.com/microsoft/WSL/issues/4103)，其中跟踪了此问题以提供更新的信息。</span><span class="sxs-lookup"><span data-stu-id="e56c5-177">Please check [WSL GitHub thread #4103](https://github.com/microsoft/WSL/issues/4103) where this issue is being tracked for updated information.</span></span>

- <span data-ttu-id="e56c5-178">**无法将词语“wsl”识别为 cmdlet、函数、脚本文件或可运行程序的名称。**</span><span class="sxs-lookup"><span data-stu-id="e56c5-178">**The term 'wsl' is not recognized as the name of a cmdlet, function, script file, or operable program.**</span></span>
  - <span data-ttu-id="e56c5-179">请确保[已安装“适用于 Linux 的 Windows 子系统”可选组件](./install-win10.md#enable-the-virtual-machine-platform-optional-component)。</span><span class="sxs-lookup"><span data-stu-id="e56c5-179">Ensure that the [Windows Subsystem for Linux Optional Component is installed](./install-win10.md#enable-the-virtual-machine-platform-optional-component).</span></span> <span data-ttu-id="e56c5-180">此外，如果你使用的是 ARM64 设备，并从 PowerShell 运行此命令，则会收到此错误。</span><span class="sxs-lookup"><span data-stu-id="e56c5-180">Additionally, if you are using an ARM64 device and running this command from PowerShell, you will receive this error.</span></span> <span data-ttu-id="e56c5-181">请改为从 [PowerShell Core](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6) 或从命令提示符运行 `wsl.exe`。</span><span class="sxs-lookup"><span data-stu-id="e56c5-181">Instead run `wsl.exe` from [PowerShell Core](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6), or Command Prompt.</span></span>
