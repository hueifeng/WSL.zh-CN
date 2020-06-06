---
title: 在适用于 Linux 的 Windows 子系统上开始使用 Git
description: 了解如何在适用于 Linux 的 Windows 子系统上设置用于版本控制的 Git。
keywords: wsl，windows，windowssubsystem，gnu，linux，bash，git，github，版本控制
ms.date: 06/04/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 94166371fc0928d6be3b3cfd6cb595c6fac76608
ms.sourcegitcommit: d95bdbc2fea991ba14a4c9ec53ee0ec19d6bbdb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84457789"
---
# <a name="get-started-using-git-on-windows-subsystem-for-linux"></a>在适用于 Linux 的 Windows 子系统上开始使用 Git

Git 是最常用的版本控制系统。 使用 Git，你可以跟踪对文件所做的更改，以便记录已完成的操作，并且可以根据需要恢复到早期版本的文件。 Git 还可简化协作，使多个用户可以将更改合并到一个源。

## <a name="git-can-be-installed-on-windows-and-on-wsl"></a>可以在 Windows 和 WSL 上安装 Git。

需要注意的一个重要事项：启用 WSL 并安装 Linux 分发版时，将安装新的文件系统，与 Windows NTFS C：\ 分离计算机上的驱动器。 在 Linux 中，驱动器没有获得字母。 它们被提供装入点。 文件系统的根 `/` 是根分区（或文件夹）的装入点（对于 WSL）。 并非所有内容 `/` 都在同一驱动器上。 例如，在我的便携式计算机上，我安装了两个版本的 Ubuntu （20.04 和18.01）以及 Debian。 如果打开这些分发，请选择包含命令的根目录 `cd ~` ，然后输入命令 `explorer.exe .` ，Windows 文件资源管理器将打开并显示该分发的目录路径。

| Linux 发行版 | 访问主文件夹的 Windows 路径 |
| ----------- | ----------- |
| Ubuntu 20.04 | `\\wsl$\Ubuntu-20.04\home\username` |
| Ubuntu 18.01 | `\\wsl$\Ubuntu-18.04\home\username` |
| Debian | `\\wsl$\Debian\home\username` |
| Windows PowerShell | `C:\Users\username` |

> [!TIP]
> 如果要从 WSL 分发命令行（而不是）访问 Windows 文件目录，请 `C:\Users\username` 使用访问该目录， `/mnt/c/Users/username` 因为 Linux 发行版会将 Windows 文件系统视为已装入驱动器。

你将需要在你打算用于的每个文件系统上安装 Git。

![按发行版显示 Git 版本](../media/git-versions.gif)

## <a name="installing-git"></a>安装 Git

Git 已随大多数适用于 Linux 的 Windows 子系统一起安装，但是，你可能想要更新到最新版本，并且你将需要设置 git 配置文件。

若要安装 Git，请参阅[适用于 Linux 的 Git 下载](https://git-scm.com/download/linux)站点。 每个 Linux 分发都有自己的包管理器和安装命令。 例如，若要在 Alpine 分发上安装 Git，请使用： `apk add git` 。 如果尚未[安装 Git For Windows](https://git-scm.com/download/win) ，则还可能需要安装。

## <a name="git-config-file-setup"></a>Git 配置文件设置

若要设置 Git 配置文件，请打开所使用的分发的命令行，并输入：， `git config --global user.name "Your Name"` 然后按 `git config --global user.email "youremail@domain.com"` 。 使用创建 Git 帐户时所用的名称和电子邮件地址替换报价中的内容。

> [!TIP]
> 如果你还没有 Git 帐户，则可以[在 GitHub 上注册一个帐户](https://github.com/join)。 如果以前从未使用过 Git，则 [GitHub 指南](https://guides.github.com/)可以帮助入门。 如果需要编辑 git 配置，则可以使用内置文本编辑器（如 nano：`nano ~/.gitconfig`）来执行此操作。

建议你[通过双因素身份验证（2FA）保护你的帐户](https://help.github.com/en/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)。

## <a name="git-credential-manager-setup"></a>Git 凭据管理器安装程序

使用 git 凭据管理器，你可以对远程 Git 服务器进行身份验证，即使你具有双因素身份验证等复杂的身份验证模式、Azure Active Directory 或使用需要 SSH 密钥密码才能进行每个 Git 推送的 SSH 远程 Url。 Git 凭据管理器集成在 GitHub 等服务的身份验证流程中，并且在你通过托管提供程序身份验证后就会请求新的身份验证令牌。 然后，它会将令牌安全地存储在[Windows 凭据管理器](https://support.microsoft.com/help/4026814/windows-accessing-credential-manager)中。 首次之后，可以使用 git 与托管提供程序通信，而无需重新进行身份验证。 它将只需访问 Windows 凭据管理器中的令牌。

若要设置 Git 凭据管理器以便与 WSL 分发版配合使用，请打开分发版，然后输入以下命令：

```Bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"
```

现在，在 WSL 分发版中执行的任何 git 操作都将使用凭据管理器。 如果已为主机缓存凭据，那么它会从凭据管理器访问这些凭据。 如果尚未缓存凭据，你将收到一个请求凭据的对话响应，即使你处于 Linux 控制台中也是如此。

## <a name="adding-a-git-ignore-file"></a>添加 Git Ignore 文件

建议将[.gitignore 文件](https://help.github.com/en/articles/ignoring-files)添加到项目。 GitHub 提供了[一个有用的 .gitignore 模板集合](https://github.com/github/gitignore)，其中包含根据用例组织的建议的 .gitignore 文件设置。

如果选择[使用 GitHub 网站创建新的](https://help.github.com/articles/create-a-repo)存储库，则可以使用以下复选框来初始化存储库，其中包含一个自述文件、一个针对特定项目类型的 .gitignore 文件，以及用于添加许可证（如果需要）的选项。

## <a name="git-and-vs-code"></a>Git 和 VS Code

Visual Studio Code 附带了对 Git 的内置支持，其中包括一个 "源代码管理" 选项卡，该选项卡将显示你所做的更改并处理各种 git 命令。 详细了解[VS Code 的 Git 支持](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)。

## <a name="git-line-endings"></a>Git 行尾

如果在 Windows、WSL 或容器之间使用相同的存储库文件夹，请确保设置一致的行尾。

由于 Windows 和 Linux 使用不同的默认行尾，Git 可能会报告大量已修改的文件，这些文件与行尾之间没有任何差别。 若要防止发生这种情况，可以 `.gitattributes` 在 Windows 端使用文件或全局禁用行尾转换。 [有关解决 Git 行结束问题的 VS Code](https://code.visualstudio.com/docs/remote/troubleshooting#_resolving-git-line-ending-issues-in-containers-resulting-in-many-modified-files)，请参阅此文档。

## <a name="additional-resources"></a>其他资源

* [WSL & VS Code](./wsl-vscode.md)
* [GitHub 学习实验室：在线课程](https://lab.github.com/)
* [Git 可视化工具](http://git-school.github.io/visualizing-git/)
* [Git 工具-凭据存储](https://git-scm.com/book/it/v2/Git-Tools-Credential-Storage)
