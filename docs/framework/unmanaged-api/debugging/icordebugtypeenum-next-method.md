---
title: ICorDebugTypeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 78ea76033b0b83c84446e16fb330bd3ba34c6e21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725701"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="89678-102">ICorDebugTypeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="89678-102">ICorDebugTypeEnum::Next Method</span></span>

<span data-ttu-id="89678-103">Obtient le nombre d’instances « ICorDebugType » spécifiées par `celt` à partir de l’énumération, en démarrant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="89678-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89678-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89678-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89678-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89678-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="89678-106">dans Nombre d' `ICorDebugType` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="89678-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="89678-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugType` objet.</span><span class="sxs-lookup"><span data-stu-id="89678-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="89678-108">à Pointeur vers le nombre d' `ICorDebugType` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="89678-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="89678-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="89678-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89678-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="89678-110">Requirements</span></span>  

 <span data-ttu-id="89678-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89678-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89678-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89678-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89678-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89678-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89678-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89678-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89678-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89678-115">See also</span></span>
