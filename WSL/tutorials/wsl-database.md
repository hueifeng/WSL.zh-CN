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
# <a name="get-started-with-databases-on-windows-subsystem-for-linux"></a>适用于 Linux 的 Windows 子系统上的数据库入门

此循序渐进指南将帮助你开始将 WSL 中的项目连接到数据库。 MySQL、PostgreSQL、MongoDB、Redis、Microsoft SQL Server 或 SQLite 入门。

## <a name="prerequisites"></a>先决条件

- 运行 Windows 10（[已更新到版本 2004](ms-settings:windowsupdate) 的**内部版本 19041** 或更高版本）。
- [启用并安装 WSL，并更新为 WSL 2](https://docs.microsoft.com/windows/wsl/install-win10)。
- [已安装 Linux 分发](https://docs.microsoft.com/windows/wsl/install-win10#install-your-linux-distribution-of-choice)版（Ubuntu 18.04，适用于我们的示例）。
- 确保 Ubuntu 18.04 分发[在 WSL 2 模式下运行](https://docs.microsoft.com/windows/wsl/install-win10#set-your-distribution-version-to-wsl-1-or-wsl-2)。 （WSL 可以在 v1 或 v2 模式下运行分发。）可以通过打开 PowerShell 并输入以下内容来进行检查：`wsl -l -v`

## <a name="differences-between-database-systems"></a>数据库系统之间的差异

对于数据库系统，最[常用的选项](https://insights.stackoverflow.com/survey/2019#technology-_-databases)包括：

- [MySQL](https://www.mysql.com/why-mysql/) （SQL）
- [PostgreSQL](https://www.postgresql.org/about/) （SQL）
- [Microsoft SQL Server](https://docs.microsoft.com/sql/?view=sql-server-ver15) （SQL）
- [SQLite](https://www.sqlite.org/about.html) （SQL）
- [MongoDB](https://www.mongodb.com/what-is-mongodb) （NoSQL）
- [Redis](https://redis.io/topics/introduction) （NoSQL）

**MySQL**是一种开源 SQL 关系数据库，将数据组织到一个或多个表中，这些表中的数据类型可能相互相关。 它是可垂直缩放的，这意味着一台终极计算机将为您完成工作。 它目前是四个数据库系统最广泛使用的。

**PostgreSQL** （有时称为 Postgres）也是开源 SQL 关系数据库，重点介绍扩展性和标准符合性。 现在，它也可以处理 JSON，但通常更适合处理结构化数据、进行垂直缩放以及符合 ACID 的需求，例如电子商务和金融交易。

**Microsoft SQL Server**包括 SQL Server Windows、Linux 上的 SQL Server 和 Azure 上的 SQL。 它们也是在服务器上设置的关系数据库管理系统，其主要功能是按软件应用程序的要求存储和检索数据。

**SQLite**是开源自包含的、基于文件的 "无服务器" 数据库，其可移植性、可靠性和良好性能，即使在低内存环境中也是如此。

**MongoDB**是一种开源 NoSQL 文档数据库，旨在使用 JSON 并存储无架构的数据。 它可以水平缩放，这意味着多个小型计算机将为你完成工作。 它适用于灵活性和非结构化数据，并缓存实时分析。

**Redis**是一个开源 NoSQL 内存中数据结构存储区。 它为存储而不是文档使用键值对。 Redis 被认为是其灵活性、性能和广泛的语言支持。 它非常灵活，可以用作缓存或消息代理，并且可以使用数据结构（如列表、集和哈希）。

选择的数据库类型应取决于将使用该数据库的应用程序的类型。 我们建议你查看结构化和非结构化数据库的优点和缺点，并根据用例进行选择。

## <a name="install-mysql"></a>安装 MySQL

在 WSL 上安装 MySQL （Ubuntu 18.04）：

1. 打开 WSL 终端（即 Ubuntu 18.04）。
2. 更新 Ubuntu 包：`sudo apt update`
3. 更新包后，使用以下内容安装 MySQL：`sudo apt install mysql-server`
4. 确认安装并获取版本号：`mysql --version`

你可能还需要运行包含的安全脚本。 这会更改远程根登录名和示例用户之类的一些安全默认选项。 运行安全脚本：

1. 启动 MySQL server：`sudo /etc/init.d/mysql start`
2. 启动安全脚本提示：`sudo mysql_secure_installation`
3. 第一个提示将询问你是否要设置 "验证密码" 插件，该插件可用于测试 MySQL 密码的强度。 然后，你将为 MySQL 根用户设置密码，决定是否要删除匿名用户，决定是否允许根用户本地和远程登录，确定是否要删除测试数据库，最后确定是否要立即重新加载特权表。

若要打开 MySQL 提示符，请输入：`sudo mysql`

若要查看可用数据库，请在 MySQL 提示符下输入：`SHOW DATABASES;`

若要创建新数据库，请输入：`CREATE DATABASE database_name;`

若要删除数据库，请输入：` DROP DATABASE database_name;`

有关使用 MySQL 数据库的详细信息，请参阅[mysql 文档](https://dev.mysql.com/doc/mysql-getting-started/en/)。

若要在 VS Code 中使用 MySQL 数据库，请尝试[mysql 扩展](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-mysql-client2)。

## <a name="install-postgresql"></a>安装 PostgreSQL

在 WSL （Ubuntu 18.04）上安装 PostgreSQL：

1. 打开 WSL 终端（即 Ubuntu 18.04）。
2. 更新 Ubuntu 包：`sudo apt update`
3. 更新该包后，使用以下命令安装 PostgreSQL（和 -contrib 包，其中包含一些有用的实用程序）：`sudo apt install postgresql postgresql-contrib`
4. 确认安装并获取版本号：`psql --version`

安装 PostgreSQL 后，需要知道以下 3 个命令：

- `sudo service postgresql status` 用于检查数据库的状态。
- `sudo service postgresql start` 用于开始运行数据库。
- `sudo service postgresql stop` 用于停止运行数据库。

默认管理员用户 `postgres` 需要分配的密码才能连接到数据库。 要设置密码，请执行以下操作：

1. 输入命令：`sudo passwd postgres`
2. 系统将提示你输入新密码。
3. 关闭并重新打开终端。

若要通过[psql](https://www.postgresql.org/docs/10/app-psql.html) Shell 运行 PostgreSQL：

1. 启动 postgres 服务：`sudo service postgresql start`
2. 连接到 postgres 服务，并打开 psql shell：`sudo -u postgres psql`

成功输入 psql shell 后，将显示更改为如下所示的命令行：`postgres=#`

> [!NOTE]
> 或者，也可以通过使用 `su - postgres` 切换为 postgres 用户，然后输入命令 `psql` 来打开 psql shell。

若要退出 postgres = # enter： `\q` 或使用快捷键： Ctrl + D

要查看在 PostgreSQL 安装上创建的用户帐户，请在 WSL 终端上使用 `psql -c "\du"`；如果已打开 psql shell，则仅使用 `\du`。 此命令将显示列：帐户用户名、角色列表和角色组的成员。 要返回命令行，请输入：`q`。

有关使用 PostgreSQL 数据库的详细信息，请参阅[PostgreSQL 文档](https://www.postgresql.org/docs/13/tutorial-createdb.html)。

若要在 VS Code 中使用 PostgreSQL 数据库，请尝试[PostgreSQL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-ossdata.vscode-postgresql)。

## <a name="install-mongodb"></a>安装 MongoDB

在 WSL 上安装 MongoDB （Ubuntu 18.04）：

1. 打开 WSL 终端（即 Ubuntu 18.04）。
2. 更新 Ubuntu 包：`sudo apt update`
3. 更新该包后，使用以下命令安装 MongoDB：`sudo apt-get install mongodb`
4. 确认安装并获取版本号：`mongod --version`

安装 MongoDB 后，需要知道以下 3 个命令：

- `sudo service mongodb status` 用于检查数据库的状态。
- `sudo service mongodb start` 用于开始运行数据库。
- `sudo service mongodb stop` 用于停止运行数据库。

> [!NOTE]
> 你可能会看到在教程或文章中使用了命令 `sudo systemctl status mongodb`。 为了保持轻量，WSL 不包括 `systemd`（Linux 中的服务管理系统）。 它改为使用 SysVinit 在计算机上启动服务。 你应该不会注意到有什么区别，但是如果教程建议使用 `sudo systemctl`，请改用 `sudo /etc/init.d/`。 例如，对于 WSL，`sudo systemctl status mongodb` 应改用 `sudo /etc/inid.d/mongodb status`，或者也可以使用 `sudo service mongodb status`。

若要在本地服务器上运行 Mongo 数据库，请执行以下操作：

1. 检查数据库的状态：除非已 `sudo service mongodb status` 启动数据库，否则应该会看到 [Fail] 响应。

2. 启动数据库： `sudo service mongodb start` 此时应会看到一个 [OK] 响应。

3. 通过连接到数据库服务器并运行诊断命令来验证： `mongo --eval 'db.runCommand({ connectionStatus: 1 })'` 这将输出当前的数据库版本、服务器地址和端口以及状态命令的输出。 响应中“ok”字段的值 `1` 表示服务器正在运行。

4. 要停止运行 MongoDB 服务，请输入：`sudo service mongodb stop`

> [!NOTE]
> MongoDB 有几个默认参数，包括在 /data/db 中存储数据和在端口 27017 上运行。 此外，`mongod` 是守护程序（数据库的主机进程），`mongo` 是连接到特定实例 `mongod` 的命令行 shell。

VS Code 支持通过[Azure CosmosDB 扩展](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb)使用 mongodb 数据库，则可以从 VS Code 中创建、管理和查询 mongodb 数据库。 若要了解详细信息，请访问 VS Code 文档：[使用 MongoDB](https://code.visualstudio.com/docs/azure/mongodb)。

有关详细信息，请参阅 MongoDB 文档：

- [使用 MongoDB 简介](https://docs.mongodb.com/manual/introduction/)
- [创建用户](https://docs.mongodb.com/manual/tutorial/create-users/)
- [连接到远程主机上的 MongoDB 实例](https://docs.mongodb.com/manual/mongo/#mongodb-instance-on-a-remote-host)
- [CRUD：创建、读取、更新、删除](https://docs.mongodb.com/manual/crud/)
- [参考文档](https://docs.mongodb.com/manual/reference/)

## <a name="install-microsoft-sql-server"></a>安装 Microsoft SQL Server

若要在 WSL 上安装 SQL Server （Ubuntu 18.04），请遵循以下快速入门：[在 ubuntu 上安装 SQL Server 并创建数据库](https://docs.microsoft.com/sql/linux/quickstart-install-connect-ubuntu?view=sql-server-ver15)。

若要在 VS Code 中使用 Microsoft SQL Server 数据库，请尝试[MSSQL 扩展](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)。

## <a name="install-sqlite"></a>安装 SQLite

在 WSL 上安装 SQLite （Ubuntu 18.04）：

1. 打开 WSL 终端（即 Ubuntu 18.04）。
2. 更新 Ubuntu 包：`sudo apt update`
3. 更新包后，使用以下内容安装 SQLite3：`sudo apt install sqlite3`
4. 确认安装并获取版本号：`sqlite3 --version`

若要创建名为 "example" 的测试数据库，请输入：`sqlite3 example.db`

若要查看 SQLite 数据库的列表，请输入：`.databases`

若要查看数据库的状态，请输入：`.dbinfo ?DB?`

若要退出 SQLite 提示符，请输入：`.exit`

有关使用 SQLite 数据库的详细信息，请参阅[SQLite 文档](https://www.sqlite.org/quickstart.html)。

若要在 VS Code 中使用 SQLite 数据库，请尝试[sqlite 扩展](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools)。

## <a name="install-redis"></a>安装 Redis

在 WSL （Ubuntu 18.04）上安装 Redis：

1. 打开 WSL 终端（即 Ubuntu 18.04）。
2. 更新 Ubuntu 包：`sudo apt update`
3. 更新包后，使用以下内容安装 Redis：`sudo apt install redis-server`
4. 确认安装并获取版本号：`redis-server --version`

开始运行 Redis 服务器：`sudo service redis-server start`

查看 redis 是否正在运行（redis 是用于与 Redis 通信的命令行接口实用工具）： `redis-cli ping` 这应返回 "l" 的答复。

停止运行 Redis 服务器：`sudo service redis-server stop`

有关使用 Redis 数据库的详细信息，请参阅[Redis 文档](https://redis.io/topics/quickstart)。

若要在 VS Code 中使用 Redis 数据库，请尝试[Redis 扩展](https://marketplace.visualstudio.com/items?itemName=cweijan.vscode-redis-client)。

## <a name="see-services-running-and-set-up-profile-aliases"></a>查看正在运行的服务并设置配置文件别名

若要查看当前在 WSL 分发上运行的服务，请输入：`service --status-all`

键入 `sudo service mongodb start` 或 `sudo service postgres start` 和 `sudo -u postgrest psql` 可能会很繁琐。  但是，你可以考虑在 WSL 上的 `.profile` 文件中设置别名，使这些命令更便于使用、易于记忆。

要设置自己的自定义别名或快捷方式来执行这些命令，请执行以下操作：

1. 打开 WSL 终端并输入 `cd ~`以确保位于根目录中。
2. 使用终端文本编辑器 Nano 打开 `.profile` 文件，该文件可控制终端的设置：`sudo nano .profile`
3. 在文件底部（请勿更改 `# set PATH` 设置），添加以下内容：

    ```bash
    # My Aliases
    alias start-pg='sudo service postgresql start'
    alias run-pg='sudo -u postgres psql'
    ```

    这样你就可以输入 `start-pg` 开始运行 postgresql 服务，并输入 `run-pg` 来打开 psql shell。 `start-pg` 和 `run-pg` 可更改为所需的任何名称，但是请注意不要覆盖 postgres 已经使用的命令！

4. 添加新别名后，请使用 Ctrl + X 退出 Nano 文本编辑器 - 系统提示“保存并输入”时选择 `Y`（是）（将文件名保留为 `.profile`）****。
5. 关闭并重新打开 WSL 终端，然后尝试使用新的别名命令。

## <a name="additional-resources"></a>其他资源

- [在 Windows 10 上设置开发环境](https://docs.microsoft.com/windows/dev-environment/)
