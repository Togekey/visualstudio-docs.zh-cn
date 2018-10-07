---
title: 项目模型的元素 |Microsoft Docs
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
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3c26bb501e28c324233e4991fc8023b2adcdcf6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47482848"
---
# <a name="elements-of-a-project-model"></a>项目模型的元素
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[的项目模型元素](https://docs.microsoft.com/visualstudio/extensibility/internals/elements-of-a-project-model)。  
  
接口和实现中的所有项目[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]共享的基本结构： 你的项目类型的项目模型。 在你的项目模型中，这是你正在开发的 VSPackage，你将创建符合您的设计决策，并且由 IDE 提供全局功能协同工作的对象。 尽管您控制如何保持项目项，例如，您不控制通知必须保留一个文件。 当用户将焦点放置于打开项目项上，选择**保存**上**文件**菜单上的[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]菜单栏中，你的项目类型代码必须截获从 IDE 命令，保存该文件，并发送通知到 IDE 的文件不能再更改。  
  
 你的 VSPackage 与 IDE 通过提供对 IDE 接口访问的服务进行交互。 例如，通过特定服务，你监视和路由命令并提供在项目中所做选择的上下文信息。 所有全局 IDE 所需的功能为你的 VSPackage 提供的服务。 有关服务的详细信息，请参阅[如何： 获取服务](../../extensibility/how-to-get-a-service.md)。  
  
 其他实现注意事项：  
  
-   单个项目模型可以包含多个项目类型。  
  
-   与 Guid 单独注册项目类型和附随项目工厂。  
  
-   每个项目必须有一个模板文件或向导来初始化新的项目文件，当用户创建新的项目通过[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]UI。 例如，[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]模板初始化什么最终成为.vcproj 文件。  
  
 下图显示了主要接口、 服务和对象组成的典型项目中实现。 应用程序帮助器，HierUtil7，可用于创建基础对象和其他编程的样本。 HierUtil7 应用程序帮助程序的详细信息，请参阅[不在生成： 使用 HierUtil7 项目类以实现项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
 ![Visual Studio 项目模型图](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
项目模型  
  
 有关接口和上图中列出的服务以及其他未包含在关系图中的可选接口的详细信息，请参阅[项目模型核心组件](../../extensibility/internals/project-model-core-components.md)。  
  
 项目可以支持命令，因此必须实现<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>接口来参与命令路由通过命令上下文的 Guid。  
  
## <a name="see-also"></a>请参阅  
 [清单： 创建新的项目类型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在生成： 使用 HierUtil7 项目类来实现一种项目类型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [项目模型核心组件](../../extensibility/internals/project-model-core-components.md)   
 [使用项目工厂创建的项目实例](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [如何： 获取服务](../../extensibility/how-to-get-a-service.md)   
 [创建项目类型](../../extensibility/internals/creating-project-types.md)
