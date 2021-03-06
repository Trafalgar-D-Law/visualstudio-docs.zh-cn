---
title: CA2146：类型必须至少与其基类型和接口一样关键
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a609e765e5c5013ea0903683439f313f7de95017
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917536"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146：类型必须至少与其基类型和接口一样关键
|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|类别|Microsoft.Security|
|是否重大更改|重大|

## <a name="cause"></a>原因
 透明类型派生自类型标记为<xref:System.Security.SecuritySafeCriticalAttribute>或<xref:System.Security.SecurityCriticalAttribute>，或将标有一种<xref:System.Security.SecuritySafeCriticalAttribute>属性派生自类型标记为<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="rule-description"></a>规则说明
 当派生类型具有的安全透明特性与其基类型或实现的接口不是同样关键时，将引发此规则。 只有关键类型可以从关键基类型派生或实现关键接口，并且只有关键或关键安全类型可以从安全关键基类型派生或实现关键安全接口。 2 级透明度中此规则的冲突导致<xref:System.TypeLoadException>派生的类型。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要解决此冲突，标记是至少同样关键时的基类型或接口的透明特性派生或实现类型。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不禁止显示此规则发出的警告。

## <a name="example"></a>示例
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]