---
title: ICorDebugProcess5::EnumerateHeapRegions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792402"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="0dcef-102">ICorDebugProcess5::EnumerateHeapRegions, méthode</span><span class="sxs-lookup"><span data-stu-id="0dcef-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="0dcef-103">Obtient un énumérateur pour les plages de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="0dcef-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dcef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dcef-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dcef-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0dcef-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="0dcef-106">à Pointeur vers l’adresse d’un objet d’interface [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) qui est un énumérateur pour les plages de mémoire dans lesquelles les objets résident dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0dcef-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dcef-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0dcef-107">Remarks</span></span>  
 <span data-ttu-id="0dcef-108">Avant d’appeler la méthode `ICorDebugProcess5::EnumerateHeapRegions`, vous devez appeler la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) et examiner la valeur du champ `areGCStructuresValid` de l’objet [COR_HEAPINFO](cor-heapinfo-structure.md) retourné pour vous assurer que le segment de mémoire garbage collection dans son état actuel est énumérable.</span><span class="sxs-lookup"><span data-stu-id="0dcef-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="0dcef-109">En outre, la méthode `ICorDebugProcess5::EnumerateHeapRegions` retourne `E_FAIL` si vous attachez trop tôt au cours de la durée de vie du processus, avant que les régions de la mémoire ne soient créées.</span><span class="sxs-lookup"><span data-stu-id="0dcef-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="0dcef-110">Cette méthode permet d’énumérer toutes les régions de mémoire qui peuvent contenir des objets managés, mais elle ne garantit pas que les objets managés résident réellement dans ces régions.</span><span class="sxs-lookup"><span data-stu-id="0dcef-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="0dcef-111">L’objet de collection [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) peut inclure des régions de mémoire vides ou réservées.</span><span class="sxs-lookup"><span data-stu-id="0dcef-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="0dcef-112">L’objet d’interface [icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md) est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer des objets [COR_SEGMENT](cor-segment-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0dcef-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="0dcef-113">Chaque objet [COR_SEGMENT](cor-segment-structure.md) fournit des informations sur la plage de mémoire d’un segment particulier, ainsi que la génération des objets dans ce segment.</span><span class="sxs-lookup"><span data-stu-id="0dcef-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dcef-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0dcef-114">Requirements</span></span>  
 <span data-ttu-id="0dcef-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dcef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dcef-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dcef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dcef-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dcef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dcef-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dcef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dcef-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dcef-119">See also</span></span>

- [<span data-ttu-id="0dcef-120">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="0dcef-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="0dcef-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0dcef-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
