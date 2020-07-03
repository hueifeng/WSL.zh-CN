---
title: WSL 2 常见问题解答
description: 有关适用于 Linux 的 Windows 子系统 2 的常见问题解答
keywords: BashOnWindows, bash, wsl, wsl2, Windows, 适用于 Linux 的 Windows 子系统, windowssubsystem, ubuntu, debian, suse, Windows 10, 安装
ms.date: 05/30/2019
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ms.custom: seodec18
ms.localizationpriority: high
ms.openlocfilehash: 89b8a29f0c2d24a3c97d9661db3d83963629f34f
ms.sourcegitcommit: cb8a61e7de08b1c18622fc78bc5dfa38786e921a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663110"
---
# <a name="wsl-2-faqs"></a><span data-ttu-id="d8f5c-104">WSL 2 常见问题解答</span><span class="sxs-lookup"><span data-stu-id="d8f5c-104">WSL 2 FAQs</span></span>

<span data-ttu-id="d8f5c-105">下面是有关适用于 Linux 的 Windows 子系统 2 的常见问题解答 (FAQ) 的列表。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-105">Below is a list of frequently asked questions (FAQ) about the Windows Subsystem for Linux 2.</span></span>

## <a name="does-wsl-2-use-hyper-v-will-it-be-available-on-windows-10-home"></a><span data-ttu-id="d8f5c-106">WSL 2 是否使用 Hyper-V？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-106">Does WSL 2 use Hyper-V?</span></span> <span data-ttu-id="d8f5c-107">它是否可用于 Windows 10 家庭版？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-107">Will it be available on Windows 10 Home?</span></span>

<span data-ttu-id="d8f5c-108">WSL 2 在当前可使用 WSL 的所有 SKU 上都可使用，包括 Windows 10 家庭版。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-108">WSL 2 will be available on all SKUs where WSL is currently available, including Windows 10 Home.</span></span>

<span data-ttu-id="d8f5c-109">最新版本的 WSL 使用 Hyper-V 体系结构来实现其虚拟化。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-109">The newest version of WSL uses Hyper-V architecture to enable its virtualization.</span></span> <span data-ttu-id="d8f5c-110">此体系结构将在“虚拟机平台”可选组件中提供。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-110">This architecture will be available in the 'Virtual Machine Platform' optional component.</span></span> <span data-ttu-id="d8f5c-111">此可选组件在所有 SKU 上都将可用。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-111">This optional component will be available on all SKUs.</span></span> <span data-ttu-id="d8f5c-112">当我们更深入地了解 WSL 2 版本时，可以看到有关此体验的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-112">You can expect to see more details about this experience soon as we get closer to the WSL 2 release.</span></span>

## <a name="what-will-happen-to-wsl-1-will-it-be-abandoned"></a><span data-ttu-id="d8f5c-113">WSL 1 将发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-113">What will happen to WSL 1?</span></span> <span data-ttu-id="d8f5c-114">它是否将被弃用？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-114">Will it be abandoned?</span></span>

<span data-ttu-id="d8f5c-115">我们目前没有计划弃用 WSL 1。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-115">We currently have no plans to deprecate WSL 1.</span></span> <span data-ttu-id="d8f5c-116">你可以并行运行 WSL 1 和 WSL 2 发行版，还可以随时升级和降级任何发行版。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-116">You can run WSL 1 and WSL 2 distros side by side, and can upgrade and downgrade any distro at any time.</span></span> <span data-ttu-id="d8f5c-117">将 WSL 2 添加为新的体系结构为 WSL 团队提供了一个更好的平台来提供一些特性，使 WSL 成为在 Windows 中运行 Linux 环境的一种令人惊叹的方式。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-117">Adding WSL 2 as a new architecture presents a better platform for the WSL team to deliver features that make WSL an amazing way to run a Linux environment in Windows.</span></span>

## <a name="will-i-be-able-to-run-wsl-2-and-other-3rd-party-virtualization-tools-such-as-vmware-or-virtualbox"></a><span data-ttu-id="d8f5c-118">我是否能够运行 WSL 2 和其他第三方虚拟化工具（例如 VMware 或 VirtualBox）？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-118">Will I be able to run WSL 2 and other 3rd party virtualization tools such as VMware, or VirtualBox?</span></span>

