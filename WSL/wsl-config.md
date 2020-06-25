---
title: 管理 Linux 分发版
description: 有关列出和配置在适用于 Linux 的 Windows 子系统上运行的多个 Linux 分发版的参考文章。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, wsl.conf, wslconfig
ms.date: 05/12/2020
ms.topic: article
ms.openlocfilehash: e97b1030d5891bf8aa1cb656646a4d9e1d480a3d
ms.sourcegitcommit: f1b049a1276782d4f2754f46a8d2025b598a0784
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85336080"
---
# <a name="wsl-commands-and-launch-configurations"></a><span data-ttu-id="35bc1-104">WSL 命令和启动配置</span><span class="sxs-lookup"><span data-stu-id="35bc1-104">WSL commands and launch configurations</span></span>

## <a name="ways-to-run-wsl"></a><span data-ttu-id="35bc1-105">WSL 的运行方式</span><span class="sxs-lookup"><span data-stu-id="35bc1-105">Ways to run WSL</span></span>

<span data-ttu-id="35bc1-106">[安装](install-win10.md)了 WSL 后，可通过多种方式运行 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-106">There are several ways to run a Linux distribution with WSL once it's [installed](install-win10.md).</span></span>

1. <span data-ttu-id="35bc1-107">通过访问 Windows 的 "开始" 菜单并键入已安装的分发的名称，打开 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-107">Open your Linux distribution by visiting the Windows Start menu and typing the name of your installed distributions.</span></span> <span data-ttu-id="35bc1-108">例如： "Ubuntu"。</span><span class="sxs-lookup"><span data-stu-id="35bc1-108">For example: "Ubuntu".</span></span>
2. <span data-ttu-id="35bc1-109">在 Windows 命令提示符或 PowerShell 中，输入已安装的分发的名称。</span><span class="sxs-lookup"><span data-stu-id="35bc1-109">From Windows Command Prompt or PowerShell, enter the name of your installed distribution.</span></span> <span data-ttu-id="35bc1-110">例如： `ubuntu`</span><span class="sxs-lookup"><span data-stu-id="35bc1-110">For example: `ubuntu`</span></span>
3. <span data-ttu-id="35bc1-111">在 Windows 命令提示符或 PowerShell 中，若要在当前命令行内打开默认的 Linux 分发，请输入： `wsl.exe` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-111">From Windows Command Prompt or PowerShell, to open your default Linux distribution inside your current command line, enter: `wsl.exe`.</span></span>
4. <span data-ttu-id="35bc1-112">在 Windows 命令提示符或 PowerShell 中，若要在当前命令行内打开默认的 Linux 分发，请输入： `wsl [command]` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-112">From Windows Command Prompt or PowerShell, to open your default Linux distribution inside your current command line, enter:`wsl [command]`.</span></span>

<span data-ttu-id="35bc1-113">要使用的方法取决于执行的操作。</span><span class="sxs-lookup"><span data-stu-id="35bc1-113">Which method you should use depends on what you're doing.</span></span> <span data-ttu-id="35bc1-114">如果已在 Windows 提示符或 PowerShell 窗口中打开 WSL 命令行并想要退出，请输入以下命令： `exit` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-114">If you've opened a WSL command line within a Windows Prompt or PowerShell window and want to exit, enter the command: `exit`.</span></span>

## <a name="launch-wsl-by-distribution"></a><span data-ttu-id="35bc1-115">按分发版启动 WSL</span><span class="sxs-lookup"><span data-stu-id="35bc1-115">Launch WSL by distribution</span></span>

<span data-ttu-id="35bc1-116">使用特定于分发版的应用程序运行某个分发版会在其自身的控制台窗口中将它启动。</span><span class="sxs-lookup"><span data-stu-id="35bc1-116">Running a distribution using it's distro-specific application launches that distribution in it's own console window.</span></span>

![从“开始”菜单启动 WSL](media/start-launch.png)

<span data-ttu-id="35bc1-118">这相当于在 Microsoft Store 中单击“启动”。</span><span class="sxs-lookup"><span data-stu-id="35bc1-118">It is the same as clicking "Launch" in the Microsoft store.</span></span>

![从 Microsoft Store 启动 WSL](media/store-launch.png)

<span data-ttu-id="35bc1-120">还可以在命令行中运行 `[distribution].exe` 来运行分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-120">You can also run the distribution from the command line by running `[distribution].exe`.</span></span>

<span data-ttu-id="35bc1-121">以这种方式从命令行运行分发版的缺点是，会自动将工作目录从当前目录更改为分发版的主目录。</span><span class="sxs-lookup"><span data-stu-id="35bc1-121">The disadvantage of running a distribution from the command line in this way is that it will automatically change your working directory from the current directory to the distribution's home directory.</span></span>

<span data-ttu-id="35bc1-122">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-122">**Example: (using PowerShell)**</span></span>

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> ubuntu

scooley@scooley-elmer:~$ pwd
/home/scooley
scooley@scooley-elmer:~$ exit
logout

PS C:\Users\sarah>
```

### <a name="wsl-and-wsl-command"></a><span data-ttu-id="35bc1-123">wsl 和 wsl [命令]</span><span class="sxs-lookup"><span data-stu-id="35bc1-123">wsl and wsl [command]</span></span>

<span data-ttu-id="35bc1-124">从命令行运行 WSL 的最佳方式是使用 `wsl.exe`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-124">The best way to run WSL from the command line is using `wsl.exe`.</span></span>

<span data-ttu-id="35bc1-125">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-125">**Example: (using PowerShell)**</span></span>

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> wsl

scooley@scooley-elmer:/mnt/c/Users/sarah$ pwd
/mnt/c/Users/sarah
```

<span data-ttu-id="35bc1-126">这样，`wsl` 不仅可以保留当前工作目录，而且还允许结合 Windows 命令运行单个命令。</span><span class="sxs-lookup"><span data-stu-id="35bc1-126">Not only does `wsl` keep the current working directory in place, it lets you run a single command along side Windows commands.</span></span>

<span data-ttu-id="35bc1-127">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-127">**Example: (using PowerShell)**</span></span>

```console
PS C:\Users\sarah> Get-Date

Sunday, March 11, 2018 7:54:05 PM

PS C:\Users\sarah> wsl
scooley@scooley-elmer:/mnt/c/Users/sarah$ date
Sun Mar 11 19:55:47 DST 2018
scooley@scooley-elmer:/mnt/c/Users/sarah$ exit
logout

PS C:\Users\sarah> wsl date
Sun Mar 11 19:56:57 DST 2018
```

<span data-ttu-id="35bc1-128">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-128">**Example: (using PowerShell)**</span></span>

