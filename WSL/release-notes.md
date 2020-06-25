---
title: 适用于 Linux 的 Windows 子系统发行说明
description: 适用于 Linux 的 Windows 子系统的发行说明。  每周更新。
keywords: 发行说明, wsl, windows, 适用于 linux 的 windows 子系统, windows 子系统, ubuntu
author: benhillis
ms.date: 05/15/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 3df4d4b4e0c542a3e87306c01a14b7073eb5e677
ms.sourcegitcommit: 3fb40fd65b34a5eb26b213a0df6a3b2746b7a9b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235947"
---
# <a name="release-notes-for-windows-subsystem-for-linux"></a>适用于 Linux 的 Windows 子系统发行说明

## <a name="build-19555"></a>内部版本 19555
有关内部版本 19555 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2020/01/30/announcing-windows-10-insider-preview-build-19555/)。

* [WSL2] 使用 memory cgroup 限制了安装和转换操作使用的内存量 [GH 4669]
* 在未启用适用于 Linux 的 Windows 子系统可选组件时使 wsl.exe 存在，以提高功能的可发现性。
* 更改了 wsl.exe 以在未安装 WSL 可选组件时输出帮助文本
* 修复了创建实例时的争用条件
* 创建了包含所有命令行功能的 slclient.dll
* 防止了在 LxssManagerUser 服务停止期间发生崩溃
* 修复了当 distroName 参数为 NULL 时的 wslapi.dll 快速失败

## <a name="build-19041"></a>内部版本 19041
有关内部版本 19041 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/12/10/announcing-windows-10-insider-preview-build-19041/)。

* [WSL2] 在启动进程之前清除信号掩码
* [WSL2] 将 Linux 内核更新到 4.19.84
* 当 symlink 非相关时，处理 /etc/resolv.conf symlink 的创建

## <a name="build-19028"></a>内部版本 19028
有关内部版本 19028 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/11/19/announcing-windows-10-insider-preview-build-19028/)。

* [WSL2] 将 Linux 内核更新到 4.19.81
* [WSL2] 将 /dev/net/tun 的默认权限更改为 0666 [GH 4629]
* [WSL2] 将分配给 Linux VM 的默认内存量调整为主机内存的 80%
* [WSL2] 修复互操作服务器以便使用“超时”功能处理请求，从而使不良调用方无法挂起服务器

## <a name="build-19018"></a>内部版本 19018
有关内部版本 19018 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/11/05/announcing-windows-10-insider-preview-build-19018/)。

* [WSL2] 使用 cache=mmap 作为 9p 装入点的默认值来修复 dotnet 应用
* [WSL2] localhost 中继的修补程序 [GH 4340]
* [WSL2] 引入了用于在发行版之间共享状态的跨发行版共享 tmpfs 装入点
* 修复了 \\\\wsl$ 的永久网络驱动器还原

## <a name="build-19013"></a>内部版本 19013
有关内部版本 19013 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/10/29/announcing-windows-10-insider-preview-build-19013/)。

* [WSL2] 提高 WSL 实用工具 VM 的内存性能。 不再处于使用状态的内存将释放回主机。
* [WSL2] 将内核版本更新到 4.19.79。 （添加 CONFIG_HIGH_RES_TIMERS、CONFIG_TASK_XACCT、CONFIG_TASK_IO_ACCOUNTING、CONFIG_SCHED_HRTICK 和 CONFIG_BRIDGE_VLAN_FILTERING）。
* [WSL2] 修复了输入中继，以处理 stdin 为未关闭管道句柄的情况 [GH 4424]
* 检查 \\\\wsl$ 是否不区分大小写。
```
[wsl2]
pageReporting = <bool>    # Enable or disable the free memory page reporting feature (default true).
idleThreshold = <integer> # Set the idle threshold for memory compaction, 0 disables the feature (default 1).
```

## <a name="build-19002"></a>版本 19002
有关版本 19002 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/10/17/announcing-windows-10-insider-preview-build-19002/)。

* [WSL] 解决了有关处理某些 Unicode 字符的问题： https://github.com/microsoft/terminal/issues/2770
* [WSL] 解决了在版本到版本升级后立即启动时可能会注销发行版的罕见情况。
* [WSL] 解决了 wsl.exe --shutdown 的以下小问题：无法取消实例空闲计时器。

## <a name="build-18995"></a>内部版本 18995
有关内部版本 18995 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/10/03/announcing-windows-10-insider-preview-build-18995/)。

* [WSL2] 修复了 DrvFs 装载在某项操作被中断（例如 ctrl-c）后失效的问题 [GH 4377]
* [WSL2] 修复了处理极大型 hvsocket 消息的问题 [GH 4105]
* [WSL2] 修复了当 stdin 为文件时互操作出现的问题 [GH 4475]
* [WSL2] 修复了当遇到意外网络状态时服务崩溃的问题 [GH 4474]
* [WSL2] 在当前进程没有环境变量的情况下从互操作服务器查询发行版名称
* [WSL2] 修复了当 stdin 为文件时互操作出现的问题
* [WSL2] 将 Linux 内核版本更新到 4.19.72
* [WSL2] 添加了通过 .wslconfig 指定其他内核命令行参数的功能
```
[wsl2]
kernelCommandLine = <string> # Additional kernel command line arguments
```

## <a name="build-18990"></a>版本 18990
有关版本 18990 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/09/24/announcing-windows-10-insider-preview-build-18990/)。

* 提高 \\\\wsl$ 中目录列表的性能
* [WSL2] 注入额外的启动熵 [GH 4416]
* [WSL2] 修复使用 su/sudo 时的 Windows 互操作 [GH 4465]

## <a name="build-18980"></a>内部版本 18980
有关内部版本 18980 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/09/11/announcing-windows-10-insider-preview-build-18980/)。

* 修复拒绝 FILE_READ_DATA 的读取符号链接。 这包括 Windows 为了实现后向兼容而创建的所有符号链接（例如“C:\Document and Settings”），以及用户配置文件目录中的一些符号链接。
* 使意外的文件系统状态变得不严重 [GH 4334、4305]
* [WSL2] 添加当 CPU/固件支持虚拟化时对 arm64 的支持
* [WSL2] 允许无特权用户查看内核日志
* [WSL2] 修复关闭 stdout/stderr 套接字后的输出中继 [GH 4375]
* [WSL2] 支持电池和交流适配器直通
* [WSL2] 将 Linux 内核更新到 4.19.67
* 添加在 /etc/wsl.conf 中设置默认用户名的功能：
```
[user]
default=<string>
```

## <a name="build-18975"></a>内部版本 18975
有关内部版本 18975 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/09/06/announcing-windows-10-insider-preview-build-18975/)。

* [WSL2] 修复大量 localhost 可靠性问题 [GH 4340]

## <a name="build-18970"></a>内部版本 18970
有关内部版本 18970 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/08/29/announcing-windows-10-insider-preview-build-18970/)。

* [WSL2] 当系统从睡眠状态恢复时，使时间与主机时间同步 [GH 4245]
* [WSL2] 在可能的情况下，在 Windows 卷上创建 NT 符号链接。
* [WSL2] 在 UTS、IPC、PID 和 Mount 命名空间中创建分发版。
* [WSL2] 修复当服务器直接绑定到 localhost 时的 localhost 端口中继 [GH 4353]
* [WSL2] 修复重定向输出时的 interop [GH 4337]
* [WSL2] 支持转换绝对 NT 符号链接。
* [WSL2] 将内核更新到 4.19.59
* [WSL2] 正确设置 eth0 的子网掩码。
* [WSL2] 发出退出事件信号时更改逻辑，以中断控制台工作线程循环。
* [WSL2] 分发版未运行时弹出分发版 VHD。
* [WSL2] 修复配置分析库以正确处理空值。
* [WSL2] 通过创建跨分发版装入点来支持 Docker Desktop。 分发版可以通过将以下行添加到 /etc/wsl.conf 文件来启用此行为：
```
[automount]
crossDistro = true
```

## <a name="build-18945"></a>内部版本 18945
有关内部版本 18945 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/07/26/announcing-windows-10-insider-preview-build-18945/)。

### <a name="wsl"></a>WSL
* [WSL2] 允许侦听可使用 localhost:port 通过主机访问的 WSL2 中的 TCP 套接字
* [WSL2] 修复安装/转换失败和其他诊断，以跟踪将来的问题 [GH 4105] 
* [WSL2] 改善 WSL2 网络问题的诊断
* [WSL2] 将内核版本更新到 4.19.55
* [WSL2] 使用 Docker 所需的配置选项更新了内核 [GH 4165]
* [WSL2] 增加分配给轻型实用程序 VM 的 CPU 数目，使其与主机相同（以前，内核配置中的 CONFIG_NR_CPUS 将数目限制为 8 个）[GH 4137]
* [WSL2] 为 WSL2 轻型 VM 创建交换文件
* [WSL2] 允许通过 \\\\wsl$\\distro（例如 sshfs）显示用户装入点 [GH 4172]
* [WSL2] 改善 9p 文件系统的性能
* [WSL2] 确保 VHD ACL 不会无限增长 [GH 4126]
* [WSL2] 更新内核配置以支持 squashfs 和 xt_conntrack [GH 4107、4123]
* [WSL2] 修复 interop.enabled /etc/wsl.conf 选项 [GH 4140]
* [WSL2] 如果文件系统不支持 EA，则返回 ENOTSUP
* [WSL2] 修复 \\\\wsl$ 时 CopyFile 挂起的问题
* 将默认 umask 切换为 0022，并将 filesystem.umask 设置添加到 /etc/wsl.conf
* 修复 wslpath 以正确解析符号链接，这是19h1 中的回归 [GH 4078]
* 引入 %UserProfile%\\.wslconfig 文件用于调整 WSL2 设置
```
[wsl2]
kernel=<path>              # An absolute Windows path to a custom Linux kernel.
memory=<size>              # How much memory to assign to the WSL2 VM.
processors=<number>        # How many processors to assign to the WSL2 VM.
swap=<size>                # How much swap space to add to the WSL2 VM. 0 for no swap file.
swapFile=<path>            # An absolute Windows path to the swap vhd.
localhostForwarding=<bool> # Boolean specifying if ports bound to wildcard or localhost in the WSL2 VM should be connectable from the host via localhost:port (default true).

# <path> entries must be absolute Windows paths with escaped backslashes, for example C:\\Users\\Ben\\kernel
# <size> entries must be size followed by unit, for example 8GB or 512MB
```

## <a name="build-18917"></a>内部版本 18917
有关内部版本 18917 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/06/12/announcing-windows-10-insider-preview-build-18917/)。

### <a name="wsl"></a>WSL
* WSL 2 现已推出！ 有关更多详细信息，请参阅[博客](https://devblogs.microsoft.com/commandline/wsl-2-is-now-available-in-windows-insiders/)。
* 修复一个回归问题：无法通过符号链接启动 Windows 进程 [GH 3999]
* 将 wsl.exe --list --verbose、wsl.exe --list --quiet 和 wsl.exe --import --version 选项添加到 wsl.exe
* 添加 wsl.exe --shutdown 选项
* Plan 9：允许打开目录以使写入成功

## <a name="build-18890"></a>内部版本 18890
有关内部版本 18890 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/05/01/announcing-windows-10-insider-preview-build-18890/)。

### <a name="wsl"></a>WSL
* 非阻塞套接字泄露 [GH 2913]
* 在终端中输入 EOF 可能会阻塞后续读取 [GH 3421]
* 更新 resolv.conf 标头以引用 wsl.conf [在 GH 3928 中介绍]
* epoll delete 代码中的死锁 [GH 3922]
* 处理 --import 和 –export 的参数中的空格 [GH 3932]
* 无法正常扩展 mmap'd 文件 [GH 3939]
* 修复了 ARM64 \\\\wsl$ 访问不正常的问题
* 为 wsl.exe 添加更好的默认图标

## <a name="build-18342"></a>内部版本 18342
有关内部版本 18342 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/02/20/announcing-windows-10-insider-preview-build-18342/)。

### <a name="wsl"></a>WSL
* 我们添加了相应的功能，使用户能够从 Windows 访问 WSL 分发版中的 Linux 文件。 可以通过命令行访问这些文件，此外，文件资源管理器、VSCode 等 Windows 应用可与这些文件交互。 通过导航到 \\\\wsl$\\<分发版名称> 访问文件，或通过导航到 \\\\wsl$ 来查看正在运行的分发版列表
* 添加额外的 CPU 信息标记，并修复 Cpus_allowed[_list] 值 [GH 2234]
* 支持从非领先线程执行 [GH 3800]
* 将配置更新失败视为非严重错误 [GH 3785]
* 更新 binfmt 以正确处理偏移 [GH 3768]
* 为 Plan 9 启用映射网络驱动器 [GH 3854]
* 支持对绑定载入点执行“Windows -> Linux”和“Linux -> Windows”路径转换
* 为以只读方式打开的文件中的映射创建只读节

## <a name="build-18334"></a>内部版本 18334
有关内部版本 18334 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2019/02/08/announcing-windows-10-insider-preview-build-18334/)。

### <a name="wsl"></a>WSL
* 重新设计 Windows 时区映射到 Linux 时区的方式 [GH 3747]
* 修复内存泄漏，并添加新的字符串转换函数 [GH 3746]
* 不包含任何线程的线程组上的 SIGCONT 是一个 no-op [GH 3741] 
* 在 /proc/self/fd 中正确显示套接字和 epoll 文件描述符

## <a name="build-18305"></a>内部版本 18305
有关内部版本 18305 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/12/19/announcing-windows-10-insider-preview-build-18305/)。

