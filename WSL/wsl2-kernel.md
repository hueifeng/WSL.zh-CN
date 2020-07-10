---
title: 更新 WSL 2 Linux 内核
description: 有关如何手动更新 WSL 2 Linux 内核的说明
keywords: wsl, windows, linux 内核, 适用于 Linux 的 Windows 子系统, 内核
ms.date: 03/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: bef722f5653380d9f6d104f1a7c116a7599658c9
ms.sourcegitcommit: ba52d673c123fe8ae61e872a33e218cfc30a1f82
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86033046"
---
# <a name="updating-the-wsl-2-linux-kernel"></a>更新 WSL 2 Linux 内核

若要手动更新 WSL 2 内的 Linux 内核，请按照以下步骤执行操作。

> [!NOTE] 
> 如果安装程序找不到 WSL 1，请右键单击 Linux 内核更新安装程序，然后按“卸载”，并重新运行安装程序

## <a name="download-the-linux-kernel-update-package"></a>下载 Linux 内核更新包

请[下载适用于 x64 计算机的最新 WSL2 Linux 内核](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)更新包。

> [!NOTE]
> 如果使用的是 ARM64 计算机，请下载 [ARM64 包](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)。

## <a name="install-the-linux-kernel-update-package"></a>安装 Linux 内核更新包

若要安装 Linux 内核更新包，请执行以下操作：

  1. 运行上一步中下载的更新包。

  2. 系统将提示你提供提升的权限，选择“是”以批准此安装。

  3. 安装完成后，便可以开始使用 WSL2 了！

## <a name="future-plans-for-updating-the-wsl2-linux-kernel"></a>有关更新 WSL2 Linux 内核的未来计划

有关详细信息，请参阅 [Windows 命令行博客](https://aka.ms/cliblog)上的文章[对更新 WSL2 Linux 内核的更改](https://devblogs.microsoft.com/commandline/wsl2-will-be-generally-available-in-windows-10-version-2004)。

## <a name="troubleshooting"></a>疑难解答

### <a name="this-update-only-applies-to-machines-with-the-windows-subsystem-for-linux"></a>此更新仅适用于具有适用于 Linux 的 Windows 子系统的计算机
要安装 MSI 内核，需要 WSL，应先启用。 如果失败，将看到以下消息：`This update only applies to machines with the Windows Subsytem for Linux`。 

出现此消息有三个可能的原因：

1. 你仍使用旧版 Windows，不支持 WSL 2。 请查看 [WSL 2 要求](https://docs.microsoft.com/windows/wsl/install-win10#update-to-wsl-2)，升级到使用 WSL 2。 
2. 未启用 `Windows Subsystem for Linux`。 请按照[适用于 Linux 的 Windows 子系统安装指南](https://docs.microsoft.com/windows/wsl/install-win10)进行操作。
3. 启用 `Windows Subsystem for Linux` 后，需要重启才能生效，请重启计算机，然后重试。

### `WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel`

每次 %SystemRoot%\system32\lxss\tools\, 中缺少内核时，都可能会出现上述错误。

解决该错误的一些方法如下：

1. 请按照以下网站上的说明手动安装 Linux 内核： https://aka.ms/wsl2kernel
2. 从“添加或删除程序”卸载 MSI，然后重新安装
