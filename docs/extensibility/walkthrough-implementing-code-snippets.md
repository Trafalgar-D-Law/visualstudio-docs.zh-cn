---
title: 演练： 实现代码段 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae260951160bc3d4ed3bb1535f47eb1f33649957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148683"
---
# <a name="walkthrough-implementing-code-snippets"></a>演练： 实现代码段
可以创建代码段，并将其包含的编辑器扩展中，以便扩展的用户可以将它们添加到其自己的代码。  
  
 代码片段是一段代码或其他可以在文件中包含的文本。 若要查看已为特定的编程语言中注册的所有代码段**工具**菜单上，单击**代码片段管理器**。 若要在文件中，右键单击想代码段中，在其中插入代码段单击**插入代码段**或**侧**，找到所需的代码段，并双击它。 按 TAB 或 SHIFT + TAB 修改代码段的相关部分，然后按 ENTER 或 esc 键来接受它。 有关详细信息，请参阅[代码片段](../ide/code-snippets.md)。  
  
 代码段包含在具有.snippet 文件扩展名的 XML 文件中。 一个代码段可以包含，以便用户可以查找并将其更改插入代码段后将突出显示的字段。 代码段文件还提供了有关**代码片段管理器**以便它可以显示正确的类别中的代码段名称。 有关代码段架构的信息，请参阅[代码片段架构参考](../ide/code-snippets-schema-reference.md)。  
  
 本演练介绍如何完成这些任务：  
  
1.  创建和注册的特定语言的代码段。  
  
2.  添加**插入代码段**向快捷菜单命令。  
  
