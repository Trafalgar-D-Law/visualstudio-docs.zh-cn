---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109670"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
获取给定名称的自定义特性的自定义特性字节。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pszCustomAttributeName`  
 [in]包含要查找的自定义属性的名称的字符串。  
  
 `ppBlob`  
 [在中，out]使用自定义特性字节填充数组。  
  
 `pdwLen`  
 [在中，out]指定的最大返回中的字节数`ppBlob`数组并返回实际写入到该数组的字节数。  
  
## <a name="return-value"></a>返回值  
 如果成功，返回，则为 S_OK，则返回 S_FALSE，如果自定义属性不存在。 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 设置`ppBlob`为 null 值，以返回数量的参数属性可用字节数。 分配一个数组，然后将为该数组中的传递`ppBlob`参数。  
  
 属性字节表示的自定义属性的原始数据。  
  
 如果`ppBlob`和`pdwLen`参数设置为 null 值，可以使用此方法来确定是否只是存在自定义属性。 更容易，但是，也可以调用[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)方法。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)