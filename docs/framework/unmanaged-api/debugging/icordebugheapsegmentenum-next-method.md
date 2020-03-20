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
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178893"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="f8fe8-102">ICorDebugHeapSegmentEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="f8fe8-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="f8fe8-103">Obtient le nombre spécifié de [cas COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les régions de mémoire du tas géré.</span><span class="sxs-lookup"><span data-stu-id="f8fe8-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8fe8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8fe8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8fe8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8fe8-105">Parameters</span></span>  
 <span data-ttu-id="f8fe8-106">celt</span><span class="sxs-lookup"><span data-stu-id="f8fe8-106">celt</span></span>  
 <span data-ttu-id="f8fe8-107">[dans] Nombre de segments à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f8fe8-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="f8fe8-108">segments</span><span class="sxs-lookup"><span data-stu-id="f8fe8-108">segments</span></span>  
 <span data-ttu-id="f8fe8-109">[out] Un tableau de pointeurs, chacun pointant vers un objet [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur une région de mémoire dans le tas géré.</span><span class="sxs-lookup"><span data-stu-id="f8fe8-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="f8fe8-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f8fe8-110">pceltFetched</span></span>  
 <span data-ttu-id="f8fe8-111">[out] Un pointeur sur [COR_HEAPOBJECT](cor-heapobject-structure.md) le nombre d’objets `segments`COR_HEAPOBJECT effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="f8fe8-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="f8fe8-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="f8fe8-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8fe8-113">Notes </span><span class="sxs-lookup"><span data-stu-id="f8fe8-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8fe8-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8fe8-114">Requirements</span></span>  
 <span data-ttu-id="f8fe8-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8fe8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8fe8-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8fe8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8fe8-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8fe8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8fe8-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8fe8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fe8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8fe8-119">See also</span></span>

- [<span data-ttu-id="f8fe8-120">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f8fe8-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="f8fe8-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f8fe8-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
