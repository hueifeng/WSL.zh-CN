---
title: 存档的 WSL 指令
ms.date: 07/23/2018
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ROBOTS: NOINDEX
ms.openlocfilehash: 1de614dccbbb8d0ef1b9ac070f6ec90281339858
ms.sourcegitcommit: 16ffb1a096a4a7fbb77c58f92258051930cc82da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86157953"
---
# <a name="archived-instructions"></a><span data-ttu-id="cd582-102">存档说明</span><span class="sxs-lookup"><span data-stu-id="cd582-102">Archived instructions</span></span>

<span data-ttu-id="cd582-103">以下指南将指导你完成一些步骤，在运行 Windows 10 的计算机上安装适用于 Linux 的 Windows 子系统 (WSL) 时，需要执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="cd582-103">The following guide will walk through the steps required to install the Windows Subsystem for Linux (WSL) on a computer running Windows 10.</span></span>

## <a name="enable-the-windows-subsystem-for-linux-optional-feature"></a><span data-ttu-id="cd582-104">启用“适用于 Linux 的 Windows 子系统”可选功能</span><span class="sxs-lookup"><span data-stu-id="cd582-104">Enable the Windows Subsystem for Linux optional feature</span></span>

<span data-ttu-id="cd582-105">在安装 Linux 分发版之前，必须先在 Windows 10 上启用“适用于 Linux 的 Windows 子系统”可选功能：</span><span class="sxs-lookup"><span data-stu-id="cd582-105">Before installing a Linux distribution, you must enable the "Windows Subsystem for Linux" optional feature on Windows 10:</span></span>

1. <span data-ttu-id="cd582-106">以管理员身份打开 PowerShell，然后输入此脚本：</span><span class="sxs-lookup"><span data-stu-id="cd582-106">Open PowerShell as Administrator and enter this script:</span></span>

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

1. <span data-ttu-id="cd582-107">出现提示时，重启计算机。</span><span class="sxs-lookup"><span data-stu-id="cd582-107">Restart your computer when prompted.</span></span>

## <a name="install-a-linux-distribution"></a><span data-ttu-id="cd582-108">安装 Linux 发行版本</span><span class="sxs-lookup"><span data-stu-id="cd582-108">Install a Linux distribution</span></span>

<span data-ttu-id="cd582-109">有三种方法可用于下载和安装你偏好的 Linux 分发版：</span><span class="sxs-lookup"><span data-stu-id="cd582-109">There are three ways to download and install your preferred Linux distribution(s):</span></span>

- <span data-ttu-id="cd582-110">从 Microsoft Store 下载并安装（参阅下文）</span><span class="sxs-lookup"><span data-stu-id="cd582-110">Download and install from the Microsoft Store (see below)</span></span>
- [<span data-ttu-id="cd582-111">下载并从命令行手动安装</span><span class="sxs-lookup"><span data-stu-id="cd582-111">Download and manually install from command line</span></span>](install-manual.md)
- [<span data-ttu-id="cd582-112">在 Windows Server 上安装</span><span class="sxs-lookup"><span data-stu-id="cd582-112">Install on Windows Server</span></span>](install-on-server.md)

### <a name="install-from-the-microsoft-store"></a><span data-ttu-id="cd582-113">从 Microsoft Store 安装</span><span class="sxs-lookup"><span data-stu-id="cd582-113">Install from the Microsoft Store</span></span>

<span data-ttu-id="cd582-114">可以从 Microsoft Store 将 Linux 分发版安装到 Windows 10（内部版本 16215+）上。</span><span class="sxs-lookup"><span data-stu-id="cd582-114">Linux distributions can be installed from the Microsoft Store on Windows 10 (Build 16215+).</span></span>

