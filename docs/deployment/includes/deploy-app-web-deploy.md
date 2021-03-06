---
title: 使用 Web 部署的部署
description: 部署在 Visual Studio 中使用 Web 部署的应用
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38811913"
---
如果您安装了 Web 部署使用 Web 平台安装程序，可以部署应用程序直接从 Visual Studio。

1. 使用管理员权限启动 Visual Studio 并重新打开该项目。

    使用 Web 部署将应用部署需要管理员权限。

1. 在“解决方案资源管理器” 中，右键单击项目节点并选择“发布” 。

    如果你以前配置了任何发布配置文件，**发布**窗格会显示。 单击**新的配置文件**。

1. 有关**选择发布目标**，选择**IIS、 FTP 等**然后单击**发布**。

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. 输入你的 IIS 设置更正配置参数。

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    如果主机名不能解决当你尝试验证在下一步中的步骤**Server**文字框中，请尝试使用 IP 地址。 包括`http://`作为前缀**Server**字段。  请确保使用中的端口 80 **Server**文字框中，并确保端口 80 和端口 8172 在防火墙中打开。

1. 选择**验证**。 如果连接安装程序会验证，您可以尝试发布。

1. 单击**发布**以发布应用。

    输出选项卡显示你是否发布已成功，并在浏览器然后打开应用。

    如果你收到一提的是 Web 部署错误，重新检查 Web 部署安装步骤，请确保正确的端口处于打开状态 （Web 部署还需要端口 8172 要在服务器上打开）。

    如果应用程序部署成功，但无法正常运行，可能有您的 IIS 配置、 ASP.NET 安装或你的 Web 站点配置存在问题。 在 Windows 服务器上，更具体的错误消息，从 IIS 中打开该网站，然后重新检查前面的步骤。
