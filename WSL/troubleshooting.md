---
title: 排查适用于 Linux 的 Windows 子系统问题
description: 提供有关在适用于 Linux 的 Windows 子系统上运行 Linux 时遇到的常见错误和问题的详细信息。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, ubuntu
ms.date: 01/20/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: cc8f032a99fb087b7ef614dd3a3574cb8ee3f2da
ms.sourcegitcommit: ba52d673c123fe8ae61e872a33e218cfc30a1f82
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86033061"
---
# <a name="troubleshooting-windows-subsystem-for-linux"></a><span data-ttu-id="0dcf1-104">排查适用于 Linux 的 Windows 子系统问题</span><span class="sxs-lookup"><span data-stu-id="0dcf1-104">Troubleshooting Windows Subsystem for Linux</span></span>

<span data-ttu-id="0dcf1-105">要获得 WSL 相关问题的支持，请参阅 GitHub 存储库：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-105">For support with issues related to WSL, please see our GitHub repo:</span></span>

## <a name="search-for-any-existing-issues-related-to-your-problem"></a><span data-ttu-id="0dcf1-106">搜索与你的问题相关的任何现有问题</span><span class="sxs-lookup"><span data-stu-id="0dcf1-106">Search for any existing issues related to your problem</span></span>

<span data-ttu-id="0dcf1-107">有关技术问题，请使用产品存储库： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="0dcf1-107">For technical issues, use the product repo: https://github.com/Microsoft/wsl/issues</span></span>

<span data-ttu-id="0dcf1-108">对于与本文档内容相关的问题，请使用文档存储库： https://github.com/MicrosoftDocs/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="0dcf1-108">For issues related to the contents of this documentation, use the docs repo: https://github.com/MicrosoftDocs/wsl/issues</span></span>

## <a name="submit-a-bug-report"></a><span data-ttu-id="0dcf1-109">提交 Bug 报告</span><span class="sxs-lookup"><span data-stu-id="0dcf1-109">Submit a bug report</span></span>

<span data-ttu-id="0dcf1-110">对于与 WSL 函数或功能相关的 bug，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="0dcf1-110">For bugs related to WSL functions or features, file an issue in the product repo: https://github.com/Microsoft/wsl/issues</span></span>

## <a name="submit-a-feature-request"></a><span data-ttu-id="0dcf1-111">提交功能请求</span><span class="sxs-lookup"><span data-stu-id="0dcf1-111">Submit a feature request</span></span>

<span data-ttu-id="0dcf1-112">若要请求与 WSL 功能或兼容性相关的新功能，请在产品存储库中创建问题： https://github.com/Microsoft/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="0dcf1-112">To request a new feature related to WSL functionality or compatibility, file an issue in the product repo: https://github.com/Microsoft/wsl/issues</span></span>

## <a name="contribute-to-the-docs"></a><span data-ttu-id="0dcf1-113">参与编辑文档</span><span class="sxs-lookup"><span data-stu-id="0dcf1-113">Contribute to the docs</span></span>

<span data-ttu-id="0dcf1-114">若要参与撰写 WSL 文档，请在文档存储库中提交拉取请求： https://github.com/MicrosoftDocs/wsl/issues</span><span class="sxs-lookup"><span data-stu-id="0dcf1-114">To contribute to the WSL documentation, submit a pull request in the docs repo: https://github.com/MicrosoftDocs/wsl/issues</span></span>

## <a name="terminal-or-command-line"></a><span data-ttu-id="0dcf1-115">终端或命令行</span><span class="sxs-lookup"><span data-stu-id="0dcf1-115">Terminal or Command Line</span></span>

<span data-ttu-id="0dcf1-116">最后，如果你的问题与 Windows 终端、Windows 控制台或命令行 UI 相关，请使用 Windows 终端存储库： https://github.com/microsoft/terminal</span><span class="sxs-lookup"><span data-stu-id="0dcf1-116">Lastly, if your issue is related to the Windows Terminal, Windows Console, or the command-line UI, use the Windows terminal repo: https://github.com/microsoft/terminal</span></span>

## <a name="common-issues"></a><span data-ttu-id="0dcf1-117">常见问题</span><span class="sxs-lookup"><span data-stu-id="0dcf1-117">Common issues</span></span>