### <a name="wsl"></a>WSL
* 当主线程退出时，pthreads 失去对文件的访问权限 [GH 3589]
* TIOCSCTTY 应忽略“force”参数，除非该参数是必需的 [GH 3652]
* 改善 wsl.exe 命令行，并添加导入/导出功能。
```
Usage: wsl.exe [Argument] [Options...] [CommandLine]

Arguments to run Linux binaries:

    If no command line is provided, wsl.exe launches the default shell.

    --exec, -e <CommandLine>
        Execute the specified command without using the default Linux shell.

    --
        Pass the remaining command line as is.

Options:
    --distribution, -d <DistributionName>
        Run the specified distribution.

    --user, -u <UserName>
        Run as the specified user.

Arguments to manage Windows Subsystem for Linux:

    --export <DistributionName> <FileName>
        Exports the distribution to a tar file.
        The filename can be - for standard output.

    --import <DistributionName> <InstallLocation> <FileName>
        Imports the specified tar file as a new distribution.
        The filename can be - for standard input.

    --list, -l [Options]
        Lists distributions.

        Options:
            --all
                List all distributions, including distributions that are currently
                being installed or uninstalled.

            --running
                List only distributions that are currently running.

    -setdefault, -s <DistributionName>
        Sets the distribution as the default.

    --terminate, -t <DistributionName>
        Terminates the distribution.

    --unregister <DistributionName>
        Unregisters the distribution.

    --upgrade <DistributionName>
        Upgrades the distribution to the WslFs file system format.

    --help
        Display usage information.
```

## <a name="build-18277"></a>内部版本 18277
有关内部版本 18277 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/11/07/announcing-windows-10-insider-preview-build-18277/)。

### <a name="wsl"></a>WSL
* 修复内部版本 18272 中引入的“不支持此类接口”错误 [GH 3645]
* 忽略 umount syscall 的 MNT_FORCE 标志 [GH 3605]
* 切换 WSL interop 以使用官方的 CreatePseudoConsole API
* FUTEX_WAIT 重启时不保留超时值

## <a name="build-18272"></a>内部版本 18272
有关内部版本 18272 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/10/31/announcing-windows-10-insider-preview-build-18272/)。

### <a name="wsl"></a>WSL
* **警告：** 此版本中存在一个导致 WSL 不可操作的问题。 尝试启动分发版时，会看到“不支持此类接口”错误。 该问题已修复，下周发布的 Insider Fast 内部版本将会应用修复程序。 如果已安装此内部版本，可以使用“设置”->“更新和安全”>“恢复”中的“回退到 Windows 10 的上一个版本”回退到上一 Windows 内部版本。

## <a name="build-18267"></a>内部版本 18267
有关内部版本 18267 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/10/24/announcing-windows-10-insider-preview-build-18267/)。

### <a name="wsl"></a>WSL
* 修复 zombie 进程不会回收，而是无限期保留的问题。
* 如果错误消息超过最大长度，WslRegisterDistribution 将会挂起 [GH 3592]
* 允许 fsync 针对 DrvFs 上的只读文件成功运行 [GH 3556]
* 在内部创建符号链接之前，确保 /bin 和 /sbin 目录存在 [GH 3584]
* 为 WSL 实例添加了实例终止超时机制。 超时目前设置为 15 秒，这意味着，实例将在上一个 WSL 进程退出 15 秒后终止。 若要立即终止分发版，请使用：
```
wslconfig.exe /terminate <DistributionName>
```

## <a name="build-17763-1809"></a>内部版本 17763 (1809)
有关内部版本 17763 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)。

### <a name="wsl"></a>WSL
* Setpriority syscall 权限检查过于严格，导致无法更改同一线程的优先级 [GH 1838]
* 确保对启动时间使用无偏差的中断时间，以避免返回 clock_gettime(CLOCK_BOOTTIME) 的负值 [GH 3434]
* 在 WSL binfmt 解释器中处理符号链接 [GH 3424]
* 更好地处理线程组领先者文件描述符清理。
* 切换 WSL 以使用 KeQueryInterruptTimePrecise 而不是 KeQueryPerformanceCounter，以避免溢出 [GH 3252]
* Ptrace attach 可能导致系统调用返回错误值 [GH 1731]
* 修复多个 AF_UNIX 相关问题 [GH 3371]
* 修复以下问题：如果当前工作目录的长度少于 5 个字符，可能导致 WSL interop 失败 [GH 3379]
* 避免导致无法与不存在的端口建立环回连接的一秒延迟 [GH 3286]
* 添加 /proc/sys/fs/file-max 存根文件 [GH 2893]
* 更准确的 IPV6 范围信息。
* PR_SET_PTRACER 支持 [GH 3053]
* 管道文件系统意外清除边缘触发的 epoll 事件 [GH 3276]
* 通过 NTFS 符号链接启动的 Win32 可执行文件不遵循符号链接命名约定 [GH 2909]
* 改善了 zombie 支持 [GH 1353]
* 添加 wsl.conf 项用于控制 Windows interop 行为 [GH 1493]
  ```
    [interop]

    enabled=false # enable launch of Windows binaries; default is true

    appendWindowsPath=false # append Windows path to $PATH variable; default is true
  ```
* 修复 getsockname 不是始终返回 UNIX 套接字系列类型的问题 [GH 1774]
* 添加对 TIOCSTI 的支持 [GH 1863]
* 连接进程中的非阻塞套接字应返回写入尝试的 EAGAIN [GH 2846]
* 支持已装载的 VHD 上的 interop [GH 3246、3291]
* 修复根文件夹的权限检查问题 [GH 3304]
* 对 TTY 键盘 ioctl KDGKBTYPE、KDGKBMODE 和 KDSKBMODE 的有限支持。
* 即使在后台启动，Windows UI 应用也应该能够执行。
* 添加 wsl -u 或 --user 选项 [GH 1203]
* 修复启用快速启动时的 WSL 启动问题 [GH 2576]
* Unix 套接字需要保留断开连接的对等凭据 [GH 3183]
* 使用 EAGAIN 时非阻塞 Unix 套接字无限期失败 [GH 3191]
* case=off 是新的默认 drvfs 装入点类型 [GH 2937、3212、3328]
    * 有关详细信息，请参阅[博客](https://blogs.msdn.microsoft.com/commandline/2018/06/14/improved-per-directory-case-sensitivity-support-in-wsl/)。
* 添加 wslconfig/terminate 以停止正在运行的分发版。
* 修复 WSL shell 上下文菜单项无法正确处理包含空格的路径的问题。
* 公开按目录区分大小写作为扩展属性
* ARM64：模拟缓存维护操作。 解决 [.NET 问题](https://github.com/dotnet/core/issues/1561)。
* DrvFs：只取消转义专用范围中与已转义字符对应的字符。
* 修复 ELF 分析程序解释器长度验证中的一位偏移错误 [GH 3154]
* 包含过去时间的 WSL 绝对计时器不会激发 [GH 3091]
* 确保新建的重分析点在父目录中以此类类型列出。
* 以原子方式在 DrvFs 中创建区分大小写的目录。
* 修复一个附加的问题：即使文件存在，多线程操作也可能返回 ENOENT。 [GH 2712]
* 修复了启用 UMCI 时 WSL 启动失败的问题。 [GH 3020]
* 添加浏览器上下文菜单用于启动 WSL [GH 437、603、1836]。 若要使用此菜单，请在资源管理器窗口中按住 Shift 键的同时单击右键。
* 修复 Unix 套接字非阻塞行为 [GH 2822、3100]
* 修复 GH 2026 中报告的 NETLINK 命令挂起问题。
* 添加对装载传播标志的支持 [GH 2911]。
* 修复截断后不会导致 inotify 事件的问题 [GH 2978]。
* 为 wsl.exe 添加 --exec 选项，以便在不使用 shell 的情况下调用单个二进制文件。
* 为 wsl.exe 添加 --distribution 选项，以选择特定的分发版。
* 对 dmesg 的有限支持。 现在，应用程序会将日志记录到 dmesg。 WSL 驱动程序会将有限的信息记录到 dmesg。 将来，此功能可能会扩展，以便从驱动程序发送其他信息/诊断数据。
    * 注意：目前通过 `/dev/kmsg` 设备接口支持 dmesg。 尚不支持 `syslog` syscall 接口。 此外，某些 `dmesg` 命令行选项（例如 `-S`、`-C`）不起作用。
* 更改串行设备的默认 gid 和模式，以匹配本机 [GH 3042]
* DrvFs 现在支持扩展属性。
    * 注意：DrvFs 对扩展属性的名称施加一些限制。 不允许使用某些字符（例如“/”、“:”和“\*”），并且扩展属性名称在 DrvFs 上不区分大小写

## <a name="build-18252-skip-ahead"></a>内部版本 18252 (Skip Ahead)
有关内部版本 18252 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/10/03/announcing-windows-10-insider-preview-build-18252/)。

### <a name="wsl"></a>WSL
* 将 init 和 bsdtar 二进制文件移出 lxssmanager dll，移入单独的 tools 文件夹
* 修复在使用 CLONE_FILES 的情况下，关闭文件描述符时出现的争用
* 处理转换 DrvFs 路径时 /proc/pid/mountinfo 中的可选字段
* 允许 DrvFs mknod 成功，但不为 S_IFREG 提供元数据支持
* 应为 DrvFs 上创建的只读文件设置只读属性 [GH 3411]
* 添加 /sbin/mount.drvfs 帮助器用于处理 DrvFs 装载
* 在 DrvFs 中使用 POSIX rename。
* 允许在无卷 GUID 的卷上执行路径转换。

## <a name="build-17738-fast"></a>内部版本 17738 (Fast)
有关内部版本 17738 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/08/14/announcing-windows-10-insider-preview-build-17738/)。

### <a name="wsl"></a>WSL
* Setpriority syscall 权限检查过于严格，导致无法更改同一线程的优先级 [GH 1838]
* 确保对启动时间使用无偏差的中断时间，以避免返回 clock_gettime(CLOCK_BOOTTIME) 的负值 [GH 3434]
* 在 WSL binfmt 解释器中处理符号链接 [GH 3424]
* 更好地处理线程组领先者文件描述符清理。

## <a name="build-17728-fast"></a>内部版本 17728 (Fast)
有关内部版本 17728 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/07/31/announcing-windows-10-insider-preview-build-17728/)。

### <a name="wsl"></a>WSL
* 切换 WSL 以使用 KeQueryInterruptTimePrecise 而不是 KeQueryPerformanceCounter，以避免溢出 [GH 3252]
* Ptrace attach 可能导致系统调用返回错误值 [GH 1731]
* 修复一些 AF_UNIX 相关的问题 [GH 3371]
* 修复以下问题：如果当前工作目录的长度少于 5 个字符，可能导致 WSL interop 失败 [GH 3379]

## <a name="build-18204-skip-ahead"></a>内部版本 18204 (Skip Ahead)
有关内部版本 18204 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/07/25/announcing-windows-10-insider-preview-build-17723-and-build-18204/)。

### <a name="wsl"></a>WSL
* 管道文件系统意外清除边缘触发的 epoll 事件 [GH 3276]
* 通过 NTFS 符号链接启动的 Win32 可执行文件不遵循符号链接命名约定 [GH 2909]

## <a name="build-17723-fast"></a>内部版本 17723 (Fast)
有关内部版本 17723 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/07/25/announcing-windows-10-insider-preview-build-17723-and-build-18204/)。

### <a name="wsl"></a>WSL
* 避免导致无法与不存在的端口建立环回连接的一秒延迟 [GH 3286]
* 添加 /proc/sys/fs/file-max 存根文件 [GH 2893]
* 更准确的 IPV6 范围信息。
* PR_SET_PTRACER 支持 [GH 3053]
* 管道文件系统意外清除边缘触发的 epoll 事件 [GH 3276]
* 通过 NTFS 符号链接启动的 Win32 可执行文件不遵循符号链接命名约定 [GH 2909]

## <a name="build-17713"></a>内部版本 17713
有关内部版本 17713 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/07/11/announcing-windows-10-insider-preview-build-17713/)。

### <a name="wsl"></a>WSL
* 改善了 zombie 支持 [GH 1353]
* 添加 wsl.conf 项用于控制 Windows interop 行为 [GH 1493]
  ```
    [interop]

    enabled=false # enable launch of Windows binaries; default is true

    appendWindowsPath=false # append Windows path to $PATH variable; default is true
  ```
* 修复 getsockname 不是始终返回 UNIX 套接字系列类型的问题 [GH 1774]
* 添加对 TIOCSTI 的支持 [GH 1863]
* 连接进程中的非阻塞套接字应返回写入尝试的 EAGAIN [GH 2846]
* 支持已装载的 VHD 上的 interop [GH 3246、3291]
* 修复根文件夹的权限检查问题 [GH 3304]
* 对 TTY 键盘 ioctl KDGKBTYPE、KDGKBMODE 和 KDSKBMODE 的有限支持。
* 即使在后台启动，Windows UI 应用也应该能够执行。

## <a name="build-17704"></a>内部版本 17704
有关内部版本 17704 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/06/27/announcing-windows-10-insider-preview-build-17704/)。

### <a name="wsl"></a>WSL
* 添加 wsl -u 或 --user 选项 [GH 1203]
* 修复启用快速启动时的 WSL 启动问题 [GH 2576]
* Unix 套接字需要保留断开连接的对等凭据 [GH 3183]
* 使用 EAGAIN 时非阻塞 Unix 套接字无限期失败 [GH 3191]
* case=off 是新的默认 drvfs 装入点类型 [GH 2937、3212、3328]
    * 有关详细信息，请参阅[博客](https://blogs.msdn.microsoft.com/commandline/2018/06/14/improved-per-directory-case-sensitivity-support-in-wsl/)。
* 添加 wslconfig/terminate 以停止正在运行的分发版。

## <a name="build-17692"></a>版本 17692
有关内部版本 17692 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/06/14/announcing-windows-10-insider-preview-build-17692)。

