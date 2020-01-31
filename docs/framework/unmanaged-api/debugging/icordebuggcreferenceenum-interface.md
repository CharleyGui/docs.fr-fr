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
ms.openlocfilehash: f01c27376191c3a2dddf56dae4b26c8b5193c73e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788641"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="d4c99-102">ICorDebugGCReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="d4c99-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="d4c99-103">Fournit un énumérateur pour les objets qui sont récupérés par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d4c99-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4c99-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d4c99-104">Methods</span></span>  
  
|<span data-ttu-id="d4c99-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d4c99-105">Method</span></span>|<span data-ttu-id="d4c99-106">Description</span><span class="sxs-lookup"><span data-stu-id="d4c99-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4c99-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d4c99-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="d4c99-108">Obtient le nombre spécifié d’instances de [COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui feront l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d4c99-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4c99-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d4c99-109">Remarks</span></span>  
 <span data-ttu-id="d4c99-110">L’interface `ICorDebugGCReferenceEnum` implémente l’interface « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="d4c99-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="d4c99-111">Une instance de `ICorDebugGCReferenceEnum` est remplie avec [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerategcreferences,](icordebugprocess5-enumerategcreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4c99-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="d4c99-112">Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) peuvent être énumérés en appelant la méthode [ICorDebugGCReference :: Next](icordebuggcreferenceenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d4c99-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="d4c99-113">Les objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) dans la collection remplie par cette méthode représentent trois types d’objets :</span><span class="sxs-lookup"><span data-stu-id="d4c99-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="d4c99-114">Objets de toutes les piles managées.</span><span class="sxs-lookup"><span data-stu-id="d4c99-114">Objects from all managed stacks.</span></span> <span data-ttu-id="d4c99-115">Cela comprend les références dynamiques en code managé, ainsi que les objets créés par l’common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d4c99-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="d4c99-116">Objets de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="d4c99-116">Objects from the handle table.</span></span> <span data-ttu-id="d4c99-117">Cela comprend des références fortes (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et des variables statiques dans un module.</span><span class="sxs-lookup"><span data-stu-id="d4c99-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="d4c99-118">Objets de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="d4c99-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="d4c99-119">Le finaliseur met les objets racine en file d’attente jusqu’à l’exécution du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="d4c99-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4c99-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d4c99-120">Requirements</span></span>  
 <span data-ttu-id="d4c99-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4c99-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4c99-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4c99-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4c99-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4c99-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4c99-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4c99-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c99-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4c99-125">See also</span></span>

- [<span data-ttu-id="d4c99-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d4c99-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