> [!NOTE]
> <span data-ttu-id="cd582-115">遵循以下步骤[检查 Windows 10 内部版本号](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="cd582-115">Follow these steps to [check your Windows 10 build number](troubleshooting.md#check-your-build-number).</span></span>

1. <span data-ttu-id="cd582-116">打开 Microsoft Store，并选择你偏好的 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="cd582-116">Open the Microsoft Store and choose your favorite Linux distribution.</span></span>

    ![Microsoft Store 中的 Linux 分发版视图](media/store.png)

    <span data-ttu-id="cd582-118">单击以下链接会打开每个分发版的 Microsoft Store 页面：</span><span class="sxs-lookup"><span data-stu-id="cd582-118">The following links will open the Microsoft store page for each distribution:</span></span>

    - [<span data-ttu-id="cd582-119">Ubuntu 16.04 LTS</span><span class="sxs-lookup"><span data-stu-id="cd582-119">Ubuntu 16.04 LTS</span></span>](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    - [<span data-ttu-id="cd582-120">Ubuntu 18.04 LTS</span><span class="sxs-lookup"><span data-stu-id="cd582-120">Ubuntu 18.04 LTS</span></span>](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    - [<span data-ttu-id="cd582-121">OpenSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="cd582-121">OpenSUSE Leap 15</span></span>](https://www.microsoft.com/store/apps/9n1tb6fpvj8c)
    - [<span data-ttu-id="cd582-122">OpenSUSE Leap 42</span><span class="sxs-lookup"><span data-stu-id="cd582-122">OpenSUSE Leap 42</span></span>](https://www.microsoft.com/store/apps/9njvjts82tjx)
    - [<span data-ttu-id="cd582-123">SUSE Linux Enterprise Server 12</span><span class="sxs-lookup"><span data-stu-id="cd582-123">SUSE Linux Enterprise Server 12</span></span>](https://www.microsoft.com/store/apps/9p32mwbh6cns)
    - [<span data-ttu-id="cd582-124">SUSE Linux Enterprise Server 15</span><span class="sxs-lookup"><span data-stu-id="cd582-124">SUSE Linux Enterprise Server 15</span></span>](https://www.microsoft.com/store/apps/9pmw35d7fnlx)
    - [<span data-ttu-id="cd582-125">Kali Linux</span><span class="sxs-lookup"><span data-stu-id="cd582-125">Kali Linux</span></span>](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    - [<span data-ttu-id="cd582-126">Debian GNU/Linux</span><span class="sxs-lookup"><span data-stu-id="cd582-126">Debian GNU/Linux</span></span>](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    - [<span data-ttu-id="cd582-127">Fedora Remix for WSL</span><span class="sxs-lookup"><span data-stu-id="cd582-127">Fedora Remix for WSL</span></span>](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    - [<span data-ttu-id="cd582-128">Pengwin</span><span class="sxs-lookup"><span data-stu-id="cd582-128">Pengwin</span></span>](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    - [<span data-ttu-id="cd582-129">Pengwin Enterprise</span><span class="sxs-lookup"><span data-stu-id="cd582-129">Pengwin Enterprise</span></span>](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    - [<span data-ttu-id="cd582-130">Alpine WSL</span><span class="sxs-lookup"><span data-stu-id="cd582-130">Alpine WSL</span></span>](https://www.microsoft.com/store/apps/9p804crf0395)

1. <span data-ttu-id="cd582-131">选择“获取”，在该分发版完成下载后，请选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="cd582-131">Select "Get" and once the distribution has finished downloading, select "Launch".</span></span>

    ![Microsoft Store 中的 Linux 分发版视图](media/UbuntuStore.png)

## <a name="complete-initialization-of-your-distro"></a><span data-ttu-id="cd582-133">完成分发版的初始化</span><span class="sxs-lookup"><span data-stu-id="cd582-133">Complete initialization of your distro</span></span>

<span data-ttu-id="cd582-134">启动 Linux 分发版后，请按照屏幕上的说明初始化分发版。</span><span class="sxs-lookup"><span data-stu-id="cd582-134">After launching your Linux distribution, follow the onscreen instructions to initialize your distro.</span></span>

> [!NOTE]
> <span data-ttu-id="cd582-135">对于 Windows Server，请使用安装文件夹中的可执行文件 `<distro>.exe` 启动分发版。</span><span class="sxs-lookup"><span data-stu-id="cd582-135">For Windows Server, launch your distribution using the executable, `<distro>.exe`, in the installation folder.</span></span>

<span data-ttu-id="cd582-136">首次运行新安装的分发版时，会打开一个控制台窗口，其中指出需要等待一两分钟时间，以便安装完成。</span><span class="sxs-lookup"><span data-stu-id="cd582-136">The first time a newly installed distribution runs, a console window will open and you'll be asked to wait for a minute or two for the installation to complete.</span></span> <span data-ttu-id="cd582-137">在这最后一个安装阶段，分发版的文件将会解压缩，并存储在电脑上供你使用。</span><span class="sxs-lookup"><span data-stu-id="cd582-137">During this final stage of installation, the distro's files are de-compressed and stored on your PC, ready for use.</span></span> <span data-ttu-id="cd582-138">这可能需要一分钟或更长时间，具体取决于电脑存储设备的性能。</span><span class="sxs-lookup"><span data-stu-id="cd582-138">This may take around a minute or more depending on the performance of your PC's storage devices.</span></span> <span data-ttu-id="cd582-139">仅当分发版是干净安装的版本时，才需要执行此初始安装阶段 - 将来在不到一秒内即可启动分发版。</span><span class="sxs-lookup"><span data-stu-id="cd582-139">This initial installation phase is only required when a distro is clean-installed - all future launches should take less than a second.</span></span>

## <a name="set-up-a-new-linux-user-account"></a><span data-ttu-id="cd582-140">设置新的 Linux 用户帐户</span><span class="sxs-lookup"><span data-stu-id="cd582-140">Set up a new Linux user account</span></span>

<span data-ttu-id="cd582-141">安装完成后，系统会提示创建新的用户帐户（及其密码）。</span><span class="sxs-lookup"><span data-stu-id="cd582-141">Once installation is complete, you will be prompted to create a new user account (and its password).</span></span>

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

<span data-ttu-id="cd582-143">此用户帐户用于普通的非管理员用户，在默认情况下，你在启动分发版时将以该用户身份登录。</span><span class="sxs-lookup"><span data-stu-id="cd582-143">This user account is for the normal non-admin user that you'll be logged-in as by default when launching a distribution.</span></span> <span data-ttu-id="cd582-144">可根据需要选择任何用户名和密码 - 它们与 Windows 用户名无关。</span><span class="sxs-lookup"><span data-stu-id="cd582-144">You can choose any username and password you wish - they have no bearing on your Windows username.</span></span>

<span data-ttu-id="cd582-145">打开新的分发版实例时，系统不会提示你输入密码，但**如果使用 `sudo` 提升了进程的权限，则需要输入密码**，因此请确保选择一个容易记住的密码！</span><span class="sxs-lookup"><span data-stu-id="cd582-145">When you open a new distro instance, you won't be prompted for your password, but **if you elevate a process using `sudo`, you will need to enter your password**, so make sure you choose a password you can easily remember!</span></span> <span data-ttu-id="cd582-146">有关详细信息，请参阅[用户支持](user-support.md)页。</span><span class="sxs-lookup"><span data-stu-id="cd582-146">See the [User Support](user-support.md) page for more info.</span></span>

## <a name="update--upgrade-packages"></a><span data-ttu-id="cd582-147">更新和升级包</span><span class="sxs-lookup"><span data-stu-id="cd582-147">Update & upgrade packages</span></span>

<span data-ttu-id="cd582-148">大多数分发版随附了一个空的的包目录或最简单的包目录。</span><span class="sxs-lookup"><span data-stu-id="cd582-148">Most distributions ship with an empty or minimal package catalog.</span></span> <span data-ttu-id="cd582-149">我们强烈建议定期更新包目录，并使用分发版的首选包管理器升级已安装的包。</span><span class="sxs-lookup"><span data-stu-id="cd582-149">We strongly recommend regularly updating your package catalog and upgrading your installed packages using your distro's preferred package manager.</span></span> <span data-ttu-id="cd582-150">对于 Debian/Ubuntu，请使用 apt：</span><span class="sxs-lookup"><span data-stu-id="cd582-150">For Debian/Ubuntu, use apt:</span></span>

```bash
sudo apt update && sudo apt upgrade
```

<span data-ttu-id="cd582-151">Windows 不会自动更新或升级 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="cd582-151">Windows does not automatically update or upgrade your Linux distro(s).</span></span> <span data-ttu-id="cd582-152">大多数 Linux 用户往往倾向于自行控制此任务。</span><span class="sxs-lookup"><span data-stu-id="cd582-152">This is a task that the most Linux users prefer to control themselves.</span></span>

<span data-ttu-id="cd582-153">现在，可以在 WSL 上享用新的 Linux 分发版！</span><span class="sxs-lookup"><span data-stu-id="cd582-153">Enjoy using your new Linux distro on WSL!</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="cd582-154">疑难解答</span><span class="sxs-lookup"><span data-stu-id="cd582-154">Troubleshooting</span></span>

<span data-ttu-id="cd582-155">下面是相关的安装错误和建议的修复措施。</span><span class="sxs-lookup"><span data-stu-id="cd582-155">Below are related installation errors and suggested fixes.</span></span> <span data-ttu-id="cd582-156">有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="cd582-156">Refer to the [WSL troubleshooting page](troubleshooting.md) for other common errors and their solutions.</span></span>

### <a name="installation-failed-with-error-0x8007007e"></a><span data-ttu-id="cd582-157">安装失败，出现错误 0x8007007e</span><span class="sxs-lookup"><span data-stu-id="cd582-157">Installation failed with error 0x8007007e</span></span>

<span data-ttu-id="cd582-158">当系统不支持来自 Store 的 Linux 时会出现此错误。</span><span class="sxs-lookup"><span data-stu-id="cd582-158">This error occurs when your system doesn't support Linux from the store.</span></span>  <span data-ttu-id="cd582-159">请确保：</span><span class="sxs-lookup"><span data-stu-id="cd582-159">Make sure that:</span></span>

- <span data-ttu-id="cd582-160">运行 Windows 内部版本 16215 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cd582-160">You're running Windows build 16215 or later.</span></span> <span data-ttu-id="cd582-161">[检查内部版本](troubleshooting.md#check-your-build-number)。</span><span class="sxs-lookup"><span data-stu-id="cd582-161">[Check your build](troubleshooting.md#check-your-build-number).</span></span>
- <span data-ttu-id="cd582-162">已启用“适用于 Linux 的 Windows 子系统”可选组件，并已重启计算机。</span><span class="sxs-lookup"><span data-stu-id="cd582-162">The Windows Subsystem for Linux optional component is enabled and the computer has restarted.</span></span>  <span data-ttu-id="cd582-163">[确保已启用 WSL](troubleshooting.md#confirm-wsl-is-enabled)。</span><span class="sxs-lookup"><span data-stu-id="cd582-163">[Make sure WSL is enabled](troubleshooting.md#confirm-wsl-is-enabled).</span></span>

### <a name="installation-failed-with-error-0x80070003"></a><span data-ttu-id="cd582-164">安装失败，出现错误 0x80070003</span><span class="sxs-lookup"><span data-stu-id="cd582-164">Installation failed with error 0x80070003</span></span>

<span data-ttu-id="cd582-165">适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。</span><span class="sxs-lookup"><span data-stu-id="cd582-165">The Windows Subsystem for Linux only runs on your system drive (usually this is your `C:` drive).</span></span> <span data-ttu-id="cd582-166">请确保将分发版存储在系统驱动器上：</span><span class="sxs-lookup"><span data-stu-id="cd582-166">Make sure that distros are stored on your system drive:</span></span>

- <span data-ttu-id="cd582-167">打开“设置” -> “存储” -> “更多存储设置:  更改新内容的保存位置”</span><span class="sxs-lookup"><span data-stu-id="cd582-167">Open **Settings** -> **Storage** -> **More Storage Settings: Change where new content is saved**</span></span>
  
    ![用于在 C: 驱动器上安装应用的系统设置屏幕截图](media/AppStorage.png)

### <a name="wslregisterdistribution-failed-with-error-0x8007019e"></a><span data-ttu-id="cd582-169">WslRegisterDistribution 失败，出现错误 0x8007019e</span><span class="sxs-lookup"><span data-stu-id="cd582-169">WslRegisterDistribution failed with error 0x8007019e</span></span>

<span data-ttu-id="cd582-170">未启用“适用于 Linux 的 Windows 子系统”可选组件：</span><span class="sxs-lookup"><span data-stu-id="cd582-170">The Windows Subsystem for Linux optional component is not enabled:</span></span>

- <span data-ttu-id="cd582-171">打开“控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中“适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。   </span><span class="sxs-lookup"><span data-stu-id="cd582-171">Open **Control Panel** -> **Programs and Features** -> **Turn Windows Feature on or off** -> Check **Windows Subsystem for Linux** or using the PowerShell cmdlet mentioned at the begining of this article.</span></span>
