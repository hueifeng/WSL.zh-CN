---
title: 在适用于 Linux 的 Windows 子系统上开始使用 Git
description: 了解如何在适用于 Linux 的 Windows 子系统上设置用于版本控制的 Git。
keywords: wsl，windows，windowssubsystem，gnu，linux，bash，git，github，版本控制
ms.date: 06/04/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 550355ea77c97d68130c8d85e9aef2a6b49ffe63
ms.sourcegitcommit: eaceda3589b9bd777e0fead5ef33bb16060a55d2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84978240"
---
# <a name="get-started-using-git-on-windows-subsystem-for-linux"></a><span data-ttu-id="ec151-104">在适用于 Linux 的 Windows 子系统上开始使用 Git</span><span class="sxs-lookup"><span data-stu-id="ec151-104">Get started using Git on Windows Subsystem for Linux</span></span>

<span data-ttu-id="ec151-105">Git 是最常用的版本控制系统。</span><span class="sxs-lookup"><span data-stu-id="ec151-105">Git is the most commonly used version control system.</span></span> <span data-ttu-id="ec151-106">使用 Git，你可以跟踪对文件所做的更改，以便记录已完成的操作，并且可以根据需要恢复到早期版本的文件。</span><span class="sxs-lookup"><span data-stu-id="ec151-106">With Git, you can track changes you make to files, so you have a record of what has been done, and have the ability to revert to earlier versions of the files if needed.</span></span> <span data-ttu-id="ec151-107">Git 还可简化协作，使多个用户可以将更改合并到一个源。</span><span class="sxs-lookup"><span data-stu-id="ec151-107">Git also makes collaboration easier, allowing changes by multiple people to all be merged into one source.</span></span>

## <a name="git-can-be-installed-on-windows-and-on-wsl"></a><span data-ttu-id="ec151-108">可以在 Windows 和 WSL 上安装 Git。</span><span class="sxs-lookup"><span data-stu-id="ec151-108">Git can be installed on Windows AND on WSL</span></span>

<span data-ttu-id="ec151-109">需要注意的一个重要事项：启用 WSL 并安装 Linux 分发版时，将安装新的文件系统，与 Windows NTFS C：\ 分离计算机上的驱动器。</span><span class="sxs-lookup"><span data-stu-id="ec151-109">An important consideration: when you enable WSL and install a Linux distribution, you are installing a new file system, separated from the Windows NTFS C:\ drive on your machine.</span></span> <span data-ttu-id="ec151-110">在 Linux 中，驱动器没有获得字母。</span><span class="sxs-lookup"><span data-stu-id="ec151-110">In Linux, drives are not given letters.</span></span> <span data-ttu-id="ec151-111">它们被提供装入点。</span><span class="sxs-lookup"><span data-stu-id="ec151-111">They are given mount points.</span></span> <span data-ttu-id="ec151-112">文件系统的根 `/` 是根分区（或文件夹）的装入点（对于 WSL）。</span><span class="sxs-lookup"><span data-stu-id="ec151-112">The root of your file system `/` is the mount point of your root partition, or folder, in the case of WSL.</span></span> <span data-ttu-id="ec151-113">并非所有内容 `/` 都在同一驱动器上。</span><span class="sxs-lookup"><span data-stu-id="ec151-113">Not everything under `/` is the same drive.</span></span> <span data-ttu-id="ec151-114">例如，在我的便携式计算机上，我安装了两个版本的 Ubuntu （20.04 和18.04）以及 Debian。</span><span class="sxs-lookup"><span data-stu-id="ec151-114">For example, on my laptop, I've installed two version of Ubuntu (20.04 and 18.04), as well as Debian.</span></span> <span data-ttu-id="ec151-115">如果打开这些分发，请选择包含命令的根目录 `cd ~` ，然后输入命令 `explorer.exe .` ，Windows 文件资源管理器将打开并显示该分发的目录路径。</span><span class="sxs-lookup"><span data-stu-id="ec151-115">If I open those distributions, select the root directory with the command `cd ~`, and then enter the command `explorer.exe .`, Windows File Explorer will open and show me the directory path for that distribution.</span></span>

