---
title: 手动下载适用于 Linux 的 Windows 子系统 (WSL) 发行版
description: 有关如何手动下载适用于 Linux 的 Windows 子系统发行版的说明。
keywords: wsl, 适用于 linux 的 windows 子系统, 手动安装, 手动安装, microsoft store, windows 10, curl, Add-appxpackage, 长期服务, LTSC
ms.date: 05/28/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: d948ce9d304314bdd15b98136b8a99ca35723139
ms.sourcegitcommit: e67eb4aedff57a304188ca3360aba25605f8bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84746273"
---
# <a name="manually-download-windows-subsystem-for-linux-distro-packages"></a>手动下载适用于 Linux 的 Windows 子系统发行版包

在许多情况下，你可能无法（或不想）通过 Microsoft Store 安装 WSL Linux 发行版。 具体而言，你可能正在运行不支持 Microsoft Store 的 Windows Server 或长期服务 (LTSC) 桌面操作系统 SKU，或者你的公司网络策略和/或管理员不允许在你的环境中使用 Microsoft Store。

在这些情况下，虽然 WSL 本身可用，但如果你无法访问应用商店，如何下载并在 WSL 中安装 Linux 发行版？

> 注意：**命令行 shell 环境（包括 Cmd、PowerShell 和 Linux/WSL 发行版）不允许在 Windows 10 S 模式下运行**。 存在此限制是为了确保 S 模式提供的完整性和安全目标：有关详细信息，请参阅[此文章](https://blogs.msdn.microsoft.com/commandline/2017/05/18/will-linux-distros-run-on-windows-10-s/)。

## <a name="downloading-distros"></a>下载发行版

如果 Microsoft Store 应用不可用，则可以通过单击以下链接来下载并手动安装 Linux 发行版：
* [Ubuntu 20.04](https://aka.ms/wslubuntu2004)
* [Ubuntu 20.04 ARM](https://aka.ms/wslubuntu2004arm)
* [Ubuntu 18.04](https://aka.ms/wsl-ubuntu-1804)
* [Ubuntu 18.04 ARM](https://aka.ms/wsl-ubuntu-1804-arm)
* [Ubuntu 16.04](https://aka.ms/wsl-ubuntu-1604)
* [Debian GNU/Linux](https://aka.ms/wsl-debian-gnulinux)
* [Kali Linux](https://aka.ms/wsl-kali-linux-new)
* [OpenSUSE Leap 42](https://aka.ms/wsl-opensuse-42)
* [SUSE Linux Enterprise Server 12](https://aka.ms/wsl-sles-12)
* [Fedora Remix for WSL](https://github.com/WhitewaterFoundry/WSLFedoraRemix/releases/)

这将导致 `<distro>.appx` 包下载到你选择的文件夹。 按照[安装说明](#installing-your-distro)来安装你下载的发行版。

## <a name="downloading-distros-via-the-command-line"></a>通过命令行下载发行版
如果愿意，也可以通过命令行下载你首选的发行版：

 ### <a name="download-using-powershell"></a>使用 PowerShell 下载
 若要使用 PowerShell 下载发行版，请使用 [Invoke-WebRequest](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1) cmdlet。 下面是用于下载 Ubuntu 16.04 的示例说明。

```powershell
Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1604 -OutFile Ubuntu.appx -UseBasicParsing
```

> [!TIP]
> 如果下载需要很长时间，请通过设置 `$ProgressPreference = 'SilentlyContinue'` 来关闭进度栏

### <a name="download-using-curl"></a>使用 curl 下载
Windows 10 Spring 2018 更新（或更高版本）包括了流行的 [curl 命令行实用程序](https://curl.haxx.se/)，你可以使用它从命令行调用 web 请求（即 HTTP GET、POST、PUT 等命令）。 可以使用 `curl.exe` 下载上述发行版：

```console
curl.exe -L -o ubuntu-1604.appx https://aka.ms/wsl-ubuntu-1604
```

在上面的示例中，将执行 `curl.exe`（而不仅仅是 `curl`），以确保在 PowerShell 中调用真正的 curl 可执行文件，而不是调用 [Invoke WebRequest](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6) 的 PowerShell curl 别名

> 注意：如果必须使用 Cmd shell 和/或 `.bat` / `.cmd` 脚本来调用/编写下载步骤，则使用 `curl` 可能更好。

## <a name="installing-your-distro"></a>安装发行版
如果使用的是 Windows 10，则可以使用 PowerShell 安装发行版。 只需导航到包含从上面下载的发行版的文件夹，然后在该目录中运行以下命令，其中，`app_name` 是 distro.appx 文件的名称。  
```Powershell
Add-AppxPackage .\app_name.appx
```

如果使用的是 Windows server，可以在 [Windows Server](install-on-server.md) 文档页上找到安装说明。

安装分发版后，请按照常规说明[更新到 WSL 2](./install-win10.md#update-to-wsl-2) 或[创建新的用户帐户和密码](./user-support.md)。
