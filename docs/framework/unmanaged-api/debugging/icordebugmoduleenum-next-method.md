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
ms.openlocfilehash: d7ad4a6b25fe6d53ab0b21066345451ae7c22c16
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213320"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="8ff64-102">ICorDebugModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="8ff64-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="8ff64-103">Obtient le nombre d’instances « ICorDebugModule » spécifiées par `celt` à partir de l’énumération, en démarrant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="8ff64-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ff64-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ff64-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ff64-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8ff64-106">dans Nombre d' `ICorDebugModule` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="8ff64-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="8ff64-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugModule` objet.</span><span class="sxs-lookup"><span data-stu-id="8ff64-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8ff64-108">à Pointeur vers le nombre d' `ICorDebugModule` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="8ff64-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="8ff64-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="8ff64-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff64-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8ff64-110">Requirements</span></span>  
 <span data-ttu-id="8ff64-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff64-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff64-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ff64-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ff64-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ff64-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ff64-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff64-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ff64-115">See also</span></span>
