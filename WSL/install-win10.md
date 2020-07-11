---
title: 在 Windows 10 上安装适用于 Linux 的 Windows 子系统 (WSL)
description: 有关在 Windows 10 上安装适用于 Linux 的 Windows 子系统的说明。
keywords: BashOnWindows, bash, wsl, Windows, 适用于 Linux 的 Windows 子系统, windows 子系统, ubuntu, debian, suse, Windows 10, 安装, 启用, WSL2, 版本 2
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 222afa3ee2a4e8948cd0159d794fc7a4375e7ba7
ms.sourcegitcommit: 16ffb1a096a4a7fbb77c58f92258051930cc82da
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86157933"
---
# <a name="windows-subsystem-for-linux-installation-guide-for-windows-10"></a>适用于 Linux 的 Windows 子系统安装指南 (Windows 10)

## <a name="install-the-windows-subsystem-for-linux"></a>安装适用于 Linux 的 Windows 子系统

必须先启用“适用于 Linux 的 Windows 子系统”可选功能，然后才能在 Windows 上安装 Linux 分发版。

以管理员身份打开 PowerShell 并运行：

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

若要仅安装 WSL 1，现在应重启计算机并继续[安装所选的 Linux 分发版](./install-win10.md#install-your-linux-distribution-of-choice)，否则请等待重启并继续更新到 WSL 2。 阅读有关[比较 WSL 2 和 WSL 1](./compare-versions.md) 的详细信息。

## <a name="update-to-wsl-2"></a>更新到 WSL 2

若要更新到 WSL 2，必须满足以下条件：

- 运行 Windows 10（[已更新到版本 2004](ms-settings:windowsupdate) 的**内部版本 19041** 或更高版本）。

- 通过按 **Windows Logo 键 + R**，检查你的 Windows 版本，然后键入 **winver**，选择**确定**。 （或者在 Windows 命令提示符下输入 `ver` 命令）。 如果内部版本低于 19041，请[更新到最新的 Windows 版本](ms-settings:windowsupdate)。 [获取 Windows 更新助手](https://www.microsoft.com/software-download/windows10)。

### <a name="enable-the-virtual-machine-platform-optional-component"></a>启用“虚拟机平台”可选组件

安装 WSL 2 之前，必须启用“虚拟机平台”可选功能。

以管理员身份打开 PowerShell 并运行：

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

**重新启动**计算机，以完成 WSL 安装并更新到 WSL 2。

### <a name="set-wsl-2-as-your-default-version"></a>将 WSL 2 设置为默认版本

安装新的 Linux 分发版时，请在 PowerShell 中运行以下命令，以将 WSL 2 设置为默认版本：

```powershell
wsl --set-default-version 2
```

运行该命令后，你可能会看到此消息：`WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`。 跟随链接（[https://aka.ms/wsl2kernel](https://aka.ms/wsl2kernel)），在文档中安装来自该页面的 MSI，以便在计算机上安装 Linux 内核供 WSL 2 使用。 安装内核后，请再次运行该命令，该命令应会成功完成而不显示消息。 

> [!NOTE]
> 从 WSL 1 更新到 WSL 2 可能需要几分钟才能完成，具体取决于目标分发版的大小。 如果从 Windows 10 周年更新或创意者更新运行 WSL 1 的旧（历史）安装，可能会遇到更新错误。 按照这些说明[卸载并删除任何旧分发](https://docs.microsoft.com/windows/wsl/install-legacy#uninstallingremoving-the-legacy-distro)。 
>
> 如果 `wsl --set-default-version` 结果为无效命令，请输入 `wsl --help`。 如果 `--set-default-version` 未列出，则表示你的 OS 不支持它，你需要更新到版本 2004、内部版本 19041 或更高版本。

## <a name="install-your-linux-distribution-of-choice"></a>安装所选的 Linux 分发版

1. 打开 [Microsoft Store](https://aka.ms/wslstore)，并选择你偏好的 Linux 分发版。

    ![Microsoft Store 中的 Linux 分发版的视图](media/store.png)

    单击以下链接会打开每个分发版的 Microsoft Store 页面：

    - [Ubuntu 16.04 LTS](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    - [Ubuntu 18.04 LTS](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    - [Ubuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71)
    - [openSUSE Leap 15.1](https://www.microsoft.com/store/apps/9NJFZK00FGKV)
    - [SUSE Linux Enterprise Server 12 SP5](https://www.microsoft.com/store/apps/9MZ3D1TRP8T1)
    - [SUSE Linux Enterprise Server 15 SP1](https://www.microsoft.com/store/apps/9PN498VPMF3Z)
    - [Kali Linux](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    - [Debian GNU/Linux](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    - [Fedora Remix for WSL](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    - [Pengwin](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    - [Pengwin Enterprise](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    - [Alpine WSL](https://www.microsoft.com/store/apps/9p804crf0395)

2. 在分发版的页面中，选择“获取”。

    ![Microsoft Store 中的 Linux 分发版](media/UbuntuStore.png)

## <a name="set-up-a-new-distribution"></a>设置新分发版

首次启动新安装的 Linux 分发版时，将打开一个控制台窗口，系统会要求你等待一分钟或两分钟，以便文件解压缩并存储到电脑上。 未来的所有启动时间应不到一秒。

然后，需要[为新的 Linux 分发版创建用户帐户和密码](./user-support.md)。

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

## <a name="set-your-distribution-version-to-wsl-1-or-wsl-2"></a>将分发版版本设置为 WSL 1 或 WSL 2

可以打开 PowerShell 命令行并输入以下命令（仅在 [Windows 内部版本 19041 或更高版本](ms-settings:windowsupdate)中可用），来检查分配给每个已安装的 Linux 分发版的 WSL 版本：`wsl -l -v`

```powershell
wsl --list --verbose
```

若要将分发版设置为受某一 WSL 版本支持，请运行：

```powershell
wsl --set-version <distribution name> <versionNumber>
```

请确保将 `<distribution name>` 替换为你的分发版的实际名称，并将 `<versionNumber>` 替换为数字“1”或“2”。 可以随时更改回 WSL 1，方法是运行与上面相同的命令，但将“2”替换为“1”。

此外，如果要使 WSL 2 成为你的默认体系结构，可以通过此命令执行该操作：

```powershell
wsl --set-default-version 2
```

这会将安装的任何新分发版的版本设置为 WSL 2。

## <a name="troubleshooting-installation"></a>排查安装问题

下面是相关的错误和建议的修复措施。 有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。

- **安装失败并出现错误 0x80070003**
  - 适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。 请确保分发版存储在系统驱动器上：  
  - 打开“设置”->“存储”->“更多存储设置：  更改新内容的保存位置”
    ![用于在 C: 驱动器中安装应用的系统设置屏幕截图](media/AppStorage.png)

- **WslRegisterDistribution 失败并出现错误 0x8007019e**
  - 未启用“适用于 Linux 的 Windows 子系统”可选组件：
  - 打开“控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中“适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。   

- **安装失败，出现错误 0x80070003 或错误 0x80370102**
  - 请确保在计算机的 BIOS 内已启用虚拟化。 有关如何执行此操作的说明因计算机而异，并且很可能在 CPU 相关选项下。

- **尝试升级时出错：`Invalid command line option: wsl --set-version Ubuntu 2`**
  - 请确保已启用适用于 Linux 的 Windows 子系统，并且你使用的是 Windows 内部版本 19041 或更高版本。 若要启用 WSL，请在 PowerShell 提示符下以具有管理员权限的身份运行此命令：`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`。 可在[此处](./install-win10.md)找到完整的 WSL 安装说明。

- **由于虚拟磁盘系统的某个限制，无法完成所请求的操作。虚拟硬盘文件必须是解压缩的且未加密的，并且不能是稀疏的。**
  - 请检查 [WSL GitHub 主题 #4103](https://github.com/microsoft/WSL/issues/4103)，其中跟踪了此问题以提供更新的信息。

- **无法将词语“wsl”识别为 cmdlet、函数、脚本文件或可运行程序的名称。**
  - 请确保[已安装“适用于 Linux 的 Windows 子系统”可选组件](./install-win10.md#enable-the-virtual-machine-platform-optional-component)。 此外，如果你使用的是 ARM64 设备，并从 PowerShell 运行此命令，则会收到此错误。 请改为从 [PowerShell Core](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6) 或从命令提示符运行 `wsl.exe`。
