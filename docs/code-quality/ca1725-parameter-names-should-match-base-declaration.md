---
title: CA1725：参数名应与基方法中的声明保持一致
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3564f3713dd24488e71703e902ae63f09b6aa74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914336"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725：参数名应与基方法中的声明保持一致
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|类别|Microsoft.Naming|
|是否重大更改|重大|

## <a name="cause"></a>原因
 外部可见方法替代中的参数的名称与该方法中，与基声明或方法的接口声明中参数的名称中的参数的名称不匹配。

## <a name="rule-description"></a>规则说明
 以一致的方式命名重写层次结构中的参数可以提高方法重写的可用性。 如果派生方法中的参数名与基声明中的名称不同，可能会导致无法区分出该方法是基方法的重写还是该方法的新重载。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复与此规则的冲突，重命名的参数以匹配与基声明。 解决方法是一项重大更改对 COM 可见方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 不要禁止显示此规则除外以前发布的库中的 COM 可见方法的警告。