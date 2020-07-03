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
# <a name="file-permissions-for-wsl"></a><span data-ttu-id="33f4c-104">WSL 的文件权限</span><span class="sxs-lookup"><span data-stu-id="33f4c-104">File Permissions for WSL</span></span>

<span data-ttu-id="33f4c-105">本页详细说明了 Linux 文件权限在适用于 Linux 的 Windows 子系统上是如何解释的，尤其是在访问 NT 文件系统上 Windows 内部的资源时。</span><span class="sxs-lookup"><span data-stu-id="33f4c-105">This page details how Linux file permissions are interpreted across the Windows Subsystem for Linux, especially when accessing resources inside of Windows on the NT file system.</span></span> <span data-ttu-id="33f4c-106">本文档假定读者基本了解 [Linux 文件系统权限结构](https://wiki.archlinux.org/index.php/File_permissions_and_attributes) 和 [umask 命令](https://en.wikipedia.org/wiki/Umask)。</span><span class="sxs-lookup"><span data-stu-id="33f4c-106">This documentation assumes a basic understanding of the [Linux file system permissions structure](https://wiki.archlinux.org/index.php/File_permissions_and_attributes) and the [umask command](https://en.wikipedia.org/wiki/Umask).</span></span>

<span data-ttu-id="33f4c-107">从 WSL 访问 Windows 文件时，文件权限是根据 Windows 权限计算的，或者是从已由 WSL 添加到文件的元数据中读取的。</span><span class="sxs-lookup"><span data-stu-id="33f4c-107">When accessing Windows files from WSL the file permissions are either calculated from Windows permissions, or are read from metadata that has been added to the file by WSL.</span></span> <span data-ttu-id="33f4c-108">默认情况下，此元数据处于未启用状态。</span><span class="sxs-lookup"><span data-stu-id="33f4c-108">This metadata is not enabled by default.</span></span>

## <a name="wsl-metadata-on-windows-files"></a><span data-ttu-id="33f4c-109">Windows 文件上的 WSL 元数据</span><span class="sxs-lookup"><span data-stu-id="33f4c-109">WSL metadata on Windows files</span></span>

<span data-ttu-id="33f4c-110">如果在 WSL 中以装载选项的形式启用了元数据，则可以在 Windows NT 文件上添加扩展属性并对其进行解释，从而提供 Linux 文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-110">When metadata is enabled as a mount option in WSL, extended attributes on Windows NT files can be added and interpreted to supply Linux file system permissions.</span></span>

<span data-ttu-id="33f4c-111">WSL 可以添加四个 NTFS 扩展属性：</span><span class="sxs-lookup"><span data-stu-id="33f4c-111">WSL can add four NTFS extended attributes:</span></span>

| <span data-ttu-id="33f4c-112">属性名称</span><span class="sxs-lookup"><span data-stu-id="33f4c-112">Attribute Name</span></span> | <span data-ttu-id="33f4c-113">说明</span><span class="sxs-lookup"><span data-stu-id="33f4c-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="33f4c-114">$LXUID</span><span class="sxs-lookup"><span data-stu-id="33f4c-114">$LXUID</span></span> | <span data-ttu-id="33f4c-115">用户所有者 ID</span><span class="sxs-lookup"><span data-stu-id="33f4c-115">User Owner ID</span></span> |
| <span data-ttu-id="33f4c-116">$LXGID</span><span class="sxs-lookup"><span data-stu-id="33f4c-116">$LXGID</span></span> | <span data-ttu-id="33f4c-117">组所有者 ID</span><span class="sxs-lookup"><span data-stu-id="33f4c-117">Group Owner ID</span></span> |
| <span data-ttu-id="33f4c-118">$LXMOD</span><span class="sxs-lookup"><span data-stu-id="33f4c-118">$LXMOD</span></span> | <span data-ttu-id="33f4c-119">文件模式（文件系统权限八进制数字和类型，例如：0777）</span><span class="sxs-lookup"><span data-stu-id="33f4c-119">File mode (File systems permission octals and type, e.g: 0777)</span></span> |
| <span data-ttu-id="33f4c-120">$LXDEV</span><span class="sxs-lookup"><span data-stu-id="33f4c-120">$LXDEV</span></span> | <span data-ttu-id="33f4c-121">设备（如果它是设备文件）</span><span class="sxs-lookup"><span data-stu-id="33f4c-121">Device, if it is a device file</span></span> |

<span data-ttu-id="33f4c-122">此外，任何并非常规文件或目录的文件（例如：符号链接、FIFO、块设备、unix 套接字和字符设备）也有 NTFS [重新分析点](https://docs.microsoft.com/windows/win32/fileio/reparse-points)。</span><span class="sxs-lookup"><span data-stu-id="33f4c-122">Additionally, any file that is not a regular file or directory (e.g: symlinks, FIFOs, block devices, unix sockets, and character devices) also have an NTFS [reparse point](https://docs.microsoft.com/windows/win32/fileio/reparse-points).</span></span> <span data-ttu-id="33f4c-123">这样一来，就能够以快得多的速度确定给定目录中的文件类型，而不必查询其扩展属性。</span><span class="sxs-lookup"><span data-stu-id="33f4c-123">This makes it much faster to determine the kind of file in a given directory without having to query its extended attributes.</span></span>

## <a name="file-access-scenarios"></a><span data-ttu-id="33f4c-124">文件访问方案</span><span class="sxs-lookup"><span data-stu-id="33f4c-124">File Access Scenarios</span></span>

<span data-ttu-id="33f4c-125">下面介绍了在使用适用于 Linux 的 Windows 子系统以不同的方式访问文件时，权限是如何确定的。</span><span class="sxs-lookup"><span data-stu-id="33f4c-125">Below is a description of how permissions are determined when accessing files in different ways using the Windows Subsystem for Linux.</span></span>

### <a name="accessing-files-in-the-windows-drive-file-system-drvfs-from-linux"></a><span data-ttu-id="33f4c-126">从 Linux 访问 Windows 驱动器文件系统 (DrvFS) 中的文件</span><span class="sxs-lookup"><span data-stu-id="33f4c-126">Accessing Files in the Windows drive file system (DrvFS) from Linux</span></span>

<span data-ttu-id="33f4c-127">在从 WSL 访问 Windows 文件（最有可能是通过 `/mnt/c`）时，会出现这些情况。</span><span class="sxs-lookup"><span data-stu-id="33f4c-127">These scenarios occur when you are accessing your Windows files from WSL, most likely via `/mnt/c`.</span></span>

#### <a name="reading-file-permissions-from-an-existing-windows-file"></a><span data-ttu-id="33f4c-128">从现有 Windows 文件读取文件权限</span><span class="sxs-lookup"><span data-stu-id="33f4c-128">Reading file permissions from an existing Windows file</span></span>

<span data-ttu-id="33f4c-129">结果取决于文件是否已具有现有元数据。</span><span class="sxs-lookup"><span data-stu-id="33f4c-129">The result depends on if the file already has existing metadata.</span></span>

##### <a name="drvfs-file-does-not-have-metadata-default"></a><span data-ttu-id="33f4c-130">DrvFS 文件没有元数据（默认）</span><span class="sxs-lookup"><span data-stu-id="33f4c-130">DrvFS file does not have metadata (default)</span></span>

<span data-ttu-id="33f4c-131">如果文件没有关联的元数据，则我们会将 Windows 用户的有效权限转换为读取/写入/执行位，并将其设置为对用户、组和其他用户而言相同的值。</span><span class="sxs-lookup"><span data-stu-id="33f4c-131">If the file has no metadata associated with it then we translate the effective permissions of the Windows user to read/write/execute bits and set them to the this as the same value for user, group, and other.</span></span> <span data-ttu-id="33f4c-132">例如，如果你的 Windows 用户帐户具有对该文件的读取和执行访问权限，但不具有对该文件的写入访问权限，则该帐户将对用户、组和其他对象显示为 `r-x`。</span><span class="sxs-lookup"><span data-stu-id="33f4c-132">For example, if your Windows user account has read and execute access but not write access to the file then this will be shown as `r-x` for user, group and other.</span></span> <span data-ttu-id="33f4c-133">如果该文件在 Windows 中设有“只读”属性，则我们不会在 Linux 中授予写入权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-133">If the file has the 'Read Only' attribute set in Windows then we do not grant write access in Linux.</span></span>

##### <a name="the-file-has-metadata"></a><span data-ttu-id="33f4c-134">文件有元数据</span><span class="sxs-lookup"><span data-stu-id="33f4c-134">The file has metadata</span></span>

<span data-ttu-id="33f4c-135">如果文件的元数据存在，则只需使用这些元数据值，而不是转换 Windows 用户的有效权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-135">If the file has metadata present, we simply use those metadata values instead of translating effective permissions of the Windows user.</span></span>

#### <a name="changing-file-permissions-on-an-existing-windows-file-using-chmod"></a><span data-ttu-id="33f4c-136">使用 chmod 更改现有 Windows 文件的文件权限</span><span class="sxs-lookup"><span data-stu-id="33f4c-136">Changing file permissions on an existing Windows file using chmod</span></span>

<span data-ttu-id="33f4c-137">结果取决于文件是否已具有现有元数据。</span><span class="sxs-lookup"><span data-stu-id="33f4c-137">The result depends on if the file already has existing metadata.</span></span>

##### <a name="chmod-file-does-not-have-metadata-default"></a><span data-ttu-id="33f4c-138">chmod 文件没有元数据（默认）</span><span class="sxs-lookup"><span data-stu-id="33f4c-138">chmod file does not have metadata (default)</span></span>

<span data-ttu-id="33f4c-139">Chmod 只有一种效果，如果删除文件的所有写入属性，则会设置 Windows 文件上的“只读”属性，因为这是与 CIFS（通用 Internet 文件系统）相同的行为。CIFS 是 Linux 中的 SMB（服务器消息块）客户端。</span><span class="sxs-lookup"><span data-stu-id="33f4c-139">Chmod will only have one effect, if you remove all the write attributes of a file then the 'read only' attribute on the Windows file will be set, since this is the same behaviour as CIFS (Common Internet File System) which is the SMB (Server Message Block) client in Linux.</span></span>

##### <a name="chmod-file-has-metadata"></a><span data-ttu-id="33f4c-140">chmod 文件有元数据</span><span class="sxs-lookup"><span data-stu-id="33f4c-140">chmod file has metadata</span></span>

<span data-ttu-id="33f4c-141">Chmod 将根据文件已有的现有元数据更改或添加元数据。</span><span class="sxs-lookup"><span data-stu-id="33f4c-141">Chmod will change or add metadata depending on the file's already existing metadata.</span></span> 

<span data-ttu-id="33f4c-142">请记住，你为自己授予的访问权限不能多于你在 Windows 上具有的访问权限，即使元数据显示的情况与此相反，也是如此。</span><span class="sxs-lookup"><span data-stu-id="33f4c-142">Please keep in mind that you cannot give yourself more access than what you have on Windows, even if the metadata says that is the case.</span></span> <span data-ttu-id="33f4c-143">例如，你可以使用 `chmod 777` 将元数据设置为显示你对文件具有写入权限，但如果你尝试访问该文件，则你仍无法写入到该文件。</span><span class="sxs-lookup"><span data-stu-id="33f4c-143">For example, you could set the metadata to display that you have write permissions to a file using `chmod 777`, but if you tried to access that file you would still not be able to write to it.</span></span> <span data-ttu-id="33f4c-144">这是由于互操作性而导致的，因为对 Windows 文件的任何读取或写入命令均通过 Windows 用户权限进行路由。</span><span class="sxs-lookup"><span data-stu-id="33f4c-144">This is thanks to interopability, as any read or write commands to Windows files are routed through your Windows user permissions.</span></span>

#### <a name="creating-a-file-in-drivefs"></a><span data-ttu-id="33f4c-145">在 DriveFS 中创建文件</span><span class="sxs-lookup"><span data-stu-id="33f4c-145">Creating a file in DriveFS</span></span>

<span data-ttu-id="33f4c-146">结果取决于是否启用了元数据。</span><span class="sxs-lookup"><span data-stu-id="33f4c-146">The result depends on if metadata is enabled.</span></span>

##### <a name="metadata-is-not-enabled-default"></a><span data-ttu-id="33f4c-147">元数据未启用（默认）</span><span class="sxs-lookup"><span data-stu-id="33f4c-147">Metadata is not enabled (default)</span></span>

<span data-ttu-id="33f4c-148">新创建的文件的 Windows 权限将与你在未使用特定安全描述符的情况下在 Windows 中创建的文件相同，它将继承父级的权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-148">The Windows permissions of the newly created file will be the same as if you created the file in Windows without a specific security descriptor, it will inherit the parent's permissions.</span></span>

##### <a name="metadata-is-enabled"></a><span data-ttu-id="33f4c-149">元数据已启用</span><span class="sxs-lookup"><span data-stu-id="33f4c-149">Metadata is enabled</span></span>

<span data-ttu-id="33f4c-150">文件的权限位设置为遵循 Linux umask，文件将随元数据一起保存。</span><span class="sxs-lookup"><span data-stu-id="33f4c-150">The file's permission bits are set to follow the Linux umask, and the file will be saved with metadata.</span></span>

#### <a name="which-linux-user-and-linux-group-owns-the-file"></a><span data-ttu-id="33f4c-151">哪个 Linux 用户和 Linux 组拥有该文件？</span><span class="sxs-lookup"><span data-stu-id="33f4c-151">Which Linux user and Linux group owns the file?</span></span> 

<span data-ttu-id="33f4c-152">结果取决于文件是否已具有现有元数据。</span><span class="sxs-lookup"><span data-stu-id="33f4c-152">The result depends on if the file already has existing metadata.</span></span>

##### <a name="user-file-does-not-have-metadata-default"></a><span data-ttu-id="33f4c-153">用户文件没有元数据（默认）</span><span class="sxs-lookup"><span data-stu-id="33f4c-153">User file does not have metadata (default)</span></span>

<span data-ttu-id="33f4c-154">在默认情况下，当自动装载 Windows 驱动器时，我们指定任何文件的用户 ID (UID) 将设置为 WSL 用户的用户 ID，并且组 ID (GID) 将设置为 WSL 用户的主体组 ID。</span><span class="sxs-lookup"><span data-stu-id="33f4c-154">In the default scenario, when automounting Windows drives, we specify that the user ID (UID) for any file is set to the user ID of your WSL user and the group ID (GID) is set to the principal group ID of your WSL user.</span></span>

##### <a name="user-file-has-metadata"></a><span data-ttu-id="33f4c-155">用户文件有元数据</span><span class="sxs-lookup"><span data-stu-id="33f4c-155">User file has metadata</span></span>

<span data-ttu-id="33f4c-156">在元数据中指定的 UID 和 GID 将应用为该文件的用户所有者和组所有者。</span><span class="sxs-lookup"><span data-stu-id="33f4c-156">The UID and GID specified in the metadata is applied as the user owner and group owner of the file.</span></span>

### <a name="accessing-linux-files-from-windows-using-wsl"></a><span data-ttu-id="33f4c-157">使用 `\\wsl$` 从 Windows 访问 Linux 文件</span><span class="sxs-lookup"><span data-stu-id="33f4c-157">Accessing Linux files from Windows using `\\wsl$`</span></span>

<span data-ttu-id="33f4c-158">通过 `\\wsl$` 访问 Linux 文件时将使用 WSL 分发版的默认用户。</span><span class="sxs-lookup"><span data-stu-id="33f4c-158">Accessing Linux files via `\\wsl$` will use the default user of your WSL distribution.</span></span> <span data-ttu-id="33f4c-159">因此，任何访问 Linux 文件的 Windows 应用都具有与默认用户相同的权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-159">Therefore any Windows app accessing Linux files will have the same permissions as the default user.</span></span>

#### <a name="creating-a-new-file"></a><span data-ttu-id="33f4c-160">创建新文件</span><span class="sxs-lookup"><span data-stu-id="33f4c-160">Creating a new file</span></span>

<span data-ttu-id="33f4c-161">从 Windows 向 WSL 分发版内部创建新文件时，将应用默认 umask。</span><span class="sxs-lookup"><span data-stu-id="33f4c-161">The default umask is applied when creating a new file inside of a WSL distribution from Windows.</span></span> <span data-ttu-id="33f4c-162">默认的 umask 是 `022`，也就是说，它允许除了组和其他用户的写入权限以外的所有权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-162">The default umask is `022`, or in other words it allows all permissions except write permissions to groups and others.</span></span> 

### <a name="accessing-files-in-the-linux-root-file-system-from-linux"></a><span data-ttu-id="33f4c-163">从 Linux 访问 Linux 根文件系统中的文件</span><span class="sxs-lookup"><span data-stu-id="33f4c-163">Accessing files in the Linux root file system from Linux</span></span>

<span data-ttu-id="33f4c-164">在 Linux 根文件系统中创建、修改或访问的任何文件都遵循标准 Linux 约定，例如将 umask 应用到新创建的文件。</span><span class="sxs-lookup"><span data-stu-id="33f4c-164">Any files created, modified, or accessed in the Linux root file system follow standard Linux conventions, such as applying the umask to a newly created file.</span></span>

## <a name="configuring-file-permissions"></a><span data-ttu-id="33f4c-165">配置文件权限</span><span class="sxs-lookup"><span data-stu-id="33f4c-165">Configuring file permissions</span></span>

<span data-ttu-id="33f4c-166">可以使用 wsl.conf 中的装载选项在 Windows 驱动器内配置文件权限。</span><span class="sxs-lookup"><span data-stu-id="33f4c-166">You can configure your file permissions inside of your Windows drives using the mount options in wsl.conf.</span></span> <span data-ttu-id="33f4c-167">装载选项允许你设置 `umask`、`dmask` 和 `fmask` 权限掩码。</span><span class="sxs-lookup"><span data-stu-id="33f4c-167">The mount options allow you to set `umask`, `dmask` and `fmask` permissions masks.</span></span> <span data-ttu-id="33f4c-168">`umask` 应用于所有文件，`dmask` 只应用于目录，而 `fmask` 只应用于文件。</span><span class="sxs-lookup"><span data-stu-id="33f4c-168">The `umask` is applied to all files, the `dmask` is applied just to directories and the `fmask` is applied just to files.</span></span> <span data-ttu-id="33f4c-169">这些权限掩码在应用到文件时会通过一个“逻辑或”操作进行计算，例如：如果 `umask` 值为 `023` 并且 `fmask` 值为 `022`，则为文件生成的权限掩码将为 `023`。</span><span class="sxs-lookup"><span data-stu-id="33f4c-169">These permission masks are then put through a logical OR operation when being applied to files, e.g: If you have a `umask` value of `023` and an `fmask` value of `022` then the resulting permissions mask for files will be `023`.</span></span>

<span data-ttu-id="33f4c-170">有关如何执行此操作的说明，请参阅[使用 wslconf 配置按分发版启动设置](./wsl-config.md#configure-per-distro-launch-settings-with-wslconf)一文。</span><span class="sxs-lookup"><span data-stu-id="33f4c-170">Please see the [Configure per distro launch settings with wslconf](./wsl-config.md#configure-per-distro-launch-settings-with-wslconf) article for instructions on how to do this.</span></span>
