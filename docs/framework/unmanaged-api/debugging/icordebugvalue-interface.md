---
title: ICorDebugValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791136"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="23a9a-102">ICorDebugValue, interface</span><span class="sxs-lookup"><span data-stu-id="23a9a-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="23a9a-103">Représente une valeur dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="23a9a-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="23a9a-104">La valeur peut être une valeur de lecture ou d’écriture.</span><span class="sxs-lookup"><span data-stu-id="23a9a-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23a9a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="23a9a-105">Methods</span></span>  
  
|<span data-ttu-id="23a9a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="23a9a-106">Method</span></span>|<span data-ttu-id="23a9a-107">Description</span><span class="sxs-lookup"><span data-stu-id="23a9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23a9a-108">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="23a9a-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="23a9a-109">Cette méthode n'est pas implémentée à l'heure actuelle.</span><span class="sxs-lookup"><span data-stu-id="23a9a-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="23a9a-110">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="23a9a-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="23a9a-111">Obtient l’adresse de cet objet `ICorDebugValue`, qui est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="23a9a-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="23a9a-112">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="23a9a-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="23a9a-113">Obtient la taille, en octets, de cet objet `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="23a9a-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="23a9a-114">GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="23a9a-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="23a9a-115">Obtient le type primitif de cet objet `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="23a9a-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23a9a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="23a9a-116">Remarks</span></span>  
 <span data-ttu-id="23a9a-117">En général, la propriété d’un objet de valeur est passée lorsqu’elle est retournée.</span><span class="sxs-lookup"><span data-stu-id="23a9a-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="23a9a-118">Le destinataire est responsable de la suppression d’une référence de l’objet lorsqu’il est terminé avec l’objet.</span><span class="sxs-lookup"><span data-stu-id="23a9a-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="23a9a-119">Selon l’emplacement à partir duquel la valeur a été récupérée, la valeur peut ne pas rester valide après la reprise du processus.</span><span class="sxs-lookup"><span data-stu-id="23a9a-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="23a9a-120">Ainsi, en général, la valeur ne doit pas être maintenue à travers un appel de la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="23a9a-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23a9a-121">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="23a9a-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a9a-122">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="23a9a-122">Requirements</span></span>  
 <span data-ttu-id="23a9a-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a9a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a9a-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23a9a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23a9a-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23a9a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23a9a-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a9a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a9a-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23a9a-127">See also</span></span>

- [<span data-ttu-id="23a9a-128">ICorDebugValue3, interface</span><span class="sxs-lookup"><span data-stu-id="23a9a-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="23a9a-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="23a9a-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