```console
PS C:\Users\sarah> Get-VM

Name            State CPUUsage(%) MemoryAssigned(M) Uptime   Status
----            ----- ----------- ----------------- ------   ------
Server17093     Off   0           0                 00:00:00 Opera...
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
Windows         Off   0           0                 00:00:00 Opera...


PS C:\Users\sarah> Get-VM | wsl grep "Ubuntu"
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
PS C:\Users\sarah>
```

## <a name="managing-multiple-linux-distributions"></a><span data-ttu-id="35bc1-129">管理多个 Linux 分发版</span><span class="sxs-lookup"><span data-stu-id="35bc1-129">Managing multiple Linux Distributions</span></span>

<span data-ttu-id="35bc1-130">在 Windows 10 版本 1903[及更高](ms-settings:windowsupdate)版本中，你可以使用在 `wsl.exe` 适用于 Linux 的 WINDOWS 子系统（WSL）中管理你的分发版，其中包括列出可用的分发、设置默认分发以及卸载分发。</span><span class="sxs-lookup"><span data-stu-id="35bc1-130">In Windows 10 Version 1903 [and later](ms-settings:windowsupdate), you can use `wsl.exe` to manage your distributions in the Windows Subsystem for Linux (WSL), including listing available distributions, setting a default distribution, and uninstalling distributions.</span></span>

<span data-ttu-id="35bc1-131">每个 Linux 分发版独立管理自身的配置。</span><span class="sxs-lookup"><span data-stu-id="35bc1-131">Each Linux distribution independently manages its own configurations.</span></span> <span data-ttu-id="35bc1-132">若要查看特定于分发版的命令，请运行 `[distro.exe] /?`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-132">To see distribution-specific commands, run `[distro.exe] /?`.</span></span>  <span data-ttu-id="35bc1-133">例如，`ubuntu /?`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-133">For example `ubuntu /?`.</span></span>

## <a name="list-distributions"></a><span data-ttu-id="35bc1-134">列出分发版</span><span class="sxs-lookup"><span data-stu-id="35bc1-134">List distributions</span></span>

<span data-ttu-id="35bc1-135">`wsl -l` , `wsl --list`</span><span class="sxs-lookup"><span data-stu-id="35bc1-135">`wsl -l` , `wsl --list`</span></span>  
<span data-ttu-id="35bc1-136">列出可用于 WSL 的 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-136">Lists available Linux distributions available to WSL.</span></span>  <span data-ttu-id="35bc1-137">如果列出了某个分发版，表示该分发版已安装且可供使用。</span><span class="sxs-lookup"><span data-stu-id="35bc1-137">If a distribution is listed, it's installed and ready to use.</span></span>

<span data-ttu-id="35bc1-138">`wsl --list --all`列出所有分发，包括当前不可用的分发。</span><span class="sxs-lookup"><span data-stu-id="35bc1-138">`wsl --list --all` Lists all distributions, including ones that aren't currently usable.</span></span>  <span data-ttu-id="35bc1-139">这些分发版可能正在安装、卸载或处于损坏状态。</span><span class="sxs-lookup"><span data-stu-id="35bc1-139">They may be in the process of installing, uninstalling, or are in a broken state.</span></span>  

<span data-ttu-id="35bc1-140">`wsl --list --running`列出当前正在运行的所有分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-140">`wsl --list --running` Lists all distributions that are currently running.</span></span>

## <a name="set-a-default-distribution"></a><span data-ttu-id="35bc1-141">设置默认分发版</span><span class="sxs-lookup"><span data-stu-id="35bc1-141">Set a default distribution</span></span>

<span data-ttu-id="35bc1-142">默认 WSL 分布版是在命令行中运行 `wsl` 时运行的分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-142">The default WSL distribution is the one that runs when you run `wsl` on a command line.</span></span>

<span data-ttu-id="35bc1-143">`wsl -s <DistributionName>`, `wsl --setdefault <DistributionName>`</span><span class="sxs-lookup"><span data-stu-id="35bc1-143">`wsl -s <DistributionName>`, `wsl --setdefault <DistributionName>`</span></span>

<span data-ttu-id="35bc1-144">将默认分发版设置为 `<DistributionName>`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-144">Sets the default distribution to `<DistributionName>`.</span></span>

<span data-ttu-id="35bc1-145">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-145">**Example: (using PowerShell)**</span></span>  
<span data-ttu-id="35bc1-146">`wsl -s Ubuntu` 会将我的默认分发版设置为 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-146">`wsl -s Ubuntu` would set my default distribution to Ubuntu.</span></span>  <span data-ttu-id="35bc1-147">现在，当我运行 `wsl npm init` 时，该分发版将在 Ubuntu 中运行。</span><span class="sxs-lookup"><span data-stu-id="35bc1-147">Now when I run `wsl npm init` it will run in Ubuntu.</span></span>  <span data-ttu-id="35bc1-148">如果我运行 `wsl`，它会打开 Ubuntu 会话。</span><span class="sxs-lookup"><span data-stu-id="35bc1-148">If I run `wsl` it will open an Ubuntu session.</span></span>

## <a name="unregister-and-reinstall-a-distribution"></a><span data-ttu-id="35bc1-149">取消注册和重新安装分发版</span><span class="sxs-lookup"><span data-stu-id="35bc1-149">Unregister and reinstall a distribution</span></span>

<span data-ttu-id="35bc1-150">尽管可以通过 Microsoft Store 安装 Linux 分发版，但无法通过 Store 将其卸载。</span><span class="sxs-lookup"><span data-stu-id="35bc1-150">While Linux distributions can be installed through the Microsoft store, they can't be uninstalled through the store.</span></span>  <span data-ttu-id="35bc1-151">可以通过 WSL Config 来取消注册/卸载分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-151">WSL Config allows distributions to be unregistered/uninstalled.</span></span>

<span data-ttu-id="35bc1-152">取消注册后，还可以重新安装分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-152">Unregistering also allows distributions to be reinstalled.</span></span>

> <span data-ttu-id="35bc1-153">**警告：** 注销后，与该分发关联的所有数据、设置和软件都将永久丢失。</span><span class="sxs-lookup"><span data-stu-id="35bc1-153">**Caution:** Once unregistered, all data, settings, and software associated with that distribution will be permanently lost.</span></span>  <span data-ttu-id="35bc1-154">从 Store 重新安装会安装分发版的干净副本。</span><span class="sxs-lookup"><span data-stu-id="35bc1-154">Reinstalling from the store will install a clean copy of the distribution.</span></span>