<span data-ttu-id="d8f5c-119">当使用 Hyper-V 时，某些第三方应用程序无法工作，这意味着当启用了 WSL 2 时，这些应用程序（如 VMware 和 VirtualBox）将无法运行。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-119">Some 3rd party applications cannot work when Hyper-V is in use, which means they will not be able to run when WSL 2 is enabled, such as VMware and VirtualBox.</span></span> <span data-ttu-id="d8f5c-120">但最近，VirtualBox 和 VMware 都发布了支持 Hyper-V 和 WSL2 的版本！</span><span class="sxs-lookup"><span data-stu-id="d8f5c-120">However, recently both VirtualBox and VMware have released versions that support Hyper-V and WSL2!</span></span> <span data-ttu-id="d8f5c-121">可[在此处了解有关 VirtualBox 的更改的详细信息][1]，并可[在此处了解有关 VMware 的更改的详细信息][4]。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-121">You can learn more about [VirtualBox's changes here][1] and [VMware's changes here][4].</span></span>

<span data-ttu-id="d8f5c-122">我们一直在开发解决方案以支持 Hyper-V 的第三方集成。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-122">We are consistently working on solutions to support third-party integration of Hyper-V.</span></span> <span data-ttu-id="d8f5c-123">例如，我们向第三方虚拟化提供商公开了一组称为[虚拟机监控程序平台][2]的 API，可以用来使其软件与 Hyper-V 兼容。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-123">For example, we expose a set of APIs called [Hypervisor Platform][2] that third-party virtualization providers can use to make their software compatible with Hyper-V.</span></span> <span data-ttu-id="d8f5c-124">这使得应用程序可以将 Hyper-V 体系结构用于其模拟，例如，现在都与 Hyper-V 兼容的 [Google 安卓模拟器][3]和 VirtualBox 6 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-124">This lets applications use the Hyper-V architecture for their emulation such as [the Google Android Emulator][3], and VirtualBox 6 and above which are both now compatible with Hyper-V.</span></span>

## <a name="can-i-access-the-gpu-in-wsl-2-are-there-plans-to-increase-hardware-support"></a><span data-ttu-id="d8f5c-125">是否可以在 WSL 2 中访问 GPU？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-125">Can I access the GPU in WSL 2?</span></span> <span data-ttu-id="d8f5c-126">是否计划增加硬件支持？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-126">Are there plans to increase hardware support?</span></span>

<span data-ttu-id="d8f5c-127">在 WSL 2 的初始版本中，将会限制硬件访问支持，例如：你将无法访问 GPU、串行或 USB 设备。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-127">In initial releases of WSL 2 hardware access support will be limited, e.g: you will be unable to access the GPU, serial or USB devices.</span></span> <span data-ttu-id="d8f5c-128">但是，在我们手头的待完成工作中，增加更好的设备支持是一项非常重要的任务，因为这将为希望与这些设备交互的开发人员开放更多的用例。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-128">However, adding better device support is high on our backlog, as this opens many more use cases for developers that wish to interact with these devices.</span></span> <span data-ttu-id="d8f5c-129">同时，你始终可以使用具有串行端口访问的 WSL 1。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-129">In the meantime, you can always use WSL 1 which has serial port access.</span></span> <span data-ttu-id="d8f5c-130">请继续关注此博客并在 Twitter 上关注 WSL 团队成员，了解预览体验版本的最新功能，并提供反馈来说明你希望与哪些设备进行交互！</span><span class="sxs-lookup"><span data-stu-id="d8f5c-130">Please stay tuned to this blog and WSL team members on Twitter to stay informed about the latest features coming to insider builds and reach out to give us feedback on what devices you'd like to interact with!</span></span>

## <a name="will-wsl-2-be-able-to-use-networking-applications"></a><span data-ttu-id="d8f5c-131">WSL 2 是否能够使用网络应用程序？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-131">Will WSL 2 be able to use networking applications?</span></span>

