---
title: ICorDebugModuleEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b052aac7a71308486676aa688fd5ad655c2015f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765295"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="66a09-102">ICorDebugModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="66a09-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="66a09-103">Obtient le nombre d’instances de « ICorDebugModule » spécifiée par `celt` à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="66a09-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66a09-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66a09-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66a09-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="66a09-106">[in] Le nombre de `ICorDebugModule` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="66a09-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="66a09-107">[out] Un tableau de pointeurs, chacun d’eux pointe vers un `ICorDebugModule` objet.</span><span class="sxs-lookup"><span data-stu-id="66a09-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="66a09-108">[out] Pointeur vers le nombre de `ICorDebugModule` instances réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="66a09-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="66a09-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="66a09-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a09-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66a09-110">Requirements</span></span>  
 <span data-ttu-id="66a09-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a09-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a09-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66a09-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66a09-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a09-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a09-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a09-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a09-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a09-115">See also</span></span>
