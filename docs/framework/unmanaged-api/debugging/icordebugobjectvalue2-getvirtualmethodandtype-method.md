---
title: ICorDebugObjectValue2::GetVirtualMethodAndType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue2.GetVirtualMethodAndType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type:
- apiref
ms.openlocfilehash: 2a74688b90fbce63c9107d9389ddfd7bf5cd717b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695177"
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a><span data-ttu-id="7b908-102">ICorDebugObjectValue2::GetVirtualMethodAndType, méthode</span><span class="sxs-lookup"><span data-stu-id="7b908-102">ICorDebugObjectValue2::GetVirtualMethodAndType Method</span></span>

<span data-ttu-id="7b908-103">Cette méthode n'est pas encore implémentée.</span><span class="sxs-lookup"><span data-stu-id="7b908-103">This method is not yet implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b908-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b908-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b908-105">Notes</span><span class="sxs-lookup"><span data-stu-id="7b908-105">Remarks</span></span>  

 <span data-ttu-id="7b908-106">Obtient des pointeurs d’interface vers les instances « ICorDebugFunction » et « ICorDebugType » qui représentent la méthode et le type les plus dérivés pour la référence de membre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7b908-106">Gets interface pointers to the "ICorDebugFunction" and "ICorDebugType" instances that represent the most derived method and type for the specified member reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b908-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b908-107">See also</span></span>
