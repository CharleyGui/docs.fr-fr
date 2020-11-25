---
title: ICorDebugGCReferenceEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 12ce800cb83ef4f79710aa441b50be860526023c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728119"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="dbfe6-102">ICorDebugGCReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="dbfe6-102">ICorDebugGCReferenceEnum Interface</span></span>

<span data-ttu-id="dbfe6-103">Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbfe6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dbfe6-104">Methods</span></span>  
  
|<span data-ttu-id="dbfe6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="dbfe6-105">Method</span></span>|<span data-ttu-id="dbfe6-106">Description</span><span class="sxs-lookup"><span data-stu-id="dbfe6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbfe6-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="dbfe6-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="dbfe6-108">Obtient le nombre spécifié d’instances de [COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui feront l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbfe6-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbfe6-109">Remarks</span></span>  

 <span data-ttu-id="dbfe6-110">L' `ICorDebugGCReferenceEnum` interface implémente l’interface « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="dbfe6-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="dbfe6-111">Une `ICorDebugGCReferenceEnum` instance est remplie avec [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerategcreferences,](icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dbfe6-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="dbfe6-112">Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) peuvent être énumérés en appelant la méthode [ICorDebugGCReference :: Next](icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dbfe6-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="dbfe6-113">Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) dans la collection remplie par cette méthode représentent trois types d’objets :</span><span class="sxs-lookup"><span data-stu-id="dbfe6-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="dbfe6-114">Objets de toutes les piles managées.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-114">Objects from all managed stacks.</span></span> <span data-ttu-id="dbfe6-115">Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="dbfe6-116">Objets de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-116">Objects from the handle table.</span></span> <span data-ttu-id="dbfe6-117">Cela comprend des références fortes ( `HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT` ) et des variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="dbfe6-118">Objets de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="dbfe6-119">Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="dbfe6-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbfe6-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dbfe6-120">Requirements</span></span>  

 <span data-ttu-id="dbfe6-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbfe6-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbfe6-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbfe6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbfe6-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbfe6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbfe6-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbfe6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbfe6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbfe6-125">See also</span></span>

- [<span data-ttu-id="dbfe6-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dbfe6-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
