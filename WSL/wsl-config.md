---
title: 管理 Linux 分发版
description: 有关列出和配置在适用于 Linux 的 Windows 子系统上运行的多个 Linux 分发版的参考文章。
keywords: BashOnWindows, bash, wsl, windows, 适用于 linux 的 windows 子系统, windowssubsystem, ubuntu, wsl.conf, wslconfig
ms.date: 05/12/2020
ms.topic: article
ms.openlocfilehash: e97b1030d5891bf8aa1cb656646a4d9e1d480a3d
ms.sourcegitcommit: f1b049a1276782d4f2754f46a8d2025b598a0784
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85336080"
---
# <a name="wsl-commands-and-launch-configurations"></a>WSL 命令和启动配置

## <a name="ways-to-run-wsl"></a>WSL 的运行方式

[安装](install-win10.md)了 WSL 后，可通过多种方式运行 Linux 分发版。

1. 通过访问 Windows 的 "开始" 菜单并键入已安装的分发的名称，打开 Linux 分发版。 例如： "Ubuntu"。
2. 在 Windows 命令提示符或 PowerShell 中，输入已安装的分发的名称。 例如： `ubuntu`
3. 在 Windows 命令提示符或 PowerShell 中，若要在当前命令行内打开默认的 Linux 分发，请输入： `wsl.exe` 。
4. 在 Windows 命令提示符或 PowerShell 中，若要在当前命令行内打开默认的 Linux 分发，请输入： `wsl [command]` 。

要使用的方法取决于执行的操作。 如果已在 Windows 提示符或 PowerShell 窗口中打开 WSL 命令行并想要退出，请输入以下命令： `exit` 。

## <a name="launch-wsl-by-distribution"></a>按分发版启动 WSL

使用特定于分发版的应用程序运行某个分发版会在其自身的控制台窗口中将它启动。

![从“开始”菜单启动 WSL](media/start-launch.png)

这相当于在 Microsoft Store 中单击“启动”。

![从 Microsoft Store 启动 WSL](media/store-launch.png)

还可以在命令行中运行 `[distribution].exe` 来运行分发版。

以这种方式从命令行运行分发版的缺点是，会自动将工作目录从当前目录更改为分发版的主目录。

**示例：（使用 PowerShell）**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> ubuntu

scooley@scooley-elmer:~$ pwd
/home/scooley
scooley@scooley-elmer:~$ exit
logout

PS C:\Users\sarah>
```

### <a name="wsl-and-wsl-command"></a>wsl 和 wsl [命令]

从命令行运行 WSL 的最佳方式是使用 `wsl.exe`。

**示例：（使用 PowerShell）**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> wsl

scooley@scooley-elmer:/mnt/c/Users/sarah$ pwd
/mnt/c/Users/sarah
```

这样，`wsl` 不仅可以保留当前工作目录，而且还允许结合 Windows 命令运行单个命令。

**示例：（使用 PowerShell）**

```console
PS C:\Users\sarah> Get-Date

Sunday, March 11, 2018 7:54:05 PM

PS C:\Users\sarah> wsl
scooley@scooley-elmer:/mnt/c/Users/sarah$ date
Sun Mar 11 19:55:47 DST 2018
scooley@scooley-elmer:/mnt/c/Users/sarah$ exit
logout

PS C:\Users\sarah> wsl date
Sun Mar 11 19:56:57 DST 2018
```

**示例：（使用 PowerShell）**

```console
PS C:\Users\sarah> Get-VM

Name            State CPUUsage(%) MemoryAssigned(M) Uptime   Status
----            ----- ----------- ----------------- ------   ------
Server17093     Off   0           0                 00:00:00 Opera...
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
Windows         Off   0           0                 00:00:00 Opera...


PS C:\Users\sarah> Get-VM | wsl grep "Ubuntu"
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
PS C:\Users\sarah>
```

## <a name="managing-multiple-linux-distributions"></a>管理多个 Linux 分发版

在 Windows 10 版本 1903[及更高](ms-settings:windowsupdate)版本中，你可以使用在 `wsl.exe` 适用于 Linux 的 WINDOWS 子系统（WSL）中管理你的分发版，其中包括列出可用的分发、设置默认分发以及卸载分发。

每个 Linux 分发版独立管理自身的配置。 若要查看特定于分发版的命令，请运行 `[distro.exe] /?`。  例如，`ubuntu /?`。