| <span data-ttu-id="ec151-116">Linux 发行版</span><span class="sxs-lookup"><span data-stu-id="ec151-116">Linux distro</span></span> | <span data-ttu-id="ec151-117">访问主文件夹的 Windows 路径</span><span class="sxs-lookup"><span data-stu-id="ec151-117">Windows Path to access home folder</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="ec151-118">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="ec151-118">Ubuntu 20.04</span></span> | `\\wsl$\Ubuntu-20.04\home\username` |
| <span data-ttu-id="ec151-119">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ec151-119">Ubuntu 18.04</span></span> | `\\wsl$\Ubuntu-18.04\home\username` |
| <span data-ttu-id="ec151-120">Debian</span><span class="sxs-lookup"><span data-stu-id="ec151-120">Debian</span></span> | `\\wsl$\Debian\home\username` |
| <span data-ttu-id="ec151-121">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec151-121">Windows PowerShell</span></span> | `C:\Users\username` |

> [!TIP]
> <span data-ttu-id="ec151-122">如果要从 WSL 分发命令行（而不是）访问 Windows 文件目录，请 `C:\Users\username` 使用访问该目录， `/mnt/c/Users/username` 因为 Linux 发行版会将 Windows 文件系统视为已装入驱动器。</span><span class="sxs-lookup"><span data-stu-id="ec151-122">If you are seeking to access the Windows file directory from your WSL distribution command line, instead of `C:\Users\username`, the directory would be accessed using `/mnt/c/Users/username`, because the Linux distribution views your Windows file system as a mounted drive.</span></span>

<span data-ttu-id="ec151-123">你将需要在你打算用于的每个文件系统上安装 Git。</span><span class="sxs-lookup"><span data-stu-id="ec151-123">You will need to install Git on each file system that you intend to use it with.</span></span>

![按发行版显示 Git 版本](../media/git-versions.gif)

## <a name="installing-git"></a><span data-ttu-id="ec151-125">安装 Git</span><span class="sxs-lookup"><span data-stu-id="ec151-125">Installing Git</span></span>

<span data-ttu-id="ec151-126">Git 已安装了大多数适用于 Linux 分发的 Windows 子系统，但你可能想要更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="ec151-126">Git comes already installed with most of the Windows Subsystem for Linux distributions, however, you may want to update to the latest version.</span></span> <span data-ttu-id="ec151-127">还需要设置 git 配置文件。</span><span class="sxs-lookup"><span data-stu-id="ec151-127">You also will need to set up your git config file.</span></span>

