---
title: IEnumCodePath2：：重置 |微软文档
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2392c25513b53137e5cdca332bc133ab998be999
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717789"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
将枚举重置为第一个元素。

## <a name="syntax"></a>语法

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>返回值
 如果成功，返回`S_OK`;否则，返回错误代码。

## <a name="remarks"></a>备注
 调用此方法后，[对 Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)方法的下一个调用将返回枚举的第一个元素。

## <a name="see-also"></a>请参阅
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
