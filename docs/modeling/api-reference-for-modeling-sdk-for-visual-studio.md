---
title: Visual Studio 的建模 SDK 的 API 参考
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7db208bf19f0a2433d4c85af7710a0f5ac70562e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947854"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Visual Studio 的建模 SDK 的 API 参考

Visual Studio 可视化和建模 SDK 提供了在其生成你的域特定语言 (DSL) 工具的平台。

本部分包含具有与"Microsoft.VisualStudio.Modeling"开头的名称的命名空间的参考资料。

|命名空间|内容|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|例如，模型元素，是在 DSL 中定义的所有域类的基类的类。|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|窗体 DSL 定义的一部分的类。|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|模型存储查看器和性能度量工具。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|如 ShapeElement，是在 DSL 中定义的所有形状的基类的类。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|笔势和所选内容的方法。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL 定义设计器的 API。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL 定义设计器的内部类。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|允许你扩展具有命令、 笔势和验证 DSL 设计器的属性。|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|实现 DSL 扩展性的扩展方法的模型元素。|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|扩展属性|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|能让你将模型的各个部分，只读的。|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus API，它可以帮助您将集成不同的模型。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|对话框中，从而让用户导航到模型和元素来创建 Modelbus 引用。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|选取器服务中。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Visual Studio 的 Modelbus 适配器框架。|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|选取器对话框中让用户能导航到模型和元素来创建 Modelbus 引用。|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl 和 Visual Studio 之间的接口。|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|你可以定义快捷 （上下文） 菜单命令。|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|你可以定义验证约束。|

## <a name="see-also"></a>请参阅

- [自定义 T4 文本转换](../modeling/customizing-t4-text-transformation.md)
