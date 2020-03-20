---
title: ICorDebugObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: e9b32980a5606629676549905d3c9956633f25b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178699"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="6fb2b-102">ICorDebugObjectEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="6fb2b-102">ICorDebugObjectEnum::Next Method</span></span>
<span data-ttu-id="6fb2b-103">Obtient les adresses virtuelles relatives (RVAs) du nombre spécifié d’objets de l’énumération, à partir de la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="6fb2b-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fb2b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb2b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6fb2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6fb2b-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="6fb2b-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6fb2b-107">[out] Un tableau de pointeurs, chacun pointant vers un objet CORDB_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="6fb2b-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6fb2b-108">[out] Pointeur sur le nombre d’objets effectivement retournés.</span><span class="sxs-lookup"><span data-stu-id="6fb2b-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="6fb2b-109">Cette valeur peut `celt` être nulle si elle en est une.</span><span class="sxs-lookup"><span data-stu-id="6fb2b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb2b-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fb2b-110">Requirements</span></span>  
 <span data-ttu-id="6fb2b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb2b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb2b-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fb2b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fb2b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fb2b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb2b-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb2b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb2b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fb2b-115">See also</span></span>
