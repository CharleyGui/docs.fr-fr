---
title: ICorDebugHeapSegmentEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e75a11ec94614b1b9d7bd16acce447a494cdec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756770"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="ab77e-102">ICorDebugHeapSegmentEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="ab77e-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="ab77e-103">Obtient le nombre spécifié de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui contiennent des informations sur les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="ab77e-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab77e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab77e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab77e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab77e-105">Parameters</span></span>  
 <span data-ttu-id="ab77e-106">celt</span><span class="sxs-lookup"><span data-stu-id="ab77e-106">celt</span></span>  
 <span data-ttu-id="ab77e-107">[in] Le nombre de segments à récupérer.</span><span class="sxs-lookup"><span data-stu-id="ab77e-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="ab77e-108">segments</span><span class="sxs-lookup"><span data-stu-id="ab77e-108">segments</span></span>  
 <span data-ttu-id="ab77e-109">[out] Un tableau de pointeurs, chacun d’eux pointe vers un [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objet qui fournit des informations sur une région de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="ab77e-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="ab77e-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="ab77e-110">pceltFetched</span></span>  
 <span data-ttu-id="ab77e-111">[out] Un pointeur vers le nombre de [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) réellement retournés dans des objets `segments`.</span><span class="sxs-lookup"><span data-stu-id="ab77e-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="ab77e-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="ab77e-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab77e-113">Notes</span><span class="sxs-lookup"><span data-stu-id="ab77e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab77e-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab77e-114">Requirements</span></span>  
 <span data-ttu-id="ab77e-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab77e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab77e-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab77e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab77e-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab77e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab77e-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab77e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab77e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab77e-119">See also</span></span>

- [<span data-ttu-id="ab77e-120">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="ab77e-120">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="ab77e-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ab77e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