`wsl --unregister <DistributionName>`  
<span data-ttu-id="35bc1-155">从 WSL 中取消注册分发版，以便能够重新安装或清理它。</span><span class="sxs-lookup"><span data-stu-id="35bc1-155">Unregisters the distribution from WSL so it can be reinstalled or cleaned up.</span></span>

<span data-ttu-id="35bc1-156">例如：`wsl --unregister Ubuntu` 将从可用于 WSL 的分发版中删除 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-156">For example: `wsl --unregister Ubuntu` would remove Ubuntu from the distributions available in WSL.</span></span>  <span data-ttu-id="35bc1-157">运行 `wsl --list` 时，不再会列出 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-157">When I run `wsl --list` it will not be listed.</span></span>

<span data-ttu-id="35bc1-158">若要重新安装，请在 Microsoft Store 中找到该分发版，然后选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="35bc1-158">To reinstall, find the distribution in the Microsoft store and select "Launch".</span></span>

## <a name="run-as-a-specific-user"></a><span data-ttu-id="35bc1-159">以特定用户的身份运行</span><span class="sxs-lookup"><span data-stu-id="35bc1-159">Run as a specific user</span></span>

<span data-ttu-id="35bc1-160">`wsl -u <Username>`, `wsl --user <Username>`</span><span class="sxs-lookup"><span data-stu-id="35bc1-160">`wsl -u <Username>`, `wsl --user <Username>`</span></span>

<span data-ttu-id="35bc1-161">以指定用户的身份运行 WSL。</span><span class="sxs-lookup"><span data-stu-id="35bc1-161">Run WSL as the specified user.</span></span> <span data-ttu-id="35bc1-162">请注意，该用户必须存在于 WSL 分发版中。</span><span class="sxs-lookup"><span data-stu-id="35bc1-162">Please note that user must exist inside of the WSL distribution.</span></span>

## <a name="change-the-default-user-for-a-distribution"></a><span data-ttu-id="35bc1-163">更改分发的默认用户</span><span class="sxs-lookup"><span data-stu-id="35bc1-163">Change the default user for a distribution</span></span>

`<DistributionName> config --default-user <Username>`

<span data-ttu-id="35bc1-164">更改分发登录的默认用户。</span><span class="sxs-lookup"><span data-stu-id="35bc1-164">Change the default user that for your distribution log-in.</span></span> <span data-ttu-id="35bc1-165">为了成为默认用户，用户必须已在分发内存在。</span><span class="sxs-lookup"><span data-stu-id="35bc1-165">The user has to already exist inside the distribution in order to become the default user.</span></span> 

<span data-ttu-id="35bc1-166">例如： `ubuntu config --default-user johndoe` 会将 Ubuntu 分发的默认用户更改为 "johndoe" 用户。</span><span class="sxs-lookup"><span data-stu-id="35bc1-166">For example: `ubuntu config --default-user johndoe` would change the default user for the Ubuntu distribution to the "johndoe" user.</span></span>

