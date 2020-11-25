---
title: ICorDebugFunction2::GetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 747f165a98dfd1264ea58d61aaa1615c6d71e073
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726289"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="11f83-102">ICorDebugFunction2::GetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="11f83-102">ICorDebugFunction2::GetJMCStatus Method</span></span>

<span data-ttu-id="11f83-103">Obtient une valeur qui indique si la fonction représentée par cet objet ICorDebugFunction2 est marquée en tant que code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="11f83-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11f83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f83-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11f83-105">Parameters</span></span>  

 `pbIsJustMyCode`  
 <span data-ttu-id="11f83-106">à Pointeur vers une valeur booléenne qui est `true` , si cette fonction est marquée comme code utilisateur ; sinon, la valeur est `false` .</span><span class="sxs-lookup"><span data-stu-id="11f83-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11f83-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="11f83-107">Remarks</span></span>  

 <span data-ttu-id="11f83-108">Si la fonction représentée par `ICorDebugFunction2` ne peut pas être déboguée, `pbIsJustMyCode` sera toujours `false` .</span><span class="sxs-lookup"><span data-stu-id="11f83-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f83-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="11f83-109">Requirements</span></span>  

 <span data-ttu-id="11f83-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f83-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f83-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11f83-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11f83-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11f83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11f83-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