<span data-ttu-id="ec151-128">若要安装 Git，请参阅[适用于 Linux 的 Git 下载](https://git-scm.com/download/linux)站点。</span><span class="sxs-lookup"><span data-stu-id="ec151-128">To install Git, see the [Git Download for Linux](https://git-scm.com/download/linux) site.</span></span> <span data-ttu-id="ec151-129">每个 Linux 分发都有自己的包管理器和安装命令。</span><span class="sxs-lookup"><span data-stu-id="ec151-129">Each Linux distribution has their own package manager and install command.</span></span>

<span data-ttu-id="ec151-130">对于 Ubuntu/Debian 中的最新稳定 GIt 版本，请输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec151-130">For the latest stable GIt version in Ubuntu/Debian, enter the command:</span></span>

```bash
sudo apt-get install git
```

> [!NOTE]
> <span data-ttu-id="ec151-131">如果尚未[安装 Git For Windows](https://git-scm.com/download/win) ，则还可能需要安装。</span><span class="sxs-lookup"><span data-stu-id="ec151-131">You also may want to [install Git for Windows](https://git-scm.com/download/win) if you haven't already.</span></span>

## <a name="git-config-file-setup"></a><span data-ttu-id="ec151-132">Git 配置文件设置</span><span class="sxs-lookup"><span data-stu-id="ec151-132">Git config file setup</span></span>

<span data-ttu-id="ec151-133">若要设置 Git 配置文件，请打开正在处理的分发的命令行，并使用以下命令设置你的名称（将 "名称" 替换为你的 Git 用户名）：</span><span class="sxs-lookup"><span data-stu-id="ec151-133">To set up your Git config file, open a command line for the distribution you're working in and set your name with this command (replacing "Your Name" with your Git username):</span></span>

```bash
 `git config --global user.name "Your Name"`
```

<span data-ttu-id="ec151-134">使用此命令设置电子邮件（将 " youremail@domain.com " 替换为你在 Git 帐户中使用的电子邮件）：</span><span class="sxs-lookup"><span data-stu-id="ec151-134">Set your email with this command (replacing "youremail@domain.com" with the email you use on your Git account):</span></span>

```bash
`git config --global user.email "youremail@domain.com"`
```

> [!TIP]
> <span data-ttu-id="ec151-135">如果你还没有 Git 帐户，则可以[在 GitHub 上注册一个帐户](https://github.com/join)。</span><span class="sxs-lookup"><span data-stu-id="ec151-135">If you don't yet have a Git account, you can [sign-up for one on GitHub](https://github.com/join).</span></span> <span data-ttu-id="ec151-136">如果以前从未使用过 Git，则 [GitHub 指南](https://guides.github.com/)可以帮助入门。</span><span class="sxs-lookup"><span data-stu-id="ec151-136">If you've never worked with Git before, [GitHub Guides](https://guides.github.com/) can help you get started.</span></span> <span data-ttu-id="ec151-137">如果需要编辑 git 配置，则可以使用内置文本编辑器（如 nano：`nano ~/.gitconfig`）来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ec151-137">If you need to edit your git config, you can do so with a built-in text editor like nano: `nano ~/.gitconfig`.</span></span>

<span data-ttu-id="ec151-138">建议你[通过双因素身份验证（2FA）保护你的帐户](https://help.github.com/en/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)。</span><span class="sxs-lookup"><span data-stu-id="ec151-138">We recommend that you [secure your account with two-factor authentication (2FA)](https://help.github.com/en/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa).</span></span>

## <a name="git-credential-manager-setup"></a><span data-ttu-id="ec151-139">Git 凭据管理器安装程序</span><span class="sxs-lookup"><span data-stu-id="ec151-139">Git Credential Manager setup</span></span>

<span data-ttu-id="ec151-140">使用 git 凭据管理器，你可以对远程 Git 服务器进行身份验证，即使你具有双因素身份验证等复杂的身份验证模式、Azure Active Directory 或使用需要 SSH 密钥密码才能进行每个 Git 推送的 SSH 远程 Url。</span><span class="sxs-lookup"><span data-stu-id="ec151-140">Git Credential Manager enables you to authenticate a remote Git server, even if you have a complex authentication pattern like two-factor authentication, Azure Active Directory, or using SSH remote URLs that require an SSH key password for every git push.</span></span> <span data-ttu-id="ec151-141">Git 凭据管理器集成在 GitHub 等服务的身份验证流程中，并且在你通过托管提供程序身份验证后就会请求新的身份验证令牌。</span><span class="sxs-lookup"><span data-stu-id="ec151-141">Git Credential Manager integrates into the authentication flow for services like GitHub and, once you're authenticated to your hosting provider, requests a new authentication token.</span></span> <span data-ttu-id="ec151-142">然后，它会将令牌安全地存储在[Windows 凭据管理器](https://support.microsoft.com/help/4026814/windows-accessing-credential-manager)中。</span><span class="sxs-lookup"><span data-stu-id="ec151-142">It then stores the token securely in the [Windows Credential Manager](https://support.microsoft.com/help/4026814/windows-accessing-credential-manager).</span></span> <span data-ttu-id="ec151-143">首次之后，可以使用 git 与托管提供程序通信，而无需重新进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="ec151-143">After the first time, you can use git to talk to your hosting provider without needing to re-authenticate.</span></span> <span data-ttu-id="ec151-144">它将只需访问 Windows 凭据管理器中的令牌。</span><span class="sxs-lookup"><span data-stu-id="ec151-144">It will just access the token in the Windows Credential Manager.</span></span>

<span data-ttu-id="ec151-145">若要设置 Git 凭据管理器以便与 WSL 分发版配合使用，请打开分发版，然后输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="ec151-145">To set up Git Credential Manager for use with a WSL distribution, open your distribution and enter this command:</span></span>

```Bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"
```

<span data-ttu-id="ec151-146">现在，在 WSL 分发版中执行的任何 git 操作都将使用凭据管理器。</span><span class="sxs-lookup"><span data-stu-id="ec151-146">Now any git operation you perform within your WSL distribution will use the credential manager.</span></span> <span data-ttu-id="ec151-147">如果已为主机缓存凭据，那么它会从凭据管理器访问这些凭据。</span><span class="sxs-lookup"><span data-stu-id="ec151-147">If you already have credentials cached for a host, it will access them from the credential manager.</span></span> <span data-ttu-id="ec151-148">如果尚未缓存凭据，你将收到一个请求凭据的对话响应，即使你处于 Linux 控制台中也是如此。</span><span class="sxs-lookup"><span data-stu-id="ec151-148">If not, you'll receive a dialog response requesting your credentials, even if you're in a Linux console.</span></span>

> [!NOTE]
> <span data-ttu-id="ec151-149">如果使用 GPG 密钥进行代码签名安全，则可能需要[将 GPG 密钥与 GitHub 电子邮件相关联](https://help.github.com/en/github/authenticating-to-github/associating-an-email-with-your-gpg-key)。</span><span class="sxs-lookup"><span data-stu-id="ec151-149">If you are using a GPG key for code signing security, you may need to [associate your GPG key with your GitHub email](https://help.github.com/en/github/authenticating-to-github/associating-an-email-with-your-gpg-key).</span></span>

## <a name="adding-a-git-ignore-file"></a><span data-ttu-id="ec151-150">添加 Git Ignore 文件</span><span class="sxs-lookup"><span data-stu-id="ec151-150">Adding a Git Ignore file</span></span>

<span data-ttu-id="ec151-151">建议将[.gitignore 文件](https://help.github.com/en/articles/ignoring-files)添加到项目。</span><span class="sxs-lookup"><span data-stu-id="ec151-151">We recommend adding a [.gitignore file](https://help.github.com/en/articles/ignoring-files) to your projects.</span></span> <span data-ttu-id="ec151-152">GitHub 提供了[一个有用的 .gitignore 模板集合](https://github.com/github/gitignore)，其中包含根据用例组织的建议的 .gitignore 文件设置。</span><span class="sxs-lookup"><span data-stu-id="ec151-152">GitHub offers [a collection of useful .gitignore templates](https://github.com/github/gitignore) with recommended .gitignore file setups organized according to your use-case.</span></span> <span data-ttu-id="ec151-153">例如，下面是[Node.js 项目的 GitHub 的默认 .gitignore 模板](https://github.com/github/gitignore/blob/master/Node.gitignore)。</span><span class="sxs-lookup"><span data-stu-id="ec151-153">For example, here is [GitHub's default gitignore template for a Node.js project](https://github.com/github/gitignore/blob/master/Node.gitignore).</span></span>

<span data-ttu-id="ec151-154">如果选择[使用 GitHub 网站创建新的](https://help.github.com/articles/create-a-repo)存储库，则可以使用以下复选框来初始化存储库，其中包含一个自述文件、一个针对特定项目类型的 .gitignore 文件，以及用于添加许可证（如果需要）的选项。</span><span class="sxs-lookup"><span data-stu-id="ec151-154">If you choose to [create a new repo using the GitHub website](https://help.github.com/articles/create-a-repo), there are check boxes available to initialize your repo with a README file, .gitignore file set up for your specific project type, and options to add a license if you need one.</span></span>

## <a name="git-and-vs-code"></a><span data-ttu-id="ec151-155">Git 和 VS Code</span><span class="sxs-lookup"><span data-stu-id="ec151-155">Git and VS Code</span></span>

<span data-ttu-id="ec151-156">Visual Studio Code 附带了对 Git 的内置支持，其中包括一个 "源代码管理" 选项卡，该选项卡将显示你所做的更改并处理各种 git 命令。</span><span class="sxs-lookup"><span data-stu-id="ec151-156">Visual Studio Code comes with built-in support for Git, including a source control tab that will show your changes and handle a variety of git commands for you.</span></span> <span data-ttu-id="ec151-157">详细了解[VS Code 的 Git 支持](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)。</span><span class="sxs-lookup"><span data-stu-id="ec151-157">Learn more about [VS Code's Git support](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).</span></span>

## <a name="git-line-endings"></a><span data-ttu-id="ec151-158">Git 行尾</span><span class="sxs-lookup"><span data-stu-id="ec151-158">Git line endings</span></span>

<span data-ttu-id="ec151-159">如果在 Windows、WSL 或容器之间使用相同的存储库文件夹，请确保设置一致的行尾。</span><span class="sxs-lookup"><span data-stu-id="ec151-159">If you are working with the same repository folder between Windows, WSL, or a container, be sure to set up consistent line endings.</span></span>

<span data-ttu-id="ec151-160">由于 Windows 和 Linux 使用不同的默认行尾，Git 可能会报告大量已修改的文件，这些文件与行尾之间没有任何差别。</span><span class="sxs-lookup"><span data-stu-id="ec151-160">Since Windows and Linux use different default line endings, Git may report a large number of modified files that have no differences aside from their line endings.</span></span> <span data-ttu-id="ec151-161">若要防止发生这种情况，可以 `.gitattributes` 在 Windows 端使用文件或全局禁用行尾转换。</span><span class="sxs-lookup"><span data-stu-id="ec151-161">To prevent this from happening, you can disable line ending conversion using a `.gitattributes` file or globally on the Windows side.</span></span> <span data-ttu-id="ec151-162">[有关解决 Git 行结束问题的 VS Code](https://code.visualstudio.com/docs/remote/troubleshooting#_resolving-git-line-ending-issues-in-containers-resulting-in-many-modified-files)，请参阅此文档。</span><span class="sxs-lookup"><span data-stu-id="ec151-162">See this [VS Code doc about resolving Git line ending issues](https://code.visualstudio.com/docs/remote/troubleshooting#_resolving-git-line-ending-issues-in-containers-resulting-in-many-modified-files).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ec151-163">其他资源</span><span class="sxs-lookup"><span data-stu-id="ec151-163">Additional resources</span></span>

* [<span data-ttu-id="ec151-164">WSL & VS Code</span><span class="sxs-lookup"><span data-stu-id="ec151-164">WSL & VS Code</span></span>](./wsl-vscode.md)
* [<span data-ttu-id="ec151-165">GitHub 学习实验室：在线课程</span><span class="sxs-lookup"><span data-stu-id="ec151-165">GitHub Learning Lab: Online courses</span></span>](https://lab.github.com/)
* [<span data-ttu-id="ec151-166">Git 可视化工具</span><span class="sxs-lookup"><span data-stu-id="ec151-166">Git Visualization Tool</span></span>](http://git-school.github.io/visualizing-git/)
* [<span data-ttu-id="ec151-167">Git 工具-凭据存储</span><span class="sxs-lookup"><span data-stu-id="ec151-167">Git Tools - Credential Storage</span></span>](https://git-scm.com/book/it/v2/Git-Tools-Credential-Storage)
