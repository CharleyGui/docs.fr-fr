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
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777537"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="0fb4e-102">ICorDebugHeapSegmentEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="0fb4e-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="0fb4e-103">Obtient le nombre spécifié d’instances de [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="0fb4e-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fb4e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fb4e-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0fb4e-105">Parameters</span></span>  
 <span data-ttu-id="0fb4e-106">celt</span><span class="sxs-lookup"><span data-stu-id="0fb4e-106">celt</span></span>  
 <span data-ttu-id="0fb4e-107">dans Nombre de segments à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0fb4e-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="0fb4e-108">segments</span><span class="sxs-lookup"><span data-stu-id="0fb4e-108">segments</span></span>  
 <span data-ttu-id="0fb4e-109">à Tableau de pointeurs, chacun pointant vers un objet [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur une zone de mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0fb4e-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="0fb4e-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="0fb4e-110">pceltFetched</span></span>  
 <span data-ttu-id="0fb4e-111">à Pointeur vers le nombre d’objets [COR_HEAPOBJECT](cor-heapobject-structure.md) réellement retournés dans `segments`.</span><span class="sxs-lookup"><span data-stu-id="0fb4e-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="0fb4e-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="0fb4e-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fb4e-113">Notes</span><span class="sxs-lookup"><span data-stu-id="0fb4e-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fb4e-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0fb4e-114">Requirements</span></span>  
 <span data-ttu-id="0fb4e-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb4e-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fb4e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fb4e-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fb4e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fb4e-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb4e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fb4e-119">See also</span></span>

- [<span data-ttu-id="0fb4e-120">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="0fb4e-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="0fb4e-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0fb4e-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
