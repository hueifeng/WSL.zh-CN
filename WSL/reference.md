---
title: 适用于 Linux 的 Windows 子系统命令参考
description: 用于管理适用于 Linux 的 Windows 子系统的命令列表
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu
ms.date: 07/31/2017
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 72b78a73bf68b28dd14b4826943a0c81ea04bbad
ms.sourcegitcommit: 1b6191351bbf9e95f3c28fc67abe4bf1bcfd3336
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83270871"
---
# <a name="command-reference-for-windows-subsystem-for-linux"></a><span data-ttu-id="e387f-104">适用于 Linux 的 Windows 子系统的命令参考</span><span class="sxs-lookup"><span data-stu-id="e387f-104">Command Reference for Windows Subsystem for Linux</span></span>

<span data-ttu-id="e387f-105">与适用于 Linux 的 Windows 子系统交互的最佳方式是使用 `wsl.exe` 命令。</span><span class="sxs-lookup"><span data-stu-id="e387f-105">The best way to interact with the Windows Subsystem for Linux is to use the `wsl.exe` command.</span></span>

## <a name="set-wsl-2-as-your-default-version"></a><span data-ttu-id="e387f-106">将 WSL 2 设置为默认版本</span><span class="sxs-lookup"><span data-stu-id="e387f-106">Set WSL 2 as your default version</span></span>

<span data-ttu-id="e387f-107">安装新的 Linux 分发版时，请在 Powershell 中运行以下命令，以将 WSL 2 设置为默认版本：</span><span class="sxs-lookup"><span data-stu-id="e387f-107">Run the following command in Powershell to set WSL 2 as the default version when installing a new Linux distribution:</span></span>

```powershell
wsl --set-default-version 2
```

## <a name="set-your-distribution-version-to-wsl-1-or-wsl-2"></a><span data-ttu-id="e387f-108">将分发版版本设置为 WSL 1 或 WSL 2</span><span class="sxs-lookup"><span data-stu-id="e387f-108">Set your distribution version to WSL 1 or WSL 2</span></span>

