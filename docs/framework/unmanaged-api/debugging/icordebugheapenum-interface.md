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
ms.openlocfilehash: ff290cd8ad331ff109c3bbbf87638d22b9b183bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208536"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="bf01b-102">ICorDebugHeapEnum, interface</span><span class="sxs-lookup"><span data-stu-id="bf01b-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="bf01b-103">Fournit un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="bf01b-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="bf01b-104">Cette interface est une sous-classe de l'interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bf01b-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf01b-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bf01b-105">Methods</span></span>  
  
|<span data-ttu-id="bf01b-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="bf01b-106">Method</span></span>|<span data-ttu-id="bf01b-107">Description</span><span class="sxs-lookup"><span data-stu-id="bf01b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf01b-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="bf01b-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="bf01b-109">Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="bf01b-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf01b-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf01b-110">Remarks</span></span>  
 <span data-ttu-id="bf01b-111">L' `ICorDebugHeapEnum` interface implémente l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bf01b-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="bf01b-112">Une `ICorDebugHeapEnum` instance est remplie avec [COR_HEAPOBJECT](cor-heapobject-structure.md) instances en appelant la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf01b-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="bf01b-113">Chaque [COR_HEAPOBJECT](cor-heapobject-structure.md) instance de la collection représente soit un objet actif sur le tas, soit un objet qui n’est associé à aucun objet, mais n’a pas encore été collecté par le récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="bf01b-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="bf01b-114">Les objets [COR_HEAPOBJECT](cor-heapobject-structure.md) de la collection peuvent être énumérés en appelant la méthode [Icordebugheapenum, :: Next](icordebugheapenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf01b-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf01b-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf01b-115">Requirements</span></span>  
 <span data-ttu-id="bf01b-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf01b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf01b-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf01b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf01b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf01b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf01b-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf01b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf01b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf01b-120">See also</span></span>

- [<span data-ttu-id="bf01b-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bf01b-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
