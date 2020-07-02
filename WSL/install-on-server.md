---
title: 在 Windows Server 上安装 Linux 子系统
description: Windows Server 上的 Linux 子系统的安装说明。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, windows server
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: ebcd7f6b10d2b734b1f2a66f64a5e3292855bcf4
ms.sourcegitcommit: 5d3898772851e6ac9a310f219cc0d71278f95d22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671017"
---
# <a name="windows-server-installation-guide"></a>Windows Server 安装指南

适用于 Linux 的 Windows 子系统可供在 Windows Server 2019（版本 1709）和更高版本上安装。 本指南将指导你完成在计算机上启用 WSL 的步骤。

## <a name="enable-the-windows-subsystem-for-linux"></a>启用适用于 Linux 的 Windows 子系统

必须启用“适用于 Linux 的 Windows 子系统”可选功能并重启，然后才能在 Windows 上运行 Linux 发行版。

以管理员身份打开 PowerShell 并运行：

```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

```

## <a name="download-a-linux-distribution"></a>下载 Linux 分发版

按照[这些说明](install-manual.md)下载你最喜爱的 Linux 发行版。

## <a name="extract-and-install-a-linux-distribution"></a>提取并安装 Linux 分发版

下载 Linux 分发版后，若要提取其内容并进行手动安装，请执行以下步骤：

1. 使用 PowerShell 提取 `<distro>.appx` 包的内容：

    ```powershell
    Rename-Item .\Ubuntu.appx .\Ubuntu.zip
    Expand-Archive .\Ubuntu.zip .\Ubuntu
    ```

2. 在目标文件夹中运行分发版启动器应用程序。 启动器通常命名为 `<distro>.exe`（例如，`ubuntu.exe`）。

    ![Windows Server 上展开的 Ubuntu 发行版](media/server-appx-expand.png)

> [!CAUTION]
> **安装失败并出现错误 0x8007007e**：如果收到此错误，则表明系统不支持 WSL。 请确保运行的是 Windows 版本 16215 或更高版本。 [检查内部版本](troubleshooting.md#check-your-build-number)。 另外，请进行检查以[确认 WSL 已启用](troubleshooting.md#confirm-wsl-is-enabled)，并且在启用此功能后重新启动了计算机。  

3. 使用 PowerShell 将你的分发版路径添加到 Windows 环境路径（在本例中为 `C:\Users\Administrator\Ubuntu`）：

```powershell
$userenv = [System.Environment]::GetEnvironmentVariable("Path", "User")
[System.Environment]::SetEnvironmentVariable("PATH", $userenv + ";C:\Users\Administrator\Ubuntu", "User")
```

现在，可以通过键入 `<distro>.exe` 从任何路径启动你的分发版。 例如： `ubuntu.exe`。

安装了分发版后，必须先[初始化新的分发版实例](initialize-distro.md)，然后才能使用它。
