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
# <a name="wsl-2-faqs"></a>WSL 2 常见问题解答

下面是有关适用于 Linux 的 Windows 子系统 2 的常见问题解答 (FAQ) 的列表。

## <a name="does-wsl-2-use-hyper-v-will-it-be-available-on-windows-10-home"></a>WSL 2 是否使用 Hyper-V？ 它是否可用于 Windows 10 家庭版？

WSL 2 在当前可使用 WSL 的所有 SKU 上都可使用，包括 Windows 10 家庭版。

最新版本的 WSL 使用 Hyper-V 体系结构来实现其虚拟化。 此体系结构将在“虚拟机平台”可选组件中提供。 此可选组件在所有 SKU 上都将可用。 当我们更深入地了解 WSL 2 版本时，可以看到有关此体验的更多详细信息。

## <a name="what-will-happen-to-wsl-1-will-it-be-abandoned"></a>WSL 1 将发生什么情况？ 它是否将被弃用？

我们目前没有计划弃用 WSL 1。 你可以并行运行 WSL 1 和 WSL 2 发行版，还可以随时升级和降级任何发行版。 将 WSL 2 添加为新的体系结构为 WSL 团队提供了一个更好的平台来提供一些特性，使 WSL 成为在 Windows 中运行 Linux 环境的一种令人惊叹的方式。

## <a name="will-i-be-able-to-run-wsl-2-and-other-3rd-party-virtualization-tools-such-as-vmware-or-virtualbox"></a>我是否能够运行 WSL 2 和其他第三方虚拟化工具（例如 VMware 或 VirtualBox）？

当使用 Hyper-V 时，某些第三方应用程序无法工作，这意味着当启用了 WSL 2 时，这些应用程序（如 VMware 和 VirtualBox）将无法运行。 但最近，VirtualBox 和 VMware 都发布了支持 Hyper-V 和 WSL2 的版本！ 可[在此处了解有关 VirtualBox 的更改的详细信息][1]，并可[在此处了解有关 VMware 的更改的详细信息][4]。

我们一直在开发解决方案以支持 Hyper-V 的第三方集成。 例如，我们向第三方虚拟化提供商公开了一组称为[虚拟机监控程序平台][2]的 API，可以用来使其软件与 Hyper-V 兼容。 这使得应用程序可以将 Hyper-V 体系结构用于其模拟，例如，现在都与 Hyper-V 兼容的 [Google 安卓模拟器][3]和 VirtualBox 6 及更高版本。

## <a name="can-i-access-the-gpu-in-wsl-2-are-there-plans-to-increase-hardware-support"></a>是否可以在 WSL 2 中访问 GPU？ 是否计划增加硬件支持？

在 WSL 2 的初始版本中，将会限制硬件访问支持，例如：你将无法访问 GPU、串行或 USB 设备。 但是，在我们手头的待完成工作中，增加更好的设备支持是一项非常重要的任务，因为这将为希望与这些设备交互的开发人员开放更多的用例。 同时，你始终可以使用具有串行端口访问的 WSL 1。 请继续关注此博客并在 Twitter 上关注 WSL 团队成员，了解预览体验版本的最新功能，并提供反馈来说明你希望与哪些设备进行交互！

## <a name="will-wsl-2-be-able-to-use-networking-applications"></a>WSL 2 是否能够使用网络应用程序？

是的，通常情况下，网络应用程序会更快，并且工作性能更好，因为我们有完全的系统调用兼容性。 但是，新的体系结构使用虚拟化的网络组件。 这意味着，在初始预览版本中，WSL 2 的行为将更类似于虚拟机，例如：WSL 2 将具有与主机不同的 IP 地址。 我们正致力于让用户感觉 WSL 2 与 WSL 1 一样，这包括改进我们的网络情况。 我们希望尽快添加改进，例如，使用 localhost 从 Linux 或 Windows 访问所有网络应用。 随着 WSL 2 的发布，我们将发布更多关于我们的网络情况和改进的细节。

## <a name="can-i-run-wsl-2-in-a-virtual-machine"></a>是否可以在虚拟机中运行 WSL 2？

可以！ 你需要确保虚拟机已启用嵌套虚拟化。 可以在父 Hyper-V 主机中在 PowerShell 窗口中使用管理员权限运行以下命令来启用此功能：

`Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true`

请确保将“&lt;VMName&gt;”替换为你的虚拟机的名称。

## <a name="can-i-use-wslconf-in-wsl-2"></a>是否可以在 WSL 2 中使用 wsl.conf？

WSL 2 支持 WSL 1 使用的同一 WSL 文件。 这意味着，你在 WSL 1 发行版中设置的任何配置选项（例如自动装载 Windows 驱动器、启用或禁用互操作、更改将装载 Windows 驱动器的目录等）在 WSL 2 中都可以工作。 还可以在[发行版管理](./wsl-config.md)页面中详细了解 WSL 中的配置选项。

 [1]: https://www.virtualbox.org/wiki/Changelog-6.0
 [2]: https://docs.microsoft.com/virtualization/api/
 [3]: https://devblogs.microsoft.com/visualstudio/hyper-v-android-emulator-support/
 [4]: https://blogs.vmware.com/workstation/2020/01/vmware-workstation-tech-preview-20h1.html