## <a name="list-distributions"></a>列出分发版

`wsl -l` , `wsl --list`  
列出可用于 WSL 的 Linux 分发版。  如果列出了某个分发版，表示该分发版已安装且可供使用。

`wsl --list --all`列出所有分发，包括当前不可用的分发。  这些分发版可能正在安装、卸载或处于损坏状态。  

`wsl --list --running`列出当前正在运行的所有分发版。

## <a name="set-a-default-distribution"></a>设置默认分发版

默认 WSL 分布版是在命令行中运行 `wsl` 时运行的分发版。

`wsl -s <DistributionName>`, `wsl --setdefault <DistributionName>`

将默认分发版设置为 `<DistributionName>`。

**示例：（使用 PowerShell）**  
`wsl -s Ubuntu` 会将我的默认分发版设置为 Ubuntu。  现在，当我运行 `wsl npm init` 时，该分发版将在 Ubuntu 中运行。  如果我运行 `wsl`，它会打开 Ubuntu 会话。

## <a name="unregister-and-reinstall-a-distribution"></a>取消注册和重新安装分发版

尽管可以通过 Microsoft Store 安装 Linux 分发版，但无法通过 Store 将其卸载。  可以通过 WSL Config 来取消注册/卸载分发版。

取消注册后，还可以重新安装分发版。

> **警告：** 注销后，与该分发关联的所有数据、设置和软件都将永久丢失。  从 Store 重新安装会安装分发版的干净副本。

`wsl --unregister <DistributionName>`  
从 WSL 中取消注册分发版，以便能够重新安装或清理它。

例如：`wsl --unregister Ubuntu` 将从可用于 WSL 的分发版中删除 Ubuntu。  运行 `wsl --list` 时，不再会列出 Ubuntu。

若要重新安装，请在 Microsoft Store 中找到该分发版，然后选择“启动”。

## <a name="run-as-a-specific-user"></a>以特定用户的身份运行

`wsl -u <Username>`, `wsl --user <Username>`

以指定用户的身份运行 WSL。 请注意，该用户必须存在于 WSL 分发版中。

## <a name="change-the-default-user-for-a-distribution"></a>更改分发的默认用户

`<DistributionName> config --default-user <Username>`

更改分发登录的默认用户。 为了成为默认用户，用户必须已在分发内存在。 

例如： `ubuntu config --default-user johndoe` 会将 Ubuntu 分发的默认用户更改为 "johndoe" 用户。