### <a name="cannot-access-wsl-files-from-windows"></a><span data-ttu-id="0dcf1-118">无法从 Windows 访问 WSL 文件</span><span class="sxs-lookup"><span data-stu-id="0dcf1-118">Cannot access WSL files from Windows</span></span>
<span data-ttu-id="0dcf1-119">9p 协议文件服务器在 Linux 端提供服务，以允许 Windows 访问 Linux 文件系统。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-119">A 9p protocol file server provides the service on the Linux side to allow Windows to access the Linux file system.</span></span> <span data-ttu-id="0dcf1-120">如果在 Windows 上无法使用 `\\wsl$` 访问 WSL，则可能是因为 9P 无法正确启动。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-120">If you cannot access WSL using `\\wsl$` on Windows, it could be because 9P did not start correctly.</span></span>

<span data-ttu-id="0dcf1-121">要检查这一点，可以使用 `dmesg |grep 9p` 来检查启动日志，这将显示任何错误。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-121">To check this, you can check the start up logs using: `dmesg |grep 9p`, and this will show you any errors.</span></span> <span data-ttu-id="0dcf1-122">成功的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-122">A successfull output looks like the following:</span></span> 

```
[    0.363323] 9p: Installing v9fs 9p2000 file system support
[    0.363336] FS-Cache: Netfs '9p' registered for caching
[    0.398989] 9pnet: Installing 9P2000 support
```