> [!NOTE]
> <span data-ttu-id="35bc1-167">如果在找出分发的名称时遇到问题，请参阅命令的[列表分发](https://docs.microsoft.com/windows/wsl/wsl-config#list-distributions)以列出已安装的分发的正式名称。</span><span class="sxs-lookup"><span data-stu-id="35bc1-167">If you are having trouble figuring out the name of your distribution, see [List distributions](https://docs.microsoft.com/windows/wsl/wsl-config#list-distributions) for the command to list the official name of the installed distributions.</span></span> 

## <a name="run-a-specific-distribution"></a><span data-ttu-id="35bc1-168">运行特定的分发版</span><span class="sxs-lookup"><span data-stu-id="35bc1-168">Run a specific distribution</span></span>

<span data-ttu-id="35bc1-169">`wsl -d <DistributionName>`, `wsl --distribution <DistributionName>`</span><span class="sxs-lookup"><span data-stu-id="35bc1-169">`wsl -d <DistributionName>`, `wsl --distribution <DistributionName>`</span></span>

<span data-ttu-id="35bc1-170">运行 WSL 的指定分发版。可用于将命令发送到特定的分发版，而无需更改默认值。</span><span class="sxs-lookup"><span data-stu-id="35bc1-170">Run a specified distribution of WSL, can be used to send commands to a specific distribution without having to change your default.</span></span>

## <a name="managing-multiple-linux-distributions-in-earlier-windows-versions"></a><span data-ttu-id="35bc1-171">在早期 Windows 版本中管理多个 Linux 分发</span><span class="sxs-lookup"><span data-stu-id="35bc1-171">Managing multiple Linux Distributions in earlier Windows versions</span></span>

<span data-ttu-id="35bc1-172">在 Windows 10 版本1903之前，应使用 WSL Config （ `wslconfig.exe` ）命令行工具管理在适用于 linux 的 Windows 子系统（WSL）上运行的 linux 分发。</span><span class="sxs-lookup"><span data-stu-id="35bc1-172">In Windows 10 prior to version 1903, the WSL Config (`wslconfig.exe`) command-line tool should be used to manage Linux distributions running on the Windows Subsystem for Linux (WSL).</span></span>  <span data-ttu-id="35bc1-173">使用该工具可以列出可用分发版、设置默认分发和卸载分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-173">It lets you list available distributions, set a default distribution, and uninstall distributions.</span></span>

<span data-ttu-id="35bc1-174">尽管 WSL Config 对于跨越或协调分发版的设置有帮助，但每个 Linux 分发版会独立管理自身的配置。</span><span class="sxs-lookup"><span data-stu-id="35bc1-174">While WSL Config is helpful for settings that span or coordinate distributions, each Linux distribution independently manages its own configurations.</span></span>  <span data-ttu-id="35bc1-175">若要查看特定于分发版的命令，请运行 `[distro.exe] /?`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-175">To see distribution-specific commands, run `[distro.exe] /?`.</span></span>  <span data-ttu-id="35bc1-176">例如，`ubuntu /?`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-176">For example `ubuntu /?`.</span></span>

<span data-ttu-id="35bc1-177">若要查看 wslconfig 的所有可用选项，请运行：`wslconfig /?`</span><span class="sxs-lookup"><span data-stu-id="35bc1-177">To see all available options for wslconfig, run:  `wslconfig /?`</span></span>

```console
wslconfig.exe
Performs administrative operations on Windows Subsystem for Linux

Usage:
    /l, /list [/all] - Lists registered distributions.
        /all - Optionally list all distributions, including distributions that
               are currently being installed or uninstalled.
    /s, /setdefault <DistributionName> - Sets the specified distribution as the default.
    /u, /unregister <DistributionName> - Unregisters a distribution.
```

<span data-ttu-id="35bc1-178">若要列出分发，请使用：</span><span class="sxs-lookup"><span data-stu-id="35bc1-178">To list distributions, use:</span></span>

`wslconfig /list`  
<span data-ttu-id="35bc1-179">列出可用于 WSL 的 Linux 分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-179">Lists available Linux distributions available to WSL.</span></span>  <span data-ttu-id="35bc1-180">如果列出了某个分发版，表示该分发版已安装且可供使用。</span><span class="sxs-lookup"><span data-stu-id="35bc1-180">If a distribution is listed, it's installed and ready to use.</span></span>

`wslconfig /list /all`  
<span data-ttu-id="35bc1-181">列出所有分发版，包括当前不可用的分发版。</span><span class="sxs-lookup"><span data-stu-id="35bc1-181">Lists all distributions, including ones that aren't currently usable.</span></span>  <span data-ttu-id="35bc1-182">这些分发版可能正在安装、卸载或处于损坏状态。</span><span class="sxs-lookup"><span data-stu-id="35bc1-182">They may be in the process of installing, uninstalling, or are in a broken state.</span></span>  

<span data-ttu-id="35bc1-183">设置在命令行上运行时运行的默认分发 `wsl` ：</span><span class="sxs-lookup"><span data-stu-id="35bc1-183">To set a default distribution that runs when you run `wsl` on a command line:</span></span>

<span data-ttu-id="35bc1-184">`wslconfig /setdefault <DistributionName>`将默认分布设置为 `<DistributionName>` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-184">`wslconfig /setdefault <DistributionName>` Sets the default distribution to `<DistributionName>`.</span></span>

<span data-ttu-id="35bc1-185">**示例：（使用 PowerShell）**</span><span class="sxs-lookup"><span data-stu-id="35bc1-185">**Example: (using PowerShell)**</span></span>  
<span data-ttu-id="35bc1-186">`wslconfig /setdefault Ubuntu` 会将我的默认分发版设置为 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-186">`wslconfig /setdefault Ubuntu` would set my default distribution to Ubuntu.</span></span>  <span data-ttu-id="35bc1-187">现在，当我运行 `wsl npm init` 时，该分发版将在 Ubuntu 中运行。</span><span class="sxs-lookup"><span data-stu-id="35bc1-187">Now when I run `wsl npm init` it will run in Ubuntu.</span></span>  <span data-ttu-id="35bc1-188">如果我运行 `wsl`，它会打开 Ubuntu 会话。</span><span class="sxs-lookup"><span data-stu-id="35bc1-188">If I run `wsl` it will open an Ubuntu session.</span></span>

<span data-ttu-id="35bc1-189">若要注销并重新安装分发：</span><span class="sxs-lookup"><span data-stu-id="35bc1-189">To unregister and reinstall a distribution:</span></span>

`wslconfig /unregister <DistributionName>`  
<span data-ttu-id="35bc1-190">从 WSL 中取消注册分发版，以便能够重新安装或清理它。</span><span class="sxs-lookup"><span data-stu-id="35bc1-190">Unregisters the distribution from WSL so it can be reinstalled or cleaned up.</span></span>

<span data-ttu-id="35bc1-191">例如：`wslconfig /unregister Ubuntu` 将从可用于 WSL 的分发版中删除 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-191">For example: `wslconfig /unregister Ubuntu` would remove Ubuntu from the distributions available in WSL.</span></span>  <span data-ttu-id="35bc1-192">运行 `wslconfig /list` 时，不再会列出 Ubuntu。</span><span class="sxs-lookup"><span data-stu-id="35bc1-192">When I run `wslconfig /list` it will not be listed.</span></span>

<span data-ttu-id="35bc1-193">若要重新安装，请在 Microsoft Store 中找到该分发版，然后选择“启动”。</span><span class="sxs-lookup"><span data-stu-id="35bc1-193">To reinstall, find the distribution in the Microsoft store and select "Launch".</span></span>

## <a name="configure-per-distro-launch-settings-with-wslconf"></a><span data-ttu-id="35bc1-194">通过 wslconf 配置每个发行版启动设置</span><span class="sxs-lookup"><span data-stu-id="35bc1-194">Configure per distro launch settings with wslconf</span></span>

> <span data-ttu-id="35bc1-195">**在 Windows 版本17093及更高版本中可用**</span><span class="sxs-lookup"><span data-stu-id="35bc1-195">**Available in Windows Build 17093 and later**</span></span>

<span data-ttu-id="35bc1-196">使用 `wsl.conf` 自动配置 WSL 中每次启动子系统时要应用的某些功能。</span><span class="sxs-lookup"><span data-stu-id="35bc1-196">Automatically configure certain functionality in WSL that will be applied every time you launch the subsystem using `wsl.conf`.</span></span>

<span data-ttu-id="35bc1-197">目前，这包括自动装载选项和网络配置。</span><span class="sxs-lookup"><span data-stu-id="35bc1-197">Right now, this includes automount options and network configuration.</span></span>

<span data-ttu-id="35bc1-198">`wsl.conf` 位于每个 Linux 分发版的 `/etc/wsl.conf` 中。</span><span class="sxs-lookup"><span data-stu-id="35bc1-198">`wsl.conf` is located in each Linux distribution in `/etc/wsl.conf`.</span></span> <span data-ttu-id="35bc1-199">如果该文件不存在，你可以自行创建。</span><span class="sxs-lookup"><span data-stu-id="35bc1-199">If the file is not there, you can create it yourself.</span></span> <span data-ttu-id="35bc1-200">WSL 会检测该文件是否存在，并读取其内容。</span><span class="sxs-lookup"><span data-stu-id="35bc1-200">WSL will detect the existence of the file and will read its contents.</span></span> <span data-ttu-id="35bc1-201">如果该文件缺失或格式不正确（即，标记格式不正确），WSL 将继续如常启动。</span><span class="sxs-lookup"><span data-stu-id="35bc1-201">If the file is missing or malformed (that is, improper markup formatting), WSL will continue to launch as normal.</span></span>

<span data-ttu-id="35bc1-202">下面是可以 `wsl.conf` 添加到分发的示例文件：</span><span class="sxs-lookup"><span data-stu-id="35bc1-202">Here is a sample `wsl.conf` file you could add into your distributions:</span></span>

```console
# Enable extra metadata options by default
[automount]
enabled = true
root = /windir/
options = "metadata,umask=22,fmask=11"
mountFsTab = false

# Enable DNS – even though these are turned on by default, we'll specify here just to be explicit.
[network]
generateHosts = true
generateResolvConf = true
```

### <a name="configuration-options"></a><span data-ttu-id="35bc1-203">配置选项</span><span class="sxs-lookup"><span data-stu-id="35bc1-203">Configuration Options</span></span>

<span data-ttu-id="35bc1-204">为了遵守 .ini 约定，键将在某个节下声明。</span><span class="sxs-lookup"><span data-stu-id="35bc1-204">In keeping with .ini conventions, keys are declared under a section.</span></span> 

<span data-ttu-id="35bc1-205">WSL 支持两个节：`automount` 和 `network`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-205">WSL supports two sections: `automount` and `network`.</span></span>

#### <a name="automount"></a><span data-ttu-id="35bc1-206">automount</span><span class="sxs-lookup"><span data-stu-id="35bc1-206">automount</span></span>

<span data-ttu-id="35bc1-207">节：`[automount]`</span><span class="sxs-lookup"><span data-stu-id="35bc1-207">Section: `[automount]`</span></span>

| <span data-ttu-id="35bc1-208">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-208">key</span></span>        | <span data-ttu-id="35bc1-209">value</span><span class="sxs-lookup"><span data-stu-id="35bc1-209">value</span></span>                          | <span data-ttu-id="35bc1-210">默认</span><span class="sxs-lookup"><span data-stu-id="35bc1-210">default</span></span>      | <span data-ttu-id="35bc1-211">备注</span><span class="sxs-lookup"><span data-stu-id="35bc1-211">notes</span></span>                                                                                                                                                                                                                                                                                                                          |
|:-----------|:-------------------------------|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="35bc1-212">已启用</span><span class="sxs-lookup"><span data-stu-id="35bc1-212">enabled</span></span>    | <span data-ttu-id="35bc1-213">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-213">boolean</span></span>                        | <span data-ttu-id="35bc1-214">true</span><span class="sxs-lookup"><span data-stu-id="35bc1-214">true</span></span>         | <span data-ttu-id="35bc1-215">`true` 导致固定驱动器（即</span><span class="sxs-lookup"><span data-stu-id="35bc1-215">`true` causes fixed drives (i.e</span></span> <span data-ttu-id="35bc1-216">`C:/` 或 `D:/`）自动装载到 DrvFs 中的 `/mnt` 下。</span><span class="sxs-lookup"><span data-stu-id="35bc1-216">`C:/` or `D:/`) to be automatically mounted with DrvFs under `/mnt`.</span></span>  <span data-ttu-id="35bc1-217">`false`表示不会自动装入驱动器，但你仍然可以手动或通过手动装载它们 `fstab` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-217">`false` means drives won't be mounted automatically, but you could still mount them manually or via `fstab`.</span></span>                                                                                                             |
| <span data-ttu-id="35bc1-218">mountFsTab</span><span class="sxs-lookup"><span data-stu-id="35bc1-218">mountFsTab</span></span> | <span data-ttu-id="35bc1-219">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-219">boolean</span></span>                        | <span data-ttu-id="35bc1-220">true</span><span class="sxs-lookup"><span data-stu-id="35bc1-220">true</span></span>         | <span data-ttu-id="35bc1-221">`true` 设置启动 WSL 时要处理的 `/etc/fstab`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-221">`true` sets `/etc/fstab` to be processed on WSL start.</span></span> <span data-ttu-id="35bc1-222">/etc/fstab 是可在其中声明其他文件系统的文件，类似于 SMB 共享。</span><span class="sxs-lookup"><span data-stu-id="35bc1-222">/etc/fstab is a file where you can declare other filesystems, like an SMB share.</span></span> <span data-ttu-id="35bc1-223">因此，在启动时，可以在 WSL 中自动装载这些文件系统。</span><span class="sxs-lookup"><span data-stu-id="35bc1-223">Thus, you can mount these filesystems automatically in WSL on start up.</span></span>                                                                                                                |
| <span data-ttu-id="35bc1-224">root</span><span class="sxs-lookup"><span data-stu-id="35bc1-224">root</span></span>       | <span data-ttu-id="35bc1-225">字符串</span><span class="sxs-lookup"><span data-stu-id="35bc1-225">String</span></span>                         | `/mnt/`      | <span data-ttu-id="35bc1-226">设置固定驱动器要自动装载到的目录。</span><span class="sxs-lookup"><span data-stu-id="35bc1-226">Sets the directory where fixed drives will be automatically mounted.</span></span> <span data-ttu-id="35bc1-227">例如，如果 WSL 中的某个目录位于 `/windir/`，而你将该目录指定为根目录，则固定驱动器预期会装载到 `/windir/c`</span><span class="sxs-lookup"><span data-stu-id="35bc1-227">For example, if you have a directory in WSL at `/windir/` and you specify that as the root, you would expect to see your fixed drives mounted at `/windir/c`</span></span>                                                                                              |
| <span data-ttu-id="35bc1-228">选项</span><span class="sxs-lookup"><span data-stu-id="35bc1-228">options</span></span>    | <span data-ttu-id="35bc1-229">逗号分隔值列表</span><span class="sxs-lookup"><span data-stu-id="35bc1-229">comma-separated list of values</span></span> | <span data-ttu-id="35bc1-230">空字符串</span><span class="sxs-lookup"><span data-stu-id="35bc1-230">empty string</span></span> | <span data-ttu-id="35bc1-231">此值将追加到默认的 DrvFs 装载选项字符串。</span><span class="sxs-lookup"><span data-stu-id="35bc1-231">This value is appended to the default DrvFs mount options string.</span></span> <span data-ttu-id="35bc1-232">**只能指定特定于 DrvFs 的选项。**</span><span class="sxs-lookup"><span data-stu-id="35bc1-232">**Only DrvFs-specific options can be specified.**</span></span> <span data-ttu-id="35bc1-233">通常由装载二进制文件分析成标志的选项不受支持。</span><span class="sxs-lookup"><span data-stu-id="35bc1-233">Options that the mount binary would normally parse into a flag are not supported.</span></span> <span data-ttu-id="35bc1-234">若要显式指定这些选项，必须在 /etc/fstab 中包含要对其执行此操作的每个驱动器。</span><span class="sxs-lookup"><span data-stu-id="35bc1-234">If you want to explicitly specify those options, you must include every drive for which you want to do so in /etc/fstab.</span></span> |

<span data-ttu-id="35bc1-235">默认情况下，WSL 会将 uid 和 gid 设置为默认用户的值（在 Ubuntu 分发版中，默认用户是使用 uid=1000,gid=1000 创建的）。</span><span class="sxs-lookup"><span data-stu-id="35bc1-235">By default, WSL sets the uid and gid to the value of the default user (in Ubuntu distro, the default user is created with uid=1000,gid=1000).</span></span> <span data-ttu-id="35bc1-236">如果用户通过此键显式指定了 gid 或 uid 选项，将覆盖关联的值。</span><span class="sxs-lookup"><span data-stu-id="35bc1-236">If the user specifies a gid or uid option explicitly via this key, the associated value will be overwritten.</span></span> <span data-ttu-id="35bc1-237">否则，将始终追加默认值。</span><span class="sxs-lookup"><span data-stu-id="35bc1-237">Otherwise, the default value will always be appended.</span></span>

<span data-ttu-id="35bc1-238">**注意：** 对于所有自动装载的驱动器，这些选项将应用为装载选项。</span><span class="sxs-lookup"><span data-stu-id="35bc1-238">**Note:** These options are applied as the mount options for all automatically mounted drives.</span></span> <span data-ttu-id="35bc1-239">如果只想更改特定驱动器的选项，请改用 /etc/fstab。</span><span class="sxs-lookup"><span data-stu-id="35bc1-239">To change the options for a specific drive only, use /etc/fstab instead.</span></span>

#### <a name="mount-options"></a><span data-ttu-id="35bc1-240">装载选项</span><span class="sxs-lookup"><span data-stu-id="35bc1-240">Mount options</span></span>

<span data-ttu-id="35bc1-241">为 Windows 驱动器 (DrvFs) 设置不同的装载选项可以控制为 Windows 文件计算文件权限的方式。</span><span class="sxs-lookup"><span data-stu-id="35bc1-241">Setting different mount options for Windows drives (DrvFs) can control how file permissions are calculated for Windows files.</span></span> <span data-ttu-id="35bc1-242">你可使用以下选项：</span><span class="sxs-lookup"><span data-stu-id="35bc1-242">The following options are available:</span></span>

| <span data-ttu-id="35bc1-243">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-243">Key</span></span> | <span data-ttu-id="35bc1-244">说明</span><span class="sxs-lookup"><span data-stu-id="35bc1-244">Description</span></span> | <span data-ttu-id="35bc1-245">默认值</span><span class="sxs-lookup"><span data-stu-id="35bc1-245">Default</span></span> |
|:----|:----|:----|
|<span data-ttu-id="35bc1-246">uid</span><span class="sxs-lookup"><span data-stu-id="35bc1-246">uid</span></span>| <span data-ttu-id="35bc1-247">用于所有文件的所有者的用户 ID</span><span class="sxs-lookup"><span data-stu-id="35bc1-247">The User ID used for the owner of all files</span></span> | <span data-ttu-id="35bc1-248">WSL 发行版的默认用户 ID（第一次安装时，此项默认为 1000）</span><span class="sxs-lookup"><span data-stu-id="35bc1-248">The default User ID of your WSL distro (On first installation this defaults to 1000)</span></span>
|<span data-ttu-id="35bc1-249">gid</span><span class="sxs-lookup"><span data-stu-id="35bc1-249">gid</span></span>| <span data-ttu-id="35bc1-250">用于所有文件的所有者的组 ID</span><span class="sxs-lookup"><span data-stu-id="35bc1-250">The Group ID used for the owner of all files</span></span> | <span data-ttu-id="35bc1-251">WSL 发行版的默认组 ID（第一次安装时，此项默认为 1000）</span><span class="sxs-lookup"><span data-stu-id="35bc1-251">The default group ID of your WSL distro (On first installation this defaults to 1000)</span></span>
|<span data-ttu-id="35bc1-252">umask</span><span class="sxs-lookup"><span data-stu-id="35bc1-252">umask</span></span> | <span data-ttu-id="35bc1-253">要对所有文件和目录排除的权限的八进制掩码</span><span class="sxs-lookup"><span data-stu-id="35bc1-253">An octal mask of permissions to exclude for all files and directories</span></span> | <span data-ttu-id="35bc1-254">000</span><span class="sxs-lookup"><span data-stu-id="35bc1-254">000</span></span>
|<span data-ttu-id="35bc1-255">fmask</span><span class="sxs-lookup"><span data-stu-id="35bc1-255">fmask</span></span> | <span data-ttu-id="35bc1-256">要对所有文件排除的权限的八进制掩码</span><span class="sxs-lookup"><span data-stu-id="35bc1-256">An octal mask of permissions to exclude for all files</span></span> | <span data-ttu-id="35bc1-257">000</span><span class="sxs-lookup"><span data-stu-id="35bc1-257">000</span></span>
|<span data-ttu-id="35bc1-258">dmask</span><span class="sxs-lookup"><span data-stu-id="35bc1-258">dmask</span></span> | <span data-ttu-id="35bc1-259">要对所有目录排除的权限的八进制掩码</span><span class="sxs-lookup"><span data-stu-id="35bc1-259">An octal mask of permissions to exclude for all directories</span></span> | <span data-ttu-id="35bc1-260">000</span><span class="sxs-lookup"><span data-stu-id="35bc1-260">000</span></span>

<span data-ttu-id="35bc1-261">**注意：** 权限掩码在应用到文件或目录之前通过一个逻辑或操作进行设置。</span><span class="sxs-lookup"><span data-stu-id="35bc1-261">**Note:** The permission masks are put through a logical OR operation before being applied to files or directories.</span></span> 

#### <a name="network"></a><span data-ttu-id="35bc1-262">网络</span><span class="sxs-lookup"><span data-stu-id="35bc1-262">network</span></span>

<span data-ttu-id="35bc1-263">节标签：`[network]`</span><span class="sxs-lookup"><span data-stu-id="35bc1-263">Section label: `[network]`</span></span>

| <span data-ttu-id="35bc1-264">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-264">key</span></span> | <span data-ttu-id="35bc1-265">value</span><span class="sxs-lookup"><span data-stu-id="35bc1-265">value</span></span> | <span data-ttu-id="35bc1-266">默认</span><span class="sxs-lookup"><span data-stu-id="35bc1-266">default</span></span> | <span data-ttu-id="35bc1-267">备注</span><span class="sxs-lookup"><span data-stu-id="35bc1-267">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="35bc1-268">generateHosts</span><span class="sxs-lookup"><span data-stu-id="35bc1-268">generateHosts</span></span> | <span data-ttu-id="35bc1-269">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-269">boolean</span></span> | `true` | <span data-ttu-id="35bc1-270">`true` 将 WSL 设置为生成 `/etc/hosts`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-270">`true` sets WSL to generate `/etc/hosts`.</span></span> <span data-ttu-id="35bc1-271">`hosts` 文件包含主机名对应的 IP 地址的静态映射。</span><span class="sxs-lookup"><span data-stu-id="35bc1-271">The `hosts` file contains a static map of hostnames corresponding IP address.</span></span> |
| <span data-ttu-id="35bc1-272">generateResolvConf</span><span class="sxs-lookup"><span data-stu-id="35bc1-272">generateResolvConf</span></span> | <span data-ttu-id="35bc1-273">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-273">boolean</span></span> | `true` | <span data-ttu-id="35bc1-274">`true` 将 WSL 设置为生成 `/etc/resolv.conf`。</span><span class="sxs-lookup"><span data-stu-id="35bc1-274">`true` set WSL to generate `/etc/resolv.conf`.</span></span> <span data-ttu-id="35bc1-275">`resolv.conf` 包含能够将给定主机名解析为其 IP 地址的 DNS 列表。</span><span class="sxs-lookup"><span data-stu-id="35bc1-275">The `resolv.conf` contains a DNS list that are capable of resolving a given hostname to its IP address.</span></span> | 

#### <a name="interop"></a><span data-ttu-id="35bc1-276">interop</span><span class="sxs-lookup"><span data-stu-id="35bc1-276">interop</span></span>

<span data-ttu-id="35bc1-277">节标签：`[interop]`</span><span class="sxs-lookup"><span data-stu-id="35bc1-277">Section label: `[interop]`</span></span>

<span data-ttu-id="35bc1-278">这些选项在预览体验成员内部版本 17713 和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="35bc1-278">These options are available in Insider Build 17713 and later.</span></span>

| <span data-ttu-id="35bc1-279">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-279">key</span></span> | <span data-ttu-id="35bc1-280">value</span><span class="sxs-lookup"><span data-stu-id="35bc1-280">value</span></span> | <span data-ttu-id="35bc1-281">默认</span><span class="sxs-lookup"><span data-stu-id="35bc1-281">default</span></span> | <span data-ttu-id="35bc1-282">备注</span><span class="sxs-lookup"><span data-stu-id="35bc1-282">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="35bc1-283">已启用</span><span class="sxs-lookup"><span data-stu-id="35bc1-283">enabled</span></span> | <span data-ttu-id="35bc1-284">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-284">boolean</span></span> | `true` | <span data-ttu-id="35bc1-285">设置此键可确定 WSL 是否支持启动 Windows 进程。</span><span class="sxs-lookup"><span data-stu-id="35bc1-285">Setting this key will determine whether WSL will support launching Windows processes.</span></span> |
| <span data-ttu-id="35bc1-286">appendWindowsPath</span><span class="sxs-lookup"><span data-stu-id="35bc1-286">appendWindowsPath</span></span> | <span data-ttu-id="35bc1-287">布尔值</span><span class="sxs-lookup"><span data-stu-id="35bc1-287">boolean</span></span> | `true` | <span data-ttu-id="35bc1-288">设置此键可确定 WSL 是否会将 Windows 路径元素添加到 $PATH 环境变量。</span><span class="sxs-lookup"><span data-stu-id="35bc1-288">Setting this key will determine whether WSL will add Windows path elements to the $PATH environment variable.</span></span> |

#### <a name="user"></a><span data-ttu-id="35bc1-289">user</span><span class="sxs-lookup"><span data-stu-id="35bc1-289">user</span></span>

<span data-ttu-id="35bc1-290">节标签：`[user]`</span><span class="sxs-lookup"><span data-stu-id="35bc1-290">Section label: `[user]`</span></span>

<span data-ttu-id="35bc1-291">这些选项在版本18980和更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="35bc1-291">These options are available in Build 18980 and later.</span></span>

| <span data-ttu-id="35bc1-292">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-292">key</span></span> | <span data-ttu-id="35bc1-293">值</span><span class="sxs-lookup"><span data-stu-id="35bc1-293">value</span></span> | <span data-ttu-id="35bc1-294">默认值</span><span class="sxs-lookup"><span data-stu-id="35bc1-294">default</span></span> | <span data-ttu-id="35bc1-295">说明</span><span class="sxs-lookup"><span data-stu-id="35bc1-295">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="35bc1-296">默认值</span><span class="sxs-lookup"><span data-stu-id="35bc1-296">default</span></span> | <span data-ttu-id="35bc1-297">string</span><span class="sxs-lookup"><span data-stu-id="35bc1-297">string</span></span> | <span data-ttu-id="35bc1-298">首次运行时创建的初始用户名</span><span class="sxs-lookup"><span data-stu-id="35bc1-298">The initial username created on first run</span></span> | <span data-ttu-id="35bc1-299">设置此项将指定在首次启动 WSL 会话时要运行的用户。</span><span class="sxs-lookup"><span data-stu-id="35bc1-299">Setting this key specifies which user to run as when first starting a WSL session.</span></span> |

## <a name="configure-global-options-with-wslconfig"></a><span data-ttu-id="35bc1-300">用 wslconfig 配置全局选项。</span><span class="sxs-lookup"><span data-stu-id="35bc1-300">Configure global options with .wslconfig</span></span>

> <span data-ttu-id="35bc1-301">**在 Windows 版本19041及更高版本中可用**</span><span class="sxs-lookup"><span data-stu-id="35bc1-301">**Available in Windows Build 19041 and later**</span></span>

<span data-ttu-id="35bc1-302">可以通过将文件放入用户文件夹的根目录来配置全局 WSL 选项 `.wslconfig` ： `C:\Users\<yourUserName>\.wslconfig` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-302">You can configure global WSL options by placing a `.wslconfig` file into the root directory of your users folder: `C:\Users\<yourUserName>\.wslconfig`.</span></span> <span data-ttu-id="35bc1-303">其中许多文件都与 WSL 2 相关，请记住，你可能需要运行 `wsl --shutdown` 以关闭 WSL 2 VM，然后重新启动 WSL 实例，这些更改才会生效。</span><span class="sxs-lookup"><span data-stu-id="35bc1-303">Many of these files are related to WSL 2, please keep in mind you may need to run `wsl --shutdown` to shut down the WSL 2 VM and then restart your WSL instance for these changes to take affect.</span></span>

<span data-ttu-id="35bc1-304">下面是 wslconfig 文件的示例：</span><span class="sxs-lookup"><span data-stu-id="35bc1-304">Here is a sample .wslconfig file:</span></span>

```console
[wsl2]
kernel=C:\\temp\\myCustomKernel
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=2 # Makes the WSL 2 VM use two virtual processors
```

<span data-ttu-id="35bc1-305">此文件可以包含以下选项：</span><span class="sxs-lookup"><span data-stu-id="35bc1-305">This file can contain the following options:</span></span>

### <a name="wsl-2-settings"></a><span data-ttu-id="35bc1-306">WSL 2 设置</span><span class="sxs-lookup"><span data-stu-id="35bc1-306">WSL 2 Settings</span></span>

<span data-ttu-id="35bc1-307">节标签：`[wsl2]`</span><span class="sxs-lookup"><span data-stu-id="35bc1-307">Section label: `[wsl2]`</span></span>

<span data-ttu-id="35bc1-308">这些设置会影响支持任何 WSL 2 分发的虚拟机。</span><span class="sxs-lookup"><span data-stu-id="35bc1-308">These settings affect the VM that powers any WSL 2 distribution.</span></span>

| <span data-ttu-id="35bc1-309">键</span><span class="sxs-lookup"><span data-stu-id="35bc1-309">key</span></span> | <span data-ttu-id="35bc1-310">值</span><span class="sxs-lookup"><span data-stu-id="35bc1-310">value</span></span> | <span data-ttu-id="35bc1-311">默认值</span><span class="sxs-lookup"><span data-stu-id="35bc1-311">default</span></span> | <span data-ttu-id="35bc1-312">说明</span><span class="sxs-lookup"><span data-stu-id="35bc1-312">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="35bc1-313">内核 (kernel)</span><span class="sxs-lookup"><span data-stu-id="35bc1-313">kernel</span></span> | <span data-ttu-id="35bc1-314">string</span><span class="sxs-lookup"><span data-stu-id="35bc1-314">string</span></span> | <span data-ttu-id="35bc1-315">Microsoft 构建的内核提供的收件箱</span><span class="sxs-lookup"><span data-stu-id="35bc1-315">The Microsoft built kernel provided inbox</span></span> | <span data-ttu-id="35bc1-316">自定义 Linux 内核的绝对 Windows 路径。</span><span class="sxs-lookup"><span data-stu-id="35bc1-316">An absolute Windows path to a custom Linux kernel.</span></span> |
| <span data-ttu-id="35bc1-317">memory</span><span class="sxs-lookup"><span data-stu-id="35bc1-317">memory</span></span> | <span data-ttu-id="35bc1-318">大小</span><span class="sxs-lookup"><span data-stu-id="35bc1-318">size</span></span> | <span data-ttu-id="35bc1-319">Windows 上的总内存的80%</span><span class="sxs-lookup"><span data-stu-id="35bc1-319">80% of your total memory on Windows</span></span> | <span data-ttu-id="35bc1-320">要分配给 WSL 2 VM 的内存量。</span><span class="sxs-lookup"><span data-stu-id="35bc1-320">How much memory to assign to the WSL 2 VM.</span></span> |
| <span data-ttu-id="35bc1-321">款</span><span class="sxs-lookup"><span data-stu-id="35bc1-321">processors</span></span> | <span data-ttu-id="35bc1-322">number</span><span class="sxs-lookup"><span data-stu-id="35bc1-322">number</span></span> | <span data-ttu-id="35bc1-323">Windows 上的处理器数相同</span><span class="sxs-lookup"><span data-stu-id="35bc1-323">The same number of processors on Windows</span></span> | <span data-ttu-id="35bc1-324">要分配给 WSL 2 VM 的处理器数量。</span><span class="sxs-lookup"><span data-stu-id="35bc1-324">How many processors to assign to the WSL 2 VM.</span></span> |
| <span data-ttu-id="35bc1-325">localhostForwarding</span><span class="sxs-lookup"><span data-stu-id="35bc1-325">localhostForwarding</span></span> | <span data-ttu-id="35bc1-326">boolean</span><span class="sxs-lookup"><span data-stu-id="35bc1-326">boolean</span></span> | `true` | <span data-ttu-id="35bc1-327">布尔值，指定是否应通过 localhost： port 将绑定到 WSL 2 VM 中的通配符或 localhost 的端口连接到主机。</span><span class="sxs-lookup"><span data-stu-id="35bc1-327">Boolean specifying if ports bound to wildcard or localhost in the WSL 2 VM should be connectable from the host via localhost:port.</span></span> |
| <span data-ttu-id="35bc1-328">kernelCommandLine</span><span class="sxs-lookup"><span data-stu-id="35bc1-328">kernelCommandLine</span></span> | <span data-ttu-id="35bc1-329">string</span><span class="sxs-lookup"><span data-stu-id="35bc1-329">string</span></span> | <span data-ttu-id="35bc1-330">空</span><span class="sxs-lookup"><span data-stu-id="35bc1-330">Blank</span></span> | <span data-ttu-id="35bc1-331">其他内核命令行参数。</span><span class="sxs-lookup"><span data-stu-id="35bc1-331">Additional kernel command line arguments.</span></span> |
| <span data-ttu-id="35bc1-332">swap</span><span class="sxs-lookup"><span data-stu-id="35bc1-332">swap</span></span> | <span data-ttu-id="35bc1-333">大小</span><span class="sxs-lookup"><span data-stu-id="35bc1-333">size</span></span> | <span data-ttu-id="35bc1-334">Windows 上的25% 内存大小向上舍入到最接近的 GB</span><span class="sxs-lookup"><span data-stu-id="35bc1-334">25% of memory size on Windows rounded up to the nearest GB</span></span> | <span data-ttu-id="35bc1-335">要添加到 WSL 2 VM 的交换空间量，0表示没有交换文件。</span><span class="sxs-lookup"><span data-stu-id="35bc1-335">How much swap space to add to the WSL 2 VM, 0 for no swap file.</span></span> |
| <span data-ttu-id="35bc1-336">交换文件</span><span class="sxs-lookup"><span data-stu-id="35bc1-336">swapFile</span></span> | <span data-ttu-id="35bc1-337">string</span><span class="sxs-lookup"><span data-stu-id="35bc1-337">string</span></span> | <span data-ttu-id="35bc1-338">%USERPROFILE%\AppData\Local\Temp\swap.vhdx</span><span class="sxs-lookup"><span data-stu-id="35bc1-338">%USERPROFILE%\AppData\Local\Temp\swap.vhdx</span></span> | <span data-ttu-id="35bc1-339">交换虚拟硬盘的绝对 Windows 路径。</span><span class="sxs-lookup"><span data-stu-id="35bc1-339">An absolute Windows path to the swap virtual hard disk.</span></span> |

<span data-ttu-id="35bc1-340">值为的项 `path` 必须是包含转义反斜杠的 Windows 路径，例如：`C:\\Temp\\myCustomKernel`</span><span class="sxs-lookup"><span data-stu-id="35bc1-340">Entries with the `path` value must be Windows paths with escaped backslashes, e.g: `C:\\Temp\\myCustomKernel`</span></span>

<span data-ttu-id="35bc1-341">具有值的项 `size` 必须是后跟一个单位的大小，例如 `8GB` 或 `512MB` 。</span><span class="sxs-lookup"><span data-stu-id="35bc1-341">Entries with the `size` value must be a size followed by a unit, for example `8GB` or `512MB`.</span></span>
