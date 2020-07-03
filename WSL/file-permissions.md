---
title: 文件权限
description: 了解 WSL 如何确定 Windows 中的文件权限
keywords: BashOnWindows, bash, wsl, wsl2, Windows, 适用于 Linux 的 Windows 子系统, windows 子系统, ubuntu, debian, suse, Windows 10, 文件, 权限
ms.date: 01/14/2020
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ms.localizationpriority: high
ms.openlocfilehash: 81d4cfa1ae57cdd077ba8cbd614111881724718a
ms.sourcegitcommit: f1b049a1276782d4f2754f46a8d2025b598a0784
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85336070"
---
# <a name="file-permissions-for-wsl"></a>WSL 的文件权限

本页详细说明了 Linux 文件权限在适用于 Linux 的 Windows 子系统上是如何解释的，尤其是在访问 NT 文件系统上 Windows 内部的资源时。 本文档假定读者基本了解 [Linux 文件系统权限结构](https://wiki.archlinux.org/index.php/File_permissions_and_attributes) 和 [umask 命令](https://en.wikipedia.org/wiki/Umask)。

从 WSL 访问 Windows 文件时，文件权限是根据 Windows 权限计算的，或者是从已由 WSL 添加到文件的元数据中读取的。 默认情况下，此元数据处于未启用状态。

## <a name="wsl-metadata-on-windows-files"></a>Windows 文件上的 WSL 元数据

如果在 WSL 中以装载选项的形式启用了元数据，则可以在 Windows NT 文件上添加扩展属性并对其进行解释，从而提供 Linux 文件系统权限。

WSL 可以添加四个 NTFS 扩展属性：

| 属性名称 | 说明 |
| --- | --- |
| $LXUID | 用户所有者 ID |
| $LXGID | 组所有者 ID |
| $LXMOD | 文件模式（文件系统权限八进制数字和类型，例如：0777） |
| $LXDEV | 设备（如果它是设备文件） |

此外，任何并非常规文件或目录的文件（例如：符号链接、FIFO、块设备、unix 套接字和字符设备）也有 NTFS [重新分析点](https://docs.microsoft.com/windows/win32/fileio/reparse-points)。 这样一来，就能够以快得多的速度确定给定目录中的文件类型，而不必查询其扩展属性。

## <a name="file-access-scenarios"></a>文件访问方案

下面介绍了在使用适用于 Linux 的 Windows 子系统以不同的方式访问文件时，权限是如何确定的。

### <a name="accessing-files-in-the-windows-drive-file-system-drvfs-from-linux"></a>从 Linux 访问 Windows 驱动器文件系统 (DrvFS) 中的文件

在从 WSL 访问 Windows 文件（最有可能是通过 `/mnt/c`）时，会出现这些情况。

#### <a name="reading-file-permissions-from-an-existing-windows-file"></a>从现有 Windows 文件读取文件权限

结果取决于文件是否已具有现有元数据。

##### <a name="drvfs-file-does-not-have-metadata-default"></a>DrvFS 文件没有元数据（默认）

如果文件没有关联的元数据，则我们会将 Windows 用户的有效权限转换为读取/写入/执行位，并将其设置为对用户、组和其他用户而言相同的值。 例如，如果你的 Windows 用户帐户具有对该文件的读取和执行访问权限，但不具有对该文件的写入访问权限，则该帐户将对用户、组和其他对象显示为 `r-x`。 如果该文件在 Windows 中设有“只读”属性，则我们不会在 Linux 中授予写入权限。

##### <a name="the-file-has-metadata"></a>文件有元数据

如果文件的元数据存在，则只需使用这些元数据值，而不是转换 Windows 用户的有效权限。

#### <a name="changing-file-permissions-on-an-existing-windows-file-using-chmod"></a>使用 chmod 更改现有 Windows 文件的文件权限

结果取决于文件是否已具有现有元数据。

##### <a name="chmod-file-does-not-have-metadata-default"></a>chmod 文件没有元数据（默认）

Chmod 只有一种效果，如果删除文件的所有写入属性，则会设置 Windows 文件上的“只读”属性，因为这是与 CIFS（通用 Internet 文件系统）相同的行为。CIFS 是 Linux 中的 SMB（服务器消息块）客户端。

##### <a name="chmod-file-has-metadata"></a>chmod 文件有元数据

Chmod 将根据文件已有的现有元数据更改或添加元数据。 

请记住，你为自己授予的访问权限不能多于你在 Windows 上具有的访问权限，即使元数据显示的情况与此相反，也是如此。 例如，你可以使用 `chmod 777` 将元数据设置为显示你对文件具有写入权限，但如果你尝试访问该文件，则你仍无法写入到该文件。 这是由于互操作性而导致的，因为对 Windows 文件的任何读取或写入命令均通过 Windows 用户权限进行路由。

#### <a name="creating-a-file-in-drivefs"></a>在 DriveFS 中创建文件

结果取决于是否启用了元数据。

##### <a name="metadata-is-not-enabled-default"></a>元数据未启用（默认）

新创建的文件的 Windows 权限将与你在未使用特定安全描述符的情况下在 Windows 中创建的文件相同，它将继承父级的权限。

##### <a name="metadata-is-enabled"></a>元数据已启用

文件的权限位设置为遵循 Linux umask，文件将随元数据一起保存。

#### <a name="which-linux-user-and-linux-group-owns-the-file"></a>哪个 Linux 用户和 Linux 组拥有该文件？ 

结果取决于文件是否已具有现有元数据。

##### <a name="user-file-does-not-have-metadata-default"></a>用户文件没有元数据（默认）

在默认情况下，当自动装载 Windows 驱动器时，我们指定任何文件的用户 ID (UID) 将设置为 WSL 用户的用户 ID，并且组 ID (GID) 将设置为 WSL 用户的主体组 ID。

##### <a name="user-file-has-metadata"></a>用户文件有元数据

在元数据中指定的 UID 和 GID 将应用为该文件的用户所有者和组所有者。

### <a name="accessing-linux-files-from-windows-using-wsl"></a>使用 `\\wsl$` 从 Windows 访问 Linux 文件

通过 `\\wsl$` 访问 Linux 文件时将使用 WSL 分发版的默认用户。 因此，任何访问 Linux 文件的 Windows 应用都具有与默认用户相同的权限。

#### <a name="creating-a-new-file"></a>创建新文件

从 Windows 向 WSL 分发版内部创建新文件时，将应用默认 umask。 默认的 umask 是 `022`，也就是说，它允许除了组和其他用户的写入权限以外的所有权限。 

### <a name="accessing-files-in-the-linux-root-file-system-from-linux"></a>从 Linux 访问 Linux 根文件系统中的文件

在 Linux 根文件系统中创建、修改或访问的任何文件都遵循标准 Linux 约定，例如将 umask 应用到新创建的文件。

## <a name="configuring-file-permissions"></a>配置文件权限

可以使用 wsl.conf 中的装载选项在 Windows 驱动器内配置文件权限。 装载选项允许你设置 `umask`、`dmask` 和 `fmask` 权限掩码。 `umask` 应用于所有文件，`dmask` 只应用于目录，而 `fmask` 只应用于文件。 这些权限掩码在应用到文件时会通过一个“逻辑或”操作进行计算，例如：如果 `umask` 值为 `023` 并且 `fmask` 值为 `022`，则为文件生成的权限掩码将为 `023`。

有关如何执行此操作的说明，请参阅[使用 wslconf 配置按分发版启动设置](./wsl-config.md#configure-per-distro-launch-settings-with-wslconf)一文。
