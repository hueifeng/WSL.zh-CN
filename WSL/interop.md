---
title: Windows 与 Linux 的互操作性
description: 介绍 Windows 与适用于 Linux 的 Windows 子系统上运行的 Linux 分发版之间的互操作性。
ms.date: 05/12/2020
ms.topic: article
ms.localizationpriority: high
ms.openlocfilehash: 2a9b6c8ac65fe28e029ada7f86475c44220a93fe
ms.sourcegitcommit: cb8a61e7de08b1c18622fc78bc5dfa38786e921a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663130"
---
# <a name="windows-interoperability-with-linux"></a>Windows 与 Linux 的互操作性

适用于 Linux 的 Windows 子系统 (WSL) 正在持续改进 Windows 与 Linux 之间的集成。  您可以：

* 从 Linux 命令行（即 Ubuntu）运行 Windows 工具（即 notepad.exe）。
* 从 Windows 命令行（即 PowerShell）运行 Linux 工具（即 grep）。
* 在 Windows 与 Windows 之间共享环境变量。 （版本 17063+）

> [!NOTE]
> 如果运行的是创意者更新（2017 年 10 月的版本16299）或周年更新（2016 年 8 月的版本 14393），请跳转到 [Windows 10 的早期版本](#earlier-versions-of-windows-10)。

## <a name="run-linux-tools-from-a-windows-command-line"></a>从 Windows 命令行运行 Linux 工具

使用 `wsl <command>`（或 `wsl.exe <command>`）从 Windows 命令提示符 (CMD) 或 PowerShell 运行 Linux 二进制文件。

例如：

```powershell
C:\temp> wsl ls -la
<- contents of C:\temp ->
```

以这种方式调用二进制文件：

* 使用当前 CMD 或 PowerShell 提示符中提到的同一工作目录。
* 以 WSL 默认用户的身份运行。
* 拥有与调用方进程和终端相同的 Windows 管理权限。

`wsl`（或 `wsl.exe`）后面的 Linux 命令的处理方式与 WSL 中运行的任何命令的处理方式类似。  可以执行 sudo、管道处理和文件重定向等操作。

使用 sudo 更新默认 Linux 分发版的示例：

```powershell
C:\temp> wsl sudo apt-get update
```

运行此命令后，将会列出默认的 Linux 分发版用户名，并将要求你输入密码。 正确输入密码后，分发版将下载更新。

## <a name="mixing-linux-and-windows-commands"></a>混合 Linux 和 Windows 命令

下面是几个使用 PowerShell 混合 Linux 和 Windows 命令的示例。

若要使用 Linux 命令 `ls -la` 列出文件，并使用 PowerShell 命令 `findstr` 来筛选包含“git”的单词的结果，请组合这些命令：

```powershell
wsl ls -la | findstr "git"
```

若要使用 PowerShell 命令 `dir` 列出文件，并使用 Linux 命令 `grep` 来筛选包含“git”的单词的结果，请组合这些命令：

```powershell
C:\temp> dir | wsl grep git
```

若要使用 Linux 命令 `ls -la` 列出文件，并使用 PowerShell 命令 `> out.txt` 将该列表输出到名为“out.txt”的文本文件，请组合这些命令：

```powershell
C:\temp> wsl ls -la > out.txt
```

传入 `wsl.exe` 的命令将按原样转发到 WSL 进程。  文件路径必须以 WSL 格式指定。

若要使用 Linux 命令 `ls -la` 列出 `/proc/cpuinfo` Linux 文件系统路径中的文件，请使用 PowerShell：

```powershell
C:\temp> wsl ls -la /proc/cpuinfo
```

若要使用 Linux 命令 `ls -la` 列出 `C:\Program Files` Windows 文件系统路径中的文件，请使用 PowerShell：

```powershell
C:\temp> wsl ls -la "/mnt/c/Program Files"
```

## <a name="run-windows-tools-from-linux"></a>从 Linux 运行 Windows 工具

WSL 可以使用 `[tool-name].exe` 直接从 WSL 命令行运行 Windows 工具。  例如，`notepad.exe`。

<!-- Craig - could you help add a section with an example here to explain this scenario: "To access your Linux files using a Windows tool, use `\\wsl$\<distroName>\'` as the file path." Currently it I can just enter `notepad.exe foo.txt` and it seems to work fine, so explaining a situation where the file path is needed would be helpful. -->

以这种方式运行的应用程序具有以下属性：

* 按 WSL 命令提示保留工作目录（大部分情况下是这样 -- 下面所述的情况除外）。
* 拥有与 WSL 进程相同的权限。
* 以活动 Windows 用户的身份运行。
* 显示在 Windows 任务管理器中，就如同直接从 CMD 提示符执行的一样。

在 WSL 中运行的 Windows 可执行文件的处理方式类似于本机 Linux 可执行文件 - 管道处理、重定向，甚至后台处理都可按预期方式工作。

若要运行 Windows 工具 `ipconfig.exe`，请使用 Linux 工具 `grep` 筛选“IPv4”结果，并使用 Linux 工具 `cut` 删除列字段，请从 Linux 分发版（例如 Ubuntu）输入：

```bash
ipconfig.exe | grep IPv4 | cut -d: -f2
```

让我们尝试一个混合使用 Windows 和 Linux 命令的示例。 打开 Linux 分发版（即 Ubuntu）并创建文本文件：`touch foo.txt`。 现在使用 Linux 命令 `ls -la` 列出直接文件及其创建详细信息，并使用 Windows PowerShell 工具 `findstr.exe` 来筛选结果，以便仅在结果中显示 `foo.txt` 文件：

```bash
ls -la | findstr.exe foo.txt
```

Windows 工具必须包含文件扩展名，匹配文件大小写，并且可执行。  包含批处理脚本的不可执行文件。  `dir` 等 CMD 本机命令可与 `cmd.exe /C` 命令一起运行。

例如，通过输入以下命令列出 Windows 文件系统 C:\ 目录的内容：

```bash
cmd.exe /C dir
```

或者使用 `ping` 命令将回显请求发送到 microsoft.com 网站：

```bash
ping.exe www.microsoft.com
```

参数将按原样传递到 Windows 二进制文件。 例如，以下命令将通过 `notepad.exe` 打开 `C:\temp\foo.txt`：

```bash
notepad.exe "C:\temp\foo.txt"
```

以下命令也会起作用：

```bash
notepad.exe C:\\temp\\foo.txt
```

## <a name="share-environment-variables-between-windows-and-wsl"></a>在 Windows 与 WSL 之间共享环境变量

WSL 和 Windows 共享一个特殊环境变量 `WSLENV`（为了桥接 Windows 和 WSL 上运行的 Linux 分发版而创建）。

`WSLENV` 变量的属性：

* 它是共享的；它同时在 Windows 和 WSL 环境中存在。
* 它是要在 Windows 与 WSL 之间共享的环境变量列表。
* 它可以设置环境变量的格式，使其能够在 Windows 和 WSL 中正常运行。
* 它可以帮助 WSL 和 Win32 之间的流。

> [!NOTE]
> 在 17063 以前，只有 WSL 可访问的 Windows 环境变量是 `PATH`（因此可以从 WSL 下启动 Win32 可执行文件）。 从 17063 开始，`WSLENV` 开始受支持。

## <a name="wslenv-flags"></a>WSLENV 标志

`WSLENV` 中有四个标志可以影响该环境变量的转换方式。

`WSLENV` 标志：

* `/p` - 在 WSL/Linux 样式路径与 Win32 路径之间转换路径。
* `/l` - 指示环境变量是路径列表。
* `/u` - 指示仅当从 Win32 运行 WSL 时，才应包含此环境变量。
* `/w` - 指示仅当从 WSL 运行 Win32 时，才应包含此环境变量。

可按需组合标志。

[阅读有关 WSLENV 的详细信息](https://devblogs.microsoft.com/commandline/share-environment-vars-between-wsl-and-windows/)，包括将 WSLENV 的值设置为其他预定义环境变量串联的常见问题解答和示例，每个示例都带有一个斜杠后缀，斜杠后跟标志，用于指定应如何转换值以及如何使用脚本传递变量。 本文还提供使用 [ 编程语言](https://golang.org/)设置开发环境的示例，该示例配置为在 WSL 和 Win32 之间共享 GOPATH。

## <a name="disable-interoperability"></a>禁用互操作性

用户可以使用 root 身份运行以下命令，禁用针对单个 WSL 会话运行 Windows 工具的功能：

```bash
echo 0 > /proc/sys/fs/binfmt_misc/WSLInterop
```

若要重新启用 Windows 二进制文件，请退出所有 WSL 会话并重新运行 bash.exe，或者以 root 身份运行以下命令：

```bash
echo 1 > /proc/sys/fs/binfmt_misc/WSLInterop
```

每次切换 WSL 会话后，禁用互操作的结果不会持久保留 -- 启动新会话后，会再次启用互操作。

## <a name="earlier-versions-of-windows-10"></a>Windows 10 的早期版本

对于早期的 Windows 10 版本，互操作性命令有一些不同之处。 如果运行的是创意者更新（2017 年10 月的版本 16299）或周年更新（2016 年 8 月的版本 14393），则建议你[更新到最新的 Windows 版本](ms-settings:windowsupdate)，但如果无法执行此操作，请了解下面概述的一些互操作差异。

摘要：

* `bash.exe` 已替换为 `wsl.exe`。
* 在 `wsl.exe` 中不需要指定用于运行单个命令的 `-c` 选项。
* Windows 路径包含在 WSL `$PATH` 中。
* 禁用互操作的过程未有变化。

可以从 Windows 命令提示或 PowerShell 运行 Linux 命令，但对于早期 Windows 版本，可能需要使用 `bash` 命令。 例如：

```powershell
C:\temp> bash -c "ls -la"
```

可按预期方式执行输入、管道处理和文件重定向等操作。

传入 `bash -c` 的 WSL 命令将按原样转发到 WSL 进程。  必须以 WSL 格式指定文件路径，并且必须谨慎转义相关字符。 例如：

```console
C:\temp> bash -c "ls -la /proc/cpuinfo"
```

或...

```powershell
C:\temp> bash -c "ls -la \"/mnt/c/Program Files\""
```

从早期的 Windows 10 版本中的 WSL 分发版调用 Windows 工具时，需要指定目录路径。 例如，在 WSL 命令行中，输入：

```bash
/mnt/c/Windows/System32/notepad.exe
```

在 WSL 中，这些可执行文件的处理方式类似于本机 Linux 可执行文件。  这意味着，可按预期方式将目录添加到 Linux 路径，以及在命令之间进行管道处理。  例如：

```bash
export PATH=$PATH:/mnt/c/Windows/System32
```
或

```bash
ipconfig.exe | grep IPv4 | cut -d: -f2
```

Windows 二进制文件必须包含文件扩展名，匹配文件大小写，并且可执行。  不可执行文件（包括批处理脚本）和 `dir` 等命令可与 `/mnt/c/Windows/System32/cmd.exe /C` 命令一起运行。 例如：

```bash
/mnt/c/Windows/System32/cmd.exe /C dir
```

## <a name="additional-resources"></a>其他资源

* [2016 年有关互操作性的 WSL 博客文章](https://blogs.msdn.microsoft.com/wsl/2016/10/19/windows-and-ubuntu-interoperability/)