### <a name="wsl"></a>WSL
* 修复 WSL shell 上下文菜单项无法正确处理包含空格的路径的问题。
* 公开按目录区分大小写作为扩展属性
* ARM64：模拟缓存维护操作。 解决 [.NET 问题](https://github.com/dotnet/core/issues/1561)。
* DrvFs：只取消转义专用范围中与已转义字符对应的字符。

## <a name="build-17686"></a>版本 17686
有关内部版本 17686 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/06/06/announcing-windows-10-insider-preview-build-17686)。

### <a name="wsl"></a>WSL
* 修复 ELF 分析程序解释器长度验证中的一位偏移错误 [GH 3154]
* 包含过去时间的 WSL 绝对计时器不会激发 [GH 3091]
* 确保新建的重分析点在父目录中以此类类型列出。
* 以原子方式在 DrvFs 中创建区分大小写的目录。

## <a name="build-17677"></a>内部版本 17677
有关内部版本 17677 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/05/24/announcing-windows-10-insider-preview-build-17677/)。

### <a name="wsl"></a>WSL
* 修复一个附加的问题：即使文件存在，多线程操作也可能返回 ENOENT。 [GH 2712]
* 修复了启用 UMCI 时 WSL 启动失败的问题。 [GH 3020]

## <a name="build-17666"></a>内部版本 17666
有关内部版本 17666 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/05/09/announcing-windows-10-insider-preview-build-17666/)。

### <a name="wsl"></a>WSL
#### <a name="warning-there-is-an-issue-preventing-wsl-from-running-on-some-amd-chipsets-gh-3134-a-fix-is-ready-and-making-its-way-to-the-insider-build-branch"></a>警告：某个问题会阻止 WSL 在某些 AMD 芯片组上运行 [GH 3134]。 修复程序已准备就绪，即将在 Insider Build 分支中发布。
* 添加浏览器上下文菜单用于启动 WSL [GH 437、603、1836]。 若要使用此菜单，请在资源管理器窗口中按住 Shift 键的同时单击右键。
* 修复 Unix 套接字非阻塞行为 [GH 2822、3100]
* 修复 GH 2026 中报告的 NETLINK 命令挂起问题。
* 添加对装载传播标志的支持 [GH 2911]。
* 修复截断后不会导致 inotify 事件的问题 [GH 2978]。
* 为 wsl.exe 添加 --exec 选项，以便在不使用 shell 的情况下调用单个二进制文件。
* 为 wsl.exe 添加 --distribution 选项，以选择特定的分发版。

## <a name="build-17655-skip-ahead"></a>内部版本 17655 (Skip Ahead)
有关内部版本 17655 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/04/25/announcing-windows-10-insider-preview-build-17655-for-skip-ahead/)。

### <a name="wsl"></a>WSL
* 对 dmesg 的有限支持。 现在，应用程序会将日志记录到 dmesg。 WSL 驱动程序会将有限的信息记录到 dmesg。 将来，此功能可能会扩展，以便从驱动程序发送其他信息/诊断数据。
    * 注意：目前通过 `/dev/kmsg` 设备接口支持 dmesg。 尚不支持 `syslog` sycall 接口。 此外，某些 `dmesg` 命令行选项（例如 `-S`、`-C`）不起作用。
* 修复了即使文件存在，多线程操作也可能返回 ENOENT 的问题。 [GH 2712]

## <a name="build-17639-skip-ahead"></a>内部版本 17639 (Skip Ahead)
有关内部版本 17639 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/04/04/announcing-windows-10-insider-preview-build-17639-for-skip-ahead/)。

### <a name="wsl"></a>WSL
* 更改串行设备的默认 gid 和模式，以匹配本机 [GH 3042]
* DrvFs 现在支持扩展属性。
    * 注意：DrvFs 对扩展属性的名称施加一些限制。 具体而言，不允许使用某些字符（例如“/”、“:”和“\*”），并且扩展属性名称在 DrvFs 上不区分大小写

## <a name="build-17133-fast"></a>内部版本 17133 (Fast)
有关内部版本 17133 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/03/27/announcing-windows-10-insider-preview-build-17133-for-fast/)。

### <a name="wsl"></a>WSL
* 修复 WSL 中的挂起问题。 [GH 3039、3034]

## <a name="build-17128-fast"></a>内部版本 17128 (Fast)
有关内部版本 17128 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/03/23/announcing-windows-10-insider-preview-build-17128-for-fast/)。

### <a name="wsl"></a>WSL
* 无

## <a name="build-17627-skip-ahead"></a>内部版本 17627 (Skip Ahead)
有关内部版本 17627 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/03/21/announcing-windows-10-insider-preview-build-17627-for-skip-ahead/)。

### <a name="wsl"></a>WSL
* 添加对 futex pi 感知操作的支持。 [GH 1006]
    * 请注意，WSL 功能目前不支持优先级，因此存在一些限制，但标准用法应该不会受到阻止。
* 对 WSL 进程的 Windows 防火墙支持。 [GH 1852]
    * 例如，若要允许 WSL python 进程侦听任何端口，请使用提升的 Windows cmd：```netsh.exe advfirewall firewall add rule name=wsl_python dir=in action=allow program="C:\users\<username>\appdata\local\packages\canonicalgrouplimited.ubuntuonwindows_79rhkp1fndgsc\localstate\rootfs\usr\bin\python2.7" enable=yes```
    * 有关如何添加防火墙规则的更多详细信息，请参阅[链接](https://support.microsoft.com/help/947709/how-to-use-the-netsh-advfirewall-firewall-context-instead-of-the-netsh)
* 使用 wsl.exe 时遵循用户的默认 shell。 [GH 2372]
* 将所有网络接口报告为以太网。 [GH 2996]
* 更好地处理损坏的 /etc/passwd 文件。 [GH 3001]

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17618-skip-ahead"></a>内部版本 17618 (Skip Ahead)
有关内部版本 17618 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/03/07/announcing-windows-10-insider-preview-build-17618-skip-ahead/)。

### <a name="wsl"></a>WSL
* 引入用于 NT interop 的伪控制台功能 [GH 988、1366、1433、1542、2370、2406]。
* 传统的安装机制 (lxrun.exe) 已弃用。 支持用于安装分发版的机制是 Microsoft Store。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17110"></a>版本 17110
有关内部版本 17110 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/02/27/announcing-windows-10-insider-preview-build-17110-fast/)。

### <a name="wsl"></a>WSL
* 允许从 Windows 终止 /init [GH 2928]。
* 现在，DrvFs 默认使用按目录区分大小写（相当于使用“case=dir”装载选项）。
    * 使用“case=dir”（旧行为）需要设置注册表项。 如果需要使用“case=dir”，请运行以下命令来启用它：reg add HKLM\SYSTEM\CurrentControlSet\Services\lxss /v DrvFsAllowForceCaseSensitivity /t REG_DWORD /d 1
    * 如果在旧版 Windows 中使用 WSL 创建的现有目录需要区分大小写，请使用 fsutil.exe 将其标记为区分大小写：fsutil.exe file setcasesensitiveinfo <path> enable
* NULL 终止从 uname syscall 返回的字符串。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17107"></a>内部版本 17107
有关内部版本 17107 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/02/23/announcing-windows-10-insider-preview-build-17107-fast-ring/)。

### <a name="wsl"></a>WSL
* 支持主 pty 终结点上的 TCSETSF 和 TCSETSW [GH 2552]。
* 启动同步 interop 进程可能会导致 EINVAL [GH 2813]。
* 修复 PTRACE_ATTACH 以在 /proc/pid/status 中显示正确的跟踪状态。
* 修复以下争用问题：在不清除 TID 地址的情况下，通过 CLEARTID 和 SETTID 标志克隆的生存期较短的进程可能会退出。
* 在从 17093 以前的内部版本迁移期间，升级 Linux 文件系统目录时会显示一条消息。 有关 17093 文件系统更改的更多详细信息，请参阅 [17093](https://github.com/MicrosoftDocs/WSL/blob/live/WSL/release-notes.md#build-17093) 的发行说明。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17101"></a>内部版本 17101
有关内部版本 17101 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/02/14/announcing-windows-10-insider-preview-build-17101-fast-build-17604-skip-ahead/)。

### <a name="wsl"></a>WSL
* signalfd 支持。 [GH 129]
* 支持包含非法 NTFS 字符的文件名，现在会将这些字符编码为专用 Unicode 字符。 [GH 1514]
* 不支持写入时，自动装载将回退到只读。 [GH 2603]
* 允许粘贴 Unicode 代理项对（类似于表情符号）。 [GH 2765]
* /proc 和/sys 中的伪文件应从 select、poll、epoll 等命令返回 read 和 write ready [GH 2838]
* 修复当注册表被篡改或损坏时，可能导致服务进入无限循环的问题。
* 修复 netlink 消息，以便能够使用更新版本（上游 4.14）的 iproute2。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17093"></a>内部版本 17093
有关内部版本 17093 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/02/07/announcing-windows-10-insider-preview-build-17093-pc/)。

#### <a name="important"></a>重要说明：
升级到此内部版本后，首次启动 WSL 时，需要执行一些操作来升级 Linux 文件系统目录。 这可能需要几分钟时间，因此 WSL 的启动速度看上去可能很慢。 对于从 Store 安装的每个分发版，只需执行此操作一次。
* 改善了 DrvFs 中的区分大小写支持。
    * DrvFs 现在支持按目录区分大小写。 这是一个可对目录设置的新标志，用于指示应将这些目录中的所有操作视为区分大小写，使得 Windows 应用程序能够正确打开按大小写区分的文件。
    * DrvFs 提供新的装载选项用于按目录控制区分大小写状态
        * case=force：将所有目录视为区分大小写（驱动器根目录除外）。 使用 WSL 创建的新目录将标记为区分大小写。 这也是一种传统行为，不过，它会将新目录标记为区分大小写。
        * case=dir：只将带有按目录区分大小写标志的目录视为区分大小写；其他目录不区分大小写。 使用 WSL 创建的新目录将标记为区分大小写。
        * case=off：只将带有按目录区分大小写标志的目录视为区分大小写；其他目录不区分大小写。 使用 WSL 创建的新目录将标记为不区分大小写。
    * 注意：不会对旧版本中的 WSL 创建的目录设置此标志，因此，如果使用“case=dir”选项，则不会将这些目录视为区分大小写。 即将推出一种对现有目录设置此标志的方法。
    * 使用这些选项进行装载的示例（对于现有的驱动器，必须先卸载，然后才能使用不同选项装载）：sudo mount -t drvfs C: /mnt/c -o case=dir
    * 目前，case=force 仍是默认选项。 以后将更改为 case=dir。
* 现在，在装载 DrvFs 时，可以在 Windows 路径中使用正斜杠，例如：sudo mount -t drvfs //server/share /mnt/share
* WSL 现在会在实例启动期间处理 /etc/fstab 文件 [GH 2636]。
    * 这种处理是在自动装载 DrvFs 驱动器之前完成的；fstab 已装载的任何驱动器不会自动重新装载，使你可以更改特定驱动器的装入点。
    * 可以使用 wsl.conf 禁用此行为。
* /proc 中的 mount、mountinfo 和 mountstats 文件会正确转义反斜杠和空格等特殊字符 [GH 2799]
* 在启用元数据的情况下使用 DrvFs 创建的特殊文件（例如 WSL 符号链接，或 fifos 和 sockets）现在可以从 Windows 复制和移动。

#### <a name="wsl-is-more-configurable-with-wslconf"></a>可以使用 wsl.conf 更方便地配置 WSL
我们添加了一个方法，用于自动配置 WSL 中每次启动子系统时要应用的某些功能。 这包括自动装载选项和网络配置。 有关详细信息，请参阅博客文章： https://aka.ms/wslconf

#### <a name="af_unix-allows-socket-connections-between-linux-processes-on-wsl-and-windows-native-processes"></a>AF_UNIX 允许在 WSL 上的 Linux 进程与 Windows 本机进程之间建立套接字连接
现在，WSL 和 Windows 应用程序可以通过 Unix 套接字相互通信。 假设你要在 Windows 中运行某个服务，并使其可在 Windows 和 WSL 应用中使用。 现在可以通过 Unix 套接字实现此目的。 有关详细信息，请参阅博客文章： https://aka.ms/afunixinterop

### <a name="wsl"></a>WSL
* 支持使用 MAP_NORESERVE 的 mmap() [GH 121、2784]
* 支持 CLONE_PTRACE 和 CLONE_UNTRACED [GH 121、2781]
* 处理克隆中的非 SIGCHLD 终止信号 [GH 121、2781]
* 存根 /proc/sys/fs/inotify/max_user_instances 和 /proc/sys/fs/inotify/max_user_watches [GH 1705]
* 加载包含偏移量非零的负载标头的 ELF 二进制文件时出错 [GH 1884]
* 加载映像时将尾随页字节归零。
* 减少 execve 以静默方式终止进程的情况

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17083"></a>版本 17083
有关内部版本 17083 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/01/24/announcing-windows-10-insider-preview-build-17083-for-pc/)。

### <a name="wsl"></a>WSL
* 修复了与 epoll 相关的 bug 检查 [GH 2798、2801、2857]
* 修复了关闭 ASLR 时挂起的问题 [GH 1185、2870]
* 确保 mmap 操作显示原子性 [GH 2732]

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17074"></a>内部版本 17074
有关内部版本 17074 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2018/01/11/announcing-windows-10-insider-preview-build-17074-pc/)。

