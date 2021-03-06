---
title: 所需的更改，运行你迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 项目
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 53a6b138509648af102a50217a8bab4d32b27a2a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693911"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>所需的更改，运行你迁移到.NET Framework 4 或.NET Framework 4.5 的 Office 项目
  如果将 Office 项目的目标框架更改为[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更高版本从.NET Framework 的早期版本，必须执行以下任务以确保在开发计算机和最终用户计算机上可以运行该解决方案：  
  
-   删除项目中的 <xref:System.Security.SecurityTransparentAttribute>如果从 Visual Studio 2008 升级它）。  
  
-   执行**清理**能够运行或调试开发计算机上的项目的 Visual Studio 中的命令。  
  
-   更新项目的 .NET Framework 必备组件。  
  
-   如果以前通过在更改目标框架之前使用 ClickOnce 部署解决方案，则最终用户还必须重新安装该解决方案。  
  
 有关上述每个任务的详细信息，请参阅以下相应章节。  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>从 Visual Studio 2008 升级的项目中移除的 SecurityTransparent 属性  
 如果从 Visual Studio 2008 升级 Office project 项目，且项目的目标框架随后更改为 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则必须从项目中删除 <xref:System.Security.SecurityTransparentAttribute>。 Visual Studio 不会为你自动删除此属性。 如果不删除此属性，则编译项目时将收到一条错误消息。  
  
 有关 Visual Studio 可以在其中更改到升级后的项目的目标框架的条件的详细信息[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，请参阅[升级和迁移 Office 解决方案](../vsto/upgrading-and-migrating-office-solutions.md)。  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>若要删除 SecurityTransparentAttribute  
  
1.  在 Visual Studio 中打开项目后，打开 **“解决方案资源管理器”**。  
  
2.  在 C# 的 **“属性”** 节点或在 Visual Basic 的 **“我的项目”** 节点下，双击 AssemblyInfo 代码文件以在代码编辑器中打开它。  
  
    > [!NOTE]  
    >  在 Visual Basic 项目中，必须单击 **“解决方案资源管理器”** 中的 **“显示所有文件”** 按钮，才能查看 AssemblyInfo 代码文件。  
  
3.  找到 <xref:System.Security.SecurityTransparentAttribute> 并且将其从文件中删除或注释掉。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>执行清理命令以便调试或运行开发计算机上的项目  
 如果生成 Office 项目时之前的项目的目标框架更改为,[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更高版本，则必须执行**清理**命令，然后在更改目标框架后重新生成项目。 如果不执行**清理**命令时，你将收到<xref:System.Runtime.InteropServices.COMException>当你尝试调试或运行重定目标的项目。  
  
 有关详细信息**清理**命令，请参阅[生成 Office 解决方案](../vsto/building-office-solutions.md)。  
  
## <a name="update-the-prerequisites-for-deployment"></a>更新部署的先决条件  
 当你重定向到 Office 项目[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或更高版本，则还必须更新中相应的.NET Framework 必备组件**先决条件**对话框。 否则，ClickOnce 部署或 InstallShield Limited Edition 项目将检查并安装 .NET Framework 的早期版本。  
  
 有关最终用户计算机更新部署的先决条件的详细信息，请参阅[How to： 若要运行 Office 解决方案的最终用户计算机上安装必备组件](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)。  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>在最终用户计算机上重新安装解决方案  
 如果使用 ClickOnce 部署面向 .NET Framework 3.5 的 Office 解决方案，然后将项目重新定位到 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更高版本，则最终用户必须卸载解决方案，然后在发布解决方案后进行重新安装。 如果重新发布重定目标的解决方案，并且最终用户计算机上已更新该解决方案，则最终用户在运行已更新解决方案时将收到 <xref:System.Runtime.InteropServices.COMException>。  
  
## <a name="see-also"></a>请参阅  
 [迁移 Office 解决方案迁移到.NET Framework 4 或更高版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  