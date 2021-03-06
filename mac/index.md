---
title: Visual Studio for Mac 介绍
description: 本文介绍 Visual Studio for Mac 的功能
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 738964deed9aa1e51d5a6e4788879bc3165284a7
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37889880"
---
# <a name="introducing-visual-studio-for-mac"></a>Visual Studio for Mac 介绍

Visual Studio for Mac 是一个新式且复杂的 IDE，内附有多种用于创建移动、桌面和 Web 应用程序的功能。 它支持以下类型的开发：

* .NET 移动应用：Android、iOS、tvOS、watchOS
* Mac 桌面应用
* .NET Core 应用程序
* ASP.NET Core Web 应用程序
* 跨平台 Unity 游戏

它包括丰富的编辑器、调试、与 iOS/Mac/Android 的本机平台集成和集成源控件等功能。

本文探究了 Visual Studio for Mac 的方方面面，还介绍了哪些功能使其成为了一款创建跨平台应用程序的强大工具。

## <a name="installation"></a>安装

按照[安装](installation.md)指南中的步骤下载和安装 Visual Studio for Mac。

## <a name="language-support"></a>语言支持

默认情况下，Visual Studio for Mac 支持以 C# 和 F# 进行的开发。

### <a name="c"></a>C#

在 Visual Studio for Mac 中创建跨平台应用程序时，C# 是最常用的语言。 IDE 对所有 C# 7 功能提供完整支持。

### <a name="f"></a>F#

F# 是强类型函数编程语言，设计为专门用于在 .NET 上运行。 Visual Studio for Mac 用户可在 Android、Mac 和 iOS 上将其用作编程语言。 有关使用 F# 以及查看用该语言创建的示例的详细信息，请访问 [F#](https://developer.xamarin.com/guides/cross-platform/fsharp/) 指南。

## <a name="platform-support"></a>平台支持

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) 平台可创建在 Windows、Linux 和 Mac 上运行的应用程序。 Visual Studio for Mac 支持上传、创建、运行和调试 .NET Core 项目。 

要运行 .NET Core 项目，应该下载和安装 .NET Core SDK。

.NET Core 支持包括：

* C# 和 F# IntelliSense。
* 控制台、库和 Web 应用程序的 .NET Core 项目模板。
* 完整的调试支持，包括断点、调用堆栈、监视窗口等。
* NuGet PackageReferences 和基于 MSBuild 的还原。
* 集成单元测试支持使用 .NET Core SDK 附带的 Visual Studio 测试平台进行运行和调试测试。
* 从旧的 project.json 格式迁移。

要开始，请查看 ASP.NET Core Web 应用[动手实验](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)。

## <a name="xamarin"></a>Xamarin

通过对 [Xamarin](https://developer.xamarin.com/) 的卓越支持，可以开发适用于 Android、macOS、iOS、tvOS 和 watchOS 的丰富本机体验。 使用 Xamarin.Forms 跨平台应用程序可以在 Android、iOS 和 macOS 之间共享基于 XAML 的 UI 代码，而不会限制对本机功能的访问。

要开始，请查看移动应用[动手实验](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started)。

### <a name="android"></a>Android

Visual Studio 有其自己的集成 Android SDK 管理器。

对于 Android 应用程序，Visual Studio for Mac 包含其自己的设计器，该设计器适用于 Android `.axml` 文件来直观地构造用户界面。 Visual Studio for Mac 将在 Android Designer 中打开这些文件，如下图所示：

![Android UI 设计器](media/intro-image31.png)

有关 Android Designer 的详细信息，请参阅 [Designer 概述](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview)文档。

### <a name="ios"></a>iOS

IOS 设计器与 Visual Studio for Mac 完全集成，可进行 .xib 的可视编辑，并使 Storyboard 文件创建 iOS、tvOS 和 WatchOS UI 并转换。 使用直观方法处理事件时，可使用工具箱和 Design Surface 之间的拖放功能生成整个用户界面。 iOS 设计器还支持具有额外的设计时呈现优势的[自定义控件](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/)。

![iOS Storyboard 设计器](media/intro-image30.png)

有关使用 iOS 设计器的详细信息，请参阅[设计器](https://developer.xamarin.com/guides/ios/user_interface/designer)文档。

### <a name="mac"></a>Mac

Xamarin 提供本机 Mac API 绑定，让用户能够创建美观的 Mac 应用程序。

有关使用 Visual Studio for Mac 编写 Mac 应用程序的详细信息，请参阅 [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) 文档。

## <a name="gaming"></a>游戏

Visual Studio for Mac 支持使用 Unity 5.6.1 进行跨平台游戏开发。

要开始，请查看 Unity [动手实验](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started)。

## <a name="enterprise-features"></a>企业功能

> [!Note]
> 这些产品仅可用于 Visual Studio Enterprise 订阅。

### <a name="profiler"></a>探查器

Xamarin Profiler 有三个可用于分析的仪表。 [Xamarin Profiler 简介](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/)指南介绍了这些仪表的度量值以及它们分析应用程序的方式，并阐明了每个屏幕上显示的数据的含义。

### <a name="inspector"></a>检查器

Xamarin Inspector 提供一个具有用户工具的交互式 C# 控制台。 它可在检查实时应用程序时用作调试或诊断辅助，还可用作教学工具、文档工具或实验工具。

![Xamarin Inspector](media/intro-inspector.png)

它包括一个独立应用程序，可提供面向各种编程平台（Android、iOS、Mac 和 Windows）并集成到 IDE 调试工作流的内容丰富的 C# 控制台。 

有关详细信息，请参阅 [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/) 指南。

## <a name="next-steps"></a>后续步骤

* **获取教程** - 若要大致了解 Visual Studio for Mac 中的众多主要功能，请参阅 Visual Studio for Mac [IDE 教程](ide-tour.md)。
* **安装** - 若要了解如何下载和安装 Visual Studio，请参阅[安装](installation.md)指南。
* **Xamarin 教程** - 若要了解有关如何使用 Xamarin 开发代码的详细信息，请转到 Xamarin [开发人员中心](https://developer.xamarin.com)。
* **视频** - 若要了解有关 Visual Studio for Mac 的其他功能和方面，请查看 [Xamarin University](https://university.xamarin.com) 网站上的视频。
* **动手实验** - 若要开始使用 Visual Studio for Mac 中包含的各种工作负载，请查看[动手实验](https://github.com/Microsoft/vs4mac-labs)。