### <a name="wsl"></a>WSL
* 固定了 DrvFs 元数据的存储格式 [GH 2777] </br>
**重要说明：** 在此内部版本之前创建的 DrvFs 元数据将不正确地显示或根本不显示。 若要修复受影响的文件，请使用 chmod 和 chown 重新应用元数据。
* 修复了多个信号和可重启 syscall 的问题。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17063"></a>内部版本 17063
有关内部版本 17063 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/12/19/announcing-windows-10-insider-preview-build-17063-pc/)。

### <a name="wsl"></a>WSL
* DrvFs 支持其他 Linux 元数据。 这样，就可以使用 chmod/chown 设置文件的所有者和模式，并可以创建特殊文件，例如 fifos、Unix 套接字和设备文件。 默认情况下，此功能暂时处于禁用状态，因为它仍是试验性的。
**注意：** 修复了 DrvFs 使用的元数据格式的 bug。 尽管试验性的元数据可在此内部版本中正常工作，但将来的内部版本无法正确读取此内部版本创建的元数据。  你可能需要手动更新已修改的文件的所有者，并且必须重新创建使用自定义设备 ID 的设备。

  若要启用元数据，请使用 metadata 选项装载 DrvFs（若要在现有装入点上启用，必须先将其卸载）：

  ```bash
  mount -t drvfs C: /mnt/c -o metadata
  ```

  Linux 权限将作为附加元数据添加到文件；它们不会影响 Windows 权限。  请记住，使用 Windows 编辑器编辑文件可能会删除元数据。 在这种情况下，文件将还原为默认权限。

* 已将 mount 选项添加到 DrvFs，用于控制不包含元数据的文件。
  * uid：所有文件的所有者使用的用户 ID。
  * gid：所有文件的所有者使用的组 ID。
  * umask：要对所有文件和目录排除的权限的八进制掩码。
  * fmask：要对所有常规文件排除的权限的八进制掩码。
  * dmask：要对所有目录排除的权限的八进制掩码。

  例如：
  ```
  mount -t drvfs C: /mnt/c -o uid=1000,gid=1000,umask=22,fmask=111
  ```

  与 metadata 选项相结合可以指定不包含元数据的文件的默认权限。

* 引入了新的环境变量 `WSLENV`，用于配置环境变量在 WSL 与 Win32 之间的流动方式。

  例如：

  ``` bash
  WSLENV=GOPATH/l:USERPROFILE/pu:DISPLAY
  ```

  `WSLENV` 是在从 Win32 启动 WSL 进程或者从 WSL 启动 Win32 进程时可以包含的环境变量的冒号分隔列表。  每个变量可以使用斜杠后接一个用于指定其转换方式的标志作为后缀。
  * p：值是应在 WSL 路径与 Win32 路径之间进行转换的路径。
  * l：值是路径列表。 在 WSL 中，它是冒号分隔的列表。 在 Win32 中，它是分号分隔的列表。
  * u：仅当从 Win32 调用 WSL 时才应该包含该值
  * w：仅当从 WSL 调用 Win32 时才应该包含该值

  可以在 .bashrc 中或者在用户的自定义 Windows 环境中设置 `WSLENV`。

* drvfs 装入点会正确保留 tar、cp -p 中的时间戳 (GH 1939)
* drvfs 符号链接会报告正确的大小 (GH 2641)
* read/write 适用于极大的 IO 大小 (GH 2653)
* waitpid 适用于进程组 ID (GH 2534)
* 极大改善了大型保留区域的 mmap 性能；改善了 ghc 性能 (GH 1671)
* READ_IMPLIES_EXEC 的个性化支持；修复 maxima 和 clisp (GH 1185)
* mprotect 支持 PROT_GROWSDOWN；修复 clisp (GH 1128)
* overcommit 模式的页面错误修复；修复 sbcl (GH 1128)
* clone 支持更多标志组合
* 支持 epoll 文件的 select/epoll（以前为 no-op）。
* 通知未实现的 syscall 的 ptrace。
* 忽略生成 resolv.conf 名称服务器时不启动的接口 [GH 2694]
* 枚举没有物理地址的网络接口。 [GH 2685]
* 其他 bug 修复和改进。

### <a name="linux-tools-available-to-developers-on-windows"></a>适用于 Windows 上的开发人员的 Linux 工具

* Windows 命令行工具链包括 bsdtar (tar) 和 curl。
  请阅读[此博客](https://aka.ms/tarcurlwindows)来详细了解如何添加这两个新工具，以及它们如何打造 Windows 上的开发人员体验。

*   `AF_UNIX` 适用于 Windows 预览体验成员 SDK (17061+)。
  请阅读[此博客](https://blogs.msdn.microsoft.com/commandline/2017/12/19/af_unix-comes-to-windows/)来详细了解 `AF_UNIX`，以及 Windows 上的开发人员如何使用它。

### <a name="console"></a>控制台
* 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。


## <a name="build-17046"></a>内部版本 17046

有关内部版本 17046 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/11/22/announcing-windows-10-insider-preview-build-17046-pc)。

### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 允许进程在没有活动终端的情况下运行。 [GH 709、1007、1511、2252、2391 等]
- 更好地支持 CLONE_VFORK 和 CLONE_VM。 [GH 1878、2615]
- 跳过 WSL 网络操作的 TDI 筛选器驱动程序。 [GH 1554]
- 在满足特定的条件时，DrvFs 将创建 NT 符号链接。 [GH 353、1475、2602]
    - 链接目标必须是相对性的，不能跨任何装入点或符号链接，并且必须存在。
    - 除非已启用开发人员模式，否则用户必须具有 SE_CREATE_SYMBOLIC_LINK_PRIVILEGE（这通常需要以提升的权限启动 wsl.exe）。
    - 在所有其他情况下，DrvFs 仍会创建 WSL 符号链接。
- 允许同时运行提升和未提升的 WSL 实例。
- 支持 /proc/sys/kernel/yama/ptrace_scope
- 添加 wslpath 用于执行 WSL<->Windows 路径转换。 [GH 522、1243、1834、2327 等]
  ```
    wslpath usage:
      -a    force result to absolute path format
      -u    translate from a Windows path to a WSL path (default)
      -w    translate from a WSL path to a Windows path
      -m    translate from a WSL path to a Windows path, with '/' instead of '\\'

      EX: wslpath 'c:\users'
  ```
  #### <a name="console"></a>控制台
- 无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。


## <a name="build-17040"></a>内部版本 17040

有关内部版本 17040 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/11/16/announcing-windows-10-insider-preview-build-17040-pc)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 自 17035 以来无修复措施。

#### <a name="console"></a>控制台
- 自 17035 以来无修复措施。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17035"></a>内部版本 17035

有关内部版本 17035 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/11/08/announcing-windows-10-insider-preview-build-17035-pc)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 访问 DrvFs 上的文件偶尔会失败并出现 EINVAL。 [GH 2448]

#### <a name="console"></a>控制台
- 在 VT 模式下插入/删除行时丢失一些颜色。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17025"></a>内部版本 17025

有关内部版本 17025 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/10/25/announcing-windows-10-insider-preview-build-17025-pc)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 在新的前台进程组中启动初始进程 [GH 1653、2510]。
- SIGHUP 传递修复 [GH 2496]。
- 如果未提供虚拟网桥名称，将生成默认名称 [GH 2497]。
- 实现 /proc/sys/kernel/random/boot_id [GH 2518]。
- 更多 interop stdout/stderr 管道修复措施。
- 存根 syncfs 系统调用。

#### <a name="console"></a>控制台
- 修复第三方控制台的输入 VT 转换 [GH 111]

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="build-17017"></a>内部版本 17017

有关内部版本 17017 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/10/13/announcing-windows-10-insider-preview-build-17017-pc)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 忽略空的 ELF 程序标头 [GH 330]。
- 允许 LxssManager 为非交互式用户创建 WSL 实例（ssh 和计划任务支持）[GH 777、1602]。
- 支持 WSL->Win32->WSL（“起始”）方案 [GH 1228]。
- 有限支持终止通过 interop 调用的控制台应用 [GH 1614]。
- 支持 devpts 的装载选项 [GH 1948]。
- Ptrace 阻止子级启动 [GH 2333]。
- EPOLLET 缺少某些事件 [GH 2462]。
- 返回 PTRACE_GETSIGINFO 的更多数据。
- 结合 lseek 运行 Getdents 会提供错误的结果。
- 修复某些 Win32 interop 应用挂起，并等待在没有更多数据的管道中提供输入的问题。
- tty/pty 文件的 O_ASYNC 支持。
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
正在测试。

## <a name="fall-creators-update"></a>Fall Creators Update

## <a name="build-16288"></a>内部版本 16288

有关内部版本 16288 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/09/12/announcing-windows-10-insider-preview-build-16288-pc-build-15250-mobile/#7pLWQbj23JisfzV5.97/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 正确初始化和报告套接字文件描述符的 uid、gid 和模式 [GH 2490]
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
自 16273 以来无更改

## <a name="build-16278"></a>内部版本 16278

有关内部版本 162738 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/08/29/announcing-windows-10-insider-preview-build-16278-pc/#HMz6Xq7Su68WKi0t.97/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 分解 LX MM 状态时显式取消映射文件后备节的映射视图 [GH 2415]
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
自 16273 以来无更改

## <a name="build-16275"></a>内部版本 16275

有关内部版本 162735 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/08/25/announcing-windows-10-insider-preview-build-16275-pc-build-15245-mobile/#8QkxWqQbY37yZslV.97/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 此版本中没有 WSL 相关的更改。

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
自 16273 以来无更改

## <a name="build-16273"></a>内部版本 16273

有关内部版本 16273 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/08/23/announcing-windows-10-insider-preview-build-16273-pc/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 修复了 DrvFs 有时报告目录的错误文件类型的问题 [GH 2392]
- 允许创建 NETLINK_KOBJECT_UEVENT 套接字来取消阻止使用 UEVENT 的程序 [GH 1121、2293、2242、2295、2235、648、637]
- 添加对非阻塞连接的支持 [GH 903、1391、1584、1585、1829、2290、2314]
- 实现 CLONE_FS 克隆系统调用标志 [GH 2242]
- 修复有关在 NT interop 中不会正确处理制表符或引号的问题 [GH 1625、2164]
- 解决尝试重新启动 WSL 实例时发生的拒绝访问错误 [GH 651、2095]
- 实现 futex FUTEX_REQUEUE 和 FUTEX_CMP_REQUEUE 操作 [GH 2242]
- 修复各种 SysFs 文件的权限 [GH 2214]
- 修复设置过程中 Haskell 堆栈挂起的问题 [GH 2290]
- 实现 binfmt_misc“C”、“O”和“P”标志 [GH 2103]
- 添加 /proc/sys/kernel /shmmax /shmmni 和 /threads-max [GH 1753]
- 添加对 ioprio_set 系统调用的部分支持 [GH 498]
- 存根 SO_REUSEPORT 和添加 netlink 套接字的 SO_PASSCRED 支持 [GH 69]
- 如果当前正在安装或卸载分发版，将从 RegisterDistribuiton 返回不同的错误代码。
- 允许通过 wslconfig.exe 取消注册部分安装的 WSL 分发版
- 修复 udp::msg_peek 的 python 套接字测试挂起问题
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
测试总数：1904<br/>
跳过的测试总数：209<br/>
失败总数：229<br/>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/16273)<br/>

## <a name="build-16257"></a>版本 16257

有关内部版本 16257 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/08/02/announcing-windows-10-insider-preview-build-16257-pc-build-15237-mobile/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 实现 prlimit64 系统调用
- 添加对 ulimit -n 的支持 (setrlimit RLIMIT_NOFILE) [GH 1688]
- TCP 套接字的存根 MSG_MORE [GH 2351]
- 修复无效的 AT_EXECFN 辅助矢量行为 [GH 2133]
- 修复 console/tty 的 copy/paste 行为，并添加更适当的完整缓冲区处理 [GH 2204、2131]
- 在 set-user-ID 和 set-group-ID 程序的辅助矢量中设置 AT_SECURE [GH 2031]
- 伪终端主终结点不处理 TIOCPGRP [GH 1063]
- 修复 lseek 在 LxFs 中的回退目录行为 [GH 2310]
- 重度使用后 /dev/ptmx 锁定 [GH 1882]
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 修复横线/下划线四处可见的问题 [GH 2168]
- 修复进程顺序更改，使 NPM 更难以关闭的问题 [GH 2170]
- 添加了新的色彩方案： https://blogs.msdn.microsoft.com/commandline/2017/08/02/updating-the-windows-console-colors/

### <a name="ltp-results"></a>LTP 结果：
自 16251 以来无更改

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`prlimit64`<br/>

### <a name="known-issues"></a>已知问题
#### <a name="github-issue-2392-windows-folders-not-recognized-by-wsl-"></a>[GitHub 问题 2392：WSL 无法识别 Windows 文件夹 ...](https://github.com/Microsoft/BashOnWindows/issues/2392)
在内部版本 16257 中，WSL 在通过 `/mnt/c/...` 枚举 Windows 文件/文件夹时会出现问题。
此问题已修复，修复程序将在 2017 年 8 月 14 日开始的周内，在预览体验成员内部版本中发布。

<br/>

## <a name="build-16251"></a>内部版本 16251