<span data-ttu-id="e387f-109">可以打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 19041 或更高版本](ms-settings:windowsupdate)中可用），来检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`</span><span class="sxs-lookup"><span data-stu-id="e387f-109">You can check the WSL version assigned to each of the Linux distributions you have installed by opening the PowerShell command line and entering the command (only available in [Windows Build 19041 or higher](ms-settings:windowsupdate)): `wsl -l -v`</span></span>

```bash
wsl --list --verbose
```

<span data-ttu-id="e387f-110">若要将分发版设置为受某一 WSL 版本支持，请运行：</span><span class="sxs-lookup"><span data-stu-id="e387f-110">To set a distribution to be backed by either version of WSL please run:</span></span>

```bash
wsl --set-version <distribution name> <versionNumber>
```

<span data-ttu-id="e387f-111">请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字“1”或“2”。</span><span class="sxs-lookup"><span data-stu-id="e387f-111">Make sure to replace `<distribution name>` with the actual name of your distribution and `<versionNumber>` with the number '1' or '2'.</span></span> <span data-ttu-id="e387f-112">可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将“2”替换为“1”。</span><span class="sxs-lookup"><span data-stu-id="e387f-112">You can change back to WSL 1 at anytime by running the same command as above but replacing the '2' with a '1'.</span></span>

<span data-ttu-id="e387f-113">此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：</span><span class="sxs-lookup"><span data-stu-id="e387f-113">Additionally, if you want to make WSL 2 your default architecture you can do so with this command:</span></span>

```bash
wsl --set-default-version 2
```

<span data-ttu-id="e387f-114">这会将安装的任何新分发版的版本设置为 WSL 2。</span><span class="sxs-lookup"><span data-stu-id="e387f-114">This will set the version of any new distribution installed to WSL 2.</span></span>

## `wsl.exe`

<span data-ttu-id="e387f-115">以下列表包含自 Windows 版本 1903 开始，在使用 `wsl.exe` 时可用的所有选项。</span><span class="sxs-lookup"><span data-stu-id="e387f-115">Below is a list containing all options when using `wsl.exe` as of Windows Version 1903.</span></span>

<span data-ttu-id="e387f-116">使用：`wsl [Argument] [Options...] [CommandLine]`</span><span class="sxs-lookup"><span data-stu-id="e387f-116">Using: `wsl [Argument] [Options...] [CommandLine]`</span></span>

### <a name="arguments-for-running-linux-commands"></a><span data-ttu-id="e387f-117">用于运行 Linux 命令的参数</span><span class="sxs-lookup"><span data-stu-id="e387f-117">Arguments for running Linux commands</span></span>

* <span data-ttu-id="e387f-118">**不带参数**</span><span class="sxs-lookup"><span data-stu-id="e387f-118">**Without arguments**</span></span>

  <span data-ttu-id="e387f-119">如果未提供命令行，wsl.exe 将启动默认 shell。</span><span class="sxs-lookup"><span data-stu-id="e387f-119">If no command line is provided, wsl.exe launches the default shell.</span></span>

* <span data-ttu-id="e387f-120">**--exec、-e \<命令行>**</span><span class="sxs-lookup"><span data-stu-id="e387f-120">**--exec, -e \<CommandLine>**</span></span>
  
  <span data-ttu-id="e387f-121">执行指定的命令，但不使用默认的 Linux shell。</span><span class="sxs-lookup"><span data-stu-id="e387f-121">Execute the specified command without using the default Linux shell.</span></span>

* **--**
  
  <span data-ttu-id="e387f-122">按原样传递剩余的命令行。</span><span class="sxs-lookup"><span data-stu-id="e387f-122">Pass the remaining command line as is.</span></span>

<span data-ttu-id="e387f-123">上述命令也接受以下选项：</span><span class="sxs-lookup"><span data-stu-id="e387f-123">The above commands also accept the following options:</span></span>

* <span data-ttu-id="e387f-124">**--distribution、-d \<分发版>**</span><span class="sxs-lookup"><span data-stu-id="e387f-124">**--distribution, -d \<Distro>**</span></span>

  <span data-ttu-id="e387f-125">运行指定的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-125">Run the specified distribution.</span></span>

* <span data-ttu-id="e387f-126">**--user、-u \<用户名>**</span><span class="sxs-lookup"><span data-stu-id="e387f-126">**--user, -u \<UserName>**</span></span>

  <span data-ttu-id="e387f-127">以指定用户的身份运行。</span><span class="sxs-lookup"><span data-stu-id="e387f-127">Run as the specified user.</span></span>

### <a name="arguments-for-managing-windows-subsystem-for-linux"></a><span data-ttu-id="e387f-128">用于管理适用于 Linux 的 Windows 子系统的参数</span><span class="sxs-lookup"><span data-stu-id="e387f-128">Arguments for managing Windows Subsystem for Linux</span></span>

* <span data-ttu-id="e387f-129">**--export \<分发版> \<文件名>**</span><span class="sxs-lookup"><span data-stu-id="e387f-129">**--export \<Distro> \<FileName>**</span></span>
  
  <span data-ttu-id="e387f-130">将分发版导出到 tar 文件。</span><span class="sxs-lookup"><span data-stu-id="e387f-130">Exports the distribution to a tar file.</span></span> <span data-ttu-id="e387f-131">在标准输出中，文件名可以是 -。</span><span class="sxs-lookup"><span data-stu-id="e387f-131">The filename can be - for standard output.</span></span>

* <span data-ttu-id="e387f-132">**--import \<分发版> \<安装位置> \<文件名>**</span><span class="sxs-lookup"><span data-stu-id="e387f-132">**--import \<Distro> \<InstallLocation> \<FileName>**</span></span>
  
  <span data-ttu-id="e387f-133">导入指定的 tar 文件作为新的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-133">Imports the specified tar file as a new distribution.</span></span> <span data-ttu-id="e387f-134">在标准输入中，文件名可以是 -。</span><span class="sxs-lookup"><span data-stu-id="e387f-134">The filename can be - for standard input.</span></span>

* <span data-ttu-id="e387f-135">**--list、-l [选项]**</span><span class="sxs-lookup"><span data-stu-id="e387f-135">**--list, -l [Options]**</span></span>
  
  <span data-ttu-id="e387f-136">列出分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-136">Lists distributions.</span></span>

  <span data-ttu-id="e387f-137">选项：</span><span class="sxs-lookup"><span data-stu-id="e387f-137">Options:</span></span>
  * <span data-ttu-id="e387f-138">**--all**</span><span class="sxs-lookup"><span data-stu-id="e387f-138">**--all**</span></span>

    <span data-ttu-id="e387f-139">列出所有分发版，包括当前正在安装或卸载的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-139">List all distributions, including distributions that are currently being installed or uninstalled.</span></span>

  * <span data-ttu-id="e387f-140">**--running**</span><span class="sxs-lookup"><span data-stu-id="e387f-140">**--running**</span></span>

    <span data-ttu-id="e387f-141">仅列出当前正在运行的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-141">List only distributions that are currently running.</span></span>

* <span data-ttu-id="e387f-142">**--set-default、-s \<分发版>**</span><span class="sxs-lookup"><span data-stu-id="e387f-142">**--set-default, -s \<Distro>**</span></span>
  
  <span data-ttu-id="e387f-143">将分发版设置为默认值。</span><span class="sxs-lookup"><span data-stu-id="e387f-143">Sets the distribution as the default.</span></span>

* <span data-ttu-id="e387f-144">**--terminate, -t \<分发版>**</span><span class="sxs-lookup"><span data-stu-id="e387f-144">**--terminate, -t \<Distro>**</span></span>
  
  <span data-ttu-id="e387f-145">终止指定的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-145">Terminates the specified distribution.</span></span>

* <span data-ttu-id="e387f-146">**--unregister \<分发版>**</span><span class="sxs-lookup"><span data-stu-id="e387f-146">**--unregister \<Distro>**</span></span>
  
  <span data-ttu-id="e387f-147">注销分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-147">Un-register the distribution.</span></span>

* <span data-ttu-id="e387f-148">**--help** 显示用法信息。</span><span class="sxs-lookup"><span data-stu-id="e387f-148">**--help** Display usage information.</span></span>

## <a name="additional-commands"></a><span data-ttu-id="e387f-149">其他命令</span><span class="sxs-lookup"><span data-stu-id="e387f-149">Additional Commands</span></span>

<span data-ttu-id="e387f-150">还可以使用一些传统命令来与适用于 Linux 的 Windows 子系统交互。</span><span class="sxs-lookup"><span data-stu-id="e387f-150">There are also historic commands to interact with the Windows Subsystem for Linux.</span></span> <span data-ttu-id="e387f-151">这些命令的功能已包含在 `wsl.exe` 中，但仍可供使用。</span><span class="sxs-lookup"><span data-stu-id="e387f-151">Their functionality is encompassed within `wsl.exe`, but they are still available for use.</span></span>

### `wslconfig.exe`

<span data-ttu-id="e387f-152">此命令可用于配置 WSL 分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-152">This command lets you configure your WSL distribution.</span></span> <span data-ttu-id="e387f-153">下面是其选项列表。</span><span class="sxs-lookup"><span data-stu-id="e387f-153">Below is a list of its options.</span></span>

<span data-ttu-id="e387f-154">使用：`wslconfig [Argument] [Options...]`</span><span class="sxs-lookup"><span data-stu-id="e387f-154">Using: `wslconfig [Argument] [Options...]`</span></span>

#### <a name="arguments"></a><span data-ttu-id="e387f-155">参数</span><span class="sxs-lookup"><span data-stu-id="e387f-155">Arguments</span></span>

* <span data-ttu-id="e387f-156">**/l、/list [选项]**</span><span class="sxs-lookup"><span data-stu-id="e387f-156">**/l, /list [Options]**</span></span>
  
  <span data-ttu-id="e387f-157">列出已注册的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-157">Lists registered distributions.</span></span>
  
<span data-ttu-id="e387f-158">选项：</span><span class="sxs-lookup"><span data-stu-id="e387f-158">Options:</span></span>

* <span data-ttu-id="e387f-159">**/all**（可选）列出所有分发版，包括当前正在安装或卸载的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-159">**/all** Optionally list all distributions, including distributions that are currently being installed or uninstalled.</span></span>

* <span data-ttu-id="e387f-160">**/running** 仅列出当前正在运行的分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-160">**/running** List only distributions that are currently running.</span></span>

* <span data-ttu-id="e387f-161">**/s, /setdefault \<Distro>** 将该分发版设置为默认版本。</span><span class="sxs-lookup"><span data-stu-id="e387f-161">**/s, /setdefault \<Distro>** Sets the distribution as the default.</span></span>

* <span data-ttu-id="e387f-162">**/t, /terminate \<Distro>** 终止分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-162">**/t, /terminate \<Distro>** Terminates the distribution.</span></span>

* <span data-ttu-id="e387f-163">**/u, /unregister \<Distro>** 注销分发版。</span><span class="sxs-lookup"><span data-stu-id="e387f-163">**/u, /unregister \<Distro>** Un-registers the distribution.</span></span>

* <span data-ttu-id="e387f-164">**/upgrade \<Distro>** 将分发版升级为 WslFs 文件系统格式。</span><span class="sxs-lookup"><span data-stu-id="e387f-164">**/upgrade \<Distro>** Upgrades the distribution to the WslFs file system format.</span></span>

### `bash.exe`

<span data-ttu-id="e387f-165">此命令用于启动 bash shell。</span><span class="sxs-lookup"><span data-stu-id="e387f-165">This command is used to start a bash shell.</span></span> <span data-ttu-id="e387f-166">下面是可在此命令中使用的选项。</span><span class="sxs-lookup"><span data-stu-id="e387f-166">Below are the options you can use with this command.</span></span>

<span data-ttu-id="e387f-167">使用：`bash [Options...]`</span><span class="sxs-lookup"><span data-stu-id="e387f-167">Using: `bash [Options...]`</span></span>

* <span data-ttu-id="e387f-168">**未指定选项**</span><span class="sxs-lookup"><span data-stu-id="e387f-168">**No Option given**</span></span>
  
  <span data-ttu-id="e387f-169">在当前目录中启动 Bash shell。</span><span class="sxs-lookup"><span data-stu-id="e387f-169">Launches the Bash shell in the current directory.</span></span> <span data-ttu-id="e387f-170">如果未自动安装 Bash shell，请运行 `lxrun /install`</span><span class="sxs-lookup"><span data-stu-id="e387f-170">If the Bash shell is not installed automatically runs `lxrun /install`</span></span>

* **~**
  
  <span data-ttu-id="e387f-171">`bash ~` 在用户的主目录中启动 bash shell。</span><span class="sxs-lookup"><span data-stu-id="e387f-171">`bash ~` launches the bash shell into the user's home directory.</span></span>  <span data-ttu-id="e387f-172">类似于运行 `cd ~`。</span><span class="sxs-lookup"><span data-stu-id="e387f-172">Similar to running `cd ~`.</span></span>

* <span data-ttu-id="e387f-173">**-c "\<命令>"**</span><span class="sxs-lookup"><span data-stu-id="e387f-173">**-c "\<command>"**</span></span>
  
  <span data-ttu-id="e387f-174">运行命令，列显输出，并返回到 Windows 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="e387f-174">Runs the command, prints the output and exits back to the Windows command prompt.</span></span>

  <span data-ttu-id="e387f-175">示例：`bash -c "ls"`。</span><span class="sxs-lookup"><span data-stu-id="e387f-175">Example:  `bash -c "ls"`.</span></span>

## <a name="deprecated-commands"></a><span data-ttu-id="e387f-176">已弃用的命令</span><span class="sxs-lookup"><span data-stu-id="e387f-176">Deprecated Commands</span></span>

<span data-ttu-id="e387f-177">`lxrun.exe` 是用于安装和管理适用于 Linux 的 Windows 子系统的第一个命令。</span><span class="sxs-lookup"><span data-stu-id="e387f-177">The `lxrun.exe` was the first command used to install and manage the Windows Subsystem for Linux.</span></span> <span data-ttu-id="e387f-178">从 Windows 10 1803 和更高版本开始，此命令已弃用。</span><span class="sxs-lookup"><span data-stu-id="e387f-178">It is deprecated as of Windows 10 1803 and later.</span></span>

<span data-ttu-id="e387f-179">可以使用命令 `lxrun.exe` 来直接与[适用于 Linux 的 Windows 子系统 (WSL)](https://msdn.microsoft.com/commandline/wsl/faq#what-windows-subsystem-for-linux-wsl-) 交互。</span><span class="sxs-lookup"><span data-stu-id="e387f-179">The command `lxrun.exe` can be used to interact with the [Windows Subsystem for Linux (WSL)](https://msdn.microsoft.com/commandline/wsl/faq#what-windows-subsystem-for-linux-wsl-) directly.</span></span>  <span data-ttu-id="e387f-180">这些命令已安装到 `\Windows\System32` 目录中，可以在 Windows 命令提示符或 PowerShell 中运行。</span><span class="sxs-lookup"><span data-stu-id="e387f-180">These commands are installed into the `\Windows\System32` directory and may be run within a Windows command prompt or in PowerShell.</span></span>

| <span data-ttu-id="e387f-181">命令</span><span class="sxs-lookup"><span data-stu-id="e387f-181">Command</span></span>                     | <span data-ttu-id="e387f-182">说明</span><span class="sxs-lookup"><span data-stu-id="e387f-182">Description</span></span>                     |
|:----------------------------|:---------------------------|
| `lxrun`                     | <span data-ttu-id="e387f-183">lxrun 命令用于管理 WSL 实例。</span><span class="sxs-lookup"><span data-stu-id="e387f-183">The lxrun command is used to manage the WSL instance.</span></span> |
| `lxrun /install`            | <span data-ttu-id="e387f-184">启动下载和安装过程。</span><span class="sxs-lookup"><span data-stu-id="e387f-184">Starts the download and install process.</span></span> <br/> <span data-ttu-id="e387f-185">可以添加 **/y** 来绕过所有提示。</span><span class="sxs-lookup"><span data-stu-id="e387f-185">**/y** may be added to bypass all prompts.</span></span>  <span data-ttu-id="e387f-186">系统会自动接受确认提示，默认用户将设置为 root。</span><span class="sxs-lookup"><span data-stu-id="e387f-186">The confirmation prompt is automatically accepted and the default user is set to root.</span></span>          |
| `lxrun /uninstall`          | <span data-ttu-id="e387f-187">卸载并删除 Ubuntu 映像。</span><span class="sxs-lookup"><span data-stu-id="e387f-187">Uninstalls and deletes the Ubuntu image.</span></span>  <span data-ttu-id="e387f-188">默认情况下，这不会删除用户的 Ubuntu 主目录。</span><span class="sxs-lookup"><span data-stu-id="e387f-188">By default this does not remove the user's Ubuntu home directory.</span></span> <br/> <span data-ttu-id="e387f-189">可以添加 **/y** 来自动接受确认提示</span><span class="sxs-lookup"><span data-stu-id="e387f-189">**/y** may be added to automatically accept the confirmation prompt</span></span> <br/><span data-ttu-id="e387f-190">**/full** 卸载并删除用户的 Ubuntu 主目录</span><span class="sxs-lookup"><span data-stu-id="e387f-190">**/full** uninstalls and deletes the user's Ubuntu home directory</span></span>         |
| `lxrun /setdefaultuser <userName>`     | <span data-ttu-id="e387f-191">设置默认的 Bash on Ubuntu 用户。</span><span class="sxs-lookup"><span data-stu-id="e387f-191">Sets the default Bash on Ubuntu user.</span></span> <span data-ttu-id="e387f-192">如果指定的用户不存在，该命令会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="e387f-192">Will prompt for a password if the specified user does not exist.</span></span>  <span data-ttu-id="e387f-193">有关详细信息，请访问： https://aka.ms/wslusers 。</span><span class="sxs-lookup"><span data-stu-id="e387f-193">For more information visit: https://aka.ms/wslusers.</span></span> <br/> <span data-ttu-id="e387f-194">**/y** 绕过密码提示。</span><span class="sxs-lookup"><span data-stu-id="e387f-194">**/y** Bypasses promping for the password.</span></span>  <span data-ttu-id="e387f-195">将创建不带密码的用户。</span><span class="sxs-lookup"><span data-stu-id="e387f-195">The user will be created without a password.</span></span>|
| `lxrun /update`            | <span data-ttu-id="e387f-196">更新子系统的包索引</span><span class="sxs-lookup"><span data-stu-id="e387f-196">Updates the subsystem's package index</span></span>          |
