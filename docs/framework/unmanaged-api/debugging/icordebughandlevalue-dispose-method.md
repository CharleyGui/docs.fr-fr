---
title: ICorDebugHandleValue::Dispose, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue.Dispose
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue::Dispose
helpviewer_keywords:
- ICorDebugHandleValue::Dispose method [.NET Framework debugging]
- Dispose method [.NET Framework debugging]
ms.assetid: c1542811-0a7f-4235-bcfd-b24370d6f24b
topic_type:
- apiref
ms.openlocfilehash: dc24afd8f78a900ea52539bf9dcb522287223c4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705629"
---
# <a name="icordebughandlevaluedispose-method"></a><span data-ttu-id="81985-102">ICorDebugHandleValue::Dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="81985-102">ICorDebugHandleValue::Dispose Method</span></span>

<span data-ttu-id="81985-103">Libère le handle référencé par cet objet ICorDebugHandleValue sans libérer explicitement le pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="81985-103">Releases the handle referenced by this ICorDebugHandleValue object without explicitly releasing the interface pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81985-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81985-104">Syntax</span></span>  
  
```cpp  
HRESULT Dispose ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="81985-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81985-105">Requirements</span></span>  

 <span data-ttu-id="81985-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81985-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81985-107">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81985-107">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81985-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81985-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81985-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81985-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
