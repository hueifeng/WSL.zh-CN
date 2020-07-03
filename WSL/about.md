---
title: 适用于 Linux 的 Windows 子系统概述
description: 了解适用于 Linux 的 Windows 子系统及其不同版本和使用方式。
keywords: BashOnWindows, bash, wsl, windows, windows 子系统, windowssubsystem, gnu, linux
ms.date: 05/12/2020
ms.topic: article
ms.assetid: 3cefe0db-7616-4848-a2b6-9296746a178b
ms.localizationpriority: high
ms.openlocfilehash: 75da6389beec4af7ac684ec7ee2ef31431e14071
ms.sourcegitcommit: f1b049a1276782d4f2754f46a8d2025b598a0784
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85336060"
---
# <a name="what-is-the-windows-subsystem-for-linux"></a>什么是适用于 Linux 的 Windows 子系统？

适用于 Linux 的 Windows 子系统可让开发人员按原样运行 GNU/Linux 环境 - 包括大多数命令行工具、实用工具和应用程序 - 且不会产生传统虚拟机或双启动设置开销。

您可以：

* [在 Microsoft Store](https://aka.ms/wslstore) 中选择你偏好的 GNU/Linux 分发版。
* 运行常用的命令行软件工具（例如 `grep`、`sed`、`awk`）或其他 ELF-64 二进制文件。
* 运行 Bash shell 脚本和 GNU/Linux 命令行应用程序，包括：  
    * 工具：vim、emacs、tmux
    * 语言：[NodeJS](https://docs.microsoft.com/windows/nodejs/setup-on-wsl2)、Javascript、[Python](https://docs.microsoft.com/windows/python/web-frameworks)、Ruby、C/ C++、C# 与 F#、Rust、Go 等。
    * 服务：SSHD、MySQL、Apache、lighttpd、[MongoDB](https://docs.microsoft.com/windows/nodejs/databases)、[PostgreSQL](https://docs.microsoft.com/windows/python/databases)。
* 使用自己的 GNU/Linux 分发包管理器安装其他软件。
* 使用类似于 Unix 的命令行 shell 调用 Windows 应用程序。
* 在 Windows 上调用 GNU/Linux 应用程序。

## <a name="what-is-wsl-2"></a>什么是 WSL 2？

WSL 2 是适用于 Linux 的 Windows 子系统体系结构的一个新版本，它支持适用于 Linux 的 Windows 子系统在 Windows 上运行 ELF64 Linux 二进制文件。 它的主要目标是**提高文件系统性能**，以及添加**完全的系统调用兼容性**。

这一新的体系结构改变了这些 Linux 二进制文件与Windows 和计算机硬件进行交互的方式，但仍然提供与 WSL 1（当前广泛可用的版本）中相同的用户体验。

单个 Linux 分发版可以在 WSL 1 或 WSL 2 体系结构中运行。 每个分发版可随时升级或降级，并且你可以并行运行 WSL 1 和 WSL 2 分发版。 WSL 2 使用全新的体系结构，该体系结构受益于运行真正的 Linux 内核。

## <a name="next-steps"></a>后续步骤

* [安装 WSL 1 并更新到 WSL 2](./install-win10.md)

* [比较 WSL 2 和 WSL 1](./compare-versions.md)

* [为新的 Linux 分发版创建用户帐户和密码](./user-support.md)

* [阅读常见问题解答](./faq.md)

* [阅读有关 WSL 2 的常见问题解答](./wsl2-faq.md)

* [疑难解答](./troubleshooting.md)

* [运行用于 Windows 和 Linux 之间的互操作的命令](./interop.md)

* [运行启动命令和配置](./wsl-config.md)

* [设置文件权限](./file-permissions.md)

* [设置适用于企业的 WSL](./enterprise.md)

* [引用 WSL 命令](./reference.md)

* [生成自定义分发版](./build-custom-distro.md)

* [阅读 WSL 发行说明](./release-notes.md)