3.  实现代码段扩展。  
  
 本演练基于[演练： 显示语句结束](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
## <a name="prerequisites"></a>系统必备  
 从 Visual Studio 2015 开始，你并不安装 Visual Studio SDK 从下载中心。 它将包括作为 Visual Studio 安装程序中的可选功能。 你还可以在以后安装 VS SDK。 有关详细信息，请参阅[安装 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="creating-and-registering-code-snippets"></a>创建和注册代码段  
 通常情况下，代码片段是与已注册的语言服务相关联。 但是，不需要实现<xref:Microsoft.VisualStudio.Package.LanguageService>注册代码段。 相反，只需在代码段的索引文件中指定一个 GUID，然后使用中的相同 GUID<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>添加到你的项目。  
  
 以下步骤演示如何创建代码段，并将其与特定 GUID 关联。  
  
1.  创建以下目录结构：  
  
     **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
     其中 *%installdir%* 是 Visual Studio 安装文件夹。 （尽管此路径通常用于安装代码段，但你可以指定任意路径）。  
  
2.  在 \1033\ 文件夹中，创建一个.xml 文件，并将其命名**TestSnippets.xml**。 （此名称通常用于代码段索引文件，尽管你可以指定任何名称，只要它具有.xml 作为文件扩展名。）添加以下文本，然后删除占位符 GUID 并添加您自己。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <SnippetCollection>  
        <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
            <SnippetDir>  
                <OnOff>On</OnOff>  
                <Installed>true</Installed>  
                <Locale>1033</Locale>  
                <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
                <LocalizedName>Snippets</LocalizedName>  
            </SnippetDir>  
        </Language>  
    </SnippetCollection>  
    ```  
  
3.  代码段文件夹中创建的文件，将其命名为**测试**`.snippet`，然后添加以下文本：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
        <CodeSnippet Format="1.0.0">  
            <Header>  
                <Title>Test replacement fields</Title>  
                <Shortcut>test</Shortcut>  
                <Description>Code snippet for testing replacement fields</Description>  
                <Author>MSIT</Author>  
                <SnippetTypes>  
                    <SnippetType>Expansion</SnippetType>  
                </SnippetTypes>  
            </Header>  
            <Snippet>  
                <Declarations>  
                    <Literal>  
                      <ID>param1</ID>  
                        <ToolTip>First field</ToolTip>  
                        <Default>first</Default>  
                    </Literal>  
                    <Literal>  
                        <ID>param2</ID>  
                        <ToolTip>Second field</ToolTip>  
                        <Default>second</Default>  
                    </Literal>  
                </Declarations>  
                <References>  
                   <Reference>  
                       <Assembly>System.Windows.Forms.dll</Assembly>  
                   </Reference>  
                </References>  
                <Code Language="TestSnippets">  
                    <![CDATA[MessageBox.Show("$param1$");  
         MessageBox.Show("$param2$");]]>  
                </Code>    
            </Snippet>  
        </CodeSnippet>  
    </CodeSnippets>  
    ```  
  
 以下步骤显示如何注册的代码段。  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>若要为特定 GUID 注册代码段  
  
1.  打开**CompletionTest**项目。 有关如何创建此项目的信息，请参阅[演练： 显示语句结束](../extensibility/walkthrough-displaying-statement-completion.md)。  
  
2.  在项目中，添加对以下程序集的引用：  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   microsoft.msxml  
  
3.  在项目中，打开 source.extension.vsixmanifest 文件。  
  
4.  请确保**资产**选项卡包含**VsPackage**内容类型，且**项目**设置为项目的名称。  
  
5.  选择 CompletionTest 项目，然后在属性窗口中设置**生成 Pkgdef 文件**到**true**。 保存项目。  
  
6.  添加静态`SnippetUtilities`到项目的类。  
  
     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  在 SnippetUtilities 类中，定义 GUID 并为其提供 SnippetsIndex.xml 文件中使用的值。  
  
     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  添加<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>到`TestCompletionHandler`类。 此属性可以添加到项目中任何公共或内部 （非静态） 类。 (你可能需要添加`using`Microsoft.VisualStudio.Shell 命名空间的语句。)  
  
     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. 生成并运行该项目。 在启动时运行该项目的 Visual Studio 的实验实例中，你只需注册的代码段应显示在**代码片段管理器**下**TestSnippets**语言。  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>将插入代码段命令添加到快捷菜单  
 **插入代码段**命令中未包括的文本文件的快捷菜单。 因此，你必须启用该命令。  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>若要添加到快捷菜单插入代码段命令  
  
1.  打开`TestCompletionCommandHandler`类文件。  
  
     因为此类实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>，可以激活**插入代码段**命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法。 启用命令之前，请检查，因为在自动化函数没有调用此方法时**插入代码段**单击命令，因此它将显示代码段选择器用户界面 (UI)。  
  
     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  生成并运行该项目。 在实验实例中，打开具有.zzz 文件扩展名的文件，然后右键单击任意位置它。 **插入代码段**命令应显示在快捷菜单。  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>在代码段选择器 UI 中实现代码段扩展  
 本部分演示如何实现代码段扩展，以使代码段选择器 UI 时，所显示**插入代码段**的快捷菜单上单击。 当用户类型的代码的代码片段快捷方式，然后按 TAB，也会扩展代码片段。  
  
 若要显示代码段选择器 UI 并启用导航并后插入代码片段接受，使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 由插入操作本身<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>方法。  
  
 代码段扩展的实现使用旧<xref:Microsoft.VisualStudio.TextManager.Interop>接口。 当你将转换的当前编辑器类为旧代码时，记住的旧接口使用行号和列号的组合来指定文本缓冲区中的位置，但当前类使用一个索引。 因此，如果缓冲区中具有每个都有 10 个字符的三行 （加上换行符，计为 1 个字符），第三行的第四个字符位于位置 27 在当前实现中，但它位于第 2 行，则放置 3 中以前的实现。  
  
#### <a name="to-implement-snippet-expansion"></a>若要实现代码段扩展  
  
1.  包含的文件到`TestCompletionCommandHandler`类中，添加以下`using`语句。  
  
     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  请`TestCompletionCommandHandler`类实现<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>接口。  
  
     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  在`TestCompletionCommandHandlerProvider`类中，导入<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>。  
  
     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  添加代码扩展接口的一些私有字段和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  构造函数中`TestCompletionCommandHandler`类中，设置以下字段。  
  
     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  用户单击时显示代码段选择器**插入代码段**命令，添加以下代码到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 （若要使此说明更具可读性，用于语句完成 exec （） 代码将不显示; 相反，将代码块添加到现有的方法。）检查的字符的代码后面添加以下代码块。  
  
     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  如果一个代码段具有字段可以进行导航，扩展会话保持打开状态直到显式接受扩展;代码段不包含任何字段，如果会话关闭，并且作为返回`null`通过<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A>方法。 在<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法，代码段选择器在以前步骤中，添加的 UI 代码之后添加以下代码以处理段导航 （当用户在代码段插入后按 TAB 或 SHIFT + TAB）。  
  
     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  若要插入代码段时用户类型的相应的快捷方式，然后按选项卡上，将代码添加到<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>方法。 插入代码段的私有方法将在稍后的步骤所示。 在上一步中添加的导航代码后面添加以下代码。  
  
     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. 实现方法的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient>接口。 在此实现中，感兴趣的唯一方法是<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>。 其他方法应只返回<xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. 实现 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> 方法。 将在稍后的步骤中介绍用于实际将扩展的帮助器方法。 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>提供行和列信息，你可以从获取<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。  
  
     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. 以下私有方法将插入代码段中，基于的快捷方式，也可以位于的标题和路径。 然后，它调用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A>与该代码段的方法。  
  
     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>生成和测试代码段扩展  
 你可以测试是否在你的项目中工作的代码段扩展。  
  
1.  生成解决方案。 在调试器中运行此项目时，Visual Studio 的第二个实例将进行实例化。  
  
2.  打开一个文本文件，并键入一些文本。  
  
3.  在文本中的任意位置右键单击，然后单击**插入代码段**。  
  
4.  代码段选择器的 UI 应显示一个弹出窗口，指出与**测试替换字段**。 双击弹出窗口。  
  
     应插入以下代码段。  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     不要按 ENTER 或 esc 键。  
  
5.  按选项卡并按 SHIFT + TAB 切换"第一个"和"第二个"之间。  
  
6.  通过按 ENTER 或 esc 键接受插入。  
  
7.  在不同的文本部分中，键入"测试"，然后按选项卡。 由于"test"的代码的代码片段快捷方式，应再次插入代码段。  
  
## <a name="next-steps"></a>后续步骤