<span data-ttu-id="0dcf1-123">请参阅[本 Github 线程](https://github.com/microsoft/wsl/issues/5307)，获取有关此问题的进一步讨论。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-123">Please see [this Github thread](https://github.com/microsoft/wsl/issues/5307) for further discussion on this issue.</span></span>

### <a name="cant-start-wsl-2-distro-and-only-see-wsl-2-in-output"></a><span data-ttu-id="0dcf1-124">无法启动 WSL 2 发行版，仅在输出中看到“WSL 2”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-124">Can't start WSL 2 distro and only see 'WSL 2' in output</span></span>
<span data-ttu-id="0dcf1-125">如果你的显示语言不是英语，则可能会看到截断的错误文本。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-125">If your display language is not English, then it is possible you are seeing a truncated version of an error text.</span></span>

```powershell
C:\Users\me>wsl
WSL 2
```

<span data-ttu-id="0dcf1-126">要解决此问题，请访问 `https://aka.ms/wsl2kernel`，按照该文档页面上的指示手动安装内核。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-126">To resolve this issue, please visit `https://aka.ms/wsl2kernel` and install the kernel manually by following the directions on that doc page.</span></span> 

### <a name="please-enable-the-virtual-machine-platform-windows-feature-and-ensure-virtualization-is-enabled-in-the-bios"></a><span data-ttu-id="0dcf1-127">请启用 Virtual Machine Platform Windows 功能，并确保在 BIOS 中启用了虚拟化。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-127">Please enable the Virtual Machine Platform Windows feature and ensure virtualization is enabled in the BIOS.</span></span>

1. <span data-ttu-id="0dcf1-128">请查看 [Hyper-V 系统要求](https://docs.microsoft.com/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span><span class="sxs-lookup"><span data-stu-id="0dcf1-128">Check the [Hyper-V system requirements](https://docs.microsoft.com/windows-server/virtualization/hyper-v/system-requirements-for-hyper-v-on-windows#:~:text=on%20Windows%20Server.-,General%20requirements,the%20processor%20must%20have%20SLAT.)</span></span>
2. <span data-ttu-id="0dcf1-129">如果你的计算机是 VM，请手动启用[嵌套虚拟化](https://docs.microsoft.com/windows/wsl/wsl2-faq#can-i-run-wsl-2-in-a-virtual-machine)。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-129">If your machine is a VM, please enable [nested virtualization](https://docs.microsoft.com/windows/wsl/wsl2-faq#can-i-run-wsl-2-in-a-virtual-machine) manually.</span></span> <span data-ttu-id="0dcf1-130">使用 admin 启动 powershell，并运行：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-130">Launch powershell with admin, and run:</span></span> 

```powershell
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
```

3. <span data-ttu-id="0dcf1-131">请按照电脑制造商提供的虚拟化启用指南进行操作。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-131">Please follow guidelines from your PC's manufacturer on how to enable virtualization.</span></span> <span data-ttu-id="0dcf1-132">通常，这可能涉及使用系统 BIOS 来确保在 CPU 上启用了这些功能。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-132">In general, this can involve using the system BIOS to ensure that these features are enabled on your CPU.</span></span> 
4. <span data-ttu-id="0dcf1-133">启用 `Virtual Machine Platform` 可选组件后，请重启计算机。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-133">Restart your machine after enabling the `Virtual Machine Platform` optional component.</span></span> 

### <a name="bash-loses-network-connectivity-once-connected-to-a-vpn"></a><span data-ttu-id="0dcf1-134">Bash 在连接到 VPN 后断开网络连接</span><span class="sxs-lookup"><span data-stu-id="0dcf1-134">Bash loses network connectivity once connected to a VPN</span></span>

<span data-ttu-id="0dcf1-135">如果在连接到 Windows 上的 VPN 后 bash 断开网络连接，请尝试从 bash 内部解决问题。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-135">If after connecting to a VPN on Windows, bash loses network connectivity, try this workaround from within bash.</span></span> <span data-ttu-id="0dcf1-136">此解决方法允许通过 `/etc/resolv.conf` 手动替代 DNS 解析。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-136">This workaround will allow you to manually override the DNS resolution through `/etc/resolv.conf`.</span></span>

1. <span data-ttu-id="0dcf1-137">执行 `ipconfig.exe /all`，记下 VPN 的 DNS 服务器</span><span class="sxs-lookup"><span data-stu-id="0dcf1-137">Take a note of the DNS server of the VPN from doing `ipconfig.exe /all`</span></span>
2. <span data-ttu-id="0dcf1-138">执行 `sudo cp /etc/resolv.conf /etc/resolv.conf.new`，创建现有 resolv.conf 的副本</span><span class="sxs-lookup"><span data-stu-id="0dcf1-138">Make a copy of the existing resolv.conf `sudo cp /etc/resolv.conf /etc/resolv.conf.new`</span></span>
3. <span data-ttu-id="0dcf1-139">执行 `sudo unlink /etc/resolv.conf` 以便与当前 resolv.conf 取消链接</span><span class="sxs-lookup"><span data-stu-id="0dcf1-139">Unlink the current resolv.conf `sudo unlink /etc/resolv.conf`</span></span>
4. `sudo mv /etc/resolv.conf.new /etc/resolv.conf`
5. <span data-ttu-id="0dcf1-140">打开 `/etc/resolv.conf` 并执行以下操作</span><span class="sxs-lookup"><span data-stu-id="0dcf1-140">Open `/etc/resolv.conf` and</span></span> <br/>
   <span data-ttu-id="0dcf1-141">a.</span><span class="sxs-lookup"><span data-stu-id="0dcf1-141">a.</span></span> <span data-ttu-id="0dcf1-142">删除该文件中显示了“\# This file was automatically generated by WSL.</span><span class="sxs-lookup"><span data-stu-id="0dcf1-142">Delete the first line from the file, which says "\# This file was automatically generated by WSL.</span></span> <span data-ttu-id="0dcf1-143">To stop automatic generation of this file, remove this line”的第一行。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-143">To stop automatic generation of this file, remove this line.".</span></span> <br/>
   <span data-ttu-id="0dcf1-144">b.</span><span class="sxs-lookup"><span data-stu-id="0dcf1-144">b.</span></span> <span data-ttu-id="0dcf1-145">将上面步骤 (1) 中记下的 DNS 条目添加为 DNS 服务器列表中的第一个条目。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-145">Add the DNS entry from (1) above as the very first entry in the list of DNS servers.</span></span> <br/>
   <span data-ttu-id="0dcf1-146">c.</span><span class="sxs-lookup"><span data-stu-id="0dcf1-146">c.</span></span> <span data-ttu-id="0dcf1-147">关闭该文件。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-147">Close the file.</span></span> <br/>

<span data-ttu-id="0dcf1-148">断开 VPN 连接后，必须将更改还原为 `/etc/resolv.conf`。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-148">Once you have disconnected the VPN, you will have to revert the changes to `/etc/resolv.conf`.</span></span> <span data-ttu-id="0dcf1-149">为此，请执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-149">To do this, do:</span></span>

1. `cd /etc`
2. `sudo mv resolv.conf resolv.conf.new`
3. `sudo ln -s ../run/resolvconf/resolv.conf resolv.conf`

### <a name="starting-wsl-or-installing-a-distribution-returns-an-error-code"></a><span data-ttu-id="0dcf1-150">启动 WSL 或安装分发版会返回一个错误代码</span><span class="sxs-lookup"><span data-stu-id="0dcf1-150">Starting WSL or installing a distribution returns an error code</span></span>

<span data-ttu-id="0dcf1-151">按照[这些说明](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs)收集详细日志并在 GitHub 上提出问题。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-151">Follow [these instructions](https://github.com/Microsoft/WSL/blob/master/CONTRIBUTING.md#8-detailed-logs) to collect detailed logs and file an issue on our GitHub.</span></span>

### <a name="updating-bash-on-ubuntu-on-windows"></a><span data-ttu-id="0dcf1-152">更新 Windows 上的 Ubuntu Bash</span><span class="sxs-lookup"><span data-stu-id="0dcf1-152">Updating Bash on Ubuntu on Windows</span></span>

<span data-ttu-id="0dcf1-153">Windows 上的 Ubuntu Bash 有两个组件需要更新。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-153">There are two components of Bash on Ubuntu on Windows that can require updating.</span></span>

1. <span data-ttu-id="0dcf1-154">适用于 Linux 的 Windows 子系统</span><span class="sxs-lookup"><span data-stu-id="0dcf1-154">The Windows Subsystem for Linux</span></span>
  
   <span data-ttu-id="0dcf1-155">升级 Windows 上的 Ubuntu Bash 的此部分会启用[发行说明](./release-notes.md)中所述的任何新修复程序。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-155">Upgrading this portion of Bash on Ubuntu on Windows will enable any new fixes outlines in the [release notes](./release-notes.md).</span></span> <span data-ttu-id="0dcf1-156">确保已订阅 Windows 预览体验计划，并且内部版本是最新的。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-156">Ensure that you are subscribed to the Windows Insider Program and that your build is up to date.</span></span> <span data-ttu-id="0dcf1-157">若要获得更精细的控制，包括重置 Ubuntu 实例，请查看[命令参考页](./reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-157">For finer grain control including resetting your Ubuntu instance check out the [command reference page](./reference.md).</span></span>

2. <span data-ttu-id="0dcf1-158">Ubuntu 用户二进制文件</span><span class="sxs-lookup"><span data-stu-id="0dcf1-158">The Ubuntu user binaries</span></span>

   <span data-ttu-id="0dcf1-159">升级 Windows 上的 Ubuntu Bash 的此部分会安装 Ubuntu 用户二进制文件（包括通过 apt-get 安装的应用程序）的任何更新。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-159">Upgrading this portion of Bash on Ubuntu on Windows will install any updates to the Ubuntu user binaries including applications that you have installed via apt-get.</span></span> <span data-ttu-id="0dcf1-160">若要更新，请在 Bash 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-160">To update run the following commands in Bash:</span></span>
  
   1. `apt-get update`
   2. `apt-get upgrade`
  
### <a name="apt-get-upgrade-errors"></a><span data-ttu-id="0dcf1-161">Apt-get upgrade 错误</span><span class="sxs-lookup"><span data-stu-id="0dcf1-161">Apt-get upgrade errors</span></span>

<span data-ttu-id="0dcf1-162">某些包使用我们尚未实现的功能。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-162">Some packages use features that we haven't implemented yet.</span></span> <span data-ttu-id="0dcf1-163">例如，`udev` 尚不受支持，会导致多个 `apt-get upgrade` 错误。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-163">`udev`, for example, isn't supported yet and causes several `apt-get upgrade` errors.</span></span>

<span data-ttu-id="0dcf1-164">若要解决与 `udev` 相关的问题，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-164">To fix issues related to `udev`, follow the following steps:</span></span>

1. <span data-ttu-id="0dcf1-165">将以下内容写入 `/usr/sbin/policy-rc.d` 并保存更改。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-165">Write the following to `/usr/sbin/policy-rc.d` and save your changes.</span></span>
  
   ```bash
   #!/bin/sh
   exit 101
   ```
  
2. <span data-ttu-id="0dcf1-166">将执行权限添加到 `/usr/sbin/policy-rc.d`：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-166">Add execute permissions to `/usr/sbin/policy-rc.d`:</span></span>

   ```bash
   chmod +x /usr/sbin/policy-rc.d
   ```
  
3. <span data-ttu-id="0dcf1-167">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-167">Run the following commands:</span></span>

   ```bash
   dpkg-divert --local --rename --add /sbin/initctl
   ln -s /bin/true /sbin/initctl
   ```
  
### <a name="error-0x80040306-on-installation"></a><span data-ttu-id="0dcf1-168">Windows 更新后出现“错误:0x80040306”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-168">"Error: 0x80040306" on installation</span></span>

<span data-ttu-id="0dcf1-169">此错误与我们不支持旧版控制台这一事实有关。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-169">This has to do with the fact that we do not support legacy console.</span></span>
<span data-ttu-id="0dcf1-170">若要关闭旧版控制台：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-170">To turn off legacy console:</span></span>

1. <span data-ttu-id="0dcf1-171">打开 cmd.exe</span><span class="sxs-lookup"><span data-stu-id="0dcf1-171">Open cmd.exe</span></span>
1. <span data-ttu-id="0dcf1-172">右键单击标题栏 -> 选择“属性”-> 取消选中“使用旧版控制台”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-172">Right click title bar -> Properties -> Uncheck Use legacy console</span></span>
1. <span data-ttu-id="0dcf1-173">单击“确定”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-173">Click OK</span></span>

### <a name="error-0x80040154-after-windows-update"></a><span data-ttu-id="0dcf1-174">Windows 更新后出现“错误:0x80040154”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-174">"Error: 0x80040154" after Windows update</span></span>

<span data-ttu-id="0dcf1-175">在 Windows 更新期间可能禁用了“适用于 Linux 的 Windows 子系统”功能。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-175">The Windows Subsystem for Linux feature may be disabled during a Windows update.</span></span> <span data-ttu-id="0dcf1-176">如果出现这种情况，则必须重新启用 Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-176">If this happens the Windows feature must be re-enabled.</span></span> <span data-ttu-id="0dcf1-177">在[安装指南](./install-win10.md)中可以找到有关启用“适用于 Linux 的 Windows 子系统”的说明。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-177">Instructions for enabling the Windows Subsystem for Linux can be found in the [Installation Guide](./install-win10.md).</span></span>

### <a name="changing-the-display-language"></a><span data-ttu-id="0dcf1-178">更改显示语言</span><span class="sxs-lookup"><span data-stu-id="0dcf1-178">Changing the display language</span></span>

<span data-ttu-id="0dcf1-179">WSL 安装会尝试自动更改 Ubuntu 区域设置，使之与 Windows 安装的区域设置相匹配。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-179">WSL install will try to automatically change the Ubuntu locale to match the locale of your Windows install.</span></span>  <span data-ttu-id="0dcf1-180">如果你不希望出现此行为，可以在安装完成后，运行此命令来更改 Ubuntu 区域设置。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-180">If you do not want this behavior you can run this command to change the Ubuntu locale after install completes.</span></span>  <span data-ttu-id="0dcf1-181">必须重新启动 bash.exe 才能使此项更改生效。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-181">You will have to relaunch bash.exe for this change to take effect.</span></span>

<span data-ttu-id="0dcf1-182">以下示例将区域设置更改为 en-US：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-182">The below example changes to locale to en-US:</span></span>

```bash
sudo update-locale LANG=en_US.UTF8
```

### <a name="installation-issues-after-windows-system-restore"></a><span data-ttu-id="0dcf1-183">Windows 系统还原后出现的安装问题</span><span class="sxs-lookup"><span data-stu-id="0dcf1-183">Installation issues after Windows system restore</span></span>

1. <span data-ttu-id="0dcf1-184">删除 `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-184">Delete the `%windir%\System32\Tasks\Microsoft\Windows\Windows Subsystem for Linux` folder.</span></span> <br/>
  <span data-ttu-id="0dcf1-185">**注意：如果可选功能已完全安装且工作正常，请不要执行此操作。**</span><span class="sxs-lookup"><span data-stu-id="0dcf1-185">**Note: Do not do this if your optional feature is fully installed and working.**</span></span>
2. <span data-ttu-id="0dcf1-186">启用 WSL 可选功能（如果尚未这样做）</span><span class="sxs-lookup"><span data-stu-id="0dcf1-186">Enable the WSL optional feature (if not already)</span></span>
3. <span data-ttu-id="0dcf1-187">重新启动</span><span class="sxs-lookup"><span data-stu-id="0dcf1-187">Reboot</span></span>
4. <span data-ttu-id="0dcf1-188">lxrun /uninstall /full</span><span class="sxs-lookup"><span data-stu-id="0dcf1-188">lxrun /uninstall /full</span></span>
5. <span data-ttu-id="0dcf1-189">安装 bash</span><span class="sxs-lookup"><span data-stu-id="0dcf1-189">Install bash</span></span>

### <a name="no-internet-access-in-wsl"></a><span data-ttu-id="0dcf1-190">在 WSL 中无法进行 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="0dcf1-190">No internet access in WSL</span></span>

<span data-ttu-id="0dcf1-191">某些用户已报告特定的防火墙应用程序会阻止 WSL 中的 Internet 访问的问题。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-191">Some users have reported issues with specific firewall applications blocking internet access in WSL.</span></span>  <span data-ttu-id="0dcf1-192">报告的防火墙包括：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-192">The firewalls reported are:</span></span>

1. <span data-ttu-id="0dcf1-193">Kaspersky</span><span class="sxs-lookup"><span data-stu-id="0dcf1-193">Kaspersky</span></span>
2. <span data-ttu-id="0dcf1-194">AVG</span><span class="sxs-lookup"><span data-stu-id="0dcf1-194">AVG</span></span>
3. <span data-ttu-id="0dcf1-195">Avast</span><span class="sxs-lookup"><span data-stu-id="0dcf1-195">Avast</span></span>

<span data-ttu-id="0dcf1-196">在某些情况下，关闭防火墙即可进行访问。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-196">In some cases turning off the firewall allows for access.</span></span>  <span data-ttu-id="0dcf1-197">在某些情况下，只需让安装的防火墙在表面上阻止访问。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-197">In some cases simply having the firewall installed looks to block access.</span></span>

### <a name="permission-denied-error-when-using-ping"></a><span data-ttu-id="0dcf1-198">使用 ping 时出现“权限被拒绝”错误</span><span class="sxs-lookup"><span data-stu-id="0dcf1-198">Permission Denied error when using ping</span></span>

<span data-ttu-id="0dcf1-199">对于 [Windows 周年更新版本 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update)，在 WSL 中运行 ping 命令需要拥有 Windows 中的**管理员特权**。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-199">For [Windows Anniversary Update, version 1607](./release-notes.md#build-14388-to-windows-10-anniversary-update), **administrator privileges** in Windows are required to run ping in WSL.</span></span>  <span data-ttu-id="0dcf1-200">若要运行 ping，请以管理员身份运行 Windows 上的 Ubuntu Bash，或使用管理员特权从 CMD/PowerShell 提示符运行 bash.exe。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-200">To run ping, run Bash on Ubuntu on Windows as an administrator, or run bash.exe from a CMD/PowerShell prompt with administrator privileges.</span></span>

<span data-ttu-id="0dcf1-201">对于更高版本的 Windows（[内部版本 14926 及更高版本](./release-notes.md#build-14926)），则不再需要管理员特权。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-201">For later versions of Windows, [Build 14926+](./release-notes.md#build-14926), administrator privileges are no longer required.</span></span>

### <a name="bash-is-hung"></a><span data-ttu-id="0dcf1-202">Bash 挂起</span><span class="sxs-lookup"><span data-stu-id="0dcf1-202">Bash is hung</span></span>

<span data-ttu-id="0dcf1-203">如果使用 bash 时发现 bash 挂起（或死锁）且不响应输入，请收集并报告内存转储来帮助我们诊断问题。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-203">If while working with bash, you find that bash is hung (or deadlocked) and not responding to inputs, help us diagnose the issue by collecting and reporting a memory dump.</span></span> <span data-ttu-id="0dcf1-204">请注意，这些步骤会导致系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-204">Note that these steps will crash your system.</span></span> <span data-ttu-id="0dcf1-205">如果你不熟悉此过程，请不要这样做，或者，请在执行此操作之前保存你的工作。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-205">Do not do this if you are not comfortable with that or save your work prior to doing this.</span></span>

<span data-ttu-id="0dcf1-206">收集内存转储</span><span class="sxs-lookup"><span data-stu-id="0dcf1-206">To collect a memory dump</span></span>

1. <span data-ttu-id="0dcf1-207">将内存转储类型更改为“完整内存转储”。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-207">Change the memory dump type to "complete memory dump".</span></span> <span data-ttu-id="0dcf1-208">更改转储类型时，请记下当前类型。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-208">While changing the dump type, take a note of your current type.</span></span>

2. <span data-ttu-id="0dcf1-209">遵循这些[步骤](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809)使用键盘控制来配置崩溃。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-209">Use the [steps](https://techcommunity.microsoft.com/t5/Core-Infrastructure-and-Security/How-to-Force-a-Diagnostic-Memory-Dump-When-a-Computer-Hangs/ba-p/257809) to configure crash using keyboard control.</span></span>

3. <span data-ttu-id="0dcf1-210">再现挂起或死锁场景。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-210">Repro the hang or deadlock.</span></span>

4. <span data-ttu-id="0dcf1-211">使用步骤 (2) 中的按键顺序来使系统崩溃。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-211">Crash the system using the key sequence from (2).</span></span>

5. <span data-ttu-id="0dcf1-212">系统将会崩溃并收集内存转储。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-212">The system will crash and collect the memory dump.</span></span>

6. <span data-ttu-id="0dcf1-213">系统重新启动后，会将 memory.dmp 报告给 secure@microsoft.com。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-213">Once the system reboots, report the memory.dmp to secure@microsoft.com.</span></span> <span data-ttu-id="0dcf1-214">转储文件的默认位置是 %SystemRoot%\memory.dmp 或 C:\Windows\memory.dmp（如果 C: 是系统驱动器）。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-214">The default location of the dump file is %SystemRoot%\memory.dmp or C:\Windows\memory.dmp if C: is the system drive.</span></span> <span data-ttu-id="0dcf1-215">请注意，在电子邮件中，转储供 WSL 或 Windows 上的 Bash 团队参考。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-215">In the email, note that the dump is for the WSL or Bash on Windows team.</span></span>

7. <span data-ttu-id="0dcf1-216">将内存转储类型还原为原始设置。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-216">Restore the memory dump type to the original setting.</span></span>

### <a name="check-your-build-number"></a><span data-ttu-id="0dcf1-217">检查内部版本号</span><span class="sxs-lookup"><span data-stu-id="0dcf1-217">Check your build number</span></span>

<span data-ttu-id="0dcf1-218">若要查找电脑的体系结构和 Windows 内部版本号，请打开</span><span class="sxs-lookup"><span data-stu-id="0dcf1-218">To find your PC's architecture and Windows build number, open</span></span>  
<span data-ttu-id="0dcf1-219">“设置” > “系统” > “关于”  </span><span class="sxs-lookup"><span data-stu-id="0dcf1-219">**Settings** > **System** > **About**</span></span>

<span data-ttu-id="0dcf1-220">查看“OS 内部版本”和“系统类型”字段。 </span><span class="sxs-lookup"><span data-stu-id="0dcf1-220">Look for the **OS Build** and **System Type** fields.</span></span>  
    <span data-ttu-id="0dcf1-221">![“内部版本”和“系统类型”字段的屏幕截图](media/system.png)</span><span class="sxs-lookup"><span data-stu-id="0dcf1-221">![Screenshot of Build and System Type fields](media/system.png)</span></span>

<span data-ttu-id="0dcf1-222">若要查找 Windows Server 内部版本号，请在 PowerShell 中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-222">To find your Windows Server build number, run the following in PowerShell:</span></span>  

``` PowerShell
systeminfo | Select-String "^OS Name","^OS Version"
```

### <a name="confirm-wsl-is-enabled"></a><span data-ttu-id="0dcf1-223">确认已启用 WSL</span><span class="sxs-lookup"><span data-stu-id="0dcf1-223">Confirm WSL is enabled</span></span>

<span data-ttu-id="0dcf1-224">可以通过在 PowerShell 中运行以下命令来确认是否已启用“适用于 Linux 的 Windows 子系统”：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-224">You can confirm that the Windows Subsystem for Linux is enabled by running the following in PowerShell:</span></span>  

``` PowerShell
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### <a name="openssh-server-connection-issues"></a><span data-ttu-id="0dcf1-225">OpenSSH 服务器连接问题</span><span class="sxs-lookup"><span data-stu-id="0dcf1-225">OpenSSH-Server connection issues</span></span>

<span data-ttu-id="0dcf1-226">尝试连接 SSH 服务器失败并出现以下错误：“127.0.0.1 端口 22 已关闭连接”。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-226">Trying to connect your SSH server is failed with the following error: "Connection closed by 127.0.0.1 port 22".</span></span>

1. <span data-ttu-id="0dcf1-227">确保 OpenSSH 服务器正在运行：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-227">Make sure your OpenSSH Server is running:</span></span>

   ```bash
   sudo service ssh status
   ```

   <span data-ttu-id="0dcf1-228">并已按照此教程进行操作： https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span><span class="sxs-lookup"><span data-stu-id="0dcf1-228">and you've followed this tutorial: https://help.ubuntu.com/lts/serverguide/openssh-server.html.en</span></span>

2. <span data-ttu-id="0dcf1-229">停止 sshd 服务，然后在调试模式下启动 sshd：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-229">Stop the sshd service and start sshd in debug mode:</span></span>

   ```bash
   sudo service ssh stop
   sudo /usr/sbin/sshd -d
   ```

3. <span data-ttu-id="0dcf1-230">检查启动日志，确保已提供主机密钥，并且未看到如下所示的日志消息：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-230">Check the startup logs and make sure HostKeys are available and you don't see log messages such as:</span></span>

   ```BASH
   debug1: sshd version OpenSSH_7.2, OpenSSL 1.0.2g  1 Mar 2016
   debug1: key_load_private: incorrect passphrase supplied to decrypt private key
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_rsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_dsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_ecdsa_key
   debug1: key_load_private: No such file or directory
   debug1: key_load_public: No such file or directory
   Could not load host key: /etc/ssh/ssh_host_ed25519_key
   ```

<span data-ttu-id="0dcf1-231">如果确实看到了此类消息，并且 `/etc/ssh/` 下缺少主机密钥，则必须重新生成这些密钥，或者只是清除并安装 OpenSSH 服务器：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-231">If you do see such messages and the keys are missing under `/etc/ssh/`, you will have to regenerate the keys or just purge&install openssh-server:</span></span>

```BASH
sudo apt-get purge openssh-server
sudo apt-get install openssh-server
```

### <a name="the-referenced-assembly-could-not-be-found-when-enabling-the-wsl-optional-feature"></a><span data-ttu-id="0dcf1-232">“找不到引用的程序集。”</span><span class="sxs-lookup"><span data-stu-id="0dcf1-232">"The referenced assembly could not be found."</span></span> <span data-ttu-id="0dcf1-233">在启用 WSL 可选功能后出现</span><span class="sxs-lookup"><span data-stu-id="0dcf1-233">when enabling the WSL optional feature</span></span>

<span data-ttu-id="0dcf1-234">此错误与处于错误的安装状态相关。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-234">This error is related to being in a bad install state.</span></span> <span data-ttu-id="0dcf1-235">请完成以下步骤来尝试解决此问题：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-235">Please complete the following steps to try and fix this issue:</span></span>

- <span data-ttu-id="0dcf1-236">如果是从 PowerShell 运行了启用 WSL 功能的命令，请尝试改用 GUI，方法是打开“开始”菜单，搜索“启用或关闭 Windows 功能”，然后在列表中选择“适用于 Linux 的 Windows 子系统”，这将安装可选组件。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-236">If you are running the enable WSL feature command from PowerShell, try using the GUI instead by opening the start menu, searching for 'Turn Windows features on or off' and then in the list select 'Windows Subsystem for Linux' which will install the optional component.</span></span>

- <span data-ttu-id="0dcf1-237">转到“设置”、“更新”，然后单击“检查更新”来更新 Windows 版本</span><span class="sxs-lookup"><span data-stu-id="0dcf1-237">Update your version of Windows by going to Settings, Updates, and clicking 'Check for Updates'</span></span>

- <span data-ttu-id="0dcf1-238">如果这两个操作均失败，并且你需要访问 WSL，请考虑使用安装介质重新安装 Windows 10 并选择“保留所有内容”以确保保留你的应用和文件，从而就地升级。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-238">If both of those fail and you need to access WSL please consider upgrading in place by reinstalling Windows 10 using installation media and selecting 'Keep Everything' to ensure your apps and files are preserved.</span></span> <span data-ttu-id="0dcf1-239">可以在[“重新安装 Windows 10”页面](https://support.microsoft.com/help/4000735/windows-10-reinstall)中找到有关如何执行此操作的说明。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-239">You can find instructions on how to do so at the [Reinstall Windows 10 page](https://support.microsoft.com/help/4000735/windows-10-reinstall).</span></span>

### <a name="correct-ssh-related-permission-errors"></a><span data-ttu-id="0dcf1-240">更正（SSH 相关）权限错误</span><span class="sxs-lookup"><span data-stu-id="0dcf1-240">Correct (SSH related) permission errors</span></span>

<span data-ttu-id="0dcf1-241">如果看到此错误：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-241">If you're seeing this error:</span></span>

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0777 for '/home/artur/.ssh/private-key.pem' are too open.
```

<span data-ttu-id="0dcf1-242">若要解决此问题，请将以下内容追加到 ```/etc/wsl.conf``` 文件：</span><span class="sxs-lookup"><span data-stu-id="0dcf1-242">To fix this, append the following to the the ```/etc/wsl.conf``` file:</span></span>

```
[automount]
enabled = true
options = metadata,uid=1000,gid=1000,umask=0022
```

<span data-ttu-id="0dcf1-243">请注意，添加此命令将包含元数据并修改有关从 WSL 中看到的 Windows 文件的文件权限。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-243">Please note that adding this command will include metadata and modify the file permissions on the Windows files seen from WSL.</span></span> <span data-ttu-id="0dcf1-244">有关详细信息，请参阅[文件系统权限](./file-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="0dcf1-244">Please see the [File System Permissions](./file-permissions.md) for more information.</span></span>
