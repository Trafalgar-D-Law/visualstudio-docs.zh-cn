---
title: OPTNAMECHANGEPFN |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ecb80b1ac0b71de935da59d29a3f5c39f85bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137240"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
这是对的调用中指定的回调函数[SccSetOption](../extensibility/sccsetoption-function.md) (使用选项`SCC_OPT_NAMECHANGEPFN`) 和用于通信名称所做的更改源代码管理插件回 IDE。  
  
## <a name="signature"></a>签名  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>参数  
 pvCallerData  
 [in]在以前调用中指定的用户值[SccSetOption](../extensibility/sccsetoption-function.md) (使用选项`SCC_OPT_USERDATA`)。  
  
 pszOldName  
 [in]原始文件的名称。  
  
 pszNewName  
 [in]文件的名称已重命名为。  
  
## <a name="return-value"></a>返回值  
 无。  
  
## <a name="remarks"></a>备注  
 如果在源代码管理操作期间重命名文件时，源代码管理插件可以通知有关通过此回调的名称更改 IDE。  
  
 如果 IDE 不支持此回调，它将调用[SccSetOption](../extensibility/sccsetoption-function.md)指定它。 如果该插件不支持此回调，它将返回`SCC_E_OPNOTSUPPORTED`从`SccSetOption`在 IDE 尝试设置回调时正常工作。  
  
## <a name="see-also"></a>另请参阅  
 [由 IDE 实现的回调函数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)