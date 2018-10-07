---
title: CA2232： 使用 STAThread 标记 Windows 窗体入口点 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9345009b889b3c382ce0030c34b547a8fd337e0e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587491"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232：使用 STAThread 标记 Windows 窗体的入口点
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[CA2232： 使用 STAThread 标记 Windows 窗体的入口点](https://docs.microsoft.com/visualstudio/code-quality/ca2232-mark-windows-forms-entry-points-with-stathread)。

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因
 程序集引用<xref:System.Windows.Forms>命名空间和其入口点未标有<xref:System.STAThreadAttribute?displayProperty=fullName>属性。

## <a name="rule-description"></a>规则说明
 <xref:System.STAThreadAttribute> 指示 COM 线程模型为该应用程序是单线程单元。 使用 Windows 窗体的任何应用程序的入口点上必须存在此特性；如果没有此特性，则 Windows 组件可能无法正常工作。 如果该属性不存在，该应用程序使用多线程的单元模型不支持为 Windows 窗体。

> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 使用应用程序框架的项目，无需将标记**Main**使用 STAThread 方法。 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]编译器自动执行。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请添加<xref:System.STAThreadAttribute>的入口点的属性。 如果<xref:System.MTAThreadAttribute?displayProperty=fullName>属性存在，将其删除。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 则可以安全地禁止显示此规则的警告，如果要为其开发为.NET Compact Framework，<xref:System.STAThreadAttribute>属性是不必要的不受支持。

## <a name="example"></a>示例
 下面的示例演示的正确用法<xref:System.STAThreadAttribute>。

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]


