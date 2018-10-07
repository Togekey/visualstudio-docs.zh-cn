---
title: IDebugProperty3::CreateObjectID |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f5b7ca39a36bafe2ebba838c7f6d03f89e2f8132
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "47478041"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主题的最新版本，请参阅[IDebugProperty3::CreateObjectID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-createobjectid)。  
  
创建此属性的唯一 ID，以确保它是唯一的而所有其他属性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 当会话调试管理器想要确保此属性唯一地标识在所有其他属性之间时，调用此方法。 调试引擎 (DE) 支持此方法，除非已唯一标识它可以处理的属性。 如果设备不支持此方法，它将返回`E_NOTIMPL`。  
  
 使用创建的任何唯一 ID`CreateObjectID`时销毁[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)调用方法; 这也表示用于唯一地标识此属性需要的结束。  
  
> [!NOTE]
>  没有方法来检索此唯一 ID，因此 DE 可以随意的唯一 Id 时`CreateObjectID`调用方法。  
  
## <a name="see-also"></a>请参阅  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
