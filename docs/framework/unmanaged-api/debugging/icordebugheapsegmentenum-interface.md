---
title: ICorDebugHeapSegmentEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138447"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="5896a-102">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="5896a-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="5896a-103">Fournit un énumérateur pour les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="5896a-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="5896a-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5896a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5896a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5896a-105">Methods</span></span>  
  
|<span data-ttu-id="5896a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="5896a-106">Method</span></span>|<span data-ttu-id="5896a-107">Description</span><span class="sxs-lookup"><span data-stu-id="5896a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5896a-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="5896a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="5896a-109">Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) qui contiennent des informations sur les régions du tas managé.</span><span class="sxs-lookup"><span data-stu-id="5896a-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5896a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="5896a-110">Remarks</span></span>  
 <span data-ttu-id="5896a-111">L’interface `ICorDebugHeapSegmentEnum` implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="5896a-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="5896a-112">Une instance de `ICorDebugHeapSegmentEnum` est remplie avec des instances [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) en appelant la méthode [ICorDebugProcess5 :: enumerateheapregions,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5896a-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="5896a-113">Les objets [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapsegmentenum, :: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5896a-113">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="5896a-114">Un objet de collection `ICorDebugHeapSegmentEnum` énumère toutes les régions de mémoire qui peuvent contenir des objets managés, mais il ne garantit pas que les objets managés résident réellement dans ces régions.</span><span class="sxs-lookup"><span data-stu-id="5896a-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="5896a-115">Elle peut inclure des informations sur les régions de mémoire vides ou réservées.</span><span class="sxs-lookup"><span data-stu-id="5896a-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5896a-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="5896a-116">Requirements</span></span>  
 <span data-ttu-id="5896a-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5896a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5896a-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5896a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5896a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5896a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5896a-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5896a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5896a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5896a-121">See also</span></span>

- [<span data-ttu-id="5896a-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5896a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
