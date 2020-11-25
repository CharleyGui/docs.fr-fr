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
ms.openlocfilehash: a4bdac42c584d5d34b072354de65ed20c6a80609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709490"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="f8f88-102">ICorDebugModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f8f88-102">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="f8f88-103">Obtient le nombre d’instances « ICorDebugModule » spécifiées par `celt` à partir de l’énumération, en démarrant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="f8f88-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8f88-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8f88-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8f88-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f8f88-106">dans Nombre d' `ICorDebugModule` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f8f88-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="f8f88-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugModule` objet.</span><span class="sxs-lookup"><span data-stu-id="f8f88-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f8f88-108">à Pointeur vers le nombre d' `ICorDebugModule` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="f8f88-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="f8f88-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="f8f88-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f88-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8f88-110">Requirements</span></span>  

 <span data-ttu-id="f8f88-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f88-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f88-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8f88-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8f88-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8f88-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8f88-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f88-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f88-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8f88-115">See also</span></span>