<span data-ttu-id="d8f5c-132">是的，通常情况下，网络应用程序会更快，并且工作性能更好，因为我们有完全的系统调用兼容性。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-132">Yes, in general networking applications will be faster and work better since we have full system call compatibility.</span></span> <span data-ttu-id="d8f5c-133">但是，新的体系结构使用虚拟化的网络组件。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-133">However, the new architecture uses virtualized networking components.</span></span> <span data-ttu-id="d8f5c-134">这意味着，在初始预览版本中，WSL 2 的行为将更类似于虚拟机，例如：WSL 2 将具有与主机不同的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-134">This means that in initial preview builds WSL 2 will behave more similarly to a virtual machine, e.g: WSL 2 will have a different IP address than the host machine.</span></span> <span data-ttu-id="d8f5c-135">我们正致力于让用户感觉 WSL 2 与 WSL 1 一样，这包括改进我们的网络情况。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-135">We are committed to making WSL 2 feel the same as WSL 1, and that includes improving our networking story.</span></span> <span data-ttu-id="d8f5c-136">我们希望尽快添加改进，例如，使用 localhost 从 Linux 或 Windows 访问所有网络应用。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-136">We expect to add improvements as quickly as we are able to, such as accessing all networking apps from Linux or Windows using localhost.</span></span> <span data-ttu-id="d8f5c-137">随着 WSL 2 的发布，我们将发布更多关于我们的网络情况和改进的细节。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-137">We will be posting more details about our networking story and improvements as we approach the release of WSL 2.</span></span>

## <a name="can-i-run-wsl-2-in-a-virtual-machine"></a><span data-ttu-id="d8f5c-138">是否可以在虚拟机中运行 WSL 2？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-138">Can I run WSL 2 in a virtual machine?</span></span>

<span data-ttu-id="d8f5c-139">可以！</span><span class="sxs-lookup"><span data-stu-id="d8f5c-139">Yes!</span></span> <span data-ttu-id="d8f5c-140">你需要确保虚拟机已启用嵌套虚拟化。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-140">You need to make sure that the virtual machine has nested virtualization enabled.</span></span> <span data-ttu-id="d8f5c-141">可以在父 Hyper-V 主机中在 PowerShell 窗口中使用管理员权限运行以下命令来启用此功能：</span><span class="sxs-lookup"><span data-stu-id="d8f5c-141">This can be enabled in your parent Hyper-V host by running the following command in a PowerShell window with Administrator privileges:</span></span>

`Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true`

<span data-ttu-id="d8f5c-142">请确保将“&lt;VMName&gt;”替换为你的虚拟机的名称。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-142">Make sure to replace '&lt;VMName&gt;' with the name of your virtual machine.</span></span>

## <a name="can-i-use-wslconf-in-wsl-2"></a><span data-ttu-id="d8f5c-143">是否可以在 WSL 2 中使用 wsl.conf？</span><span class="sxs-lookup"><span data-stu-id="d8f5c-143">Can I use wsl.conf in WSL 2?</span></span>

<span data-ttu-id="d8f5c-144">WSL 2 支持 WSL 1 使用的同一 WSL 文件。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-144">WSL 2 supports the same wsl.conf file that WSL 1 uses.</span></span> <span data-ttu-id="d8f5c-145">这意味着，你在 WSL 1 发行版中设置的任何配置选项（例如自动装载 Windows 驱动器、启用或禁用互操作、更改将装载 Windows 驱动器的目录等）在 WSL 2 中都可以工作。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-145">This means that any configuration options that you had set in a WSL 1 distro, such as automounting Windows drives, enabling or disabling interop, changing the directory where Windows drives will be mounted, etc. will all work inside of WSL 2.</span></span> <span data-ttu-id="d8f5c-146">还可以在[发行版管理](./wsl-config.md)页面中详细了解 WSL 中的配置选项。</span><span class="sxs-lookup"><span data-stu-id="d8f5c-146">You can learn more about the configuration options in WSL in the [Distro Management](./wsl-config.md) page.</span></span>

 [1]: https://www.virtualbox.org/wiki/Changelog-6.0
 [2]: https://docs.microsoft.com/virtualization/api/
 [3]: https://devblogs.microsoft.com/visualstudio/hyper-v-android-emulator-support/
 [4]: https://blogs.vmware.com/workstation/2020/01/vmware-workstation-tech-preview-20h1.html