有关内部版本 16251 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/07/26/announcing-windows-10-insider-preview-build-16251-pc-build-15235-mobile/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 从 WSL 可选组件中删除 beta 标记，有关详细信息，请参阅[博客文章](https://blogs.msdn.microsoft.com/commandline/2017/07/28/windows-subsystem-for-linux-out-of-beta/)。
- 在执行时正确初始化 set-user-ID 和 set-group-ID 二进制文件的 saved-set uid 和 gid [GH 962、1415、2072]
- 添加了对 ptrace PTRACE_O_TRACEEXIT 的支持 [GH 555]
- 添加了对包含 NT_FPREGSET 的 ptrace PTRACE_GETFPREGS 和 PTRACE_GETREGSET 的支持 [GH 555]
- 修复了 ptrace 在忽略信号时停止的问题
- 其他改进和 bug 修复

#### <a name="console"></a>控制台
- 此版本中没有控制台相关的更改。

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：768</br>
失败的测试数：244</br>
跳过的测试数：96</br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/16251)<br/>

</br>

## <a name="build-16241"></a>内部版本 16241

有关内部版本 16241 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/07/13/announcing-windows-10-insider-preview-build-16241-pc-build-15230-mobile/)。<br/>


### <a name="fixed"></a>固定
#### <a name="wsl"></a>WSL
- 此版本中没有 WSL 相关的更改。

#### <a name="console"></a>控制台
- 修复输出跨行 DEC 的错误字符的问题，最初报告位于[此处](https://www.reddit.com/r/Windows10/comments/6in82t/i_believe_ive_found_the_most_obscure_bug_ever/)
- 修复代码页 65001 (utf8) 中不显示输出文本的问题
- 更改选择内容时，不会将对某种颜色的 RGB 值所做的更改传输到调色板的其他部分。 这在一定程度上使得控制台属性表变得更易于使用。
- Ctrl+S 似乎不起作用
- ANSI 转义代码中根本没有 Un-Bold/-Dim [GH 2174]
- 控制台不正常支持 Vim 色彩主题 [GH 1706]
- 无法粘贴特定的字符 [GH 2149]
- 当编辑/命令行上有内容时，重复流的调整大小操作以奇怪的方式与 bash 窗口调整大小操作交互 [GH ConEmu 1123]
- 按 Ctrl-L 不会清屏 [GH 1978]
- 在 HDPI 上显示 VT 时的控制台呈现 bug [GH 1907]
- 日文字符出现乱码和 Unicode 字符 U+30FB [GH 2146]
- 其他改进和 bug 修复

</br>

## <a name="build-16237"></a>版本 16237

有关内部版本 16237 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/07/07/announcing-windows-10-insider-preview-build-16237-pc/)。<br/>


### <a name="fixed"></a>固定
- 对 lxfs 中不包含 EA 的文件使用默认属性 (root, root, 0000)
- 添加了对使用扩展属性的分发版的支持
- 修复 getdents 和 getdents64 返回的项的填充
- 修复针对 shmctl SHM_STAT 系统调用的权限检查 [GH 2068]
- 修复了 tty 的错误初始 epoll 状态 [GH 2231]
- 修复 DrvFs readdir 不返回所有项的问题 [GH 2077]
- 修复取消链接文件时的 LxFs readdir [GH 2077]
- 允许通过 procfs 重新打开未链接的 drvfs 文件
- 添加了用于禁用 WSL 功能的全局注册表项重写（interop/驱动器装载）
- 修复 DrvFs（和 LxFs）的“统计信息”中的错误块计数 [GH 1894]
- 其他改进和 bug 修复

</br>

## <a name="build-16232"></a>内部版本 16232

有关内部版本 16232 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/06/28/announcing-windows-10-insider-preview-build-16232-pc-build-15228-mobile/)。<br/>


### <a name="fixed"></a>固定
- 此版本中没有 WSL 相关的更改。

</br>

## <a name="build-16226"></a>内部版本 16226

有关内部版本 16226 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/)。<br/>


### <a name="fixed"></a>固定
- xattr 相关的 syscall 支持（getxattr、setxattr、listxattr、removexattr）。
- security.capablity xattr 支持。
- 改善了与某些文件系统和筛选器（包括非 MS SMB 服务器）的兼容性。 [GH #1952]
- 改善了对 OneDrive 占位符、GVFS 占位符和精简 OS 压缩文件的支持。
- 其他改进和 bug 修复

</br>

## <a name="build-16215"></a>内部版本 16215

有关内部版本 16215 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/06/08/announcing-windows-10-insider-preview-build-16215-pc-build-15222-mobile/)。<br/>


### <a name="fixed"></a>固定
- WSL 不再需要开发人员模式。
- 支持 drvfs 中的目录接合。
- 处理 WSL appx 分发包的卸载。
- 更新 procfs 以显示专用映射和共享映射。
- 为 wslconfig.exe 添加清理部分安装或已卸载的分发版的功能。
- 添加了对 TCP 套接字的 IP_MTU_DISCOVER 的支持。 [GH 1639、2115、2205]
- 推断 AF_INADDR 路由的协议系列。
- 串行设备改进 [GH 1929]。

</br>

## <a name="build-16199"></a>内部版本 16199

有关内部版本 16199 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/05/17/announcing-windows-10-insider-preview-build-16199-pc-build-15215-mobile/)。<br/>


### <a name="fixed"></a>固定
- 这些版本中没有 WSL 相关的更改。

</br>

## <a name="build-16193"></a>内部版本 16193

有关内部版本 16193 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/05/11/announcing-windows-10-insider-preview-build-16193-pc-build-15213-mobile/)。<br/>


### <a name="fixed"></a>固定
- 发送 SIGCONT 与终止线程组之间的争用状态 [GH 1973]
- 更改 tty 和 pty 设备以报告 FILE_DEVICE_NAMED_PIPE 而不是 FILE_DEVICE_CONSOLE [GH 1840]
- IP_OPTIONS 的 SSH 修复
- 已将 DrvFs 装载移到初始化守护程序 [GH 1862、1968、1767、1933]
- 在 DrvFs 中添加了遵循 NT 符号链接的支持。

</br>

## <a name="build-16184"></a>内部版本 16184

有关内部版本 16184 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/04/28/announcing-windows-10-insider-preview-build-16184-pc-build-15208-mobile/)。<br/>


### <a name="fixed"></a>固定
- 删除了 apt 包维护任务 (lxrun.exe /update)
- 修复了 node.js 中的 Windows 进程不显示输出的问题 [GH 1840]
- 放宽 lxcore 中的对齐要求 [GH 1794]
- 修复了许多系统调用中处理 AT_EMPTY_PATH 标志的问题。
- 修复了删除存在已打开句柄的 DrvFs 文件时，导致文件出现未定义的行为的问题 [GH 544、966、1357、1535、1615]
- /etc/hosts 现在会从 Windows hosts 文件 (%windir%\system32\drivers\etc\hosts) 继承项 [GH 1495]

</br>

## <a name="build-16179"></a>内部版本 16179

有关内部版本 16179 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/04/19/announcing-windows-10-insider-preview-build-16179-pc-build-15205-mobile/)。<br/>


### <a name="fixed"></a>固定
- 本周没有 WSL 更改。

</br>

## <a name="build-16176"></a>内部版本 16176

有关内部版本 16176 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/04/14/announcing-windows-10-insider-preview-build-16176-pc-build-15204-mobile/)。<br/>


### <a name="fixed"></a>固定

- [已启用串行支持](https://blogs.msdn.microsoft.com/wsl/2017/04/14/serial-support-on-the-windows-subsystem-for-linux/)
- 添加了 IP 套接字选项 IP_OPTIONS [GH 1116]
- 实现了 pwritev 函数（将文件上传到 nginx/PHP-FPM 时）[GH 1506]
- 添加了 IP 套接字选项 IP_MULTICAST_IF 和 IPV6_MULTICAST_IF [GH 990]
- 支持套接字选项 IP_MULTICAST_LOOP 和 IPV6_MULTICAST_LOOP [GH 1678]
- 为应用节点、traceroute、dig、nslookup、主机添加了 IP(V6)_MTU 套接字选项
- 添加了 IP 套接字选项 IPV6_UNICAST_HOPS
- [文件系统改进](https://blogs.msdn.microsoft.com/wsl/2017/04/18/file-system-improvements-to-the-windows-subsystem-for-linux/)
    * 允许装载 UNC 路径
    * 在 drvfs 中启用 CDFS 支持
    * 正确处理 drvfs 中网络文件系统的权限
    * 在 drvfs 中添加远程驱动器的支持
    * 在 drvfs 中启用 FAT 支持
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果
自 15042 以来无更改

</br>

## <a name="build-16170"></a>内部版本 16170

有关内部版本 16170 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/04/07/announcing-windows-10-insider-preview-build-16170-pc/)。<br/>

我们发布的新[博客文章](https://blogs.msdn.microsoft.com/wsl/2017/04/11/testing-the-windows-subsystem-for-linux/)中介绍了我们在测试 WSL 方面所做的努力。

### <a name="fixed"></a>固定

- 支持套接字选项 IP_ADD_MEMBERSHIP 和 IPV6_ADD_MEMBERSHIP [GH 1678]
- 添加对 PTRACE_OLDSETOPTIONS 的支持。 [GH 1692]
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果
自 15042 以来无更改

</br>

## <a name="build-15046-to-windows-10-creators-update"></a>内部版本 15046 到 Windows 10 创意者更新
我们未计划在 Windows 10 创意者更新中包含其他 WSL 修复或功能。 WSL 的发行说明将在未来几周恢复发布，其中补充了面向下一个 Windows 更新主要版本的信息。 有关内部版本 15046 和将来的预览体验版的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/02/28/announcing-windows-10-insider-preview-build-15046-pc/)。 <br/><br/>
 <br/>

## <a name="build-15042"></a>内部版本 15042

有关内部版本 15042 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/02/24/announcing-windows-10-insider-preview-build-15042-pc-build-15043-mobile/)。<br/>


### <a name="fixed"></a>固定

- 修复删除以“...”结尾的路径时出现死锁的问题
- 修复了 FIONBIO 在成功时不返回 0 的问题 [GH 1683]
- 修复了 inet 数据报套接字的零长度读取问题
- 修复 drvfs inode 查找中的争用状况可能导致死锁的问题 [GH 1675]
- 扩展了对 unix 套接字辅助数据的支持；SCM_CREDENTIALS 和 SCM_RIGHTS [GH 514、613、1326]
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：737</br>
未通过的测试数（失败、已跳过等）：255

</br>

## <a name="build-15031"></a>内部版本 15031

有关内部版本 15031 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/02/08/announcing-windows-10-insider-preview-build-15031-pc/)。<br/>


### <a name="fixed"></a>固定

- 修复了 time(2) 偶尔行为异常的 bug。
- 修复了 *SIGPROCMASK syscall 可能损坏信号掩码的问题。
- 现在会在 WSL 进程创建通知中返回完整的命令行长度。 [GH 1632]
- WSL 现在会针对 GDB 挂起通过 ptrace 报告线程退出。 [GH 1196]
- 修复了在收到繁重 tmux IO 后 ptys 挂起的 bug。 [GH 1358]
- 修复了许多系统调用中的超时验证（futex、semtimedop、ppoll、sigtimedwait、itimer、timer_create）
- 添加了 eventfd EFD_SEMAPHORE 支持 [GH 452]
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：737</br>
未通过的测试数（失败、已跳过等）：255 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15031)<br/>

<br/>

## <a name="build-15025"></a>内部版本 15025

有关内部版本 15025 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/02/01/announcing-windows-10-insider-preview-build-15025-pc/)。<br/>


### <a name="fixed"></a>固定

- 修复破坏 grep 2.27 的 bug [GH 1578]
- 为 eventfd2 syscall 实现了 EFD_SEMAPHORE 标志 [GH 452]
- 实现了 /proc/[pid]/net/ipv6_route [GH 1608]
- 针对 unix 流套接字的信号驱动 IO 支持 [GH 393、68]
- 支持 F_GETPIPE_SZ 和 F_SETPIPE_SZ [GH 1012]
- 实现 recvmmsg() syscall [GH 1531]
- 修复了 epoll_wait() 不等待的 bug [GH 1609]
- 实现 /proc/version_signature
- 现在，如果两个文件描述符引用同一管道，则 syscall 会返回失败
- 为 Unix 套接字的 SO_PEERCRED 实现了正确的行为
- 修复了 tkill syscall 处理无效参数的方法
- 做出更改以提高 drvfs 的性能
- 针对 Ruby IO 阻塞的次要修复
- 修复了 recvmsg() 对 inet 套接字的 MSG_DONTWAIT 标志返回 EINVAL 的问题 [GH 1296]
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：732</br>
未通过的测试数（失败、已跳过等）：255 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15025)<br/>

<br/>

## <a name="build-15019"></a>内部版本 15019

有关内部版本 15019 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/01/27/announcing-windows-10-insider-preview-build-15019-pc/)。<br/>


### <a name="fixed"></a>固定

- 修复了 htop 等工具在 procfs 中错误报告 CPU 使用率的 bug（GH 823、945、971）
- 对现有的文件结合 O_TRUNC 调用 open() 时，inotify 现在会在 IN_OPEN 的前面生成 IN_MODIFY
- 修复 unix 套接字 getsockopt SO_ERROR 以启用 postgress [GH 61、1354]
- 为 GO 语言实现 /proc/sys/net/core/somaxconn
- Apt-get package update 后台任务现在会在视图中以隐藏方式运行
- 清除 ipv6 localhost 的范围（Spring-Framework(Java) 失败）。
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：714 </br>
未通过的测试数（失败、已跳过等）：249 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15019)<br/>

<br/>

## <a name="build-15014"></a>内部版本 15014

有关内部版本 15014 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/01/19/announcing-windows-10-insider-preview-build-15014-for-pc-and-mobile-hello-windows-insiders-today-we-are-excited-to-be-releasing-windows-10-insider-preview-build-15014-for-pc-and-mobile)。<br/>


