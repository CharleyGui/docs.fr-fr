---
title: ICorDebugValueEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ae09b4f1cd069edf81be583c7c4226717736094
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764278"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="3459e-102">ICorDebugValueEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="3459e-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="3459e-103">Obtient le nombre spécifié d’instances de « ICorDebugValue » à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="3459e-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3459e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3459e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3459e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3459e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3459e-106">[in] Le nombre de `ICorDebugValue` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="3459e-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="3459e-107">[out] Un tableau de pointeurs, chacun d’eux pointe vers un `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="3459e-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3459e-108">[out] Pointeur vers le nombre de `ICorDebugValue` instances réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="3459e-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="3459e-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="3459e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3459e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3459e-110">Requirements</span></span>  
 <span data-ttu-id="3459e-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3459e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3459e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3459e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3459e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3459e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3459e-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3459e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3459e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3459e-115">See also</span></span>
