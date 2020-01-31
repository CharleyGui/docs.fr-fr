---
title: ICorDebugHeapEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794434"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="83a95-102">ICorDebugHeapEnum, interface</span><span class="sxs-lookup"><span data-stu-id="83a95-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="83a95-103">Fournit un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="83a95-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="83a95-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="83a95-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83a95-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="83a95-105">Methods</span></span>  
  
|<span data-ttu-id="83a95-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="83a95-106">Method</span></span>|<span data-ttu-id="83a95-107">Description</span><span class="sxs-lookup"><span data-stu-id="83a95-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83a95-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="83a95-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="83a95-109">Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="83a95-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83a95-110">Notes</span><span class="sxs-lookup"><span data-stu-id="83a95-110">Remarks</span></span>  
 <span data-ttu-id="83a95-111">L’interface `ICorDebugHeapEnum` implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="83a95-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="83a95-112">Une instance de `ICorDebugHeapEnum` est remplie avec [COR_HEAPOBJECT](cor-heapobject-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83a95-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="83a95-113">Chaque [COR_HEAPOBJECT](cor-heapobject-structure.md) instance de la collection représente soit un objet actif sur le tas, soit un objet qui n’est associé à aucun objet, mais n’a pas encore été collecté par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="83a95-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="83a95-114">Les objets [COR_HEAPOBJECT](cor-heapobject-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapenum, :: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83a95-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a95-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="83a95-115">Requirements</span></span>  
 <span data-ttu-id="83a95-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a95-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a95-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83a95-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83a95-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83a95-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83a95-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a95-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a95-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83a95-120">See also</span></span>

- [<span data-ttu-id="83a95-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="83a95-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
