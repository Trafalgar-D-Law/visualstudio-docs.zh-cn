---
title: 如何： 以编程方式将网页与 Outlook 文件夹相关联
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb1ef525917288dc44609b899611db884da9073
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256460"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>如何： 以编程方式将网页与 Outlook 文件夹相关联
  此示例检查名为`HtmlView`Microsoft Office Outlook 中。 如果文件夹不存在，代码会创建该文件夹，并为其分配到 Web 页。 如果该文件夹存在，代码将显示该文件夹的内容。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>请参阅  
 [使用文件夹](../vsto/working-with-folders.md)   
 [如何： 以编程方式按名称检索文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何： 以编程方式创建自定义文件夹项](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  