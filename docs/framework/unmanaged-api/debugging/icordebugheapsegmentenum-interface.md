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
ms.openlocfilehash: acf490895db35af1c5d0d1e7fe7e3de5ae2a16b6
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904284"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="6c2f0-102">ICorDebugHeapSegmentEnum, interface</span><span class="sxs-lookup"><span data-stu-id="6c2f0-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="6c2f0-103">Fournit un énumérateur pour les régions de mémoire du tas managé.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="6c2f0-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c2f0-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6c2f0-105">Methods</span></span>  
  
|<span data-ttu-id="6c2f0-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="6c2f0-106">Method</span></span>|<span data-ttu-id="6c2f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="6c2f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c2f0-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="6c2f0-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="6c2f0-109">Obtient le nombre spécifié d’instances de [COR_SEGMENT](cor-segment-structure.md) qui contiennent des informations sur les régions du tas managé.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-109">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c2f0-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6c2f0-110">Remarks</span></span>  
 <span data-ttu-id="6c2f0-111">L' `ICorDebugHeapSegmentEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6c2f0-112">Une `ICorDebugHeapSegmentEnum` instance est remplie avec [COR_SEGMENT](cor-segment-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerateheapregions,](icordebugprocess5-enumerateheapregions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c2f0-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="6c2f0-113">Les objets [COR_SEGMENT](cor-segment-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapsegmentenum, :: Next](icordebugheapsegmentenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c2f0-113">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="6c2f0-114">Un `ICorDebugHeapSegmentEnum` objet collection énumère toutes les régions de mémoire qui peuvent contenir des objets managés, mais il ne garantit pas que les objets managés résident réellement dans ces régions.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="6c2f0-115">Elle peut inclure des informations sur les régions de mémoire vides ou réservées.</span><span class="sxs-lookup"><span data-stu-id="6c2f0-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c2f0-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c2f0-116">Requirements</span></span>  
 <span data-ttu-id="6c2f0-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c2f0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c2f0-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c2f0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c2f0-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c2f0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c2f0-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c2f0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c2f0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c2f0-121">See also</span></span>

- [<span data-ttu-id="6c2f0-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6c2f0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
