---
title: 开始使用 MySQL MongoDB、PostgreSQL、SQLite、Microsoft SQL Server 或 Redis 在适用于 Linux 的 Windows 子系统上设置数据库
description: 了解如何在适用于 Linux 的 Windows 子系统上设置 MySQL MongoDB、PostgreSQL、SQLite、Microsoft SQL Server 或 Redis。
keywords: wsl、windows、windowssubsystem、MySQL MongoDB、PostgreSQL、SQLite、Microsoft SQL Server、Redis、windows 10
ms.date: 07/07/2020
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 8ffd40ef21e8fb8ece529157852ba5d8bb676076
ms.sourcegitcommit: 16ffb1a096a4a7fbb77c58f92258051930cc82da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86160216"
---
# <a name="get-started-with-databases-on-windows-subsystem-for-linux"></a><span data-ttu-id="cd763-104">适用于 Linux 的 Windows 子系统上的数据库入门</span><span class="sxs-lookup"><span data-stu-id="cd763-104">Get started with databases on Windows Subsystem for Linux</span></span>

<span data-ttu-id="cd763-105">此循序渐进指南将帮助你开始将 WSL 中的项目连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-105">This step-by-step guide will help you get started connecting your project in WSL to a database.</span></span> <span data-ttu-id="cd763-106">MySQL、PostgreSQL、MongoDB、Redis、Microsoft SQL Server 或 SQLite 入门。</span><span class="sxs-lookup"><span data-stu-id="cd763-106">Get started with MySQL, PostgreSQL, MongoDB, Redis, Microsoft SQL Server, or SQLite.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd763-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="cd763-107">Prerequisites</span></span>