### <a name="fixed"></a>固定

- Ctrl+C 现在可按预期方式工作
- htop 和 ps auxw 现在会显示正确的资源利用率 (GH #516)
- NT 异常到信号的基本转换。 (GH #513)
- 当空间耗尽时，fallocate 现在会失败并返回 ENOSPC，而不是返回 EINVAL (GH #1571)
- 添加了 /proc/sys/kernel/sem。
- 实现了 semop 和 semtimedop 系统调用
- 修复了 IP_RECVTOS 和 IPV6_RECVTCLASS 套接字选项的 nslookup 错误 (GH 69)
- 支持套接字选项 IP_RECVTTL 和 IPV6_RECVHOPLIMIT
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：709 </br>
未通过的测试数（失败、已跳过等）：255 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15014)<br/>

### <a name="syscall-summary"></a>Syscall 摘要
Syscall 总数：384 </br>
已实现总数：235 </br>
已存根总数：22 </br>
未实现总数：127 </br>
[详细分解](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15014/Syscalls.txt)<br/>

<br/>

## <a name="build-15007"></a>内部版本 15007

有关内部版本 15007 的一般 Windows 信息，请访问 [Windows 博客]( https://blogs.windows.com/windowsexperience/2017/01/12/announcing-windows-10-insider-preview-build-15007-pc-mobile)。<br/>


### <a name="known-issue"></a>已知问题

- 已知 bug：控制台无法识别某些 Ctrl + <key> 输入。  这包括将充当普通“c”按键的 ctrl-c 命令。

  - 解决方法：将备用键映射到 Ctrl+C。 例如，若要将 Ctrl+K 映射到 Ctrl+C，请执行：`stty intr \^k`。  这种映射是按终端进行的，每次启动 bash 都必须执行。 用户可以探索该选项，以将此映射包含在其 `.bashrc` 中

### <a name="fixed"></a>固定

- 更正了运行 WSL 会消耗 100% 的 CPU 核心的问题
- 现在支持套接字选项 IP_PKTINFO、IPV6_RECVPKTINFO。 （GH #851、987）
- 在 lxcore 中将网络接口物理地址截断为 16 个字节（GH #1452、1414、1343、468、308）
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：709 </br>
未通过的测试数（失败、已跳过等）：255 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15007)<br/>

<br/>

## <a name="build-15002"></a>内部版本 15002

有关内部版本 15002 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2017/01/09/announcing-windows-10-insider-preview-build-15002-pc/)。<br/>


### <a name="known-issue"></a>已知问题

两个已知问题：
- 已知 bug：控制台无法识别某些 Ctrl + <key> 输入。  这包括将充当普通“c”按键的 ctrl-c 命令。

  - 解决方法：将备用键映射到 Ctrl+C。 例如，若要将 Ctrl+K 映射到 Ctrl+C，请执行：`stty intr \^k`。  这种映射是按终端进行的，每次启动 bash 都必须执行。 用户可以探索该选项，以将此映射包含在其 `.bashrc` 中

- 当 WSL 运行时，系统线程将消耗 100% 的 CPU 核心。  根本原因已解决并已在内部修复。

### <a name="fixed"></a>固定

- 现在，必须在同一权限级别创建所有 bash 会话。  尝试在不同级别启动会话将遭到阻止。  这意味着，管理员和非管理员控制台不能同时运行。 (GH #626)
<br/>
- 实现了以下 NETLINK_ROUTE 消息（需要 Windows 管理员）
     - RTM_NEWADDR（支持 `ip addr add`）
     - RTM_NEWROUTE（支持 `ip route add`）
     - RTM_DELADDR（支持 `ip addr del`）
     - RTM_DELROUTE（支持 `ip route del`）
- 用于检查要更新的包的计划任务将不再在按流量计费的连接上运行 (GH #1371)
- 修复了运行 bash -c "ls -alR /" | bash -c "cat" 时管道停滞的错误 (GH #1214)
- 实现了 TCP_KEEPCNT 套接字选项 (GH #843)
- 实现了 IP_MTU_DISCOVER INET 套接字选项（GH #720、717、170、69）
- 删除了旧功能，以通过 NT 路径查找从 init 运行 NT 二进制文件。 (GH #1325)
- 修复 /dev/kmsg 的模式，以允许进行组访问/其他读取访问 (0644) (GH #1321)
- 实现了 /proc/sys/kernel/random/uuid (GH #1092)
- 更正了进程开始时间显示为 2432 年的错误 (GH #974)
- 已将默认 TERM 环境变量切换为 xterm-256color (GH #1446)
- 修改了进程分叉期间进程提交的计算方式。 (GH #1286)
- 实现了 /proc/sys/vm/overcommit_memory。 (GH #1286)
- 实现了 /proc/net/route 文件 (GH #69)
- 修复了不正确本地化快捷方式名称的错误 (GH #696)
- 修复了错误地验证程序标头必须小于（或等于）PATH_MAX 的 elf 分析逻辑。 (GH #1048)
- 为 procfs、sysfs、cgroupfs 和 binfmtfs 实现了 statfs 回调 (GH #1378)
- 修复了 AptPackageIndexUpdate 窗口不会关闭的问题（GH #1184，GH #1193 中也进行了讨论）
- 添加了 ASLR 个性化 ADDR_NO_RANDOMIZE 支持。 （GH #1148、1128）
- 改善了 PTRACE_GETSIGINFO、SIGSEGV，在 AV 期间会提供正确的 gdb 堆栈跟踪 (GH #875)
- 针对 patchelf 二进制文件的 Elf 分析不再失败。 (GH #471)
- VPN DNS 已传播到 /etc/resolv.conf（GH #416、1350）
- TCP 关闭改进，可以更可靠地传输数据。 （GH #610、616、1025、1335）
- 现在，在打开过多的文件时可返回正确的错误代码 (EMFILE)。 （GH #1126、2090）
- Windows 审核日志现在会在进程创建审核中报告映像名称。
- 现在，在从 bash 窗口内部启动 bash 时会正常失败
- 添加了在 interop 无法访问 LxFs 下的工作目录（即 notepad.exe .bashrc）时显示的错误消息
- 修复了 Windows 路径在 WSL 中截断的问题
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：690 </br>
未通过的测试数（失败、已跳过等）：274 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/15002)<br/>

<br/>

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`shmctl`<br/>
`shmget`<br/>
`shmdt`<br/>
`shmat`<br/>
<br/>

## <a name="build-14986"></a>内部版本 14986

有关内部版本 14986 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/12/07/announcing-windows-10-insider-preview-build-14986-pc/)。<br/>


### <a name="fixed"></a>固定

- 修复了 Netlink 和 Pty IOCTL 的 bug 检查
- 内核版本现在会报告 4.4.0-43，以便与 Xenial 保持一致
- 现在，当输入定向到 'nul:' 时会启动 Bash.exe (GH #1259)
- 现在，procfs 中会正确报告线程 ID (GH #967)
- 现在，inotify_add_watch() 中支持 IN_UNMOUNT | IN_Q_OVERFLOW | IN_IGNORED | IN_ISDIR 标志 (GH #1280)
- 实现 timer_create 和相关的系统调用。  这会启用 GHC 支持 (GH #307)
- 修复了 ping 返回时间 0.000ms 的问题 (GH #1296)
- 打开过多的文件时返回正确的错误代码。
- 修复了 WSL 中的问题：如果网络接口的硬件地址为 32 字节（例如 Teredo 接口），则针对该网络接口数据的 Netlink 请求将会失败并返回 EINVAL。
   - 请注意，Linux“ip”实用工具包含一个 bug：如果 WSL 报告 32 字节硬件地址，该实用工具将会崩溃。 这是“ip”（而不是 WSL）中的一个 bug。 “ip”实用工具会将用于输出硬件地址的字符串缓冲区的长度进行硬编码，而该缓冲区太小，无法输出 32 字节硬件地址。
- 其他修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：669 </br>
未通过的测试数（失败、已跳过等）：258 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14986)<br/>

<br/>

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`timer_create`<br/>
`timer_delete`<br/>
`timer_gettime`<br/>
`timer_settime`<br/>
<br/>

## <a name="build-14971"></a>内部版本 14971

有关内部版本 14971 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/11/17/announcing-windows-10-insider-preview-build-14971-for-pc/)。<br/>


### <a name="fixed"></a>固定

 - 由于这种情况超出了我们的控制，在此内部版本的适用于 Linux 的 Windows 子系统中未做更新。  定期计划的更新将在下一版本中恢复。

### <a name="ltp-results"></a>LTP 结果：
自 14965 以来无更改 </br>
通过的测试数：664 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14965)<br/>

<br/>

## <a name="build-14965"></a>内部版本 14965

有关内部版本 14965 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/11/09/announcing-windows-10-insider-preview-build-14965-for-mobile-and-pc/)。<br/>


### <a name="fixed"></a>固定

- 支持 Netlink 套接字 NETLINK_ROUTE 协议的 RTM_GETLINK 和 RTM_GETADDR (GH #468)
  - 为网络枚举启用 ifconfig 和 ip 命令
  - 在 [WSL 网络博客文章](https://blogs.msdn.microsoft.com/wsl/2016/11/08/225/)中可以找到详细信息。

- /sbin 现在默认位于用户的路径中
- NT 用户路径现在默认会追加到 WSL 路径（即，现在可以键入 notepad.exe，无需将 System32 添加到 Linux 路径）
- 添加了对 /proc/sys/kernel/cap_last_cap 的支持
- 现在，如果当前工作目录包含非 ANSI 字符，则可以从 WSL 启动 NT 二进制文件 (GH #1254)
- 允许在断开连接的 unix 流套接字上关闭。
- 添加了对 PR_GET_PDEATHSIG 的支持。
- 添加了对 CLONE_PARENT 的支持
- 修复了运行 bash -c "ls -alR /" | bash -c "cat" 时管道停滞的错误 (GH #1214)
- 处理连接到当前终端的请求。
- 将 /proc/<pid>/oom_score_adj 标记为可写。
- 添加 /sys/fs/cgroup 文件夹。
- sched_setaffinity 应返回关联位掩码的数目
- 修复错误地假设解释器路径长度必须小于 64 个字符的 ELF 验证逻辑。 (GH #743)
- 打开文件描述符会使控制台窗口保持打开状态 (GH #1187)
- 修复了当目标名称包含尾随斜杠时 rename() 失败的错误 (GH #1008)
- 实现 /proc/net/dev 文件
- 修复了计时器精度导致的 0.000ms ping 错误。
- 实现了 /proc/self/environ (GH #730)
- 其他 bug 修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：664 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14965)<br/>

<br/>

## <a name="build-14959"></a>内部版本 14959

有关内部版本 14959 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/11/03/announcing-windows-10-insider-preview-build-14959-for-mobile-and-pc/#iI82GufJxMF3POU1.97)。<br/>


### <a name="fixed"></a>固定

- 改善了 Windows 的 Pico 进程通知。  在 [WSL 博客](https://blogs.msdn.microsoft.com/wsl/2016/11/01/wsl-antivirus-and-firewall-compatibility/)中可以找到更多信息。
- 改善了 Windows 互操作的稳定性
- 修复了在启用企业数据保护 (EDP) 后启动 bash.exe 时出现的错误 0x80070057
- 其他 bug 修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：665 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14959)<br/>

<br/>

## <a name="build-14955"></a>内部版本 14955

有关内部版本 14955 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/10/25/announcing-windows-10-insider-preview-build-14955-for-mobile-and-pc/#guGXQzKVFrZIDUYR.97)。<br/>


### <a name="fixed"></a>固定

 - 由于这种情况超出了我们的控制，在此内部版本的适用于 Linux 的 Windows 子系统中未做更新。  定期计划的更新将在下一版本中恢复。

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：665 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14955)<br/>

<br/>

## <a name="build-14951"></a>内部版本 14951

有关内部版本 14951 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/10/19/announcing-windows-10-insider-preview-build-14951-for-mobile-and-pc/)。<br/>


### <a name="new-feature-windows--ubuntu-interoperability"></a>新功能：Windows/Ubuntu 互操作性
现在可以直接从 WSL 命令行调用 Windows 二进制文件。  这样，用户便可以通过前所未有的方式来与其 Windows 环境和系统交互。  举个简单的例子，用户现在可以运行以下命令：

    ```
    $ export PATH=$PATH:/mnt/c/Windows/System32
    $ notepad.exe
    $ ipconfig.exe | grep IPv4 | cut -d: -f2
    $ ls -la | findstr.exe foo.txt
    $ cmd.exe /c dir
    ```

可在以下资源中找到详细信息：

- [WSL 团队的互操作博客](https://blogs.msdn.microsoft.com/wsl/2016/10/19/windows-and-ubuntu-interoperability/)<br/>
- [MSDN 互操作文档](https://msdn.microsoft.com/commandline/wsl/interop)<br/>

### <a name="fixed"></a>固定

- 现在将为所有新的 WSL 实例安装 Ubuntu 16.04 (Xenial)。  使用现有 14.04 (Trusty) 实例的用户不会自动升级。
- 现在会显示安装过程中指定的区域设置
- 终端改进，包括修复了不是总能将 WSL 进程重定向到文件的 bug
- 控制台生存期应与 bash.exe 生存期密切关联
- 控制台窗口大小应使用可视大小，而不是缓冲区大小
- 其他 bug 修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：665 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14951)<br/>

<br/>

## <a name="build-14946"></a>内部版本 14946

有关内部版本 14946 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/10/13/announcing-windows-10-insider-preview-build-14946-for-pc-and-mobile/#xj8GdVooEqo4H7H7.97)。<br/>


### <a name="fixed"></a>固定

- 修复了阻止使用包含空格或引号的 NT 用户名为用户创建 WSL 用户帐户的问题。 
- 更改 VolFs 和 DrvFs，以在统计信息中返回 0 作为目录的链接计数
- 支持 IPV6_MULTICAST_HOPS 套接字选项。
- 限制为每个 tty 只有一个控制台 I/O 循环。 例如，可运行以下命令：
  - bash -c "echo data" | bash -c "ssh user@example.com 'cat > foo.txt'"

- 在 /proc/cpuinfo 中将空格替换为制表符 (GH #1115)
- DrvFs 现在会显示在 mountinfo 中，其中包含一个与已装载的 Windows 卷匹配的名称
- /home 和 /root 现在会显示在 mountinfo 中，并显示正确的名称
- 其他 bug 修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：665 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14946)<br/>

<br/>

## <a name="build-14942"></a>内部版本 14942

有关内部版本 14942 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/onefourninefourtwoooooo)。<br/>


### <a name="fixed"></a>固定

- 解决了一些 bug 检查问题，包括阻止 SSH 的“尝试执行不可执行的内存”网络崩溃
- inotifiy 现在支持从 DrvFs 上的 Windows 应用程序生成通知
- 实现 mongod 的 TCP_KEEPIDLE 和 TCP_KEEPINTVL。 (GH #695)
- 实现 pivot_root 系统调用
- 实现 SO_DONTROUTE 的套接字选项
- 其他 bug 修复和改进


### <a name="ltp-results"></a>LTP 结果：
通过的测试数：665 </br>
未通过的测试数（失败、已跳过等）：263 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14942)<br/>

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`pivot_root`<br/>
<br/>

## <a name="build-14936"></a>内部版本 14936

有关内部版本 14936 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/09/28/announcing-windows-10-insider-preview-build-14936-for-pc/)。<br/>


注意：在即将发布的版本中，WSL 将会安装 Ubuntu 版本16.04 (Xenial) 而不是 Ubuntu 14.04 (Trusty)。  此更改将应用到安装新实例的预览体验版（lxrun /install 或首次运行 bash.exe）。  包含 Trusty 的现有实例不会自动升级。 用户可以使用 do-release-upgrade 命令将其 Trusty 映像升级到 Xenial。

### <a name="known-issue"></a>已知问题
WSL 遇到了某些套接字实现的问题。  bug 检查将自身显示为崩溃，出现错误“尝试执行不可执行的内存”。  此问题的最常见表现形式是使用 ssh 时发生崩溃。  根本原因已在内部版本中修复，将会尽快推送到预览体验版。

### <a name="fixed"></a>固定

- 实现了 chroot 系统调用
- inotifiy 的改进，~~包括支持从 DrvFs 上的 Windows 应用程序生成通知~~
  - 更正：对源自 Windows 应用程序的更改的 Inotify 支持目前不可用。
- 与 IPV6::<port n> 的套接字绑定现在支持 IPV6_V6ONLY（GH #68、#157、#393、#460、#674、#740、#982、#996）
- 实现了 waitid 系统调用的 WNOWAIT 行为 (GH #638)
- 支持 IP 套接字选项 IP_HDRINCL 和 IP_TTL
- 零长度 read() 应立即返回 (GH #975)
- 在 .tar 文件中正确处理不包含 NULL 终止符的文件名和文件名前缀。
- 对 /dev/null 的 epoll 支持
- 修复 /dev/alarm 时间源
- Bash -c 现在可以重定向到文件
- 其他 bug 修复和改进

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：664 </br>
未通过的测试数（失败、已跳过等）：264 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14936)<br/>

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`chroot`<br/>
<br/>

## <a name="build-14931"></a>内部版本 14931

有关内部版本 14931 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/09/21/announcing-windows-10-insider-preview-build-14931-for-pc/)。<br/>


### <a name="fixed"></a>固定

 - 由于这种情况超出了我们的控制，在此内部版本的适用于 Linux 的 Windows 子系统中未做更新。  定期计划的更新将在下一版本中恢复。

<br/>

## <a name="build-14926"></a>内部版本 14926

有关内部版本 14926 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/09/14/announcing-windows-10-insider-preview-build-14926-for-pc-and-mobile/)。<br/>


### <a name="fixed"></a>固定

- Ping 现在可以在没有管理员特权的控制台中正常运行
- 现在支持 Ping6，也无需管理员特权
- 对通过 WSL 修改的文件的 Inotify 支持。 (GH #216)
  - 支持的标志：
    - inotify_init1：LX_O_CLOEXEC、LX_O_NONBLOCK
    - inotify_add_watch 事件：LX_IN_ACCESS、LX_IN_MODIFY、LX_IN_ATTRIB、LX_IN_CLOSE_WRITE、LX_IN_CLOSE_NOWRITE、LX_IN_OPEN、LX_IN_MOVED_FROM、LX_IN_MOVED_TO、LX_IN_CREATE、LX_IN_DELETE、LX_IN_DELETE_SELF、LX_IN_MOVE_SELF
    - inotify_add_watch 属性：LX_IN_DONT_FOLLOW、LX_IN_EXCL_UNLINK、LX_IN_MASK_ADD、LX_IN_ONESHOT、LX_IN_ONLYDIR
    - 读取输出：LX_IN_ISDIR、LX_IN_IGNORED
  - 已知问题：修改 Windows 应用程序中的文件不会生成任何事件
- Unix 套接字现在支持 SCM_CREDENTIALS

### <a name="ltp-results"></a>LTP 结果：
通过的测试数：651 </br>
未通过的测试数（失败、已跳过等）：258 </br>
[LTP 测试运行日志](https://github.com/Microsoft/CommandLine-Documentation/tree/live/LTP_Results/14926)<br/>

<br/>

## <a name="build-14915"></a>内部版本 14915

有关内部版本 14915 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/08/31/announcing-windows-10-insider-preview-build-14915-for-pc-and-mobile)。<br/>


### <a name="fixed"></a>固定
-  Unix 数据报套接字的套接字对 (GH #262)
- 对 SO_REUSEADDR 的 Unix 套接字支持
- 对 SO_BROADCAST 的 UNIX 套接字支持 (GH #568)
- 对 SOCK_SEQPACKET 的 Unix 套接字支持（GH #758、#546）
- 添加对 Unix 数据报套接字 send、recv 和 shutdown 的支持
- 修复对非固定地址的无效 mmap 参数验证导致的 bug 检查。 (GH #847)
- 支持暂停/恢复终端状态
- 支持使用 TIOCPKT ioctl 阻止 Screen 实用工具 (GH #774)
    - 已知问题：功能键不起作用
- 更正了 TimerFd 中的一种争用状态，该状态可能导致 LxpTimerFdWorkerRoutine 访问已释放的成员“ReaderReady” (GH #814)
- 为 futex、poll 和 clock_nanosleep 启用可重启系统调用支持
- 添加了绑定装载支持
- 装载命名空间支持的取消共享
    - 已知问题：使用 `unshare(CLONE_NEWNS)` 创建新的装载命名空间时，当前工作目录将继续指向旧命名空间
- 其他改进和 bug 修复

<br/>

## <a name="build-14905"></a>内部版本 14905

有关内部版本 14905 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/08/17/announcing-windows-10-insider-preview-build-14905-for-pc-mobile/)。<br/>


### <a name="fixed"></a>固定
- 现在支持可重启系统调用（GH #349、GH #520）
- 现在可正常使用指向以 / 结尾的目录的符号链接 (GH #650)
- 为 /dev/random 实现了 RNDGETENTCNT ioctl
- 实现了 /proc/[pid]/mounts、/proc/[pid]/mountinfo 和 /proc/[pid]/mountstats 文件
- 其他 bug 修复和改进

</br>

## <a name="build-14901"></a>内部版本 14901
Windows 10 周年更新版的第一个预览体验内部版本。

有关内部版本 14901 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/08/11/announcing-windows-10-insider-preview-build-14901-for-pc/)。<br/>


### <a name="fixed"></a>固定
- 修复了尾随斜杠问题
    - `$ mv a/c/ a/b/` 等命令现在可正常运行
- 安装程序现在会提示是否应将 Ubuntu 区域设置指定为 Windows 区域设置
- 对 ns 文件夹的 Procfs 支持
- 添加了 tmpfs、procfs 和 sysfs 文件系统的装入点和卸载点
- 修复 mknod [at] 32 位 ABI 签名
- Unix 套接字已移到调度模型
- 应遵循使用 setsockopt 设置的 INET 套接字接收缓冲区大小
- 实现 MSG_CMSG_CLOEXEC unix 套接字接收消息标志
- Linux 进程 stdin/stdout 管道重定向 (GH #2)
    - 允许在 CMD 中使用竖线分隔 bash -c 命令。  示例：>dir | bash -c "grep foo"
- Bash 现在可以安装在包含多个页面文件的系统上（GH #538、#358）
- 默认的 INET 套接字缓冲区大小应与默认 Ubuntu 安装的大小相匹配
- 将 xattr syscall 与 listxattr 对齐
- 仅返回使用 SIOCGIFCONF 中有效 IPv4 地址的接口
- 修复 ptrace 注入时的信号默认操作
- 实现 /proc/sys/vm/min_free_kbytes
- 在 sigreturn 中还原上下文时使用计算机上下文寄存器值
    - 这解决了某些用户遇到的 java 和 javac 挂起问题
- 实现 /proc/sys/kernel/hostname

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`waitid`<br/>
`epoll_pwait`<br/>

<br/>

## <a name="build-14388-to-windows-10-anniversary-update"></a>Windows 10 周年更新的内部版本 14388
有关内部版本 14388 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/14388wip)。 <br/>

### <a name="fixed"></a>固定
- 修复在 8/2 准备 Windows 10 周年更新时出现的问题
  - 可在我们的[博客](https://blogs.msdn.microsoft.com/wsl/)中找到有关周年更新中的 WSL 的详细信息。

<br/>

## <a name="build-14376"></a>内部版本 14376
有关内部版本 14376 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/06/28/announcing-windows-10-insider-preview-build-14376-for-pc-and-mobile/)。 <br/>

### <a name="fixed"></a>固定
- 删除了一些存在 apt-get 挂起问题的实例 (GH #493)
- 修复了不正确处理空装入点的问题
- 修复了不正确装载 ramdisk 的问题
- 更改 unix 套接字接受行为以支持标志（在 GH #451 中做了部分描述）
- 修复了与网络相关的常见蓝屏问题
- 修复了访问 /proc/[pid]/task 时出现蓝屏的问题 (GH #523)
- 修复了在某些 pty 方案中 CPU 利用率偏高的问题（GH #488、#504）
- 其他 bug 修复和改进

<br/>

## <a name="build-14371"></a>内部版本 14371
有关内部版本 14371 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/06/22/announcing-windows-10-insider-preview-build-14371-for-pc/)。 <br/>

### <a name="fixed"></a>固定
- 更正了使用 ptrace 时 SIGCHLD 和 wait() 出现计时争用的问题
- 更正了当路径包含尾随 / 时出现的某种行为 (GH #432)
- 修复了由于打开子级句柄导致重命名/取消链接失败的问题
- 其他 bug 修复和改进

<br/>

## <a name="build-14366"></a>内部版本 14366
有关内部版本 14366 的一般 Windows 信息，请访问 [Windows 博客](https://blogs.windows.com/windowsexperience/2016/06/14/announcing-windows-10-insider-preview-build-14366-mobile-build-14364/)。 <br/>

### <a name="fixed"></a>固定
- 修复通过符号链接创建文件的问题
-   添加了 Python 的 listxattr (GH 385)
-   其他 bug 修复和改进

### <a name="syscall-support"></a>Syscall 支持
-   下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`listxattr`<br/>
<br/>

## <a name="build-14361"></a>内部版本 14361
有关内部版本 14361 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/wip14361)。 <br/>

### <a name="fixed"></a>固定
- 现在，在 Windows 上的 Ubuntu Bash 中运行时，DrvFs 区分大小写。
  - 用户可在其 /mnt/c 驱动器中保存 case.txt 和 CASE.TXT
  - 只有 Windows 上的 Ubuntu Bash 支持区分大小写。 在 Bash 外部，NTFS 会正确报告文件，但在与 Windows 中的文件交互时，可能会出现意外的行为。
  - 每个卷的根目录（即 /mnt/c）不区分大小写
  - 可在[此处](https://support.microsoft.com/kb/100625)找到有关处理 Windows 中的这些文件的详细信息。
- 大幅增强了 pty/tty 支持。  现在支持 TMUX 等应用程序 (GH #40)
- 修复了不总会创建用户帐户的安装问题
- 优化了命令行参数结构，允许极长的参数列表。 (GH #153)
- 现在可对 DrvFs 中的只读文件执行删除和 chmod
- 修复了一些在断开连接时终端会挂起的实例 (GH #43)
- 现在可在 tty 设备上正常运行 chmod 和 chown
- 允许连接到作为 localhost 的 0.0.0.0 和 :: (GH #388)
- Sendmsg/recvmsg 现在可处理大于 1 的 IO 矢量长度（在 GH #376 中做了部分描述）
- 用户现在可以选择禁用自动生成的 hosts 文件 (GH #398)
- 在安装期间自动将 Linux 区域设置与 NT 区域设置进行匹配 (GH #11)
- 添加了 /proc/sys/vm/swappiness 文件 (GH #306)
- strace 现在会正常退出
- 允许通过 /proc/self/fd 重新打开管道 (GH #222)
- 在 DrvFs 中隐藏 %LOCALAPPDATA%\lxss 下的目录 (GH #270)
- 更好地处理 bash.exe ~。  现在支持类似于“bash ~ -c ls”的命令 (GH #467)
- 现在，在关闭期间，套接字会通知 epoll read 可用 (GH #271)
- lxrun /uninstall 可以更好地删除文件和文件夹
- 更正了 ps -f (GH #246)
- 改善了对 xEmacs 等 x11 应用的支持 (GH #481)
- 更新了初始线程堆栈大小，以匹配默认的 Ubuntu 设置，并正确地向 get_rlimit syscall 报告大小（GH #172、#258）
- 改善了 pico 进程映像名称的报告（例如，用于审核）
- 实现了 df 命令的 /proc/mountinfo
- 修复了子名称 . 和 .. 的符号链接错误代码
- 其他 bug 修复和改进

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`GETTIMER`<br/>
`MKNODAT`<br/>
`RENAMEAT`<br/>
`SENDFILE`<br/>
`SENDFILE64`<br/>
`SYNC_FILE_RANGE`<br/>
<br/>

## <a name="build-14352"></a>内部版本 14352
有关内部版本 14352 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/wip14352)。<br/>


### <a name="fixed"></a>固定
- 修复了不正常下载/创建大型文件的问题。  这应该可以解除 npm 和其他方案的阻碍（GH #3、GH #313）
- 删除了一些存在套接字挂起情况的实例
- 更正了一些 ptrace 错误
- 修复了 WSL 中的问题，允许超过 255 个字符的文件名
- 改善了对非英语字符的支持
- 添加当前 Windows 时区数据并将其设为默认值
- 每个装入点的唯一设备 ID（JRE 修复 – GH #49）
- 更正了路径包含“.”和“..”的问题
- 添加了 Fifo 支持 (GH #71)
- 更新了 resolv.conf 的格式，以匹配本机 Ubuntu 格式
- 一些 procfs 清理
- 为管理员控制台启用了 ping (GH #18)

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`FALLOCATE`<br/>
`EXECVE`<br/>
`LGETXATTR`<br/>
`FGETXATTR`<br/>
<br/>

## <a name="build-14342"></a>内部版本 14342
有关内部版本 14342 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/wip14342)。 <br/>

在 [WSL 博客](https://blogs.msdn.microsoft.com/wsl)中可以找到有关 VolFs 和 DriveFs 的信息。 <br/>

### <a name="fixed"></a>固定
- 修复了 Windows 用户在用户名中包含 Unicode 字符时出现的安装问题
- 现在，在首次运行时，默认会提供“常见问题解答”中的 apt-get update udev 解决方法
- 在 DriveFs (/mnt/<drive>) 目录中启用了符号链接
- 现在可以在 DriveFs 和 VolFs 之间使用符号链接
- 解决了顶级路径分析问题：ls .// 现在可按预期方式工作
- DriveFs 上的 npm install 和 -g 选项现在可正常工作
- 修复了阻止 PHP 服务器启动的问题
- 更新了默认环境值（例如 $PATH），以便与本机 Ubuntu 更匹配
- 在 Windows 中添加了每周维护任务以更新 apt 包缓存
- 修复了 ELF 标头验证的问题，WSL 现在支持所有 Melkor 选项
- Zsh shell 可正常运行
- 现在支持预编译的 Go 二进制文件
- 现已正确本地化首次运行 Bash 时出现的提示
- /proc/meminfo 现在会返回正确的信息
- VFS 现在支持套接字
- /dev 现在装载为 tempfs
- 现在支持 Fifo
- 多核系统现在会在 /proc/cpuinfo 中正确显示
- 其他改进以及首次运行期间下载内容时显示的错误消息
- Syscall 改进和 bug 修复。 下面列出了支持的 syscall。
- 其他 bug 修复和改进

### <a name="known-issues"></a>已知问题
- 在某些情况下， 不会正确解析 DriveFs 上的“..”

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新的或增强的 syscall 列表。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一都受支持。

`FCHOWNAT`<br/>
`GETEUID`<br/>
`GETGID`<br/>
`GETRESUID`<br/>
`GETXATTR`<br/>
`PTRACE`<br/>
`SETGID`<br/>
`SETGROUPS`<br/>
`SETHOSTNAME`<br/>
`SETXATTR`<br/>
<br/>

## <a name="build-14332"></a>内部版本 14332

有关内部版本 14332 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/wip14332)。 <br/>


### <a name="fixed"></a>固定
- 更好地生成 resolv.conf，包括指定 DNS 项的优先级
- 在 /mnt 与非 /mnt 驱动器之间移动文件和目录时出现的问题
- 现在可以使用符号链接创建 Tar 文件。
- 创建实例时会添加默认的 /run/lock 目录
- 更新 /dev/null 以返回正确的统计信息
- 首次运行期间下载内容时出现的其他错误
- Syscall 改进和 bug 修复。 下面列出了支持的 syscall。
- 其他 bug 修复和改进

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的新 syscall。 此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一定都受支持。

`READLINKAT`<br/>
<br/>

## <a name="build-14328"></a>内部版本 14328

有关内部版本 14332 的一般 Windows 信息，请访问 [Windows 博客](https://aka.ms/wip14328)。 <br/>


### <a name="new-features"></a>新功能
* 现在支持 Linux 用户。  安装 Windows 上的 Ubuntu Bash 时会提示创建 Linux 用户。  有关详细信息，请访问 https://aka.ms/wslusers
* 现在，主机名将设置为 Windows 计算机名，而不再是 @localhost
* 有关内部版本 14328 的详细信息，请访问： https://aka.ms/wip14328

### <a name="fixed"></a>固定
* 非 /mnt/<drive> 文件的符号链接改进
    * 现在可正常运行 npm install
    * 现在可以根据[此处](https://xubuntugeek.blogspot.com/2012/09/how-to-install-oracle-jdk-7-manually-in.html)的说明安装 jdk/jre。
    * 已知问题：符号链接不适用于 Windows 装载。  此功能将在以后的内部版本中可用
* 现在会显示 top 和 htop
* 有关某些安装失败的其他错误消息
* Syscall 改进和 bug 修复。  下面列出了支持的 syscall。
* 其他 bug 修复和改进

### <a name="syscall-support"></a>Syscall 支持
下面是在 WSL 中具有某种实现的 syscall 列表。  此列表中的 syscall 至少在一种方案中受支持，但目前其所有参数不一定都受支持。

`ACCEPT`<br/>
`ACCEPT4`<br/>
`ACCESS`<br/>
`ALARM`<br/>
`ARCH_PRCTL`<br/>
`BIND`<br/>
`BRK`<br/>
`CAPGET`<br/>
`CAPSET`<br/>
`CHDIR`<br/>
`CHMOD`<br/>
`CHOWN`<br/>
`CLOCK_GETRES`<br/>
`CLOCK_GETTIME`<br/>
`CLOCK_NANOSLEEP`<br/>
`CLONE`<br/>
`CLOSE`<br/>
`CONNECT`<br/>
`CREAT`<br/>
`DUP`<br/>
`DUP2`<br/>
`DUP3`<br/>
`EPOLL_CREATE`<br/>
`EPOLL_CREATE1`<br/>
`EPOLL_CTL`<br/>
`EPOLL_WAIT`<br/>
`EVENTFD`<br/>
`EVENTFD2`<br/>
`EXECVE`<br/>
`EXIT`<br/>
`EXIT_GROUP`<br/>
`FACCESSAT`<br/>
`FADVISE64`<br/>
`FCHDIR`<br/>
`FCHMOD`<br/>
`FCHMODAT`<br/>
`FCHOWN`<br/>
`FCHOWNAT`<br/>
`FCNTL64`<br/>
`FDATASYNC`<br/>
`FLOCK`<br/>
`FORK`<br/>
`FSETXATTR`<br/>
`FSTAT64`<br/>
`FSTATAT64`<br/>
`FSTATFS64`<br/>
`FSYNC`<br/>
`FTRUNCATE`<br/>
`FTRUNCATE64`<br/>
`FUTEX`<br/>
`GETCPU`<br/>
`GETCWD`<br/>
`GETDENTS`<br/>
`GETDENTS64`<br/>
`GETEGID`<br/>
`GETEGID16`<br/>
`GETEUID`<br/>
`GETEUID16`<br/>
`GETGID`<br/>
`GETGID16`<br/>
`GETGROUPS`<br/>
`GETPEERNAME`<br/>
`GETPGID`<br/>
`GETPGRP`<br/>
`GETPID`<br/>
`GETPPID`<br/>
`GETPRIORITY`<br/>
`GETRESGID`<br/>
`GETRESGID16`<br/>
`GETRESUID`<br/>
`GETRESUID16`<br/>
`GETRLIMIT`<br/>
`GETRUSAGE`<br/>
`GETSID`<br/>
`GETSOCKNAME`<br/>
`GETSOCKOPT`<br/>
`GETTID`<br/>
`GETTIMEOFDAY`<br/>
`GETUID`<br/>
`GETUID16`<br/>
`GETXATTR`<br/>
`GET_ROBUST_LIST`<br/>
`GET_THREAD_AREA`<br/>
`INOTIFY_ADD_WATCH`<br/>
`INOTIFY_INIT`<br/>
`INOTIFY_RM_WATCH`<br/>
`IOCTL`<br/>
`IOPRIO_GET`<br/>
`IOPRIO_SET`<br/>
`KEYCTL`<br/>
`KILL`<br/>
`LCHOWN`<br/>
`LINK`<br/>
`LINKAT`<br/>
`LISTEN`<br/>
`LLSEEK`<br/>
`LSEEK`<br/>
`LSTAT64`<br/>
`MADVISE`<br/>
`MKDIR`<br/>
`MKDIRAT`<br/>
`MKNOD`<br/>
`MLOCK`<br/>
`MMAP`<br/>
`MMAP2`<br/>
`MOUNT`<br/>
`MPROTECT`<br/>
`MREMAP`<br/>
`MSYNC`<br/>
`MUNLOCK`<br/>
`MUNMAP`<br/>
`NANOSLEEP`<br/>
`NEWUNAME`<br/>
`OPEN`<br/>
`OPENAT`<br/>
`PAUSE`<br/>
`PERF_EVENT_OPEN`<br/>
`PERSONALITY`<br/>
`PIPE`<br/>
`PIPE2`<br/>
`POLL`<br/>
`PPOLL`<br/>
`PRCTL`<br/>
`PREAD64`<br/>
`PROCESS_VM_READV`<br/>
`PROCESS_VM_WRITEV`<br/>
`PSELECT6`<br/>
`PTRACE`<br/>
`PWRITE64`<br/>
`READ`<br/>
`READLINK`<br/>
`READV`<br/>
`REBOOT`<br/>
`RECV`<br/>
`RECVFROM`<br/>
`RECVMSG`<br/>
`RENAME`<br/>
`RMDIR`<br/>
`RT_SIGACTION`<br/>
`RT_SIGPENDING`<br/>
`RT_SIGPROCMASK`<br/>
`RT_SIGRETURN`<br/>
`RT_SIGSUSPEND`<br/>
`RT_SIGTIMEDWAIT`<br/>
`SCHED_GETAFFINITY`<br/>
`SCHED_GETPARAM`<br/>
`SCHED_GETSCHEDULER`<br/>
`SCHED_GET_PRIORITY_MAX`<br/>
`SCHED_GET_PRIORITY_MIN`<br/>
`SCHED_SETAFFINITY`<br/>
`SCHED_SETPARAM`<br/>
`SCHED_SETSCHEDULER`<br/>
`SCHED_YIELD`<br/>
`SELECT`<br/>
`SEND`<br/>
`SENDMMSG`<br/>
`SENDMSG`<br/>
`SENDTO`<br/>
`SETDOMAINNAME`<br/>
`SETGID`<br/>
`SETGROUPS`<br/>
`SETHOSTNAME`<br/>
`SETITIMER`<br/>
`SETPGID`<br/>
`SETPRIORITY`<br/>
`SETREGID`<br/>
`SETRESGID`<br/>
`SETRESUID`<br/>
`SETREUID`<br/>
`SETRLIMIT`<br/>
`SETSID`<br/>
`SETSOCKOPT`<br/>
`SETTIMEOFDAY`<br/>
`SETUID`<br/>
`SETXATTR`<br/>
`SET_ROBUST_LIST`<br/>
`SET_THREAD_AREA`<br/>
`SET_TID_ADDRESS`<br/>
`SHUTDOWN`<br/>
`SIGACTION`<br/>
`SIGALTSTACK`<br/>
`SIGPENDING`<br/>
`SIGPROCMASK`<br/>
`SIGRETURN`<br/>
`SIGSUSPEND`<br/>
`SOCKET`<br/>
`SOCKETCALL`<br/>
`SOCKETPAIR`<br/>
`SPLICE`<br/>
`STAT64`<br/>
`STATFS64`<br/>
`SYMLINK`<br/>
`SYMLINKAT`<br/>
`SYNC`<br/>
`SYSINFO`<br/>
`TEE`<br/>
`TGKILL`<br/>
`TIME`<br/>
`TIMERFD_CREATE`<br/>
`TIMERFD_GETTIME`<br/>
`TIMERFD_SETTIME`<br/>
`TIMES`<br/>
`TKILL`<br/>
`TRUNCATE`<br/>
`TRUNCATE64`<br/>
`UMASK`<br/>
`UMOUNT`<br/>
`UMOUNT2`<br/>
`UNLINK`<br/>
`UNLINKAT`<br/>
`UNSHARE`<br/>
`UTIME`<br/>
`UTIMENSAT`<br/>
`UTIMES`<br/>
`VFORK`<br/>
`WAIT4`<br/>
`WAITPID`<br/>
`WRITE`<br/>
`WRITEV`<br/>
