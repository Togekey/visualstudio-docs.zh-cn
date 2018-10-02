---
title: 如何： 强制实现代码使用代码分析签入策略 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97b321fe5a72c6f3ace680476340eca48f7ed309
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47481495"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>如何：使用代码分析签入策略强制实现代码的可维护性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主题的最新版本，请参阅[如何： 使用代码分析签入策略强制实施可维护代码](https://docs.microsoft.com/visualstudio/code-quality/how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy)。  
  
开发人员可以使用代码度量值工具来衡量的复杂性和可维护性的其代码，但不是能调用代码度量值作为签入策略的一部分。 但是，团队可以启用代码分析规则，验证其代码符合代码度量标准和强制实施通过签入策略的规则。 代码度量值的详细信息，请参阅[代码度量值](../code-quality/code-metrics-values.md)。  
  
 开发人员可以实现继承深度、 类耦合、 可维护性指数和复杂性规则以强制实施通过代码分析签入策略可维护的代码。 这些规则的所有四个代码分析策略编辑器中找到"可维护性规则"类别下。  
  
 版本控制的管理员为[!INCLUDE[esprfound](../includes/esprfound-md.md)]可以将代码分析可维护性规则添加到签入策略要求。 这些签入策略要求开发人员运行代码分析签入启动之前基于这些规则的更改。  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>若要打开代码分析策略编辑器  
  
1.  在中**团队资源管理器**，右键单击团队项目，单击**团队项目设置**，然后单击**源代码管理**。  
  
     **源代码管理**对话框随即出现。  
  
2.  上**签入策略**选项卡，然后单击**添加**。  
  
     **添加签入策略**对话框随即出现。  
  
3.  在中**签入策略**列表中，选择**代码分析**复选框，然后依次**确定**。  
  
     **代码分析策略编辑器**对话框随即出现。  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>若要启用代码分析可维护性规则  
  
1.  在中**代码分析策略编辑器**对话框中的**规则设置**，展开**可维护性规则**节点。  
  
2.  选择以下规则对应的复选框：  
  
    -   继承深度： **CA1501 AvoidExcessiveInheritance** -阈值： 警告在 5 个以上级别的深度  
  
    -   复杂性： **CA1502 AvoidExcessiveComplexity** -阈值： 在超过 25 种的警告  
  
    -   可维护性索引： **CA1505 AvoidUnmaintainableCode** -阈值： 少于 20 发出警告  
  
    -   类耦合度： **CA1506 AvoidExcessiveClassCoupling** -阈值： 多个方法，为 30 个禬筁 80 类发出警告  
  
    -   此外，如果你想禁止生成规则冲突，则选择**将警告视为错误**规则说明旁边的复选框。  
  
3.  单击 **“确定”**。 新签入策略现在适用于未来的签入。  
  
## <a name="see-also"></a>请参阅  
 [代码度量值](../code-quality/code-metrics-values.md)   
 [创建和使用代码分析签入策略](../code-quality/creating-and-using-code-analysis-check-in-policies.md)


