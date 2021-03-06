---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ea79a27b933380bcfc9e21add841b3a5fc6beeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103053"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
创建断点，已绑定到此事件上的一个枚举的器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumBoundBreakpoints(   
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumBoundBreakpoints(   
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>参数  
 `ppEnum`  
 [out]返回[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)从此事件绑定枚举所有断点的对象。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`。 返回`S_FALSE`是否存在任何绑定的断点; 否则，返回错误代码。  
  
## <a name="remarks"></a>备注  
 对绑定断点列表为绑定到此事件的那些，并且可能不是绑定从挂起断点的断点的整个列表。 若要获取绑定到挂起断点的所有断点的列表，调用[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)方法以获取关联[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)对象，然后调用[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)方法以获取[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)包含挂起断点的绑定的所有断点的对象。  
  
## <a name="example"></a>示例  
 下面的示例演示如何实现此方法对于**CBreakpointSetDebugEventBase**公开的对象[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)接口。  
  
```cpp  
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(  
    IEnumDebugBoundBreakpoints2 **ppEnum)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppEnum )  
    {  
        if ( m_pEnumBound )  
        {  
            hRes = m_pEnumBound->Clone(ppEnum);  
  
            if ( EVAL(S_OK == hRes) )  
                (*ppEnum)->Reset();  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)