- <span data-ttu-id="cd763-108">运行 Windows 10（[已更新到版本 2004](ms-settings:windowsupdate) 的**内部版本 19041** 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="cd763-108">Running Windows 10, [updated to version 2004](ms-settings:windowsupdate), **Build 19041** or higher.</span></span>
- <span data-ttu-id="cd763-109">[启用并安装 WSL，并更新为 WSL 2](https://docs.microsoft.com/windows/wsl/install-win10)。</span><span class="sxs-lookup"><span data-stu-id="cd763-109">[WSL enabled and installed, and updated to WSL 2](https://docs.microsoft.com/windows/wsl/install-win10).</span></span>
- <span data-ttu-id="cd763-110">[已安装 Linux 分发](https://docs.microsoft.com/windows/wsl/install-win10#install-your-linux-distribution-of-choice)版（Ubuntu 18.04，适用于我们的示例）。</span><span class="sxs-lookup"><span data-stu-id="cd763-110">[Linux distribution installed](https://docs.microsoft.com/windows/wsl/install-win10#install-your-linux-distribution-of-choice) (Ubuntu 18.04 for our examples).</span></span>
- <span data-ttu-id="cd763-111">确保 Ubuntu 18.04 分发[在 WSL 2 模式下运行](https://docs.microsoft.com/windows/wsl/install-win10#set-your-distribution-version-to-wsl-1-or-wsl-2)。</span><span class="sxs-lookup"><span data-stu-id="cd763-111">Ensure your Ubuntu 18.04 distribution is [running in WSL 2 mode](https://docs.microsoft.com/windows/wsl/install-win10#set-your-distribution-version-to-wsl-1-or-wsl-2).</span></span> <span data-ttu-id="cd763-112">（WSL 可以在 v1 或 v2 模式下运行分发。）可以通过打开 PowerShell 并输入以下内容来进行检查：`wsl -l -v`</span><span class="sxs-lookup"><span data-stu-id="cd763-112">(WSL can run distributions in both v1 or v2 mode.) You can check this by opening PowerShell and entering: `wsl -l -v`</span></span>

## <a name="differences-between-database-systems"></a><span data-ttu-id="cd763-113">数据库系统之间的差异</span><span class="sxs-lookup"><span data-stu-id="cd763-113">Differences between database systems</span></span>

<span data-ttu-id="cd763-114">对于数据库系统，最[常用的选项](https://insights.stackoverflow.com/survey/2019#technology-_-databases)包括：</span><span class="sxs-lookup"><span data-stu-id="cd763-114">The most [popular choices](https://insights.stackoverflow.com/survey/2019#technology-_-databases) for a database system include:</span></span>

- <span data-ttu-id="cd763-115">[MySQL](https://www.mysql.com/why-mysql/) （SQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-115">[MySQL](https://www.mysql.com/why-mysql/) (SQL)</span></span>
- <span data-ttu-id="cd763-116">[PostgreSQL](https://www.postgresql.org/about/) （SQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-116">[PostgreSQL](https://www.postgresql.org/about/) (SQL)</span></span>
- <span data-ttu-id="cd763-117">[Microsoft SQL Server](https://docs.microsoft.com/sql/?view=sql-server-ver15) （SQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-117">[Microsoft SQL Server](https://docs.microsoft.com/sql/?view=sql-server-ver15) (SQL)</span></span>
- <span data-ttu-id="cd763-118">[SQLite](https://www.sqlite.org/about.html) （SQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-118">[SQLite](https://www.sqlite.org/about.html) (SQL)</span></span>
- <span data-ttu-id="cd763-119">[MongoDB](https://www.mongodb.com/what-is-mongodb) （NoSQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-119">[MongoDB](https://www.mongodb.com/what-is-mongodb) (NoSQL)</span></span>
- <span data-ttu-id="cd763-120">[Redis](https://redis.io/topics/introduction) （NoSQL）</span><span class="sxs-lookup"><span data-stu-id="cd763-120">[Redis](https://redis.io/topics/introduction) (NoSQL)</span></span>

<span data-ttu-id="cd763-121">**MySQL**是一种开源 SQL 关系数据库，将数据组织到一个或多个表中，这些表中的数据类型可能相互相关。</span><span class="sxs-lookup"><span data-stu-id="cd763-121">**MySQL** is an open-source SQL relational database, organizing data into one or more tables in which data types may be related to each other.</span></span> <span data-ttu-id="cd763-122">它是可垂直缩放的，这意味着一台终极计算机将为您完成工作。</span><span class="sxs-lookup"><span data-stu-id="cd763-122">It is vertically scalable, which means one ultimate machine will do the work for you.</span></span> <span data-ttu-id="cd763-123">它目前是四个数据库系统最广泛使用的。</span><span class="sxs-lookup"><span data-stu-id="cd763-123">It is currently the most widely used of the four database systems.</span></span>

<span data-ttu-id="cd763-124">**PostgreSQL** （有时称为 Postgres）也是开源 SQL 关系数据库，重点介绍扩展性和标准符合性。</span><span class="sxs-lookup"><span data-stu-id="cd763-124">**PostgreSQL** (sometimes referred to as Postgres) is also an open-source SQL relational database with an emphasis on extensibility and standards compliance.</span></span> <span data-ttu-id="cd763-125">现在，它也可以处理 JSON，但通常更适合处理结构化数据、进行垂直缩放以及符合 ACID 的需求，例如电子商务和金融交易。</span><span class="sxs-lookup"><span data-stu-id="cd763-125">It can handle JSON now too, but it is generally better for structured data, vertical scaling, and ACID-compliant needs like eCommerce and financial transactions.</span></span>

<span data-ttu-id="cd763-126">**Microsoft SQL Server**包括 SQL Server Windows、Linux 上的 SQL Server 和 Azure 上的 SQL。</span><span class="sxs-lookup"><span data-stu-id="cd763-126">**Microsoft SQL Server** includes SQL Server on Windows, SQL Server on Linux, and SQL on Azure.</span></span> <span data-ttu-id="cd763-127">它们也是在服务器上设置的关系数据库管理系统，其主要功能是按软件应用程序的要求存储和检索数据。</span><span class="sxs-lookup"><span data-stu-id="cd763-127">These are also relational database management systems set up on servers with primary function of storing and retrieving data as requested by software applications.</span></span>

<span data-ttu-id="cd763-128">**SQLite**是开源自包含的、基于文件的 "无服务器" 数据库，其可移植性、可靠性和良好性能，即使在低内存环境中也是如此。</span><span class="sxs-lookup"><span data-stu-id="cd763-128">**SQLite** is an open-source self-contained, file-based, “serverless” database, known for its portability, reliability, and good performance even in low-memory environments.</span></span>

<span data-ttu-id="cd763-129">**MongoDB**是一种开源 NoSQL 文档数据库，旨在使用 JSON 并存储无架构的数据。</span><span class="sxs-lookup"><span data-stu-id="cd763-129">**MongoDB** is an open-source NoSQL document database designed to work with JSON and store schema-free data.</span></span> <span data-ttu-id="cd763-130">它可以水平缩放，这意味着多个小型计算机将为你完成工作。</span><span class="sxs-lookup"><span data-stu-id="cd763-130">It is horizontally scalable, which means multiple smaller machines will do the work for you.</span></span> <span data-ttu-id="cd763-131">它适用于灵活性和非结构化数据，并缓存实时分析。</span><span class="sxs-lookup"><span data-stu-id="cd763-131">It's good for flexibility and unstructured data, and caching real-time analytics.</span></span>

<span data-ttu-id="cd763-132">**Redis**是一个开源 NoSQL 内存中数据结构存储区。</span><span class="sxs-lookup"><span data-stu-id="cd763-132">**Redis** is is an open-source NoSQL in-memory data structure store.</span></span> <span data-ttu-id="cd763-133">它为存储而不是文档使用键值对。</span><span class="sxs-lookup"><span data-stu-id="cd763-133">It uses key-value pairs for storage instead of documents.</span></span> <span data-ttu-id="cd763-134">Redis 被认为是其灵活性、性能和广泛的语言支持。</span><span class="sxs-lookup"><span data-stu-id="cd763-134">Redis is known for its flexibility, performance, and wide language support.</span></span> <span data-ttu-id="cd763-135">它非常灵活，可以用作缓存或消息代理，并且可以使用数据结构（如列表、集和哈希）。</span><span class="sxs-lookup"><span data-stu-id="cd763-135">It’s flexible enough to be used as a cache or message broker and can use data structures like lists, sets, and hashes.</span></span>

<span data-ttu-id="cd763-136">选择的数据库类型应取决于将使用该数据库的应用程序的类型。</span><span class="sxs-lookup"><span data-stu-id="cd763-136">The sort of database you choose should depend on the type of application you will be using the database with.</span></span> <span data-ttu-id="cd763-137">我们建议你查看结构化和非结构化数据库的优点和缺点，并根据用例进行选择。</span><span class="sxs-lookup"><span data-stu-id="cd763-137">We recommend that you look up the advantages and disadvantages of structured and unstructured databases and choose based on your use case.</span></span>

## <a name="install-mysql"></a><span data-ttu-id="cd763-138">安装 MySQL</span><span class="sxs-lookup"><span data-stu-id="cd763-138">Install MySQL</span></span>

<span data-ttu-id="cd763-139">在 WSL 上安装 MySQL （Ubuntu 18.04）：</span><span class="sxs-lookup"><span data-stu-id="cd763-139">To install MySQL on WSL (Ubuntu 18.04):</span></span>

1. <span data-ttu-id="cd763-140">打开 WSL 终端（即 Ubuntu 18.04）。</span><span class="sxs-lookup"><span data-stu-id="cd763-140">Open your WSL terminal (ie. Ubuntu 18.04).</span></span>
2. <span data-ttu-id="cd763-141">更新 Ubuntu 包：`sudo apt update`</span><span class="sxs-lookup"><span data-stu-id="cd763-141">Update your Ubuntu packages: `sudo apt update`</span></span>
3. <span data-ttu-id="cd763-142">更新包后，使用以下内容安装 MySQL：`sudo apt install mysql-server`</span><span class="sxs-lookup"><span data-stu-id="cd763-142">Once the packages have updated, install MySQL with: `sudo apt install mysql-server`</span></span>
4. <span data-ttu-id="cd763-143">确认安装并获取版本号：`mysql --version`</span><span class="sxs-lookup"><span data-stu-id="cd763-143">Confirm installation and get the version number: `mysql --version`</span></span>

<span data-ttu-id="cd763-144">你可能还需要运行包含的安全脚本。</span><span class="sxs-lookup"><span data-stu-id="cd763-144">You may also want to run the included security script.</span></span> <span data-ttu-id="cd763-145">这会更改远程根登录名和示例用户之类的一些安全默认选项。</span><span class="sxs-lookup"><span data-stu-id="cd763-145">This changes some of the less secure default options for things like remote root logins and sample users.</span></span> <span data-ttu-id="cd763-146">运行安全脚本：</span><span class="sxs-lookup"><span data-stu-id="cd763-146">To run the security script:</span></span>

1. <span data-ttu-id="cd763-147">启动 MySQL server：`sudo /etc/init.d/mysql start`</span><span class="sxs-lookup"><span data-stu-id="cd763-147">Start a MySQL server: `sudo /etc/init.d/mysql start`</span></span>
2. <span data-ttu-id="cd763-148">启动安全脚本提示：`sudo mysql_secure_installation`</span><span class="sxs-lookup"><span data-stu-id="cd763-148">Start the security script prompts: `sudo mysql_secure_installation`</span></span>
3. <span data-ttu-id="cd763-149">第一个提示将询问你是否要设置 "验证密码" 插件，该插件可用于测试 MySQL 密码的强度。</span><span class="sxs-lookup"><span data-stu-id="cd763-149">The first prompt will ask whether you’d like to set up the Validate Password Plugin, which can be used to test the strength of your MySQL password.</span></span> <span data-ttu-id="cd763-150">然后，你将为 MySQL 根用户设置密码，决定是否要删除匿名用户，决定是否允许根用户本地和远程登录，确定是否要删除测试数据库，最后确定是否要立即重新加载特权表。</span><span class="sxs-lookup"><span data-stu-id="cd763-150">You will then set a password for the MySQL root user, decide whether or not to remove anonymous users, decide whether to allow the root user to login both locally and remotely, decide whether to remove the test database, and, lastly, decide whether to reload the privilege tables immediately.</span></span>

<span data-ttu-id="cd763-151">若要打开 MySQL 提示符，请输入：`sudo mysql`</span><span class="sxs-lookup"><span data-stu-id="cd763-151">To open the MySQL prompt, enter: `sudo mysql`</span></span>

<span data-ttu-id="cd763-152">若要查看可用数据库，请在 MySQL 提示符下输入：`SHOW DATABASES;`</span><span class="sxs-lookup"><span data-stu-id="cd763-152">To see what databases you have available, in the MySQL prompt, enter: `SHOW DATABASES;`</span></span>

<span data-ttu-id="cd763-153">若要创建新数据库，请输入：`CREATE DATABASE database_name;`</span><span class="sxs-lookup"><span data-stu-id="cd763-153">To create a new database, enter: `CREATE DATABASE database_name;`</span></span>

<span data-ttu-id="cd763-154">若要删除数据库，请输入：` DROP DATABASE database_name;`</span><span class="sxs-lookup"><span data-stu-id="cd763-154">To delete a database, enter: ` DROP DATABASE database_name;`</span></span>

<span data-ttu-id="cd763-155">有关使用 MySQL 数据库的详细信息，请参阅[mysql 文档](https://dev.mysql.com/doc/mysql-getting-started/en/)。</span><span class="sxs-lookup"><span data-stu-id="cd763-155">For more about working with MySQL databases, see the [MySQL docs](https://dev.mysql.com/doc/mysql-getting-started/en/).</span></span>

<span data-ttu-id="cd763-156">若要在 VS Code 中使用 MySQL 数据库，请尝试[mysql 扩展](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2)。</span><span class="sxs-lookup"><span data-stu-id="cd763-156">To work with with MySQL databases in VS Code, try the [MySQL extension](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2).</span></span>

## <a name="install-postgresql"></a><span data-ttu-id="cd763-157">安装 PostgreSQL</span><span class="sxs-lookup"><span data-stu-id="cd763-157">Install PostgreSQL</span></span>

<span data-ttu-id="cd763-158">在 WSL （Ubuntu 18.04）上安装 PostgreSQL：</span><span class="sxs-lookup"><span data-stu-id="cd763-158">To install PostgreSQL on WSL (Ubuntu 18.04):</span></span>

1. <span data-ttu-id="cd763-159">打开 WSL 终端（即 Ubuntu 18.04）。</span><span class="sxs-lookup"><span data-stu-id="cd763-159">Open your WSL terminal (ie. Ubuntu 18.04).</span></span>
2. <span data-ttu-id="cd763-160">更新 Ubuntu 包：`sudo apt update`</span><span class="sxs-lookup"><span data-stu-id="cd763-160">Update your Ubuntu packages: `sudo apt update`</span></span>
3. <span data-ttu-id="cd763-161">更新该包后，使用以下命令安装 PostgreSQL（和 -contrib 包，其中包含一些有用的实用程序）：`sudo apt install postgresql postgresql-contrib`</span><span class="sxs-lookup"><span data-stu-id="cd763-161">Once the packages have updated, install PostgreSQL (and the -contrib package which has some helpful utilities) with: `sudo apt install postgresql postgresql-contrib`</span></span>
4. <span data-ttu-id="cd763-162">确认安装并获取版本号：`psql --version`</span><span class="sxs-lookup"><span data-stu-id="cd763-162">Confirm installation and get the version number: `psql --version`</span></span>

<span data-ttu-id="cd763-163">安装 PostgreSQL 后，需要知道以下 3 个命令：</span><span class="sxs-lookup"><span data-stu-id="cd763-163">There are 3 commands you need to know once PostgreSQL is installed:</span></span>

- <span data-ttu-id="cd763-164">`sudo service postgresql status` 用于检查数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="cd763-164">`sudo service postgresql status` for checking the status of your database.</span></span>
- <span data-ttu-id="cd763-165">`sudo service postgresql start` 用于开始运行数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-165">`sudo service postgresql start`  to start running your database.</span></span>
- <span data-ttu-id="cd763-166">`sudo service postgresql stop` 用于停止运行数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-166">`sudo service postgresql stop` to stop running your database.</span></span>

<span data-ttu-id="cd763-167">默认管理员用户 `postgres` 需要分配的密码才能连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-167">The default admin user, `postgres`, needs a password assigned in order to connect to a database.</span></span> <span data-ttu-id="cd763-168">要设置密码，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cd763-168">To set a password:</span></span>

1. <span data-ttu-id="cd763-169">输入命令：`sudo passwd postgres`</span><span class="sxs-lookup"><span data-stu-id="cd763-169">Enter the command: `sudo passwd postgres`</span></span>
2. <span data-ttu-id="cd763-170">系统将提示你输入新密码。</span><span class="sxs-lookup"><span data-stu-id="cd763-170">You will get a prompt to enter your new password.</span></span>
3. <span data-ttu-id="cd763-171">关闭并重新打开终端。</span><span class="sxs-lookup"><span data-stu-id="cd763-171">Close and reopen your terminal.</span></span>

<span data-ttu-id="cd763-172">若要通过[psql](https://www.postgresql.org/docs/10/app-psql.html) Shell 运行 PostgreSQL：</span><span class="sxs-lookup"><span data-stu-id="cd763-172">To run PostgreSQL with [psql](https://www.postgresql.org/docs/10/app-psql.html) shell:</span></span>

1. <span data-ttu-id="cd763-173">启动 postgres 服务：`sudo service postgresql start`</span><span class="sxs-lookup"><span data-stu-id="cd763-173">Start your postgres service: `sudo service postgresql start`</span></span>
2. <span data-ttu-id="cd763-174">连接到 postgres 服务，并打开 psql shell：`sudo -u postgres psql`</span><span class="sxs-lookup"><span data-stu-id="cd763-174">Connect to the postgres service and open the psql shell: `sudo -u postgres psql`</span></span>

<span data-ttu-id="cd763-175">成功输入 psql shell 后，将显示更改为如下所示的命令行：`postgres=#`</span><span class="sxs-lookup"><span data-stu-id="cd763-175">Once you have successfully entered the psql shell, you will see your command line change to look like this: `postgres=#`</span></span>

> [!NOTE]
> <span data-ttu-id="cd763-176">或者，也可以通过使用 `su - postgres` 切换为 postgres 用户，然后输入命令 `psql` 来打开 psql shell。</span><span class="sxs-lookup"><span data-stu-id="cd763-176">Alternatively, you can open the psql shell by switching to the postgres user with: `su - postgres` and then entering the command: `psql`.</span></span>

<span data-ttu-id="cd763-177">若要退出 postgres = # enter： `\q` 或使用快捷键： Ctrl + D</span><span class="sxs-lookup"><span data-stu-id="cd763-177">To exit postgres=# enter: `\q` or use the shortcut key: Ctrl+D</span></span>

<span data-ttu-id="cd763-178">要查看在 PostgreSQL 安装上创建的用户帐户，请在 WSL 终端上使用 `psql -c "\du"`；如果已打开 psql shell，则仅使用 `\du`。</span><span class="sxs-lookup"><span data-stu-id="cd763-178">To see what user accounts have been created on your PostgreSQL installation, use from your WSL terminal: `psql -c "\du"` ...or just `\du` if you have the psql shell open.</span></span> <span data-ttu-id="cd763-179">此命令将显示列：帐户用户名、角色列表和角色组的成员。</span><span class="sxs-lookup"><span data-stu-id="cd763-179">This command will display columns: Account User Name, List of Roles Attributes, and Member of role group(s).</span></span> <span data-ttu-id="cd763-180">要返回命令行，请输入：`q`。</span><span class="sxs-lookup"><span data-stu-id="cd763-180">To exit back to the command line, enter: `q`.</span></span>

<span data-ttu-id="cd763-181">有关使用 PostgreSQL 数据库的详细信息，请参阅[PostgreSQL 文档](https://www.postgresql.org/docs/13/tutorial-createdb.html)。</span><span class="sxs-lookup"><span data-stu-id="cd763-181">For more about working with PostgreSQL databases, see the [PostgreSQL docs](https://www.postgresql.org/docs/13/tutorial-createdb.html).</span></span>

<span data-ttu-id="cd763-182">若要在 VS Code 中使用 PostgreSQL 数据库，请尝试[PostgreSQL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-ossdata.vscode-postgresql)。</span><span class="sxs-lookup"><span data-stu-id="cd763-182">To work with with PostgreSQL databases in VS Code, try the [PostgreSQL extension](https://marketplace.visualstudio.com/items?itemName=ms-ossdata.vscode-postgresql).</span></span>

## <a name="install-mongodb"></a><span data-ttu-id="cd763-183">安装 MongoDB</span><span class="sxs-lookup"><span data-stu-id="cd763-183">Install MongoDB</span></span>

<span data-ttu-id="cd763-184">在 WSL 上安装 MongoDB （Ubuntu 18.04）：</span><span class="sxs-lookup"><span data-stu-id="cd763-184">To install MongoDB on WSL (Ubuntu 18.04):</span></span>

1. <span data-ttu-id="cd763-185">打开 WSL 终端（即 Ubuntu 18.04）。</span><span class="sxs-lookup"><span data-stu-id="cd763-185">Open your WSL terminal (ie. Ubuntu 18.04).</span></span>
2. <span data-ttu-id="cd763-186">更新 Ubuntu 包：`sudo apt update`</span><span class="sxs-lookup"><span data-stu-id="cd763-186">Update your Ubuntu packages: `sudo apt update`</span></span>
3. <span data-ttu-id="cd763-187">更新该包后，使用以下命令安装 MongoDB：`sudo apt-get install mongodb`</span><span class="sxs-lookup"><span data-stu-id="cd763-187">Once the packages have updated, install MongoDB with: `sudo apt-get install mongodb`</span></span>
4. <span data-ttu-id="cd763-188">确认安装并获取版本号：`mongod --version`</span><span class="sxs-lookup"><span data-stu-id="cd763-188">Confirm installation and get the version number: `mongod --version`</span></span>

<span data-ttu-id="cd763-189">安装 MongoDB 后，需要知道以下 3 个命令：</span><span class="sxs-lookup"><span data-stu-id="cd763-189">There are 3 commands you need to know once MongoDB is installed:</span></span>

- <span data-ttu-id="cd763-190">`sudo service mongodb status` 用于检查数据库的状态。</span><span class="sxs-lookup"><span data-stu-id="cd763-190">`sudo service mongodb status` for checking the status of your database.</span></span>
- <span data-ttu-id="cd763-191">`sudo service mongodb start` 用于开始运行数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-191">`sudo service mongodb start`  to start running your database.</span></span>
- <span data-ttu-id="cd763-192">`sudo service mongodb stop` 用于停止运行数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-192">`sudo service mongodb stop` to stop running your database.</span></span>

> [!NOTE]
> <span data-ttu-id="cd763-193">你可能会看到在教程或文章中使用了命令 `sudo systemctl status mongodb`。</span><span class="sxs-lookup"><span data-stu-id="cd763-193">You might see the command `sudo systemctl status mongodb` used in tutorials or articles.</span></span> <span data-ttu-id="cd763-194">为了保持轻量，WSL 不包括 `systemd`（Linux 中的服务管理系统）。</span><span class="sxs-lookup"><span data-stu-id="cd763-194">In order to remain lightweight, WSL does not include `systemd` (a service management system in Linux).</span></span> <span data-ttu-id="cd763-195">它改为使用 SysVinit 在计算机上启动服务。</span><span class="sxs-lookup"><span data-stu-id="cd763-195">Instead, it uses SysVinit to start services on your machine.</span></span> <span data-ttu-id="cd763-196">你应该不会注意到有什么区别，但是如果教程建议使用 `sudo systemctl`，请改用 `sudo /etc/init.d/`。</span><span class="sxs-lookup"><span data-stu-id="cd763-196">You shouldn't notice a difference, but if a tutorial recommends using `sudo systemctl`, instead use: `sudo /etc/init.d/`.</span></span> <span data-ttu-id="cd763-197">例如，对于 WSL，`sudo systemctl status mongodb` 应改用 `sudo /etc/inid.d/mongodb status`，或者也可以使用 `sudo service mongodb status`。</span><span class="sxs-lookup"><span data-stu-id="cd763-197">For example, `sudo systemctl status mongodb`, for WSL would be `sudo /etc/inid.d/mongodb status` ...or you can also use `sudo service mongodb status`.</span></span>

<span data-ttu-id="cd763-198">若要在本地服务器上运行 Mongo 数据库，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cd763-198">To run your Mongo database in a local server:</span></span>

1. <span data-ttu-id="cd763-199">检查数据库的状态：除非已 `sudo service mongodb status` 启动数据库，否则应该会看到 [Fail] 响应。</span><span class="sxs-lookup"><span data-stu-id="cd763-199">Check the status of your database: `sudo service mongodb status` You should see a [Fail] response, unless you've already started your database.</span></span>

2. <span data-ttu-id="cd763-200">启动数据库： `sudo service mongodb start` 此时应会看到一个 [OK] 响应。</span><span class="sxs-lookup"><span data-stu-id="cd763-200">Start your database: `sudo service mongodb start` You should now see an [OK] response.</span></span>

3. <span data-ttu-id="cd763-201">通过连接到数据库服务器并运行诊断命令来验证： `mongo --eval 'db.runCommand({ connectionStatus: 1 })'` 这将输出当前的数据库版本、服务器地址和端口以及状态命令的输出。</span><span class="sxs-lookup"><span data-stu-id="cd763-201">Verify by connecting to the database server and running a diagnostic command: `mongo --eval 'db.runCommand({ connectionStatus: 1 })'` This will output the current database version, the server address and port, and the output of the status command.</span></span> <span data-ttu-id="cd763-202">响应中“ok”字段的值 `1` 表示服务器正在运行。</span><span class="sxs-lookup"><span data-stu-id="cd763-202">A value of `1` for the "ok" field in the response indicates that the server is working.</span></span>

4. <span data-ttu-id="cd763-203">要停止运行 MongoDB 服务，请输入：`sudo service mongodb stop`</span><span class="sxs-lookup"><span data-stu-id="cd763-203">To stop your MongoDB service from running, enter: `sudo service mongodb stop`</span></span>

> [!NOTE]
> <span data-ttu-id="cd763-204">MongoDB 有几个默认参数，包括在 /data/db 中存储数据和在端口 27017 上运行。</span><span class="sxs-lookup"><span data-stu-id="cd763-204">MongoDB has several default parameters, including storing data in /data/db and running on port 27017.</span></span> <span data-ttu-id="cd763-205">此外，`mongod` 是守护程序（数据库的主机进程），`mongo` 是连接到特定实例 `mongod` 的命令行 shell。</span><span class="sxs-lookup"><span data-stu-id="cd763-205">Also, `mongod` is the daemon (host process for the database) and `mongo` is the command-line shell that connects to a specific instance of `mongod`.</span></span>

<span data-ttu-id="cd763-206">VS Code 支持通过[Azure CosmosDB 扩展](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)使用 mongodb 数据库，则可以从 VS Code 中创建、管理和查询 mongodb 数据库。</span><span class="sxs-lookup"><span data-stu-id="cd763-206">VS Code supports working with MongoDB databases via the [Azure CosmosDB extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb), you can create, manage and query MongoDB databases from within VS Code.</span></span> <span data-ttu-id="cd763-207">若要了解详细信息，请访问 VS Code 文档：[使用 MongoDB](https://code.visualstudio.com/docs/azure/mongodb)。</span><span class="sxs-lookup"><span data-stu-id="cd763-207">To learn more, visit the VS Code docs: [Working with MongoDB](https://code.visualstudio.com/docs/azure/mongodb).</span></span>

<span data-ttu-id="cd763-208">有关详细信息，请参阅 MongoDB 文档：</span><span class="sxs-lookup"><span data-stu-id="cd763-208">Learn more in the MongoDB docs:</span></span>

- [<span data-ttu-id="cd763-209">使用 MongoDB 简介</span><span class="sxs-lookup"><span data-stu-id="cd763-209">Introduction to using MongoDB</span></span>](https://docs.mongodb.com/manual/introduction/)
- [<span data-ttu-id="cd763-210">创建用户</span><span class="sxs-lookup"><span data-stu-id="cd763-210">Create users</span></span>](https://docs.mongodb.com/manual/tutorial/create-users/)
- [<span data-ttu-id="cd763-211">连接到远程主机上的 MongoDB 实例</span><span class="sxs-lookup"><span data-stu-id="cd763-211">Connect to a MongoDB instance on a remote host</span></span>](https://docs.mongodb.com/manual/mongo/#mongodb-instance-on-a-remote-host)
- [<span data-ttu-id="cd763-212">CRUD：创建、读取、更新、删除</span><span class="sxs-lookup"><span data-stu-id="cd763-212">CRUD: Create, Read, Update, Delete</span></span>](https://docs.mongodb.com/manual/crud/)
- [<span data-ttu-id="cd763-213">参考文档</span><span class="sxs-lookup"><span data-stu-id="cd763-213">Reference Docs</span></span>](https://docs.mongodb.com/manual/reference/)

## <a name="install-microsoft-sql-server"></a><span data-ttu-id="cd763-214">安装 Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="cd763-214">Install Microsoft SQL Server</span></span>

<span data-ttu-id="cd763-215">若要在 WSL 上安装 SQL Server （Ubuntu 18.04），请遵循以下快速入门：[在 ubuntu 上安装 SQL Server 并创建数据库](https://docs.microsoft.com/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver15)。</span><span class="sxs-lookup"><span data-stu-id="cd763-215">To install SQL Server on WSL (Ubuntu 18.04), follow this quickstart: [Install SQL Server and create a database on Ubuntu](https://docs.microsoft.com/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver15).</span></span>

<span data-ttu-id="cd763-216">若要在 VS Code 中使用 Microsoft SQL Server 数据库，请尝试[MSSQL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)。</span><span class="sxs-lookup"><span data-stu-id="cd763-216">To work with Microsoft SQL Server databases in VS Code, try the [MSSQL extension](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql).</span></span>

## <a name="install-sqlite"></a><span data-ttu-id="cd763-217">安装 SQLite</span><span class="sxs-lookup"><span data-stu-id="cd763-217">Install SQLite</span></span>

<span data-ttu-id="cd763-218">在 WSL 上安装 SQLite （Ubuntu 18.04）：</span><span class="sxs-lookup"><span data-stu-id="cd763-218">To install SQLite on WSL (Ubuntu 18.04):</span></span>

1. <span data-ttu-id="cd763-219">打开 WSL 终端（即 Ubuntu 18.04）。</span><span class="sxs-lookup"><span data-stu-id="cd763-219">Open your WSL terminal (ie. Ubuntu 18.04).</span></span>
2. <span data-ttu-id="cd763-220">更新 Ubuntu 包：`sudo apt update`</span><span class="sxs-lookup"><span data-stu-id="cd763-220">Update your Ubuntu packages: `sudo apt update`</span></span>
3. <span data-ttu-id="cd763-221">更新包后，使用以下内容安装 SQLite3：`sudo apt install sqlite3`</span><span class="sxs-lookup"><span data-stu-id="cd763-221">Once the packages have updated, install SQLite3 with: `sudo apt install sqlite3`</span></span>
4. <span data-ttu-id="cd763-222">确认安装并获取版本号：`sqlite3 --version`</span><span class="sxs-lookup"><span data-stu-id="cd763-222">Confirm installation and get the version number: `sqlite3 --version`</span></span>

<span data-ttu-id="cd763-223">若要创建名为 "example" 的测试数据库，请输入：`sqlite3 example.db`</span><span class="sxs-lookup"><span data-stu-id="cd763-223">To create a test database, called "example.db", enter: `sqlite3 example.db`</span></span>

<span data-ttu-id="cd763-224">若要查看 SQLite 数据库的列表，请输入：`.databases`</span><span class="sxs-lookup"><span data-stu-id="cd763-224">To see a list of your SQLite databases, enter: `.databases`</span></span>

<span data-ttu-id="cd763-225">若要查看数据库的状态，请输入：`.dbinfo ?DB?`</span><span class="sxs-lookup"><span data-stu-id="cd763-225">To see the status of your database, enter: `.dbinfo ?DB?`</span></span>

<span data-ttu-id="cd763-226">若要退出 SQLite 提示符，请输入：`.exit`</span><span class="sxs-lookup"><span data-stu-id="cd763-226">To exit the SQLite prompt, enter: `.exit`</span></span>

<span data-ttu-id="cd763-227">有关使用 SQLite 数据库的详细信息，请参阅[SQLite 文档](https://www.sqlite.org/quickstart.html)。</span><span class="sxs-lookup"><span data-stu-id="cd763-227">For more information about working with a SQLite database, see the [SQLite docs](https://www.sqlite.org/quickstart.html).</span></span>

<span data-ttu-id="cd763-228">若要在 VS Code 中使用 SQLite 数据库，请尝试[sqlite 扩展](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools)。</span><span class="sxs-lookup"><span data-stu-id="cd763-228">To work with SQLite databases in VS Code, try the [SQLite extension](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools).</span></span>

## <a name="install-redis"></a><span data-ttu-id="cd763-229">安装 Redis</span><span class="sxs-lookup"><span data-stu-id="cd763-229">Install Redis</span></span>

<span data-ttu-id="cd763-230">在 WSL （Ubuntu 18.04）上安装 Redis：</span><span class="sxs-lookup"><span data-stu-id="cd763-230">To install Redis on WSL (Ubuntu 18.04):</span></span>

1. <span data-ttu-id="cd763-231">打开 WSL 终端（即 Ubuntu 18.04）。</span><span class="sxs-lookup"><span data-stu-id="cd763-231">Open your WSL terminal (ie. Ubuntu 18.04).</span></span>
2. <span data-ttu-id="cd763-232">更新 Ubuntu 包：`sudo apt update`</span><span class="sxs-lookup"><span data-stu-id="cd763-232">Update your Ubuntu packages: `sudo apt update`</span></span>
3. <span data-ttu-id="cd763-233">更新包后，使用以下内容安装 Redis：`sudo apt install redis-server`</span><span class="sxs-lookup"><span data-stu-id="cd763-233">Once the packages have updated, install Redis with: `sudo apt install redis-server`</span></span>
4. <span data-ttu-id="cd763-234">确认安装并获取版本号：`redis-server --version`</span><span class="sxs-lookup"><span data-stu-id="cd763-234">Confirm installation and get the version number: `redis-server --version`</span></span>

<span data-ttu-id="cd763-235">开始运行 Redis 服务器：`sudo service redis-server start`</span><span class="sxs-lookup"><span data-stu-id="cd763-235">To start running your Redis server: `sudo service redis-server start`</span></span>

<span data-ttu-id="cd763-236">查看 redis 是否正在运行（redis 是用于与 Redis 通信的命令行接口实用工具）： `redis-cli ping` 这应返回 "l" 的答复。</span><span class="sxs-lookup"><span data-stu-id="cd763-236">Check to see if redis is working (redis-cli is the command line interface utility to talk with Redis): `redis-cli ping` this should return a reply of "PONG".</span></span>

<span data-ttu-id="cd763-237">停止运行 Redis 服务器：`sudo service redis-server stop`</span><span class="sxs-lookup"><span data-stu-id="cd763-237">To stop running your Redis server: `sudo service redis-server stop`</span></span>

<span data-ttu-id="cd763-238">有关使用 Redis 数据库的详细信息，请参阅[Redis 文档](https://redis.io/topics/quickstart)。</span><span class="sxs-lookup"><span data-stu-id="cd763-238">For more information about working with a Redis database, see the [Redis docs](https://redis.io/topics/quickstart).</span></span>

<span data-ttu-id="cd763-239">若要在 VS Code 中使用 Redis 数据库，请尝试[Redis 扩展](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-redis-client)。</span><span class="sxs-lookup"><span data-stu-id="cd763-239">To work with Redis databases in VS Code, try the [Redis extension](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-redis-client).</span></span>

## <a name="see-services-running-and-set-up-profile-aliases"></a><span data-ttu-id="cd763-240">查看正在运行的服务并设置配置文件别名</span><span class="sxs-lookup"><span data-stu-id="cd763-240">See services running and set up profile aliases</span></span>

<span data-ttu-id="cd763-241">若要查看当前在 WSL 分发上运行的服务，请输入：`service --status-all`</span><span class="sxs-lookup"><span data-stu-id="cd763-241">To see the services that you currently have running on your WSL distribution, enter: `service --status-all`</span></span>

<span data-ttu-id="cd763-242">键入 `sudo service mongodb start` 或 `sudo service postgres start` 和 `sudo -u postgrest psql` 可能会很繁琐。</span><span class="sxs-lookup"><span data-stu-id="cd763-242">Typing out `sudo service mongodb start` or `sudo service postgres start` and `sudo -u postgrest psql` can get tedious.</span></span>  <span data-ttu-id="cd763-243">但是，你可以考虑在 WSL 上的 `.profile` 文件中设置别名，使这些命令更便于使用、易于记忆。</span><span class="sxs-lookup"><span data-stu-id="cd763-243">However, you could consider setting up aliases in your `.profile` file on WSL to make these commands quicker to use and easier to remember.</span></span>

<span data-ttu-id="cd763-244">要设置自己的自定义别名或快捷方式来执行这些命令，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="cd763-244">To set up your own custom alias, or shortcut, for executing these commands:</span></span>

1. <span data-ttu-id="cd763-245">打开 WSL 终端并输入 `cd ~`以确保位于根目录中。</span><span class="sxs-lookup"><span data-stu-id="cd763-245">Open your WSL terminal and enter `cd ~` to be sure you're in the root directory.</span></span>
2. <span data-ttu-id="cd763-246">使用终端文本编辑器 Nano 打开 `.profile` 文件，该文件可控制终端的设置：`sudo nano .profile`</span><span class="sxs-lookup"><span data-stu-id="cd763-246">Open the `.profile` file, which controls the settings for your terminal, with the terminal text editor, Nano: `sudo nano .profile`</span></span>
3. <span data-ttu-id="cd763-247">在文件底部（请勿更改 `# set PATH` 设置），添加以下内容：</span><span class="sxs-lookup"><span data-stu-id="cd763-247">At the bottom of the file (don't change the `# set PATH` settings), add the following:</span></span>

    ```bash
    # My Aliases
    alias start-pg='sudo service postgresql start'
    alias run-pg='sudo -u postgres psql'
    ```

    <span data-ttu-id="cd763-248">这样你就可以输入 `start-pg` 开始运行 postgresql 服务，并输入 `run-pg` 来打开 psql shell。</span><span class="sxs-lookup"><span data-stu-id="cd763-248">This will allow you to enter `start-pg` to start running the postgresql service and `run-pg` to open the psql shell.</span></span> <span data-ttu-id="cd763-249">`start-pg` 和 `run-pg` 可更改为所需的任何名称，但是请注意不要覆盖 postgres 已经使用的命令！</span><span class="sxs-lookup"><span data-stu-id="cd763-249">You can change `start-pg` and `run-pg` to whatever names you want, just be careful not to overwrite a command that postgres already uses!</span></span>

4. <span data-ttu-id="cd763-250">添加新别名后，请使用 Ctrl + X 退出 Nano 文本编辑器 - 系统提示“保存并输入”时选择 `Y`（是）（将文件名保留为 `.profile`）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cd763-250">Once you've added your new aliases, exit the Nano text editor using **Ctrl+X** -- select `Y` (Yes) when prompted to save and Enter (leaving the file name as `.profile`).</span></span>
5. <span data-ttu-id="cd763-251">关闭并重新打开 WSL 终端，然后尝试使用新的别名命令。</span><span class="sxs-lookup"><span data-stu-id="cd763-251">Close and re-open your WSL terminal, then try your new alias commands.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cd763-252">其他资源</span><span class="sxs-lookup"><span data-stu-id="cd763-252">Additional resources</span></span>

- [<span data-ttu-id="cd763-253">在 Windows 10 上设置开发环境</span><span class="sxs-lookup"><span data-stu-id="cd763-253">Setting up your development environment on Windows 10</span></span>](https://docs.microsoft.com/windows/dev-environment/)