> [!NOTE]
> 如果在找出分发的名称时遇到问题，请参阅命令的[列表分发](https://docs.microsoft.com/windows/wsl/wsl-config#list-distributions)以列出已安装的分发的正式名称。 

## <a name="run-a-specific-distribution"></a>运行特定的分发版

`wsl -d <DistributionName>`, `wsl --distribution <DistributionName>`

运行 WSL 的指定分发版。可用于将命令发送到特定的分发版，而无需更改默认值。

## <a name="managing-multiple-linux-distributions-in-earlier-windows-versions"></a>在早期 Windows 版本中管理多个 Linux 分发

在 Windows 10 版本1903之前，应使用 WSL Config （ `wslconfig.exe` ）命令行工具管理在适用于 linux 的 Windows 子系统（WSL）上运行的 linux 分发。  使用该工具可以列出可用分发版、设置默认分发和卸载分发版。

尽管 WSL Config 对于跨越或协调分发版的设置有帮助，但每个 Linux 分发版会独立管理自身的配置。  若要查看特定于分发版的命令，请运行 `[distro.exe] /?`。  例如，`ubuntu /?`。

若要查看 wslconfig 的所有可用选项，请运行：`wslconfig /?`

```console
wslconfig.exe
Performs administrative operations on Windows Subsystem for Linux

Usage:
    /l, /list [/all] - Lists registered distributions.
        /all - Optionally list all distributions, including distributions that
               are currently being installed or uninstalled.
    /s, /setdefault <DistributionName> - Sets the specified distribution as the default.
    /u, /unregister <DistributionName> - Unregisters a distribution.
```

若要列出分发，请使用：

`wslconfig /list`  
列出可用于 WSL 的 Linux 分发版。  如果列出了某个分发版，表示该分发版已安装且可供使用。

`wslconfig /list /all`  
列出所有分发版，包括当前不可用的分发版。  这些分发版可能正在安装、卸载或处于损坏状态。  

设置在命令行上运行时运行的默认分发 `wsl` ：

`wslconfig /setdefault <DistributionName>`将默认分布设置为 `<DistributionName>` 。

**示例：（使用 PowerShell）**  
`wslconfig /setdefault Ubuntu` 会将我的默认分发版设置为 Ubuntu。  现在，当我运行 `wsl npm init` 时，该分发版将在 Ubuntu 中运行。  如果我运行 `wsl`，它会打开 Ubuntu 会话。

若要注销并重新安装分发：

`wslconfig /unregister <DistributionName>`  
从 WSL 中取消注册分发版，以便能够重新安装或清理它。

例如：`wslconfig /unregister Ubuntu` 将从可用于 WSL 的分发版中删除 Ubuntu。  运行 `wslconfig /list` 时，不再会列出 Ubuntu。

若要重新安装，请在 Microsoft Store 中找到该分发版，然后选择“启动”。

## <a name="configure-per-distro-launch-settings-with-wslconf"></a>通过 wslconf 配置每个发行版启动设置

> **在 Windows 版本17093及更高版本中可用**

使用 `wsl.conf` 自动配置 WSL 中每次启动子系统时要应用的某些功能。

目前，这包括自动装载选项和网络配置。

`wsl.conf` 位于每个 Linux 分发版的 `/etc/wsl.conf` 中。 如果该文件不存在，你可以自行创建。 WSL 会检测该文件是否存在，并读取其内容。 如果该文件缺失或格式不正确（即，标记格式不正确），WSL 将继续如常启动。

下面是可以 `wsl.conf` 添加到分发的示例文件：

```console
# Enable extra metadata options by default
[automount]
enabled = true
root = /windir/
options = "metadata,umask=22,fmask=11"
mountFsTab = false

# Enable DNS – even though these are turned on by default, we'll specify here just to be explicit.
[network]
generateHosts = true
generateResolvConf = true
```

### <a name="configuration-options"></a>配置选项

为了遵守 .ini 约定，键将在某个节下声明。 

WSL 支持两个节：`automount` 和 `network`。

#### <a name="automount"></a>automount

节：`[automount]`

| 键        | value                          | 默认      | 备注                                                                                                                                                                                                                                                                                                                          |
|:-----------|:-------------------------------|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 已启用    | 布尔值                        | true         | `true` 导致固定驱动器（即 `C:/` 或 `D:/`）自动装载到 DrvFs 中的 `/mnt` 下。  `false`表示不会自动装入驱动器，但你仍然可以手动或通过手动装载它们 `fstab` 。                                                                                                             |
| mountFsTab | 布尔值                        | true         | `true` 设置启动 WSL 时要处理的 `/etc/fstab`。 /etc/fstab 是可在其中声明其他文件系统的文件，类似于 SMB 共享。 因此，在启动时，可以在 WSL 中自动装载这些文件系统。                                                                                                                |
| root       | 字符串                         | `/mnt/`      | 设置固定驱动器要自动装载到的目录。 例如，如果 WSL 中的某个目录位于 `/windir/`，而你将该目录指定为根目录，则固定驱动器预期会装载到 `/windir/c`                                                                                              |
| 选项    | 逗号分隔值列表 | 空字符串 | 此值将追加到默认的 DrvFs 装载选项字符串。 **只能指定特定于 DrvFs 的选项。** 通常由装载二进制文件分析成标志的选项不受支持。 若要显式指定这些选项，必须在 /etc/fstab 中包含要对其执行此操作的每个驱动器。 |

默认情况下，WSL 会将 uid 和 gid 设置为默认用户的值（在 Ubuntu 分发版中，默认用户是使用 uid=1000,gid=1000 创建的）。 如果用户通过此键显式指定了 gid 或 uid 选项，将覆盖关联的值。 否则，将始终追加默认值。

**注意：** 对于所有自动装载的驱动器，这些选项将应用为装载选项。 如果只想更改特定驱动器的选项，请改用 /etc/fstab。

#### <a name="mount-options"></a>装载选项

为 Windows 驱动器 (DrvFs) 设置不同的装载选项可以控制为 Windows 文件计算文件权限的方式。 你可使用以下选项：

| 键 | 说明 | 默认值 |
|:----|:----|:----|
|uid| 用于所有文件的所有者的用户 ID | WSL 发行版的默认用户 ID（第一次安装时，此项默认为 1000）
|gid| 用于所有文件的所有者的组 ID | WSL 发行版的默认组 ID（第一次安装时，此项默认为 1000）
|umask | 要对所有文件和目录排除的权限的八进制掩码 | 000
|fmask | 要对所有文件排除的权限的八进制掩码 | 000
|dmask | 要对所有目录排除的权限的八进制掩码 | 000

**注意：** 权限掩码在应用到文件或目录之前通过一个逻辑或操作进行设置。 

#### <a name="network"></a>网络

节标签：`[network]`

| 键 | value | 默认 | 备注|
|:----|:----|:----|:----|
| generateHosts | 布尔值 | `true` | `true` 将 WSL 设置为生成 `/etc/hosts`。 `hosts` 文件包含主机名对应的 IP 地址的静态映射。 |
| generateResolvConf | 布尔值 | `true` | `true` 将 WSL 设置为生成 `/etc/resolv.conf`。 `resolv.conf` 包含能够将给定主机名解析为其 IP 地址的 DNS 列表。 | 

#### <a name="interop"></a>interop

节标签：`[interop]`

这些选项在预览体验成员内部版本 17713 和更高版本中可用。

| 键 | value | 默认 | 备注|
|:----|:----|:----|:----|
| 已启用 | 布尔值 | `true` | 设置此键可确定 WSL 是否支持启动 Windows 进程。 |
| appendWindowsPath | 布尔值 | `true` | 设置此键可确定 WSL 是否会将 Windows 路径元素添加到 $PATH 环境变量。 |

#### <a name="user"></a>user

节标签：`[user]`

这些选项在版本18980和更高版本中可用。

| 键 | 值 | 默认值 | 说明|
|:----|:----|:----|:----|
| 默认值 | string | 首次运行时创建的初始用户名 | 设置此项将指定在首次启动 WSL 会话时要运行的用户。 |

## <a name="configure-global-options-with-wslconfig"></a>用 wslconfig 配置全局选项。

> **在 Windows 版本19041及更高版本中可用**

可以通过将文件放入用户文件夹的根目录来配置全局 WSL 选项 `.wslconfig` ： `C:\Users\<yourUserName>\.wslconfig` 。 其中许多文件都与 WSL 2 相关，请记住，你可能需要运行 `wsl --shutdown` 以关闭 WSL 2 VM，然后重新启动 WSL 实例，这些更改才会生效。

下面是 wslconfig 文件的示例：

```console
[wsl2]
kernel=C:\\temp\\myCustomKernel
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=2 # Makes the WSL 2 VM use two virtual processors
```

此文件可以包含以下选项：

### <a name="wsl-2-settings"></a>WSL 2 设置

节标签：`[wsl2]`

这些设置会影响支持任何 WSL 2 分发的虚拟机。

| 键 | 值 | 默认值 | 说明|
|:----|:----|:----|:----|
| 内核 (kernel) | string | Microsoft 构建的内核提供的收件箱 | 自定义 Linux 内核的绝对 Windows 路径。 |
| memory | 大小 | Windows 上的总内存的80% | 要分配给 WSL 2 VM 的内存量。 |
| 款 | number | Windows 上的处理器数相同 | 要分配给 WSL 2 VM 的处理器数量。 |
| localhostForwarding | boolean | `true` | 布尔值，指定是否应通过 localhost： port 将绑定到 WSL 2 VM 中的通配符或 localhost 的端口连接到主机。 |
| kernelCommandLine | string | 空 | 其他内核命令行参数。 |
| swap | 大小 | Windows 上的25% 内存大小向上舍入到最接近的 GB | 要添加到 WSL 2 VM 的交换空间量，0表示没有交换文件。 |
| 交换文件 | string | %USERPROFILE%\AppData\Local\Temp\swap.vhdx | 交换虚拟硬盘的绝对 Windows 路径。 |

值为的项 `path` 必须是包含转义反斜杠的 Windows 路径，例如：`C:\\Temp\\myCustomKernel`

具有值的项 `size` 必须是后跟一个单位的大小，例如 `8GB` 或 `512MB` 。
