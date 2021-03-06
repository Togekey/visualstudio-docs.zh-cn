---
title: CA2102：在常规处理程序中捕捉非 CLSCompliant 异常 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521298"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102:在常规处理程序中捕捉非 CLSCompliant 异常
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|项|值|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|类别|Microsoft.Security|
|是否重大更改|不间断|

## <a name="cause"></a>原因
 未标记为或的程序集中的成员 <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> 被标记为 `RuntimeCompatibility(WrapNonExceptionThrows = false)` 包含一个 catch 块，该 catch 块处理 <xref:System.Exception?displayProperty=fullName> 并且不包含立即遵循的常规 catch 块。 此规则将忽略 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 程序集。

## <a name="rule-description"></a>规则描述
 处理捕获 <xref:System.Exception> 所有符合公共语言规范（CLS）的异常的 catch 块。 但是，它不会捕获不符合 CLS 的异常。 不符合 CLS 的异常可以从本机代码或 Microsoft 中间语言（MSIL）组装器生成的托管代码中引发。 请注意，c # 和 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 编译器不允许引发不符合 cls 的异常，且不 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 会捕获不符合 cls 的异常。 如果 catch 块的目的是处理所有异常，请使用以下常规 catch 块语法。

- C#：`catch {}`

- C + +： `catch(...) {}` 或`catch(Object^) {}`

  在 catch 块中删除以前允许的权限时，未处理的不符合 CLS 的异常会成为安全问题。 由于不会捕获不符合 CLS 的异常，导致不符合 CLS 的异常的恶意方法可以使用提升的权限运行。

## <a name="how-to-fix-violations"></a>如何解决冲突
 若要修复此规则的冲突，请在此目的是捕获所有异常时，替换或添加常规 catch 块或标记程序集 `RuntimeCompatibility(WrapNonExceptionThrows = true)` 。 如果在 catch 块中删除了权限，请在常规 catch 块中复制该功能。 如果不是处理所有异常的意图，请将处理的 catch 块替换 <xref:System.Exception> 为处理特定异常类型的 catch 块。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告
 如果 try 块不包含任何可能生成不符合 CLS 的异常的语句，则可以安全地禁止显示此规则发出的警告。 由于任何本机或托管代码可能会引发不符合 CLS 的异常，因此这需要了解可以在 try 块内的所有代码路径中执行的所有代码。 请注意，公共语言运行时不会引发不符合 CLS 的异常。

## <a name="example"></a>示例
 下面的示例演示引发了不符合 CLS 的异常的 MSIL 类。

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>示例
 下面的示例演示一个方法，该方法包含满足规则的常规 catch 块。

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 按如下所示编译前面的示例。

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>相关规则
 [CA1031:不要捕捉一般异常类型](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>另请参阅
 [异常和异常处理](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe （IL 汇编程序）](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [覆盖安全检查](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28)[语言独立性和与语言无关的组件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
