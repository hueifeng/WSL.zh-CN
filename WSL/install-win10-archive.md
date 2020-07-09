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
# <a name="archived-instructions"></a>存档说明

以下指南将指导你完成一些步骤，在运行 Windows 10 的计算机上安装适用于 Linux 的 Windows 子系统 (WSL) 时，需要执行这些步骤。

## <a name="enable-the-windows-subsystem-for-linux-optional-feature"></a>启用“适用于 Linux 的 Windows 子系统”可选功能

在安装 Linux 分发版之前，必须先在 Windows 10 上启用“适用于 Linux 的 Windows 子系统”可选功能：

1. 以管理员身份打开 PowerShell，然后输入此脚本：

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

1. 出现提示时，重启计算机。

## <a name="install-a-linux-distribution"></a>安装 Linux 发行版本

有三种方法可用于下载和安装你偏好的 Linux 分发版：

- 从 Microsoft Store 下载并安装（参阅下文）
- [下载并从命令行手动安装](install-manual.md)
- [在 Windows Server 上安装](install-on-server.md)

### <a name="install-from-the-microsoft-store"></a>从 Microsoft Store 安装

可以从 Microsoft Store 将 Linux 分发版安装到 Windows 10（内部版本 16215+）上。

> [!NOTE]
> 遵循以下步骤[检查 Windows 10 内部版本号](troubleshooting.md#check-your-build-number)。

1. 打开 Microsoft Store，并选择你偏好的 Linux 分发版。

    ![Microsoft Store 中的 Linux 分发版视图](media/store.png)

    单击以下链接会打开每个分发版的 Microsoft Store 页面：

    - [Ubuntu 16.04 LTS](https://www.microsoft.com/store/apps/9pjn388hp8c9)
    - [Ubuntu 18.04 LTS](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)
    - [OpenSUSE Leap 15](https://www.microsoft.com/store/apps/9n1tb6fpvj8c)
    - [OpenSUSE Leap 42](https://www.microsoft.com/store/apps/9njvjts82tjx)
    - [SUSE Linux Enterprise Server 12](https://www.microsoft.com/store/apps/9p32mwbh6cns)
    - [SUSE Linux Enterprise Server 15](https://www.microsoft.com/store/apps/9pmw35d7fnlx)
    - [Kali Linux](https://www.microsoft.com/store/apps/9PKR34TNCV07)
    - [Debian GNU/Linux](https://www.microsoft.com/store/apps/9MSVKQC78PK6)
    - [Fedora Remix for WSL](https://www.microsoft.com/store/apps/9n6gdm4k2hnc)
    - [Pengwin](https://www.microsoft.com/store/apps/9NV1GV1PXZ6P)
    - [Pengwin Enterprise](https://www.microsoft.com/store/apps/9N8LP0X93VCP)
    - [Alpine WSL](https://www.microsoft.com/store/apps/9p804crf0395)

1. 选择“获取”，在该分发版完成下载后，请选择“启动”。

    ![Microsoft Store 中的 Linux 分发版视图](media/UbuntuStore.png)

## <a name="complete-initialization-of-your-distro"></a>完成分发版的初始化

启动 Linux 分发版后，请按照屏幕上的说明初始化分发版。

> [!NOTE]
> 对于 Windows Server，请使用安装文件夹中的可执行文件 `<distro>.exe` 启动分发版。

首次运行新安装的分发版时，会打开一个控制台窗口，其中指出需要等待一两分钟时间，以便安装完成。 在这最后一个安装阶段，分发版的文件将会解压缩，并存储在电脑上供你使用。 这可能需要一分钟或更长时间，具体取决于电脑存储设备的性能。 仅当分发版是干净安装的版本时，才需要执行此初始安装阶段 - 将来在不到一秒内即可启动分发版。

## <a name="set-up-a-new-linux-user-account"></a>设置新的 Linux 用户帐户

安装完成后，系统会提示创建新的用户帐户（及其密码）。

![Windows 控制台中的 Ubuntu 解包](media/UbuntuInstall.png)

此用户帐户用于普通的非管理员用户，在默认情况下，你在启动分发版时将以该用户身份登录。 可根据需要选择任何用户名和密码 - 它们与 Windows 用户名无关。

打开新的分发版实例时，系统不会提示你输入密码，但**如果使用 `sudo` 提升了进程的权限，则需要输入密码**，因此请确保选择一个容易记住的密码！ 有关详细信息，请参阅[用户支持](user-support.md)页。

## <a name="update--upgrade-packages"></a>更新和升级包

大多数分发版随附了一个空的的包目录或最简单的包目录。 我们强烈建议定期更新包目录，并使用分发版的首选包管理器升级已安装的包。 对于 Debian/Ubuntu，请使用 apt：

```bash
sudo apt update && sudo apt upgrade
```

Windows 不会自动更新或升级 Linux 分发版。 大多数 Linux 用户往往倾向于自行控制此任务。

现在，可以在 WSL 上享用新的 Linux 分发版！

## <a name="troubleshooting"></a>疑难解答

下面是相关的安装错误和建议的修复措施。 有关其他常见错误及其解决方法，请参阅 [WSL 故障排除页](troubleshooting.md)。

### <a name="installation-failed-with-error-0x8007007e"></a>安装失败，出现错误 0x8007007e

当系统不支持来自 Store 的 Linux 时会出现此错误。  请确保：

- 运行 Windows 内部版本 16215 或更高版本。 [检查内部版本](troubleshooting.md#check-your-build-number)。
- 已启用“适用于 Linux 的 Windows 子系统”可选组件，并已重启计算机。  [确保已启用 WSL](troubleshooting.md#confirm-wsl-is-enabled)。

### <a name="installation-failed-with-error-0x80070003"></a>安装失败，出现错误 0x80070003

适用于 Linux 的 Windows 子系统只能在系统驱动器（通常是 `C:` 驱动器）中运行。 请确保将分发版存储在系统驱动器上：

- 打开“设置” -> “存储” -> “更多存储设置:  更改新内容的保存位置”
  
    ![用于在 C: 驱动器上安装应用的系统设置屏幕截图](media/AppStorage.png)

### <a name="wslregisterdistribution-failed-with-error-0x8007019e"></a>WslRegisterDistribution 失败，出现错误 0x8007019e

未启用“适用于 Linux 的 Windows 子系统”可选组件：

- 打开“控制面板” -> “程序和功能” -> “打开或关闭 Windows 功能”-> 选中“适用于 Linux 的 Windows 子系统”，或使用本文开头所述的 PowerShell cmdlet。   
