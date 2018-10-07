---
title: 表达式计算 (Visual Studio 调试 SDK) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd5fb9ac88b2535c897978cdd63f9cf0716d53a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47477983"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>表达式计算 (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[表达式计算 (Visual Studio Debugging SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk)。  
  
在中断模式下，IDE 必须能够对涉及的应用程序的多个变量的简单表达式求值。 若要完成此操作，调试引擎 (DE) 必须能够分析和计算表达式，用于输入到其中一个 IDE 的窗口。  
  
 使用创建表达式[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法并被生成由[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口。  
  
 **IDebugExpression2**接口实现通过 DE 并调用其**EvalAsync**方法以返回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)到 IDE 中，以便显示接口在 IDE 中的表达式评估结果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)返回可用于将表达式的值放到监视窗口或局部变量窗口的结构。  
  
 调试包或会话调试管理器 (SDM) 调用[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)若要获取[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示接口计算的结果。 `IDebugProperty2` 已返回名称、 类型和表达式的值的方法。 在不同的调试器窗口中显示此信息。  
  
## <a name="using-expression-evaluation"></a>使用表达式计算  
 若要使用表达式计算，必须实现[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法和所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)接口，如以下表中所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以异步方式计算表达式。|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|结束异步表达式求值。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式计算表达式。|  
  
 同步和异步评估需要实现[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 异步表达式计算需要实现[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>请参阅  
 [执行控件和状态计算](../../extensibility/debugger/execution-control-and-state-evaluation.md)
